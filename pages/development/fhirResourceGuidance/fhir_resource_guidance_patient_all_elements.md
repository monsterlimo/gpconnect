---
title: Patient FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_patient_all_elements.html
summary: "Population requirements for the Patient FHIR Resource"
---

The headings below list the elements of the Patient resource and describe how to populate and consume them.

{% include tip.html content="You'll find it helpful to read it in conjunction with the underlying [Patient profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1)." %} 

## Patient resource elements ##

----
### id ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Id</code></td>
    <td><b>Optionality:</b>Must-Support</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

The Logical ID of the resource should be populated as per the [FHIR specification requirements](https://www.hl7.org/fhir/STU3/resource.html#id).

----
### meta.profile ###
<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>uri</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

The Patient profile URL.

<b>Fixed value:</b> https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1

----
### extension[registrationDetails] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Complex Extension</code></td>
    <td><b>Optionality:</b>Must-Support</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Contains details relating to the registration of the patient within fhir server.

----
### extension[registrationDetails].extension[registrationPeriod] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Must-Support</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

The period for which the patient is registered on the provider system:
* the `valuePeriod.start` element SHALL contain the date the patient was registered on the system
* the `valuePeriod.end1 element MAY be included if the registration has an expiry date

----
### extension[registrationDetails].extension[registrationType] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Must-Support</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

The “registrationType” SHALL be populated by the provider system using a value from the valueset which matches the registration type used within the provider system. If an appropriate registration type is not available within the valueset then the Other type SHALL be use and more detail around the specific type of registration SHOULD be added using the “text” element of the CodeableConcept.

----
### extension[registrationDetails].extension[preferredBranchSurgery] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Must-Support</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Provider SHALL populate the preferred branch surgery extension with a reference to a location resource which represents the patient’s preferred branch surgery OR a reference to a location resource representing the GP Practice where the patient is registered if there is no preferred branch surgery recorded.

----
### extension[ethnicCategory] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Ethnicity of the patient.

----
### extension[religiousAffiliation] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Religious affiliation of the patient.

----
### extension[residentialStatus] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Residential status of the patient.

----
### extension[treatmentCategory] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Requirements relating to payment for treatment.

----
### extension[nhsCommunication] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Complex Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..*</td>
  </tr>
</table>

Communication preferences of patient.

----
### extension[birthPlace] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Address where patient was born.

----
### extension[nominatedPharmacy] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

The patient's nominated pharmacy.

----
### extension[deathNotificationStatus] ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

The type of death notice as held on Personal Demographics Service (PDS).




----
### identifier ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>Identifier</code></td>
    <td><b>Optionality:</b> Mandatroy</td>
    <td><b>Cardinality:</b> 1..*</td>
  </tr>
</table>

Within GP Connect an NHS Number identifier SHALL always be included in the Patient resource.



<h2 style="color:#ED1951;">AllergyIntolerance elements <b>not in use</b></h2>

The following elements **SHALL NOT** be populated:

----
<h3 style="color:#ED1951;">extension[patient-cadavericDonor]</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code>Extension</code></td>
    <td><b>Optionality:</b>Optional</td>
    <td><b>Cardinality:</b>0..1</td>
  </tr>
</table>

Due to a centralised donor register this element may cause confusion as it may be different to the national donor register therefore it should not be populate within the patient resource.

