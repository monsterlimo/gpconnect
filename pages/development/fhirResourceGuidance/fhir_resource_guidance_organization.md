---
title: Organization FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_organization.html
summary: "Population requirements for the Organization FHIR Resource"
---

The headings below list the elements of the Organization resource and describe how to populate and consume them.

{% include tip.html content="You'll find it helpful to read it in conjunction with the underlying [Organization profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1)." %} 

## Organization resource elements ##

### id ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>Id</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

The logical identifier of the Organization resource.

### meta.profile ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>uri</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

The Organization profile URL.

Fixed value [https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1)





<h2 style="color:#ED1951;">Organization elements <b>not in use</b></h2>

The following elements **SHALL NOT** be populated:

