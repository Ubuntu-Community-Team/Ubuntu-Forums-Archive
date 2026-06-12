---
title: "Skypemate or USB phone adaptor for AMD64 Hardy?"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by uMuppet on 2008-08-17
I have dug around alot and cannot find a suitable piece of software to replicate my skypemate in windows.  This is the last thing stopping me from running Ubuntu as a primary OS.  Please help, I am so sick of seeing that windows logo on startup.

There are a few out there 
[http://kb2kskype.sourceforge.net/](http://kb2kskype.sourceforge.net/)
[http://www.usbphoneworld.com/fido.html](http://www.usbphoneworld.com/fido.html)

but none for AMD64 Hardy.  Can someone compile a kb2k for me?  I'm confident with Ubuntu but when it comes to compiling, making etc I'm lost.

Thanks.

---

### Post by cariboo on 2008-08-18
If you download the file from your second link it is a precompiled install script these are pretty easy to use in a terminal cd into the directory you downloaded the file to if you haven't changed the download directory in firefox it is probably on your desktop so:

```
cd ~/Destop
```

Which will put you in the Desktop directory then

```
sudo chmod +x install-SkypeMate
```

This will make the install file executeable next install it:

```
sudo ./install-SkypeMate
```

It will ask you whether you want to install it or not, say yes

From here you're own your own.

Jim

---

### Post by uMuppet on 2008-08-20
after following your instructions it all looks like its working, but sfter I type "I" it pops up the alsamixer with 2 channels on it.  Not too sure what to do there so I esc and I get this error,

```
/Desktop$ sudo ./install-SkypeMate


    SkypeMate Version == v 1.1.0.1

    i(I) == Install SkypeMate program.
    q(Q) == Exit install SkypeMate program.
    Please input your select:i

alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory

```

any ideas what that is?  Anything to do with my Alsa mixer?

---

### Post by schurtek on 2008-08-26
I have the USB-P4K phone, and I would like to use it in my linux... just can't get SkypeMate to install. It tells me that there is a problem with the phone. It works fine in Windoze...

---

### Post by uMuppet on 2008-08-28
I still can't get this software to work.  Has anyone got skypemate running on Hardy 64?

This is the last piece of software keeping me in dual boot with windows.

Help anyone?

---

### Post by altariel on 2008-09-07
I would gladly help you to compile this on a 64box! 
I don't have ANY possibility to compile the packages on a 64 version myself ... 
but PM me and we could perhaps sort it out online in a chat-session?

---

### Post by uMuppet on 2008-09-07
> **altariel said:**
> I would gladly help you to compile this on a 64box! 
I don't have ANY possibility to compile the packages on a 64 version myself ... 
but PM me and we could perhaps sort it out online in a chat-session?

That sounds great.  I would definitely need help with this.  Will PM you soon...

---

### Post by GrahamM on 2008-12-31
> **uMuppet said:**
> after following your instructions it all looks like its working, but sfter I type "I" it pops up the alsamixer with 2 channels on it.  Not too sure what to do there so I esc and I get this error,

```
/Desktop$ sudo ./install-SkypeMate


    SkypeMate Version == v 1.1.0.1

    i(I) == Install SkypeMate program.
    q(Q) == Exit install SkypeMate program.
    Please input your select:i

alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory

```

any ideas what that is?  Anything to do with my Alsa mixer?

I am trying to install Skypemate on my I-I system (32bit) but get to same screen and don't know where to go from there. Phone shows up in Device manager

I got it to work, but without button functionality - Received a lot of error messages because it seemed to be wabting to use dbus or something. Decided enough of that and scrubbed the whole thing! Maybe just a headset would be better for me.

---

### Post by treitmayr on 2009-02-11
> **schurtek said:**
> I have the USB-P4K phone, and I would like to use it in my linux... just can't get SkypeMate to install. It tells me that there is a problem with the phone. It works fine in Windoze...

schurtek,
you may want to try the Python script "YlSkypeConnector" I wrote to replace SkypeMate on Linux. It works with the P1K(H) and the P4K, although on the latter a few keys are non-functional. Support for the B2K and B3G is still untested.

Apart from the actual script an updated yealink kernel module is required, as described here:
[http://www.devbase.at/voip/ylskypeconnector.php]("http://www.devbase.at/voip/ylskypeconnector.php")

-Thomas

---

### Post by schurtek on 2009-02-12
> **treitmayr said:**
> schurtek,
you may want to try the Python script "YlSkypeConnector" I wrote to replace SkypeMate on Linux. It works with the P1K(H) and the P4K, although on the latter not all keys are functional. Support for the B2K and B3G is still untested.

Apart from the actual script an updated yealink kernel module is required, as described here:
[http://www.devbase.at/voip/ylskypeconnector.php]("http://www.devbase.at/voip/ylskypeconnector.php")

-Thomas

Thanks Thomas, but how can I go about supporting all the keys? Is there a way to record the scancodes so that I can add them to the Python Script? I am more of a network programmer...

---

### Post by treitmayr on 2009-02-12
> **schurtek said:**
> Thanks Thomas, but how can I go about supporting all the keys? Is there a way to record the scancodes so that I can add them to the Python Script? I am more of a network programmer...

The kernel module communicates with the USB device and feeds key and hook presses to the Linux input subsystem, i.e. pressing a key on the phone appears no different than pressing a key on your PC keyboard.

Now YlSkypeConnector grabs the input device (/dev/input/eventX) exclusively on startup and waits for key presses reported by this device. The different keys are handled in a function called "_key_press" where you can see that all number keys, *, and # are handled as well as UP/DOWN, DIAL, SEND, DEL.

The other available key codes can be found in the kernel module's source code in yealink.c:

```
/* USB-P4K button layout:
 *
 *	     IN      up     OUT
 *	     VOL+	    DEL
 *	     VOL-   down    DIAL
 *
 *	       1      2      3
 *	       4      5      6
 *	       7      8      9
 *	       *      0      #
 *
 *       HELP                   SEND
 *      FLASH     handsfree     REDIAL
 */

which are mapped to:
		KEY_ENTER,		 	/* DIAL	*/
		KEY_3,				/* 3		*/
		KEY_6,				/* 6		*/
		KEY_9,				/* 9		*/
		KEY_LEFTSHIFT | KEY_3 << 8,	/* #		*/
		KEY_HELP,			/* HELP	*/
		KEY_RIGHT,			/* OUT	*/
		KEY_2,				/* 2		*/
		KEY_5,				/* 5		*/
		KEY_8,				/* 8		*/
		KEY_0,				/* 0		*/
		KEY_ESC,			/* FLASH	*/
		KEY_H,				/* handsfree	*/
		KEY_1,				/* 1		*/
		KEY_4,				/* 4		*/
		KEY_7,				/* 7		*/
		KEY_KPASTERISK,			/* *		*/
		KEY_S,				/* SEND	*/
		KEY_DOWN,			/* DOWN	*/
		KEY_VOLUMEUP,			/* VOL+	*/
		KEY_UP,				/* UP	*/
		KEY_BACKSPACE,			/* DEL	*/
		KEY_LEFT,			/* IN	*/
		KEY_VOLUMEDOWN,			/* VOL-	*/
		KEY_R				/* REDIAL	*/

```
The numeric codes for the KEY_* constants used in the Python code are defined in /usr/include/linux/input.h.

So it should be possible to additionally support VOL+/- for the speaker phone, or REDIAL and handsfree in the Python script. FLASH for switching to a second line might not be that trivial. Not sure what HELP, OUT, or IN are supposed to do.
When I get the time I will add some of the keys mentioned.

-Thomas

---

### Post by altariel on 2009-03-19
I hope to be able to compile the new version and thus make all the packages for the kb2kskype this weekend! :)

---

### Post by altariel on 2009-03-29
> **uMuppet said:**
> 
but none for AMD64 Hardy.  Can someone compile a kb2k for me?  I'm confident with Ubuntu but when it comes to compiling, making etc I'm lost.

Thanks.
packages for amd64 8.0.4.2 LTS are available at sourceforge as of today - but please test them thouroughly and report back any problems!

[https://sourceforge.net/project/showfiles.php?group_id=186708](https://sourceforge.net/project/showfiles.php?group_id=186708)

have begun setting up a ppa on lauchpad, expect them to show up there too shortly

---

