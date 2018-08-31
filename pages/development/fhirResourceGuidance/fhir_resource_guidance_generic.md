---
title: FHIR Resource element guidance
keywords: fhir development
tags: [fhir,development]
sidebar: overview_sidebar
permalink: fhir_resource_guidance_elements.html
summary: "Requirements for population of specific element types within FHIR resources"
---

This page covers generic population guidance and requirements for elements within FHIR resources. These FHIR resource element level requirements apply to the population of all FHIR resources unless stated otherwise in the more specific FHIR resource level guidance pages or the interaction specific guidance pages.


<h2 class="alphaHeading">A</h2>

### Address

The `address` element exists in many of the FHIR resources used in the GP Connect API. Where an address element is present in a FHIR resource the following population guidance SHALL be followed:

* Where the individual address sub elements are available within the suppliers system, the address SHALL be populated using the elements:
  * line
  * city
  * district
  * postalCode
  * country
  
  The `text` element SHOULD not be populated within the address.
  
* Where the address is not store as the individual elements within the suppliers system, the address SHALL be populated using the `text` element. The `line`, `city`, `district`, `postalCode` and `country` SHALL not be populated.



<h2 class="alphaHeading">I</h2>

### id

The logical id of all FHIR resources SHALL be populated in accordance with the [FHIR specification requirements](https://www.hl7.org/fhir/STU3/resource.html#id), meaning that population of the element is expected.


