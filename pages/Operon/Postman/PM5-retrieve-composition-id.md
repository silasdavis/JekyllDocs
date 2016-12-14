---
title:  "Retrieve composition Id"
permalink: PM5-retrieve-composition-id.html
---

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
