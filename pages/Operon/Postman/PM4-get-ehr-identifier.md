---
title:  "Get EHR Identifier"
permalink: PM4-get-ehr-identifier.html
---

The next step is to get the patient’s internal EHR identifier by sending their external identifier (in this case NHS Number). The ehrId is a unique string which, for security reasons, cannot be associated with the patient, if for instance their openEHR records were leaked.

Select ***Get ehrStatus from subjectId*** in the ***ehr*** folder and then click on the ***Send*** button. Again, the patient’s NHS number is taken from the Pre-sets file and is therefore filled in automatically.

<img src="/images/GetEHRId.jpg" alt="Get EHRId">

Click on the ***Scroll to responses*** button in the bottom right hand corner to display the response details.

The JSON snippet below shows the ehrId for our dummy patient.

<img src="/images/GetEHRIdResult.jpg" alt="Display EHRId" width="50%" height="50%">

To store the returned ehrId as a pre-set for the selected environment, highlight the string in the response details, right mouse click, set the environment (*C4H Ripple OSI in this example*) and then select ***ehrId*** from the list of attributes.

<img src="/images/StoreEhrIDAsPreset.jpg" alt="Store EHRId" width="50%" height="50%">
