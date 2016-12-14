---
title:  "Run AQL query"
permalink: PM8-run-aql-query.html
---

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
