---
title: Organization FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_organization.html
summary: "Population requirements for the Organization FHIR Resource"
---

## Overview ##

An organization resource represents a legally recognized organization, within GP Connect these organizations will have an ODS Code.


## Organization resource elements ##

The headings below list the elements of the Organization resource which have additional or specific requirements beyond those expressed by the [Organization resource profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1).

Requirements and guidance expressed on this page SHALL take precedence over the guidance and requirements expressed by the generic [FHIR Resource element guidance](fhir_resource_guidance_elements.html) page. Requirements from this population guidance page may be overridden by additional guidance and requirements expressed on the specific interaction capability pages.

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
	<p>The organization resource profile definition URL.</p>
	<p><b>Fixed value:</b> https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1</p>

	<h4>meta.versionId</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Id</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The version identifier for the instance of the organization resource.</p>
	<p>
		<b>Providers:</b>
		<ul>
			<li>SHALL populated the version identifier when returning a organization resource.</li>
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
	<p>The date and time the organization resource instance was last updated.</p>
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


Organization business identifier types applicable to GP Connect:

| Identifier system | Optionality | Cardinality | Description |
| --- | --- | --- |
| https://fhir.nhs.uk/Id/ods-organization-code | Optional | 0..1 | The ODS code of the organizaiton. |

