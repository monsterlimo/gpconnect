---
title: Patient FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_patient.html
summary: "Population requirements for the Patient FHIR Resource"
---

The headings below list the elements of the Patient resource which have additional or specific requirements beyond those expressed by the [Patient resource profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1).

Requirements and guidance expressed on this page SHALL take precedence over the guidance and requirements expressed by the generic [FHIR Resource element guidance](fhir_resource_guidance_elements.html) page. Requirements from this population guidance page may be overridden by additional guidance and requirements expressed on the specific interaction capability pages.

## Patient resource elements ##

----
<h3 class="resourceElement">id</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> Id</code></td>
    <td><b>Optionality:</b> Must-Support</td>
    <td><b>Cardinality:</b> 0..1</td>
  </tr>
</table>

The Logical ID of the resource should be populated as per the [FHIR specification requirements](https://www.hl7.org/fhir/STU3/resource.html#id).

----
<h3 class="resourceElement">meta</h3>
<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> Meta</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

Meta data describing the resource structure and content.

<div class="subResourceElement">
	<h4>meta.profile</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> uri</code></td>
		<td><b>Optionality:</b> Mandatory</td>
		<td><b>Cardinality:</b> 1..1</td>
	  </tr>
	</table>
	<p>The patient resource profile definition URL.</p>
	<p><b>Fixed value:</b> https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1</p>

	<h4>meta.versionId</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Id</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The version identifier for the instance of the patient resource.</p>
	<p>
		<b>Providers:</b>
		<ul>
			<li>SHALL populated the version identifier when returning a patient resource.</li>
		</ul>
	</p>

	<h4>meta.lastUpdated</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> instant</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The date and time the patient resource instance was last updated.</p>
</div>

----
<h3 class="resourceElement">extension[registrationDetails]</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> Complex Extension</code></td>
    <td><b>Optionality:</b> Must-Support</td>
    <td><b>Cardinality:</b> 0..1</td>
  </tr>
</table>

Contains details relating to the registration of the patient within fhir server.

<div class="subResourceElement">
	<h4>extension[registrationDetails].extension[registrationPeriod]</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Extension</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>
		The period for which the patient is registered on the provider system:
		<ul>
			<li>the `valuePeriod.start` element SHALL contain the date the patient was registered on the system</li>
			<li>the `valuePeriod.end` element MAY be included if the registration has an expiry date</li>
		</ul>
	</p>

	<h4>extension[registrationDetails].extension[registrationType]</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Extension</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The “registrationType” SHALL be populated by the provider system using a value from the valueset which matches the registration type used within the provider system. If an appropriate registration type is not available within the valueset then the Other type SHALL be use and more detail around the specific type of registration SHOULD be added using the “text” element of the CodeableConcept.</p>

	<h4>extension[registrationDetails].extension[preferredBranchSurgery]</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Extension</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>Provider SHALL populate the preferred branch surgery extension with a reference to a location resource which represents the patient’s preferred branch surgery OR a reference to a location resource representing the GP Practice where the patient is registered if there is no preferred branch surgery recorded.</p>
</div>


----
<h3 class="resourceElement">identifier</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> Identifier</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..*</td>
  </tr>
</table>

Patient business identifier types applicable to GP Connect:

| Identifier system | Optionality | Description |
| --- | --- | --- |
| https://fhir.nhs.uk/Id/nhs-number | Mandatory | For all capabilities within GP Connect the patient has to have been traced and verified, therefore the NHS Number identifier SHALL always be included in the Patient resource. |

----
<h3 class="resourceElement">name</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> HumanName</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..*</td>
  </tr>
</table>

* The Patient resource SHALL contain one name element with the `use` of `official`, as per the resource profile definition. This `official` name should contain the patient details as they appear within the patient record on the [Spine](integration_personal_demographic_service.html).


<h2 class="warningHeading"><i class="fa fa-warning"></i>  Patient resource elements <b>not in use</b></h2>

The following elements **SHALL NOT** be populated:

----
<h3 style="color:#ED1951;">extension[patient-cadavericDonor]</h3>

Due to a centralised donor register this element may cause confusion as it may be different to the national donor register therefore it should not be populate within the patient resource.

