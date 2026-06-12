---
title: "Wine, WineASIO, QjackCtl and FL Studio 11"
date: 2013-09-06
forum: Wine
---

### Post by matt-wendel on 2013-09-06
I've been trying to get this to work for the past 5 hours. And yet, no avail...

So i've installed wine, wineasio, jack, and qjackctl. The WineASIO.dll registered fine with wine's regsvr32. The option for using the 'WineASIO' audio hardware is even available in FL Studio! When I try to load it, it fails, and crashes.

I have a problem with jack though. Every time i try and start a server, it gives me all this poop about me not being able to start a server (I'm not sure if D-BUS has anything to do with it? I'm kindof a noob when it comes to Ubuntu, especially low-level driver interfaces). Jack gives me this:

 ```
[COLOR=#999999]04:01:24.640 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]04:01:24.648 Statistics reset.[/COLOR]

 [COLOR=#cccc99]04:01:24.652 ALSA connection change.[/COLOR]
 [COLOR=#999999]04:01:24.680 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#66cc99]04:01:24.700 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]04:01:33.009 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Fri Sep  6 04:01:32 2013: Starting jack server...

 Fri Sep  6 04:01:32 2013: JACK server starting in realtime mode with priority 10
 Fri Sep  6 04:01:32 2013: [1m[31mERROR: Cannot lock down 107335194 byte memory area (Cannot allocate memory)[0m
 Fri Sep  6 04:01:32 2013: [1m[31mERROR: Can't load "/usr/lib/x86_64-linux-gnu/jack/jack_alsa.so": /usr/lib/x86_64-linux-gnu/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init[0m

 Fri Sep  6 04:01:32 2013: [1m[31mERROR: Cannot initialize driver[0m
 Fri Sep  6 04:01:32 2013: [1m[31mERROR: JackServer::Open failed with -1[0m

 Fri Sep  6 04:01:33 2013: [1m[31mERROR: Failed to open server[0m
 Fri Sep  6 04:01:34 2013: Saving settings to "/home/matt/.config/jack/conf.xml" ...
 [COLOR=#ff0000]04:01:39.869 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


```

I'm not sure where to go from here on properly initiating the ASIO driver. Here's some specs on my system

Version: ubuntu 13.04
Processor: AMD Phenom(tm) II N970 Quad-Core Processor × 4
OS Type: 64-bit
Audio Card: High Deffinition Audio (Realtek Audio) on hw0



PLEASE HELP ME GET RID OF WINDOWS. THIS IS THE LAST COMPATIBILITY ISSUE I HAVE.

---

