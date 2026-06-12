---
title: "Green 64-bit skype webcam"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by gontofe on 2008-11-06
Decided on a whim to install 64-bit Intrepid, but can't get Skype to work... I installed the 64-bit version, as suggested by Ubuntu, but my Creative WebCam NX (installed via easycam), doesn't work as expected. I can get it to work fine in cheese, but in Skype I get a green/static screen (see attachments)...

I've looked at this tutorial:

[http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)

But still can't get it to work.

Please let me know which logs you need to see and the required commands to get them!

Thanks in advance,

Mike

---

### Post by peacewithall on 2008-11-06
You could try the commands from this post, I had this green mess too, and this fixed it, unfortunately there is a bug with web-cams in Intrepid, heres the link

[http://ubuntuforums.org/showpost.php?p=6115686&postcount=30](http://ubuntuforums.org/showpost.php?p=6115686&postcount=30)


If the first command don't work, try the next.

Hope this helps :).

---

### Post by gontofe on 2008-11-06
I get this error:

ERROR: ld.so: object '/usr/lib64/libv4l/v4l2compat.so' from LD_PRELOAD cannot be preloaded: ignored.
 

same with /usr/lib/libv4l/v4l2compat.so, /usr/lib64/libv4l/v4l2convert.so and /usr/lib/libv4l/v4l2convert.so

What can I do? I read [here]("http://bugs.gentoo.org/show_bug.cgi?id=240090") that this might not work...

---

### Post by peacewithall on 2008-11-06
Do you have a 64 bit system?, if so check you have both lib32v4l-0 and libv4l-0 installed.

Type this in terminal,


```
sudo apt-get install lib32v4l-0 libv4l-0
```

This will install both 32 and 64 bit libraries.


Then re-try the first step, skype is a 32bit application and if you have 64 bit Intrepid, you will need the 32 bit library to run.

---

### Post by gontofe on 2008-11-06
```
mike@mike-laptop:~$ sudo apt-get install lib32v4l-0 libv4l-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32v4l-0 is already the newest version.
libv4l-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

---

### Post by peacewithall on 2008-11-06
Not sure why your camera is not working, following all those steps made mine work.

All I can advise is keep looking around for a solution, hopefully someone else can post with experience of your particular problem.

Sorry it didn't work.

---

### Post by manuhalo on 2008-11-10
I'm having the same issues as the OP. Tried all of the possible fixes reported here but nothing helped. Incidentally, the webcam (a Logitech QuickCam for Notebooks) works correctly under Cheese. If anyone comes up with a solution, please post it here; I will keep looking for a workaround as well.

---

### Post by gontofe on 2008-11-11
I did a fresh install of Intrepid (32-bit version this time), and to my surprise this still didn't fix the problem, I get a green webcam in Skype, though it works in cheese...

Any ideas now? I've looked at the [sticky thread]("http://ubuntuforums.org/showthread.php?t=966436") in the General Help section, but that method doesn't work either :(

Mike

---

### Post by Jimtheplanner on 2008-11-11
Hi Folks,

I've had similar issues using Mandriva 2009 as I have with 8.10. I had Ekiga working in Mandriva with video output but Skype came up with the "Green Screen".

I'm also looking for an answer...

Regards

Jim

---

### Post by stmiller on 2008-11-11
It's either that you need a more updated v4l driver, or that the software is trying to do some sort of color adjust that you do not need. Try to disable any automatic color adjustment if that is possible.

Is the picture green when running xawtv?

If another video app looks OK, then it is some sort of color control in Skype causing trouble. If everything looks green in ALL apps, then it is potentially a driver issue. :/

---

### Post by gontofe on 2008-11-12
@stmiller

Have a look at the screenshot I posted, it's not just a green cast to the image, it's totally corrupted and partially static-filled...

---

### Post by Romu on 2009-02-23
I had the problem and fix it by modifying the file <user>/.Skype/<user>/config.xml and add the following line in the "video" section:

```
    <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <RecvPolicy>callpolicy</RecvPolicy> 
```

Of course change the resolution to fit your webcam capabilities.

---

### Post by gontofe on 2009-03-13
Strange...this didn't work for me...

I couldn't find the video section, so I deleted the config.xml file...when Skype recreated it, it still didn't have a video section in it until I change the video options. When I pasted this new section in, it still didn't work :(

---

