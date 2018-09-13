---
title: Location FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_location.html
summary: "Population requirements for the Location FHIR Resource"
---

## Overview ##

A location resource represents a physical location such as a GP Surgery building or the location of a branch surgery. A location resource could also represent specific rooms or building, but for GP Connect our use cases and capabilities currently only use location resources which represent the physical location of a GP Surgery or the physical location of a branch surgery, specifically for the use within the appointment management capability.

A location resource returned through the GP Connect API should contain meaningful information to consumers external to the FHIR server.


## Location resource elements ##

The headings below list the elements of the Location resource which have additional or specific requirements beyond those expressed by the [Location resource profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1).

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
	<p>The location resource profile definition URL.</p>
	<p><b>Fixed value:</b> https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1</p>

	<h4>meta.versionId</h4>
	<table class='resource-attributes'>
	  <tr>
		<td><b>Data type:</b><code> Id</code></td>
		<td><b>Optionality:</b> Must-Support</td>
		<td><b>Cardinality:</b> 0..1</td>
	  </tr>
	</table>
	<p>The version identifier for the instance of the location resource.</p>
	<p>
		<b>Providers:</b>
		<ul>
			<li>SHALL populated the version identifier when returning a location resource.</li>
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
	<p>The date and time the location resource instance was last updated.</p>
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

Location business identifier types applicable to GP Connect:

| Identifier system | Optionality | Cardinality | Description |
| --- | --- | --- |
| https://fhir.nhs.uk/Id/ods-site-code | Optional | 0..1 | The ODS Site Code of the location, usually relates to branch surgeries. |

