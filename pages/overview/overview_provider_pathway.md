---
title: Provider pathway
keywords: provider, pathway
tags: [provider]
sidebar: overview_sidebar
permalink: overview_provider_pathway.html
---

Follow this pathway if you're a GP clinical data provider (such as EMIS Health, INPS Vision,  Microtest Health, TPP) and you want to use GP Connect to develop a way of allowing other systems to access GP data on your system for direct patient care:
<br/> 

-   [Prerequisites]()
-   [Target operating model (TOM)]()
-   [Solutions assurance]()
-   [Clinical safety]()
-   [Information governance]()
-   [Agreements]()
-   [Get started](overview_provider_pathway.html)
    - read about the [GP Connect priority capabilities](overview_priority_capabilities.html)
    - look through the design decisions made so far in relation to each capability pack:[Foundations](foundations_design.html), [Access Record Structured](accessrecord_structured_design.html), [Appointment Management](appointments_design.html)
-   [Explore GP Connect](overview_explore.html)
    - try out the [GP Connect Demonstrator system](system_demonstrator.html)
    - download the [GP Connect Demonstrator Codebase](gpconnect-demonstrator) to see how it works
    - download our [PostMan Collection](system_reference_postman.html) and explore the GP Connect interactions
-   [Develop with GP Connect](overview_development.html)
    - familiarise yourself with HL7® FHIR® ([developer introduction](http://www.hl7.org/implement/standards/fhir/overview-dev.html), [executive summary](http://www.hl7.org/implement/standards/fhir/summary.html), or [clinical intro](http://www.hl7.org/implement/standards/fhir/overview-clinical.html))
    - choose an open source [FHIR development library](development_fhir_open_source_guidance.html) for your favourite programming language
    - familiarise yourself with our [GP Connect FHIR API guidance](development_fhir_api_guidance.html) common to all APIs
    - explore the GP Connect profiled FHIR resources (a variation of the international [FHIR resources](https://www.hl7.org/fhir/STU3/)) for [Foundations](datalibraryfoundation.html), [Access Record Structured](accessrecord_structured_development_resources_overview.html) and [Appointment Management](datalibraryappointment.html).
    - explore one or more of the GP Connect capability packs and start building new or hitting existing APIs:
      - [Foundations](foundations.html) (for example, resolve a patient to their logical identifier for further API calls).
      - [Access Record Structured](accessrecord_structured.html) (for example, access structured data from the primary care record).
      - [Appointment Management](appointments.html) (for example, book an appointment for a patient).
    - look at cross-cutting areas:
      - JSON Web Token - provides [cross-organisation audit and provenance details](integration_cross_organisation_audit_and_provenance.html)
      - [additional HTTP headers and proxy URL]() - this gives you access to the [Spine Security Proxy](integration_spine_security_proxy.html), the secure ‘front door’ of GP Connect APIs
      - configure HTTPS and TLS/MA - [security guidance](development_api_security_guidance.html) allows you to secure and mutually authenticate your service with the Spine (which refers to two parties authenticating each other at the same time)
    - use the [development cheat sheet](development_deliverables.html)
-   [Test and assure](overview_test_and_assurance.html)     
    - read about [provider testing](testing_api_provider_testing.html)

<br/> 
Our provider ecosystem shows you each stage of a typical GP Connect API project:

![Img](images/overview/API_Ecosystem_Diagram_Provider.png)
