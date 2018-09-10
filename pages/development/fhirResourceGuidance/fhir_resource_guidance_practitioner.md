---
title: Practitioner FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_practitioner.html
summary: "Population requirements for the Practitioner FHIR Resource"
---

The headings below list the elements of the Practitioner resource which have additional or specific requirements beyond those expressed by the [Practitioner profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1).

Requirements and guidance expressed on this page SHALL take precedence over the guidance and requirements expressed by the generic [FHIR Resource element guidance](fhir_resource_guidance_elements.html) page. Requirements from this population guidance page may be overridden by additional guidance and requirements expressed on the specific interaction capability pages.

## Practitioner resource elements ##

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
	<p>The practitioner resource profile definition URL.</p>
	<p><b>Fixed value:</b> https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1</p>

	<h4>meta.versionId</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Id</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The version identifier for the instance of the practitioner resource.</p>
	<p>
		<b>Providers:</b>
		<ul>
			<li>SHALL populated the version identifier when returning a practitioner resource.</li>
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
	<p>The date and time the practitioner resource instance was last updated.</p>
</div>


----
<h3 class="resourceElement">identifier</h3>

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b><code> Identifier</code></td>
    <td><b>Optionality:</b> Optional</td>
    <td><b>Cardinality:</b> 0..*</td>
  </tr>
</table>

Practitioner business identifier types applicable to GP Connect:

| Identifier system | Optionality | Cardinality | Description |
| --- | --- | --- |
| https://fhir.nhs.uk/Id/sds-user-id | Optional | 0..1 | The practitioner ID as present on the Spine Directory Service (SDS). Each practitioner resource may only have a single sds-user-id. |
| https://fhir.nhs.uk/Id/sds-role-profile-id | Optional | 0..* | The practitioner roles as present on the Spine Directory Service (SDS). A practitioner may have multiple sds-role-profile-id. |

