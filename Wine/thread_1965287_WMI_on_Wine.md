---
title: "WMI on Wine"
date: 2012-04-25
forum: Wine
---

### Post by Fhajad on 2012-04-25
Is WMI possible to work on Wine? I've done winetricks wmi, but it doesn't appear to work as I get this error message each time I try to run my application.


Invalid parameter 
at System.Management.ManagementScope.Initialize() 
at System.Management.ManagementObjectSearcher.Initialize() 
at System.Management.ManagementObjectSearcher.Get() 
At Siemens_EMML.AppIsRegistered.DaysRemaning(Int32 
ProductCode, String Registration, String Signature)

This is a WMI issue, correct? If so, how can I resolve it? I've asked on Wine and Winetricks help, but so far no real luck.

---

### Post by cogadh on 2012-04-25
What application are you trying to run?

---

### Post by Fhajad on 2012-04-25
The application is called Siemens Command Assistant.

---

### Post by cogadh on 2012-04-25
Is this you:
[http://forum.winehq.org/viewtopic.php?t=15235&start=0&postdays=0&postorder=asc&highlight=](http://forum.winehq.org/viewtopic.php?t=15235&start=0&postdays=0&postorder=asc&highlight=)

If so, you should do as suggested and create an AppDB entry for the app as well as file a bug report. If that's not you, then it appears based on that other user's experience that the app simply will not work in Wine yet and you should still do what is recommended in that thread.

---

