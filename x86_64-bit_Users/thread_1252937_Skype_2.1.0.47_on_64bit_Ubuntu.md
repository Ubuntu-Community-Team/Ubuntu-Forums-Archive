---
title: "Skype 2.1.0.47 on 64bit Ubuntu"
date: 2009-08-29
forum: x86 64-bit Users
---

### Post by hexmode on 2009-08-29
(Cross posted: [http://forum.skype.com/index.php?act=ST&f=18&t=412841](http://forum.skype.com/index.php?act=ST&f=18&t=412841))
Summary:

Yay! it starts! Testing video and sound and they seem to work. A test call fails, though. I can see it start, but after the first second or so, it just counts off seconds. After attempting a test call, it fails when I try to quit.  Any ideas for debugging?

Details:

I'm trying to get skype to work on 64bit Ubuntu Karmic and 64bit Jaunty. For Karmic, I get:
[INDENT][FONT="Courier New"]
    $ skype
    skype: symbol lookup error: /usr/lib32/libQtGui.so.4: undefined symbol: XkbSetPerClientControls[/FONT][/INDENT]



A bit of searching and I try:

[INDENT][FONT="Courier New"]    $ LD_PRELOAD=/usr/lib32/libX11.so skype
    Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
    Segmentation fault (core dumped)
[/FONT][/INDENT]


Removing the package libcanerra-gtk-module at least drops the message, but doesn't solve the segfault:
[INDENT][FONT="Courier New"]
    $ LD_PRELOAD=/usr/lib32/libX11.so
    Segmentation fault (core dumped)
[/FONT][/INDENT]


An strace includes this just before the segfault:

[FONT="Courier New"][INDENT]    connect(17, {sa_family=AF_FILE, path="/tmp/.ICE-unix/@/tmp/.ICE-unix/4835"}, 37) = -1 ENOENT (No such file or directory)[/INDENT][/FONT]



Finding

[INDENT][FONT="Courier New"]    SESSION_MANAGER=local/dococt:@/tmp/.ICE-unix/4835,unix/dococt:/tmp/.ICE-unix/4835[/FONT][/INDENT]


in my environment, I suspect this is causing the crash. So I set SESSION_MANAGER and try again:


[FONT="Courier New"][INDENT]    env SESSION_MANAGER=local/dococt:4835 LD_PRELOAD=/usr/lib32/libX11.so skype 
[/INDENT][/FONT]


Yay! it starts! Testing video and sound and they seem to work. A test call fails, though. I can see it start, but after the first second or so, it just counts off seconds. After attempting a test call, it fails when I try to quit.


For Jaunty, it starts up out of the box. And when I make a test call, I can hear the other side of the conversation. But then, after 30seconds, skype crashes with:

[FONT="Courier New"][INDENT]    E: pstream-util.c: Assertion 'p' failed at pulsecore/pstream-util.c:36, function pa_pstream_send_tagstruct_with_creds(). Aborting.
    Aborted[/INDENT][/FONT]

---

### Post by hexmode on 2009-08-29
Just tried the static version.  It worked on Karmic.  On Jaunty, everything but sound worked.  That is, I could hear the other person, but they couldn't hear me.  They could see me, though.  Yes, I checked that my mic wasn't muted.

---

### Post by timgood on 2009-08-30
The new Skype will only see PulseAudio if you have it installed, and so does not allow you to choose different devices for ringing in, for example. While you can use PulseAudio Volume Control to set a device like a USB phone to be the default output and input, you can't set the ringer to be on a different device, like the sound card. This lack of functionality makes it less useful than the older version.

---

### Post by Rubadubdub on 2009-10-21
My skype works fine in when I start it the following way:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

hope it helps you

---

### Post by LarryMi on 2009-10-28
> **Rubadubdub said:**
> My skype works fine in when I start it the following way:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

hope it helps you

[Rubadubdub]("http://ubuntuforums.org/member.php?u=348912") 

Thank you for the command!

Is there a way to add this command to System,Preferences,Internet,Skype's command line so others won't have to open a terminal?  

I'm running 9.10 64 bit and downloaded "Skype" and "Skype Common" from the [Medibuntu]("http://packages.medibuntu.org/karmic/index.html") page yesterday.  This didn't work as well as the version directly from Skype.  I noticed some have downloaded the "Skype-static" version.  Is the version directly from Skype the correct version to use?

Lastly, even though I can see myself on Skype's: Options, Video Devices, Test screen, I do not see anything which allows me to place a Video Call on my contacts list, even though they have called me successfully using their webcams (Vista) and obviously have their cams setup correctly.  Any idea how I can place a Video Call?

Thanks for all you time, and your command!

---

### Post by 86rocco on 2009-10-29
I am having a similar problem.  I am trying to run this version of skype on 64bit Ubuntu as well.  The skype program seemed to install and work the way it is supposed to.  However, I try to set up the input output and ringing device in skype and my only option is pulse audio.  So, I can hear things through my speakers and I do not have a microphone so a two way conversation is not possible.  

I have tried to go into through system, preferences, sound and select input output device there and select my phone (it shows up there) but when I do that then all my audio, whether it is from a CD, web video, or whatever is then routed through the phone instead of computer speakers.

At this moment in time skype is useless to me and I am not sure what to try.  I am fairly new to Linux so if the command line info above would help me I am unaware.

Sorry for such a long post.  If there are any suggestions, I would appreciate it.
I have Ubuntu 9.10 and the skype phone in question is a Philips_VOIP080.

Skype works normally on other distros and OS's.
thanks.

---

