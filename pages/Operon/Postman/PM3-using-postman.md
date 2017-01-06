---
title:  "Using Postman with Ehrscape"
sidebar: operon_sidebar
permalink: PM3-using-postman.html
summary: This section contains instructions how to use the Postman tool to create sessions, retrieve data, persist data and run a basic query
---

## Create Session
The first step is to create an openEHR session and retrieve the ***sessionId*** token. This allows subsequent API calls to be made without needing to login on each occasion.

Navigate to the ***session*** folder and highlight ***Create Session*** on the left, then click on the ***Send*** button. The required credentials are automatically filled in from the Pre-sets file (see ***Navigating Postman*** section above)

<img src="/images/CreateSession.jpg" alt="Create Session" width="50%" height="50%">

Click the ***Scroll to responses*** button in the bottom right hand corner to display the response details.

The screenshot below shows the session Id which has been returned in the call.

<img src="/images/CreateSessionResult.jpg" alt="Session ID" width="50%" height="50%">

## Get EHR Identifier
The next step is to get the patient’s internal EHR identifier by sending their external identifier (in this case NHS Number). The ehrId is a unique string which, for security reasons, cannot be associated with the patient, if for instance their openEHR records were leaked.

Select ***Get ehrStatus from subjectId*** in the ***ehr*** folder and then click on the ***Send*** button. Again, the patient’s NHS number is taken from the Pre-sets file and is therefore filled in automatically.

<img src="/images/GetEHRId.jpg" alt="Get EHRId">

Click on the ***Scroll to responses*** button in the bottom right hand corner to display the response details.

The JSON snippet below shows the ehrId for our dummy patient.

<img src="/images/GetEHRIdResult.jpg" alt="Display EHRId" width="50%" height="50%">

To store the returned ehrId as a pre-set for the selected environment, highlight the string in the response details, right mouse click, set the environment (*C4H Ripple OSI in this example*) and then select ***ehrId*** from the list of attributes.

<img src="/images/StoreEhrIDAsPreset.jpg" alt="Store EHRId" width="50%" height="50%">

## Retrieve Composition ID
Now that we have the patient’s EHR identifier, we can use it to locate and retrieve some clinical details. We use an Archetype Query Language (AQL) call to retrieve a list of the identifiers and dates of existing Nursing Vital Signs Observations Composition records. Compositions are document-level records which act as the container for all openEHR patient data.

The name/value of the Composition is the root name of the templates composition archetype (case-sensitive). In a real-world example we would query on other factors to ensure we had the ‘correct’ list.

The query we need to run in order to get the composition Id for the most recent vital signs composition for the selected patient is as follows:

<img src="/Images/RetrieveCompositionIdExplanation.jpg" alt="Retrieve compositionId explanation" width="50%" height="50%">

At this stage you don’t need to worry about the exact syntax and how to create an AQL query. These topics are covered elsewhere, and the Specifications provide the required details.

Open the ***query*** folder and select ***Ad-hoc query***

<img src="/Images/RetrieveCompositionIdFolderSelect.jpg" alt="Retrieve CompositionId">

This is the query string in a format which can be copied and pasted:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ***select<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a/uid/value as compositionId,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a/context/start_time/value as start_time<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; from EHR e[ehr_id/value='{{ehrId}}']<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contains COMPOSITION a[openEHR-EHR-COMPOSITION.encounter.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; where a/name/value= 'Nursing Vital Signs Observations'<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; order by a/context/start_time/value desc<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; offset 0 limit 1***

In the Ad-hoc Query window click on ***Param*** and paste the query string above into the ***Value*** field, then click on the ***Send*** button.

<img src="/Images/RetrieveCompositionIdString.jpg" alt="Get CompositionId" width="50%" height="50%">

Click the ***Scroll to response*** button in the buttom right hand corner to display the response details. The ***compositionId*** element in the response is the unqique identifier for the composition and the ***start_time*** is the time that the document was authored.

<img src="/Images/RetrieveCompositionIdResult.jpg" alt="Get CompositionID result" width="50%" height="50%">

We will use the results of this query to retrieve the full composition, so the final action is to store the composition Id as a pre-set.

Highlight the string in the response details, right mouse click, set the environment (***C4H Ripple OSI*** in this example) and then select ***compositionId*** from the list of attributes

<img src="/Images/StoreCompositionIdAsPreset.jpg" alt="Store compositionId" width="50%" height="50%">

## Retrieve Composition
The next step is to retrieve the composition itself, based on the compositionId we stored in the previous step.

Navigate to the ***composition*** folder and highlight ***Read Composition JSON FLAT***, then click the ***Send*** button

<img src="/Images/RetrieveComposition.jpg" alt="Retrieve composition" width="50%" height="50%">

The result is shown as a FLAT JSON file below

<img src="/Images/RetrieveCompositionResult.jpg" alt="Retrieve composition result" width="50%" height="50%">

Other formats are JSON RAW, XML RAW or JSON STRUCTURED – the snippets below show part of the Pulse data

<img src="/Images/RetrieveCompositionResultOtherFormats1.jpg" alt="JSON RAW" width="50%" height="50%">

<img src="/Images/RetrieveCompositionResultOtherFormats2.jpg" alt="XML RAW" width="50%" height="50%">

<img src="/Images/RetrieveCompositionResultOtherFormats3.jpg" alt="JSON STRUCTURED" width="50%" height="50%">

## Persist Composition
The next step is to persist a new composition. The data in the composition is validated against a template, and the first action is to set the correct template Id for composition to be persisted.

Navigate to the ***Template*** folder and highlight ***List available templates***, then click the ***Send*** button. Highlight the ***Vital Signs Encounter template*** in the list of available templates, right mouse click, set the environment (***C4H Ripple OSI*** in this example) and then select ***templateId*** from the list of attributes

<img src="/images/ListTemplates.jpg" alt="Set templateId" width="50%" height="50%">

Once the template Id is set, we can commit a composition. The following string is an example of a vital signs composition:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ***"ctx/language": "en",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/territory": "GB",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/composer_name": "Hazel Smith",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/time": "2015-12-10T02:19:00.000Z",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/health_care_facility|id": "999999-345",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/health_care_facility|name": "Northumbria Community NHS",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/id_namespace": "NHS-UK",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "ctx/id_scheme": "2.16.840.1.113883.2.1.4.3",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/respirations:0/any_event:0/rate|magnitude": 22,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/respirations:0/any_event:0/rate|unit": "/min",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/pulse:0/any_event:0/heart_rate|magnitude": 101,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/pulse:0/any_event:0/heart_rate|unit": "/min",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/body_temperature:0/any_event:0/temperature|magnitude": 36.6,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/body_temperature:0/any_event:0/temperature|unit": "°C",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/blood_pressure:0/any_event:0/systolic|magnitude": 100,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/blood_pressure:0/any_event:0/systolic|unit": "mm[Hg]",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/blood_pressure:0/any_event:0/diastolic|magnitude": 60,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/blood_pressure:0/any_event:0/diastolic|unit": "mm[Hg]",<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/indirect_oximetry:0/any_event:0/spo2|numerator": 94,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/indirect_oximetry:0/any_event:0/spo2|denominator": 100,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "nursing_vital_signs_observations/vital_signs:0/national_early_warning_score_rcp_uk:0/total_score": 3***

As mentioned before, the exact syntax and how to create a composition will be covered elsewhere. At this stage you should just use the syntax string provided above.

Navigate to the ***Composition*** folder and highlight ***Commit Composition JSON FLAT***. Paste the text above into the Body text box on the right hand side and click on the ***Send*** button.

<img src="/images/CommitComposition.jpg" alt="Commit composition" width="50%" height="50%">

The result shows the composition Id for the newly committed composition.

<img src="/images/CommitCompositionResult.jpg" alt="Commit composition result" width="50%" height="50%">

## Run AQL Query
The next step is to run a query on recent vital signs compositions and return a set of key data.

Navigate to the ***query*** folder and select ***Ad-hoc Query***.

This is the query string we are going to use to retrieve the last 5 vital signs compositions and return the relevant readings. Once again, just to clarify: the exact syntax and how to create an AQL query will be covered elsewhere. At this stage you can just copy and paste the query syntax string shown below:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ***select<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a/uid/value as compositionId,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a/context/start_time/value as start_time,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_a/data[at0001]/events[at0002]/data[at0003]/items[at0004]/value/magnitude as Rate_magnitude,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_b/data[at0002]/events[at0003]/data[at0001]/items[at0004]/value/magnitude as Heart_Rate_magnitude,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_c/data[at0002]/events[at0003]/data[at0001]/items[at0004]/value/magnitude as Temperature_magnitude,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_f/data[at0001]/events[at0006]/data[at0003]/items[at0004]/value/magnitude as Systolic_magnitude,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_f/data[at0001]/events[at0006]/data[at0003]/items[at0005]/value/magnitude as Diastolic_magnitude,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_g/data[at0001]/events[at0002]/data[at0003]/items[at0006]/value/numerator as spO2_numerator,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b_h/data[at0001]/events[at0002]/data[at0003]/items[at0028]/value/magnitude as Total_Score_magnitude<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; from EHR e[ehr_id/value='{{ehrId}}']<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contains COMPOSITION a[openEHR-EHR-COMPOSITION.encounter.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contains (OBSERVATION b_a[openEHR-EHR-OBSERVATION.respiration.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or OBSERVATION b_b[openEHR-EHR-OBSERVATION.pulse.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or OBSERVATION b_c[openEHR-EHR-OBSERVATION.body_temperature.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or OBSERVATION b_f[openEHR-EHR-OBSERVATION.blood_pressure.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or OBSERVATION b_g[openEHR-EHR-OBSERVATION.indirect_oximetry.v1]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; or OBSERVATION b_h[openEHR-EHR-OBSERVATION.news_rcp_uk.v1])<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; where a/name/value= 'Nursing Vital Signs Observations'<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; order by a/context/start_time/value desc***

In the Ad-hoc query window click on ***Params*** and enter the query string into the ***Value*** field on the right hand side, then click the ***Send*** button.

<img src="\images\RunAQLQuery.jpg" alt="Run AQL Query" width="50%" height="50%">

The result set contains the last 5 vital signs compositions and the data points within the compositions.

<img src="\images\RunAQLQueryResult.jpg" alt="AQL Query Result" width="50%" height="50%">

## Close Session
The final step is to close the openEHR session.

To do this, navigate to the ***session*** folder and select ***Delete Session***. Click on the ***Send*** button.

The result will show a null sessionId, indicating that there is no open session.

<img src="\images\CloseSession.jpg" alt="Close Session" width="50%" height="50%">
