---
title: "CRM Popup application triggering issue"
date: 2017-11-13
forum: Wine
---

### Post by edwinstudios on 2017-11-13
I have Ubuntu 12.04 Desktop installed. Our company has developed a Windows based CRM popup application which triggers any Windows based application or URL via web browser using custom parameters as search string.

There are three different windows involved in this process.

1. Agent logged in to his Dialer window (using Firefox) where he talks to customer directly from browser.
2. CRM popup application is installed and runs in background. This CRM Popup application is configured to popup the client's CRM and opens the web browser by passing the parameter. Assuming the Agent is already logged in to the CRM using valid credentials using Firefox web browser.

The expected sequence is that when a agent receives a call, the CRM popup will read the customer phone number and automatically triggers the CRM window on the firefox browser.

This works on Windows and when we try to replicate the same on Ubuntu OS the Popup application does not perform any actions as it should. While I understand that the application is originally built for Windows it is not designed to run on any other OS's, I tried to make use of Wine installer and installed the windows application successfully.

However I would like to understand why the application cannot work when it is installed. Or what is the workaround.

Vinod

---

