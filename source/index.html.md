---
title: Tubman Project API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL

toc_footers:
  - <a href='http://www.tubmanproject.com'>Tubman Project</a>
  - <a href='https://tubmanproject-jupyterhub.mintyross.com'>JupyterHub</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - dispositions
  - filings
  - fields
  - errors

search: true
---

# Overview

## What is the Tubman Project

The Tubman Project's mission is to...

## Who is the Tubman Project API for?

This Tubman Project is for...

### Defendants

TODO: Common tasks expected...

* research their specific circumstances and compare

### Public Defenders and Hired Attorneys

TODO: Common tasks expected

*  Help defendants when pressed for time

### Developers

TODO: Common tasks expected...

* Develop applications based on data
* Experiment with developing machine learning models on the Tubman Project's JupyterHub.

# Getting Started

The Tubman Project API exposes a web service that allows you to interact with our system programmatically from your own application.  The following resources are exposed through the API.

* Criminal Dispositions
* Criminal Filings

The API attempts to conform to the [RESTful](https://en.wikipedia.org/wiki/Representational_State_Transfer) design principles.  You interact with the resources exposed via the API by accessing resource collection and element URIs using the HTTP verbs (GET, POST, PUT, and DELETE).

For hint on interacting with the API you can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

All endpoints are public. The Tubman Project API does not require authentication.
