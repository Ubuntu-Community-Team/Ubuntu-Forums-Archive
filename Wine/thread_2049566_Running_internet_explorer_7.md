---
title: "Running internet explorer 7"
date: 2012-08-28
forum: Wine
---

### Post by Stephenkboyer on 2012-08-28
I have an issue where I have installed ie7 in wine and it seems to work ok. I can brows to google etc. but I can't access Microsoft Dynamics CRM which only supports ie7 or newer. When I try to go there I get this error (HTTP Error 401.1 - Unauthorized: Access is denied.) I don't know what could be wrong but any suggestions would be appreciated.

---

### Post by Terl on 2012-08-28
What are you trying to do there exactly?  Is this the site?  [http://crm.dynamics.com/en-us/home]("http://crm.dynamics.com/en-us/home")  If it is it works for me in google chrome browser.

EDIT:  If this one:  [http://crm.dynamics.com/en-us/on-demand]("http://crm.dynamics.com/en-us/on-demand")  it hangs...

Bear in mind, not all things windows/microsoft are going to work perfectly under Wine...  You may have to run windows in a virtual machine to get this to work right.

---

### Post by Stephenkboyer on 2012-08-28
No, its actually [https://mscrm.optos.com](https://mscrm.optos.com). I need to be able to access it for work.

---

### Post by Futant on 2012-08-28
Ignore my post! Came before your reply :P

---

### Post by Stephenkboyer on 2012-08-28
I'm using firefox and it does the same error except it says it's an unsupported browser.  I have done some research on MS Dynamics CRM and the developers say that the latest version of Dynamics CRM will support Fireforx, Chrome etc. but I think we are using last years version.  

Is it prompting you to put in the credentials?  Because when I do it gives me the HTTP Error 401.1

---

### Post by Terl on 2012-08-28
Have you tried Chrome?  I hit your link and was prompted immediately for a user and password (which of course I do not have :) ).

Worth a shot...

EDIT:  I get prompted for credentials using chrome... it is an easy download and is in software center... faster than firefox too

---

### Post by Stephenkboyer on 2012-08-28
Yeah, I have it installed and just tried it. Same thing again it says it's a unsupported browser.

---

### Post by Terl on 2012-08-29
If you have a copy of windows, you may want to try the VM route.  My son used to work from home via a VM install of windows on his Ubuntu machine.  That way you'd have all the windowy things the site may require

---

