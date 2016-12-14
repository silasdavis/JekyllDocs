---
title:  "Create Session"
permalink: PM3-create-session.html
---

The first step is to create an openEHR session and retrieve the ***sessionId*** token. This allows subsequent API calls to be made without needing to login on each occasion.

Navigate to the ***session*** folder and highlight ***Create Session*** on the left, then click on the ***Send*** button. The required credentials are automatically filled in from the Pre-sets file (see ***Navigating Postman*** section above)

<img src="/images/CreateSession.jpg" alt="Create Session" width="50%" height="50%">

Click the ***Scroll to responses*** button in the bottom right hand corner to display the response details.

The screenshot below shows the session Id which has been returned in the call.

<img src="/images/CreateSessionResult.jpg" alt="Session ID" width="50%" height="50%">
