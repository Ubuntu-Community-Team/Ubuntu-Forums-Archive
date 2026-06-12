---
title: "Working Java Plugin on 64-bit Ubuntu Gutsy?"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by mtrainer on 2008-08-25
Hi,

Apparently the latest iced-tea browser plugin is working properly with signed applets etc. on 64-bit Ubuntu 8.04.  Is it going to be made to work on Ubuntu 7.10? 

Thanks

Murray

---

### Post by Thelasko on 2008-08-25
I don't think it's likely.  If you really want Java to work, I would wait a bit and then upgrade to Intrepid.  I hear it has the best version of OpenJDK.

---

### Post by Ehtetur on 2008-08-25
> **mtrainer said:**
> Is it going to be made to work on Ubuntu 7.10?

Hrmmmm... [Backports]("https://help.ubuntu.com/community/UbuntuBackports") anyone?

You can check and see if the iced-tea browser plugin is already available as a backport.. If it's not, you could request it.

---

### Post by Thelasko on 2008-08-26
> **Ehtetur said:**
> Hrmmmm... [Backports]("https://help.ubuntu.com/community/UbuntuBackports") anyone?

You can check and see if the iced-tea browser plugin is already available as a backport.. 

I did that before I posted my previous comment.

---

### Post by xen-uno on 2008-08-26
I can say that x64 Hardy's stock Java implementation has worked with every applet I've tried plus my bank's account web page right out of the box. I could never get it working properly no matter what I tried with Gutsy. Flash works a hell of a lot better too though there is some tearing on playback and once in a while it does not start up the video (hangs on the load ... black boxed).

---

### Post by prostar on 2008-08-29
I see a few comments saying that they haven't had a problem.  I've had about 1 in 4 pages give me a problem.  Most annoying is the photo upload tools at Walmart or [www.photolab.ca](www.photolab.ca).  Also random tools like a [mortgage calculator]("http://www.jeacle.ie/mortgage/ca/") don't work for me either.

If you can run that on x64 I'd like to know what versions or FF and Java stuff you are using.

---

### Post by Sef on 2008-08-29
Have you seen [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz") on installing 32-bit firefox with java?

---

### Post by xen-uno on 2008-08-31
Mort Calc doesn't work for me either so your not alone.

---

### Post by prostar on 2008-08-31
> **Sef said:**
> Have you seen [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz") on installing 32-bit firefox with java?

Yeah, but I keep saying to myself, why go that route and have to maintain it when Java is due out this summer?  Still holding out hope it's "any day now".  It kinda hurts the wife acceptance factor though....

Xen: thanks for the info, so I'm not crazy.

---

### Post by IntuitiveNipple on 2008-09-01
> **prostar said:**
> Most annoying is the photo upload tools at Walmart or [www.photolab.ca](www.photolab.ca).  Also random tools like a [mortgage calculator]("http://www.jeacle.ie/mortgage/ca/") don't work for me either.
I've fixed this bug. It is referenced in [Launchpad Bug #199732 "applet fails to load with nullpointerexception"](https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/199732)

I'm uploading the fixed package to my PPA for testing right now. It'll take a while (several hours) to build but then should be available for installation from there (after adding my PPA to apt's sources list, and updating the package-list, install openjdk-6-jre - the version will be 6b11-2ubuntu3~ppa1h or later).

The fix handles the case where a web-site author uses an <EMBED> tag for the applet but doesn't specify the main Java class (the entry-point) using a CODE attribute.

The patch *does not* fix situations where the web-site author doesn't specify WIDTH or HEIGHT attributes in the <EMBED> tag.

To monitor the loading of applets at the console, open a terminal and start firefox:
```

firefox

```
When you visit a site with an applet embedded the GCJ IcedTea plugin handler will start **pluginappletviewer** and start communicating with it. You'll see a comprehensive log of the messages sent between the two, including any exceptions that cause the applet to fail.

If you see something like:
```

Warning: <embed> tag requires width attribute.

```
then the EMBED tag is missing the WIDTH attribute (and probably the HEIGHT attribute too).

Please make success/failure reports to the bug report, not this thread.

```

openjdk-6 (6b11-2ubuntu3~ppa1h) hardy; urgency=low

  * PluginAppletViewer: accept PARAM tags inside EMBED and try to translate
    "classid" to "code" so appletviewer has a start-up class, before deciding
    to nullify all attributes. LP #199732

 -- TJ <ubuntu@tjworld.net>  Mon, 1 Sep 2008 06:00:00 +0100

```

---

### Post by Thelasko on 2008-09-02
> Please make success/failure reports to the bug report, not this thread.
I know, I know, but I figure I should let people in the thread know what happened too.

The applet loads, but I can't print.  The display is also difficult to read (see attached image).

This does not solve the Facebook photo uploader issue.

---

### Post by Thelasko on 2008-09-02
In my opinion, [this bug]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/207064") is still the number one issue with OpenJDK, as I discovered when I wrote [this thread]("http://ubuntuforums.org/showthread.php?t=890143&highlight=java").

Thank You, IntuitiveNipple, for your hard work.:)

---

### Post by IntuitiveNipple on 2008-09-02
> **Thelasko said:**
> In my opinion, [this bug]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/207064") is still the number one issue with OpenJDK, as I discovered when I wrote [this thread]("http://ubuntuforums.org/showthread.php?t=890143&highlight=java").

There's a new IcedTea plug-in that supports LiveConnect. I'm currently testing it. It could be available pretty soon.

---

### Post by prostar on 2008-09-09
Thanks for the info!  I'm glad to see progress, I wouldn't expect printing from Java to work anyway.  If it did, I'd go buy a lottery ticket...

Where can we keep track of when an updated plugin might be released?

---

### Post by Sef on 2008-09-10
>  Where can we keep track of when an updated plugin might be released?

[Early 2009]("http://ubuntuforums.org/showthread.php?t=774956").

---

