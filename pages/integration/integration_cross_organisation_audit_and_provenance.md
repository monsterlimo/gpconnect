---
title: Cross organisation audit and provenance
keywords: spine, ssp, integration, audit, provenance
tags: [integration]
sidebar: overview_sidebar
permalink: integration_cross_organisation_audit_and_provenance.html
summary: "Overview of how audit and provenance data transported over GP Connect FHIR interfaces."
---

## Governance ##

Provider systems SHALL ensure that access to confidential data, including patient or clinical data, through the API must meet, as a minimum, the same requirements for information governance (IG), authentication and authorisation, and auditing as that of the host system the API exposes.

## Audit trail ##

{% include important.html content="As the GP Connect APIs are commissioned under the GPSoC framework, provider and consumer systems are expected to follow the standard 'IG Requirements for GP Systems V4' and 'GP Systems Interface Mechanism' requirements." %}

For implementers that don't have access to the GPSoC Framework / 'IG Requirements for GP Systems V4' requirements then the following extract of requirements covers the main audit trail requirements:

- provider systems SHALL record in an audit trail all access and data changes within the system as a result of API activity in the same way that internal access and changes are required to be recorded

- provider systems SHALL ensure that all API transactions are recorded in an audit trail and that audit trails must be subject to the standard IG audit requirements as defined in 'IG Requirements for GP Systems V4' or as subsequently amended

- provider systems SHALL ensure failed or rejected API transactions are recorded with the same detail as for successful API requests, with error codes as per the [error handling guidance](development_fhir_error_handling_guidance.html)

Audit trail records shall include the following minimum information:

- a record of the user identity - this is the User ID, Name, Role profile (including Role and Organisation, URP id when Smartcard authenticated) attribute values, obtained from the user’s session structure
- a record of the identity of the authority – the person authorising the entry of or access to data (if different from the user)
- the date and time on which the event occurred
- details of the nature of the audited event and the identity of the associated data (for example, patient ID, message ID) of the audited event
- a sequence number to protect against malicious attempts to subvert the audit trail by, for example, altering the system date
- audit trail records should include details of the end-user device (or system) involved in the recorded activity

Audit trails shall be enabled at all times and there shall be no means for users, or any other individuals, to disable any audit trail.

{% include note.html content="Whilst some details (such as name, role) associated with individual users are likely to change over time, the display of user information must reflect the state of such information as it was at the time of the associated event (such as data entry)." %}

## Provenance ##

Provider systems SHALL ensure that all additions, amendments or logical deletions to administrative and clinical data made via an API is clearly identified with information regarding the provenance of the data (such as, timestamp, details of consumer system, details of user (including role)), so it is clear which information has been generated through an API rather than through the provider system itself.

Provider systems SHALL record the following provenance details of all API personal and sensitive personal data recorded within the system:

- author details (identified through unique ID), including name and role
- data entered by (if different from author)
- date and time (to the second) entered
- originating organisation
- API interaction

## Legal processing ##

Provider systems SHALL ensure that data provided to consumer systems only includes data for which the GP practice acts as data controller.


## Patient demographic cross-checking ##

Consumer systems SHALL always perform a patient demographic check as part of the use of a GP Connect capability to ensure that the patient for whom the information has been provided is the same patient for whom the request was made, and make clear to the end user any discrepancies. 

## Use of Bearer tokens ##

Consumer systems SHALL provide audit and provenance details in the HTTP authorisation header as an oAuth Bearer Token as described within the [Spine Core FHIR API Framework Access Tokens and Audit (JWT)](https://nhsconnect.github.io/FHIR-SpineCore/security_jwt.html)


### JWT payload ###

The payload section of the JWT shall be populated as described at [Spine Core FHIR API Framework Access Tokens and Audit (JWT) - Payload](https://nhsconnect.github.io/FHIR-SpineCore/security_jwt.html)

The following points should be noted regarding the GP Connect API specifically:

| Claim | Description |
|-------|----------|
| iss   | As the consuming system is presently responsible for generating the access token, this SHALL contain the URL of the Spine endpoint of the consuming system. |
| sub | Will match requesting_user only until a future Patient Facing capability is implemented |
| reason_for_request | A value of `directcare` only will be valid until a future Patient Facing capability is implemented |
| requesting_user | This claim will will not be valid until a future Patient Facing capability is implemented |

The following additional claim is expected to be included by consumers:

| Claim | Priority | Description | Fixed Value | Dynamic Value |
|-------|----------|-------------|-------------|------------------|
| requested_record | R | A minimal FHIR resource which describes the resource being requested or searched for. | No | NHS Number<sup>1</sup> <br/>OR <br/>Organization identifier<sup>2</sup> |


<sup>1</sup>Naming prefix `http://fhir.nhs.net/Id/nhs-number` to be used
<sup>2</sup>Naming prefix `https://fhir.nhs.uk/Id/ods-organization-code` to be used


#### Population of requested_record ####

The `consumer` SHALL populate the `requested_record` claim with:

* Either a FHIR [Organization](https://www.hl7.org/fhir/STU3/organization.html) ![STU3](images/stu3.png) resource or a FHIR [Patient](https://www.hl7.org/fhir/STU3/patient.html) ![STU3](images/stu3.png) resource which describes the resource being requested or searched for, where possible, and will contain any relevant business identifiers for the request.

  The table below shows some of the GP Connect API interactions and the expected content for the JWT requested_record claim:

  | Request | Known Business Identifiers | requested_record Resource Type | requested_record Content |
  | --- | --- | --- | --- |
  | Access Record HTML | NHS Number | Patient | SHALL contain an identifier element containing the NHS number being passed as a parameter to the `gpc.getcarerecord` operation. |
  | Patient Search | NHS Number | Patient | SHALL contain an identifier element containing the NHS Number being passed as the search parameter of the request. |
  | Patient Read | N/A | Patient | SHOULD contain the logical id of the patient resource being requested. |
  | Organisation Search | ODS Code | Organisation | SHALL contain an identifier element containing the organisation ODS Code which is being passed as the parameter to the search. |
  | Practitioner Search | N/A | Organisation | SHOULD contain any relevant identifier for the organisation on which the FHIR endpoint resides. |
  | Practitioner Read | N/A | Organisation | SHOULD contain any relevant identifier for the organisation on which the FHIR endpoint resides. |
  | Search for free slots | N/A | Organisation | SHOULD contain any relevant identifier for the organisation on which the FHIR endpoint resides. |
  | Book Appointment | NHS Number | Patient | The consumer will have previously used the patients NHS Number to find the patients logical id on the providers system, therefore the requested_record Patient SHOULD contain the NHS number identifier element. |
  | Read Appointment | NHS Number | Patient | The consumer will have previously used the patients NHS Number to find the patients logical id on the providers system, therefore the requested_record Patient SHOULD contain the NHS number identifier element. |
  
  The following identifier sytems SHALL be used when populating the relevant business identifiers:
  
  | Known business identifiers | Relevant business identifiers |
  | --- | --- |
  | NHS number | https://fhir.nhs.uk/Id/nhs-number |
  | ODS code | https://fhir.nhs.uk/Id/ods-organization-code |

  {% include note.html content="The provider SHALL validate that the requested_record claim details match the request parameters where possible, to ensure valid auditing of the requests end-to-end." %}
  

### JWT payload example ###

```json
{
	"iss": "[ConsumerSpineEndpointURL]",
	"sub": "https://fhir.nhs.uk/Id/sds-role-profile-id|[SDSRoleProfileID]",
	"aud": "https://provider.thirdparty.nhs.uk/GP0001/STU3/1",
	"exp": 1519220477,
	"iat": 1519220177,
	"reason_for_request": "directcare",
	"scope": "patient/*.read",
	"requesting_system": "https://fhir.nhs.uk/Id/accredited-system|[ASID]",
	"requesting_organization": "https://fhir.nhs.uk/Id/ods-organization-code|[ODSCode]",
	"requesting_user": "https://fhir.nhs.uk/Id/sds-role-profile-id|[SDSRoleProfileID]",
	"requested_record": http://fhir.nhs.net/Id/nhs-number|6101231234"
	},
}
```

{% include important.html content="Whilst the use of a JWT and the claims naming is inspired by the [SMART on FHIR](https://github.com/smart-on-fhir/smart-on-fhir.github.io/wiki/cross-organizational-auth) the GP Connect programme hasn't committed to using the SMART on FHIR specification." %}

Where the practitioner has both a local system role as well as a Spine RBAC role, then the Spine RBAC role SHALL be supplied.

{% include todo.html content="Spine RBAC role support to be added in [Stage 2.](designprinciples_maturity_model.html)" %}

## Example code ##

### C# ###

{% include tip.html content="The following code snippet utilises the [Microsoft Identity Model JWT Token NuGet Package](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/) for creating, serializing and validating JWT tokens." %}

```C#

using System.Security.Claims;
using System.IdentityModel.Tokens.Jwt;
using System.Collections.Generic;
using System;

[snip]

    const int FIVE_MINUTES = 300;
    TimeSpan t = DateTime.UtcNow - new DateTime(1970, 1, 1);
    int secondsSinceEpoch = (int)t.TotalSeconds;

    var claims = new List<Claim>
    {
         new Claim("iss", "https://https://[ConsumerSpineEndpointURL]", ClaimValueTypes.String),
         new Claim("sub", "https://fhir.nhs.uk/Id/sds-role-profile-id|[SDSRoleProfileID]", ClaimValueTypes.String),
         new Claim("aud", "https://provider.thirdparty.nhs.uk/GP0001/STU3/1", ClaimValueTypes.String),
         new Claim("exp", (secondsSinceEpoch+FIVE_MINUTES).ToString(), ClaimValueTypes.Integer64),
         new Claim("iat", secondsSinceEpoch.ToString(), ClaimValueTypes.Integer64),
         new Claim("reason_for_request", "directcare", ClaimValueTypes.String),
         new Claim("requested_scope", "patient/*.read", ClaimValueTypes.String),
         new Claim("requesting_system", "https://https://[ConsumerSpineEndpointURL", ClaimValueTypes.String),
         new Claim("requesting_organization", "https://fhir.nhs.uk/Id/ods-organization-code|[ODSCode]", ClaimValueTypes.String),
         new Claim("requesting_user", "https://fhir.nhs.uk/Id/sds-role-profile-id|[SDSRoleProfileID]", ClaimValueTypes.String)
     };

     // Serialize To Json
     JwtPayload payload = new JwtPayload(claims);
     string jsonPayload = payload.SerializeToJson();

[snip]

```

## External documents / policy documents ##

| Name | Author | Version | Updated |
| GPSoC IG Requirements for GP Systems | NHS Digital | v4.0 | 19/09/2014 |
| GP Systems Interface Mechanism Requirements V 1| NHS Digital | v0.10|


