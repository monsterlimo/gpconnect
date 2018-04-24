---
title: Provider pathway
keywords: provider, pathway
tags: [provider]
sidebar: overview_sidebar
permalink: overview_provider_pathway.html
---

Follow this pathway if you represent:

-   a GP clinical data provider, such as EMIS Health, INPS Vision,  Microtest Health, TPP
<br/> 
<br/> 

**Why do you want to access GP Connect?**
-   you want to use GP Connect to develop a way of allowing other systems to access GP data on your system for direct patient care
<br/> 
<br/> 

Work through the following steps:

-   Get started
 - read about the GP Connect priority capabilities
 - look through the design decisions made so far in relation to each capability pack
-   Explore GP Connect
 - try out the GP Connect Demonstrator system
 - download the GP Connect Demonstrator Codebase to see how it works
download our PostMan Collection and explore the GP Connect interactions
-   Develop with GP Connect
 - familiarise yourself with HL7® FHIR® (developer introduction, executive summary, or clinical intro)
 - grab an open source FHIR development library for your favourite programming language
 - familiarise yourself with our GP Connect FHIR API guidance common to all APIs
 - explore the GP Connect profiled FHIR resources, a variation of the international FHIR resources, for Foundations, Access Record HTML, and Appointment Management.
 - explore one or more of the GP Connect capability packs and start building new or hitting existing APIs
 - look at cross-cutting areas:
  - JSON Web Token - provides cross-organisation audit and provenance details
  - additional HTTP headers and proxy URL - this gives you access to the Spine Security Proxy, the secure ‘front door’ of GP Connect APIs
  - configure HTTPS and TLS/MA - security guidance allows you to secure and mutually authenticate your service with the Spine (which refers to two parties authenticating each other at the same time)
 - use development assets:
 - structure definitions
 - value sets
 - operation definitions
 - FHIR implementation guide


Our provider ecosystem shows you each stage of a typical GP Connect API project:

![Img](images/overview/API_Ecosystem_Diagram_Provider.png)
