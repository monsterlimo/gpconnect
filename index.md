---
title: Introduction - what is GP Connect?
keywords: homepage
tags: [introduction]
sidebar: home_sidebar
permalink: index.html
toc: false
summary: An introduction to the GP Connect FHIR® APIs
---

{% comment %}
[![Semver](http://img.shields.io/badge/semver-2.0.0-yellow.svg)](http://semver.org/spec/v2.0.0.html){:target="_blank" class="no_icon"} [![License](http://img.shields.io/:license-apache2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html){:target="_blank" class="no_icon"} 
{% endcomment %}

GP Connect is a national interoperability programme that's opening up information and data held within the different GP clinical systems for use across the whole of health and social care - ensuring patient medical information is available to the right clinician, at the right time, wherever they are. 

We're developing a set of application programming interfaces (APIs) that will seamlessly connect the four main provider systems (EMIS Web, Vision, Microtest Open Evolution and TPP SystmOne) and allow them to exchange data with ease.

The development of applications that consume the data (allowing people to use or view information) will be the responsibility of local NHS organisations, which means they choose the system that best meets their needs and those of their patients (while, of course, ensuring that appropriate safety and governance measures are in place).

## GP Connect overview ##

![Img](images/overview/GP Connect Model.png)

## Development pathways ##
<p align="left">This GitHub repository contains all the technical resources you need to connect between clinical systems and GP data using our FHIR&reg; APIs.
 
To continue on your development journey, follow the relevant pathway:</p>

<div class="row">
         <div class="col-lg-12">
                                                           </div>
                        <div class="col-6 col-md-4">
             <div class="panel panel-default text-center">
                 <div class="panel-heading">
                     <span class="fa-stack fa-5x">
                           <i class="fa fa-circle fa-stack-2x text-primary" style="color:#005EB8"></i>
                           <i class="fa fa-desktop fa-stack-1x fa-inverse"></i>
                     </span>
                 </div>
                 <div class="panel-body" align="left">
                      <h4>Consumer supplier</h4>
                         <p align="left">You're a software development company already working with the NHS or would like to work with the NHS. You have checked that you comply with IG requirements.</p>
                         <p align="left">You want to use GP Connect to develop an API to consume GP data.  You intend to work with a suitable end-user organisation, which you may or not have already identified.</p>
                     <a href="overview_consumer_pathway.html" class="btn btn-primary">Learn more</a>
                 </div>
             </div>
         </div>
            <div class="col-6 col-md-4">
             <div class="panel panel-default text-center">
                 <div class="panel-heading">
                     <span class="fa-stack fa-5x">
                           <i class="fa fa-circle fa-stack-2x text-primary" style="color:#005EB8"></i>
                           <i class="fa fa-globe fa-stack-1x fa-inverse"></i>
                     </span>
                 </div>
                 <div class="panel-body" align="left">
                     <h4>Clinical system provider</h4>
                         <p align="left">You're a GP clinical data provider.</p>
                     <p align="left">You want to use GP Connect to develop a way of allowing other systems to access GP data on your system for direct patient care.</p>
                     <a href="overview_provider_pathway.html" class="btn btn-primary">Learn more</a>
                 </div>
             </div>
         </div>
           <div class="col-6 col-md-4">
             <div class="panel panel-default text-center">
                 <div class="panel-heading">
                     <span class="fa-stack fa-5x">
                           <i class="fa fa-circle fa-stack-2x text-primary" style="color:#005EB8"></i>
                           <i class="fa fa-user-md fa-stack-1x fa-inverse"></i>
                     </span>
                 </div>
                 <div class="panel-body" align="left">
                     <h4>End-user organisation</h4>
                     <p align="left">You're a CCG with GP practices organised in a federation or hub; you're a hospital or provider of emergency care.</p>
                              <p align="left">You want to use an existing GP Connect API - or commission someone to create a new one - to access GP data from more than one GP clinical data provider to improve direct patient care.</p>
                     <a href="overview_end_user_pathway.html" class="btn btn-primary">Learn more</a>
                                     </div>
         </div>
         </div> 
</div>
     
{% include important.html content="This site is under active development by the GP Connect team and is intended to provide all the technical resources you need to successfully develop GP Connect provider APIs or consuming applications. Some areas are being formulated and iterative updates to content will be added on a regular basis. See our GitHub [releases page](https://github.com/nhsconnect/gpconnect/releases) for more information." %}

{% include warning.html content="This site is provided for information only and is intended for those engaged with NHS Digital in First of Type activities. Other parties are advised not to develop against these specifications until a formal announcement has been made." %}

{% include twitterfollow.html %}

{% include gitterbadge.html %}



