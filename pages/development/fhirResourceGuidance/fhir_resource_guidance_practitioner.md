---
title: Practitioner FHIR Resource guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_practitioner.html
summary: "Population requirements for the Practitioner FHIR Resource"
---

The headings below list the elements of the Practitioner resource and describe how to populate and consume them.

{% include tip.html content="You'll find it helpful to read it in conjunction with the underlying [Practitioner profile definition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1)." %} 

## Practitioner resource elements ##

### id ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>Id</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

The logical identifier of the Practitioner resource.

### meta.profile ###

<table class='resource-attributes'>
  <tr>
    <td><b>Data type:</b> <code>uri</code></td>
    <td><b>Optionality:</b> Mandatory</td>
    <td><b>Cardinality:</b> 1..1</td>
  </tr>
</table>

The Practitioner profile URL.

Fixed value [https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1)





<h2 style="color:#ED1951;">AllergyIntolerance elements <b>not in use</b></h2>

The following elements **SHALL NOT** be populated:

