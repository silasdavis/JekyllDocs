---
title:  "Getting ready with Postman"
sidebar: operon_sidebar
permalink: PM1-postman-ehrscape-getting-ready.html
summary: This section contains an introduction to the Postman Tool. This tool can be used to run API calls to send and receive data from the Ehrscape Clinical Data Repository
---

First you need to install a copy of the API runner application ***Postman*** (Chrome/Macos/Windows)

[Get Postman Application](http://getpostman.com)

This lets you send and receive data from the Ehrscape API without the need for a specific programming language.

Postman also allows you to import a preset collection of API calls which we can use to supply a copy of the Ehrscape API and associated 'environment' file, which contains settings for a specific ehrscape domain (either )

## A. Run Postman

Click the 'Run Postman Button' to import the Postman 'openEHR Ehrscape Clinical Data Repository' API collection and associated ***Operon Sandpit*** environment settings.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/aa0eeb03ab2d1324b774#?env%5Boprn_t1_Sandpit%5D=W3siZW5hYmxlZCI6dHJ1ZSwia2V5Ijoib3BlbkVockFwaSIsInR5cGUiOiJ0ZXh0IiwidmFsdWUiOiJodHRwczovL3Rlc3Qub3Blcm9uLnN5c3RlbXMifSx7ImVuYWJsZWQiOnRydWUsImtleSI6ImRvbWFpbk5hbWUiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoic2FuZHBpdCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoiZG9tYWluU3VmZml4IiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6Im9wcm4xIn0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJDRFJOYW1lIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6ImVocnNjYXBlLmNvbSJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoiU2Vzc2lvbkhlYWRlciIsInR5cGUiOiJ0ZXh0IiwidmFsdWUiOiJFaHItU2Vzc2lvbi1kaXNhYmxlZCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5Ijoie3tTZXNzaW9uSGVhZGVyfX0iLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoiIn0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJQYXNzd29yZCIsInR5cGUiOiJ0ZXh0IiwidmFsdWUiOiJWeW9CQTYsODlncCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoiVXNlcm5hbWUiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoib3BybjFfc2FuZHBpdCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoiYWNjb3VudE5hbWUiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoib3BybjFfc2FuZHBpdCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoiZG9tYWluU3lzdGVtSWQiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoic2FuZHBpdC5vcHJuMS5laHJzY2FwZS5jb20ifSx7ImVuYWJsZWQiOnRydWUsImtleSI6IkF1dGhvcml6YXRpb24iLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoiQmFzaWMgYjNCeWJqRmZjMkZ1WkhCcGREcFdlVzlDUVRZc09EbG5jQT09In0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJjb21taXR0ZXJOYW1lIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6IkRyIHNhbmRwaXQifSx7ImVuYWJsZWQiOnRydWUsImtleSI6InBhdGllbnROYW1lIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6Ikl2b3IgQ294In0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJzdWJqZWN0SWQiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoiOTk5OTk5OTAwMCJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoibmhzTnVtYmVyIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6Ijk5OTk5OTkwMDAifSx7ImVuYWJsZWQiOnRydWUsImtleSI6InN1YmplY3ROYW1lc3BhY2UiLCJ0eXBlIjoidGV4dCIsInZhbHVlIjoidWsubmhzLm5oc19udW1iZXIifSx7ImVuYWJsZWQiOnRydWUsImtleSI6ImVocklkIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6IjM3NmU1YzRiLWYyYjEtNGQxZi04ZGUwLTNhNTkzZWVhNjE1YyJ9LHsiZW5hYmxlZCI6dHJ1ZSwia2V5IjoicGFydHlJZCIsInR5cGUiOiJ0ZXh0IiwidmFsdWUiOiIxMDA2In0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJ0ZW1wbGF0ZUlkIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6IlZpdGFsIFNpZ25zIEVuY291bnRlciAoQ29tcG9zaXRpb24pIn0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJjb21wb3NpdGlvbklkIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6IjgyZGE5M2NkLWEzZmMtNGY5Mi1hM2MzLTYzYjJlODM0MjBkOTo6c2FuZHBpdC5vcHJuMS5laHJzY2FwZS5jb206OjEifSx7ImVuYWJsZWQiOnRydWUsImtleSI6IkVoci1TZXNzaW9uLWRpc2FibGVkIiwidHlwZSI6InRleHQiLCJ2YWx1ZSI6ImExMmJlMWJiLTRjMTEtNDBlYy04MzZhLTZkODIyODllMGJiOCJ9XQ==)

This will automatically install the Ehrscape Collection and Operon Sandpit environment files.

## or B. Download Postman files from Git

Click on these links to download the files to your system:

[openEHR Ehrscape Collection](https://raw.githubusercontent.com/operonsys/postman-ehrscape/master/openEHR%2520Ehrscape%2520Clinical%2520Data%2520Repository.postman_collection.json)

[Operon Sandpit Environment](https://raw.githubusercontent.com/operonsys/postman-ehrscape/master/oprn_t1_Sandpit.postman_environment.json)

## or C. Download your collection files from email
If you have received an email containing the collection and environment files to use with Postman. The first step is to download these files ready to then be imported into Postman.

Find ***openEHR%20Ehrscape%20Clinical%20Data%20Repository.postman_collection*** in your email and download it to a folder of your choice (normally the Download folder).

Find ***<your_environment_name.postman_environment*** in your email and download it to a folder of your choice (normally the Download folder). Please note that for demonstration purposes we are using the `C4H Ripple OSI` environment in this document.



## Import Downloaded files into Postman
If you have downloaded files from Github of from your email, these now need to be installed in Postman.

Open Postman and select ***Import***

<img src="\images\ImportFilesIntoPostman.jpg" alt="Import Files into Postman" width="50%" height="50%">

Locate your two save files and import them. You can either use the ***Choose Files*** option to import one at a time or drag and drop the files into the window

<img src=\images\DropFilesInPostman.jpg" alt="Drop Files into Postman" width="50%" height="50%">


In the top right hand corner, change the environment to your environment (in the screenshot below that's the C4H Ripple OSI environment)

<img src="\images\SelectEnvironment.jpg" alt="Change environment" width="50%" height="50%">

On the left hand side you can now see the collection files

<img src="\images\Collection.jpg" alt="Collection" width="50%" height="50%">
