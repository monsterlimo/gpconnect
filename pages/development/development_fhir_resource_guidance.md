---
title: FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: development_fhir_resource_guidance.html
summary: "Where to find details of what resources and operations a FHIR server should expose to be a fully compliant GP Connect solution"
---

GP Connect has specified profiled versions of the international [FHIR Resources](https://www.hl7.org/fhir/STU3/){:target="_blank"}, tailoring them to meet the requirements of the GP Connect use cases and to aid in interoperability between systems.

When creating the profiled FHIR resources GP Connect have aimed to improve interoperability by:

* aligning, where possible, to the base FHIR profiles. GP Connect has also aligned, where possible, to the FHIR resource profiles produced by CareConnect and InterOpen
* not making FHIR profile elements mandatory unless absolute certainty that this cardinality will apply for all existing and future use cases
* applying must support flags to elements which hold key information within the resources

The profiled FHIR resources required for each of the GP Connect capability packs are specified within the specific specification sections for each of the capabilities:

* [Foundations](datalibraryfoundation.html)
* [Access Record HTML](accessrecord.html)
* [Access Record Structured](accessrecord_structured_development_resources_overview.html)
* [Appointment Management](datalibraryappointment.html)
* [Task Management](tasks.html)

## General FHIR resource populating requirements

The purpose of GP Connect is to make the patient data stored within the GP systems available externally so that it can be used to help improve the quality of patient care across the NHS. To give patients the best care possible the data made available through the GP Connect API should be as complete as possible. Therefore, it is expected that both provider and consumers:

* ***SHALL*** populate all the elements within FHIR resources subject to any Capability-specific variance, where data is available within their system irrespective of the cardinality of the elements within the FHIR resource profiles.

As GP Connect has made the FHIR resources open to aid in interoperability this means that there are some elements included in FHIR profiles which are not applicable to our deployment settings, for example 'specialism' in the appointment resource. These elements which should not be populated are specified within the specification.

Requirements and guidance for population of resources is divided across the specification to reduce duplication within the specification:
- generic requirements around the populations of element types  within the profile, such as how to populate an address element, is specified on the [FHIR Resource element guidance](fhir_resource_guidance_elements.html)
- generic requirements and guidance for specific resources which is not specific to a single interaction can be found on the resource population guidance pages, these requirements take precidence over the FHIR profile and element population requirements and guidance.
  - [Location FHIR Resource guidance](fhir_resource_guidance_location.html)
  - [Organization FHIR Resource guidance](fhir_resource_guidance_organization.html)
  - [Patient FHIR Resource guidance](fhir_resource_guidance_patient.html)
  - [Practitioner FHIR Resource guidance](fhir_resource_guidance_practitioner.html)
- interaction specific requirements around population of elements is outlined within the API use case pages within the capability pages. Interaction specific requirements take precidence over the generic resource and element population guidance and requirements.


### Use of Must-Support flag

Some resource profiles used in GP Connect make use of the [Must-Support](https://www.hl7.org/fhir/STU3/conformance-rules.html#mustSupport) flag. 

Where a Must-Support flag is present on a resource element, a `consumer` system SHALL populate the field in the request body if data is available to do so, irrespective of the fact that field cardinality may be `0..1` or `0..*`. 

Similarly, `provider` systems SHALL populate an element in responses where data is available to do so, irrespective of optional cardinality. When a `provider` system receives data from a consumer for a field marked with the Must-Support flag, the provider system SHALL store this data field in such a way that the data element is preserved and the element can be populated in future responses to consumer requests for the resource in question.

If an element within a fhir profile is marked as must support then all sub elements of that element SHALL also be considered must support. For example, within the GP Connect Appointment profile the booking organization extension is flagged with must support on the extension, this means that the extension and all sub elements within the extension are must support and SHALL be stored in a way that the data is preserved and the booking organization can be populated in future responses to consumers requesting that resource.

For example, see the [Register a patient request body](foundations_use_case_register_a_patient.html#payload-request-body).

