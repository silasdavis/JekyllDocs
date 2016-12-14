---
title:  "Persist Composition"
permalink: PM7-persist-composition.html
---

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
