---
title: Clinical overview
keywords: homepage
tags: [clinical; overview]
sidebar: overview_sidebar
permalink: overview_clinical.html
toc: false
summary: What is GP Connect?
---

GP Connect aims to open up information and data held within the different GP clinical systems for use across the whole of health and social care - ensuring patient medical information is available to the right clinician, at the right time, wherever they are.

We’re developing a set of application programming interfaces (APIs) that connect the four main provider systems (EMIS, Vision, Microtest and TPP), allowing them to exchange data effortlessly. The development of applications that then consume the data (allowing people to use or view information) will be the responsibility of local NHS organisations. This will allow the local organisation to decide how it can best use the data to support its patients, clinicians and other staff, ensuring the appropriate safety and governance measures are in place.

## Business drivers ##

Supporting improved access to general practice by:

- providing access to the detailed care record to every practice at the point of care
- allowing appointment management (booking and cancelling) between practices in a federation or hub or other affiliation
- allowing tasks to be sent between practices in a federation
- enabling clinicans at other care settings (such as hospitals, 111 and urgent care providers) to access information to suit their local needs

## Benefits ##

- Clinical
  - real-time access to patients' records to allow clinicians access to the right information, at the right time to help make the right decisions

- Patient/carer
  - increase access opportunities (such as ability to access an appointment anywhere within the federation/hub)
  - improved patient experience and satisfaction

- Administrative
  - ability to book or cancel appointments and send tasks or notifications within a local geography across federations/hubs
 
- Management
  - ability to understand appointment capacity across federated practices, providing single points of access for patients to book -  meaning more efficient access to services, better resource planning, and improved reporting data

- Technical
  - first nationally defined, standards-based step on the interoperability journey for GP systems

## Capabilities ##

A capability uses GP Connect APIs to focus on a particular area of general practice. Capabilities are organised within 'capability packs', which include:

 - Foundations - covers the basic API requirements and prerequisites needed to use the GP Connect APIs
 - Appointment Management - enable end users to book and manage GP practice appointments held in any of the four GP principal practice systems
 - Access Record HTML - provides health professionals with access to a patient’s primary care record by requesting sections or headings
 - Access Record Structured - enables a system to consume a patient’s GP record in a machine-readable format, removing the need to transcribe information from one system to another
 - Task Management
 - Unstructured Writeback

HTML re are several [initial capabilities defined](overview_priority_capabilities.html).

## GP Connect Model ##

space for image

## Pathways ##

This GitHub repository contains everything you need to know to develop using GP Connect APIs. To make it easier to naviagate your way through the site, we've devised four pathways:

| Pathway  | Follow if...  |   
|---|---|
| [Consumer pathway](http://gpconnect-specrestructure.netlify.com/overview_consumer_pathway.html)  | You're developing an app that's going to consume data from GP clinical systems.  |   
| [Provider pathway](http://gpconnect-specrestructure.netlify.com/overview_provider_pathway.html)  | You're making data available to share from a GP clinical system.  |   
| [Commissioning pathway](http://gpconnect-specrestructure.netlify.com/overview_commissioning_pathway.html)  | You're commissioning a supplier to build a consuming app.  |   
| [Deploy-only pathway](http://gpconnect-specrestructure.netlify.com/overview_deploy_only_pathway.html)  | You're deploying an app to consume GP data on behalf of a GP federation/hub or similar.  |   

## Strategic drivers ##

- [Government Paperless 2020 (Personalised Health and Care Framework)](https://www.gov.uk/government/publications/personalised-health-and-care-2020)
  - ‘all patient and care records will be digital, interoperable and real-time by 2020’

- [NHS England General Practice Five Year Forward View](https://www.england.nhs.uk/gp/gpfv/)
  - Greater collaboration and sharing of information through IT system interoperability across the health and care system




