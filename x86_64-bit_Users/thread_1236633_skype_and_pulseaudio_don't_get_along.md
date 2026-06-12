---
title: "skype and pulseaudio don't get along"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by tudor117 on 2009-08-10
Hi,

I realize that there are already many different posts about pulseaudio and skype. However, I tried all of them with all the different configurations and everything they said and skype still refuses to work properly. The sound is **scratchy**, **grainy**, and very **interrupted**. It keeps on giving "**RtApiAlsa: underrun detected.**"

Now if skype never worked for me, I would agree that something is wrong. BUT I got it to work well and the sound was great. But then one day an update came and then skype started misbehaving again.
```

2009-08-07 11:44:21 startup archives unpack
2009-08-07 11:44:35 upgrade ia32-libs 2.7ubuntu6 2.7ubuntu6.1
2009-08-07 11:44:35 status half-configured ia32-libs 2.7ubuntu6
2009-08-07 11:44:35 status unpacked ia32-libs 2.7ubuntu6
2009-08-07 11:44:35 status half-installed ia32-libs 2.7ubuntu6
2009-08-07 11:44:44 status half-installed ia32-libs 2.7ubuntu6
2009-08-07 11:44:45 status unpacked ia32-libs 2.7ubuntu6.1
2009-08-07 11:44:47 status unpacked ia32-libs 2.7ubuntu6.1
2009-08-07 11:44:48 upgrade firefox-3.5-branding 3.5.1+build1+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:48 status half-configured firefox-3.5-branding 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:48 status unpacked firefox-3.5-branding 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:48 status half-installed firefox-3.5-branding 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:48 status half-installed firefox-3.5-branding 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status unpacked firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status unpacked firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 upgrade xulrunner-1.9.1-gnome-support 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status half-installed xulrunner-1.9.1-gnome-support 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status half-installed xulrunner-1.9.1-gnome-support 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:49 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:50 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:50 upgrade xulrunner-1.9.1 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:50 status half-configured xulrunner-1.9.1 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:50 status unpacked xulrunner-1.9.1 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:50 status half-installed xulrunner-1.9.1 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:52 status half-installed xulrunner-1.9.1 1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 status unpacked xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 status unpacked xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 upgrade firefox-3.5-gnome-support 3.5.1+build1+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 status half-configured firefox-3.5-gnome-support 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 status unpacked firefox-3.5-gnome-support 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:53 status half-installed firefox-3.5-gnome-support 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status half-installed firefox-3.5-gnome-support 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status unpacked firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status unpacked firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 upgrade firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status half-configured firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status unpacked firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status half-installed firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:54 status triggers-pending menu 2.1.41ubuntu1
2009-08-07 11:44:55 status half-installed firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:55 status half-installed firefox-3.5 3.5.1+build1+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:55 status triggers-awaited menu 2.1.41ubuntu1
2009-08-07 11:44:56 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:56 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:44:56 upgrade flashplugin-installer 10.0.22.87ubuntu2 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:44:56 status half-configured flashplugin-installer 10.0.22.87ubuntu2
2009-08-07 11:44:58 status unpacked flashplugin-installer 10.0.22.87ubuntu2
2009-08-07 11:44:58 status half-installed flashplugin-installer 10.0.22.87ubuntu2
2009-08-07 11:44:58 status half-installed flashplugin-installer 10.0.22.87ubuntu2
2009-08-07 11:44:58 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:44:58 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:44:58 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1
2009-08-07 11:44:58 status half-configured menu 2.1.41ubuntu1
2009-08-07 11:44:59 status installed menu 2.1.41ubuntu1
2009-08-07 11:45:00 startup packages configure
2009-08-07 11:45:00 configure ia32-libs 2.7ubuntu6.1 2.7ubuntu6.1
2009-08-07 11:45:00 status unpacked ia32-libs 2.7ubuntu6.1
2009-08-07 11:45:00 status half-configured ia32-libs 2.7ubuntu6.1
2009-08-07 11:45:00 status installed ia32-libs 2.7ubuntu6.1
2009-08-07 11:45:00 status triggers-pending libc6 2.9-4ubuntu6
2009-08-07 11:45:00 configure xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:00 status unpacked xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:00 status unpacked xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:00 status unpacked xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:00 status half-configured xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 status installed xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 configure xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 status installed xulrunner-1.9.1-gnome-support 1.9.1.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:01 configure flashplugin-installer 10.0.32.18ubuntu0.9.04.1 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:45:01 status unpacked flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:45:01 status half-configured flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:45:15 status installed flashplugin-installer 10.0.32.18ubuntu0.9.04.1
2009-08-07 11:45:15 configure firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status half-configured firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status installed firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 configure firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:15 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status unpacked firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status half-configured firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status installed firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status triggers-pending menu 2.1.41ubuntu1
2009-08-07 11:45:16 status triggers-awaited menu 2.1.41ubuntu1
2009-08-07 11:45:16 configure firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status unpacked firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status half-configured firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 status installed firefox-3.5-gnome-support 3.5.2+nobinonly-0ubuntu0.9.04.1
2009-08-07 11:45:16 trigproc libc6 2.9-4ubuntu6 2.9-4ubuntu6
2009-08-07 11:45:16 status half-configured libc6 2.9-4ubuntu6
2009-08-07 11:45:17 status installed libc6 2.9-4ubuntu6
2009-08-07 11:45:17 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1
2009-08-07 11:45:17 status half-configured menu 2.1.41ubuntu1
2009-08-07 11:45:18 status installed menu 2.1.41ubuntu1

```I believe that it might have something to do with the **ia32-libs** but can't be sure.
Skype said, in March that they were having an update with better pulseaudio support, but they were working out some little tinks. I doubt it.

I use pulseaudio and alsa from Luke's ppa (as described in [this post]("http://ubuntuforums.org/showthread.php?t=843012")).
Ubuntu Jaunty 64bit.
Skype 2.0.0.72 from skype's website (amd64 version).
One last thing is that I MUST use pulseaudio for skype because I need skype along with other sound solutions at once. This includes jack.

I am open to absolutely anything, except reinstalling ubuntu.

---

### Post by TheBuzzSaw on 2009-08-10
There is a AMD64 version?

---

### Post by tudor117 on 2009-08-10
not really.
it's the 32 bit with solved dependencies.
its at [http://ww.skype.com/go/getskype-linux-ubuntu-amd64]("http://www.skype.com/go/getskype-linux-ubuntu-amd64")
and that's what I have

any ideas?

---

### Post by TheBuzzSaw on 2009-08-10
Ah yeah. That's what I have too. I'm actually interested in the solution in this thread.

When I use Skype, it will work fine for a good 10 minutes, but then the sound suddenly cuts out. Then Skype starts to freeze up. My buddy can still hear my voice, but I cannot hear his. Even after closing Skype, he can still hear me. I have to go in and kill the Skype process directly to get it to finally stop.

---

### Post by tudor117 on 2009-08-10
That's exactly what I used to have. Then I fixed it. Now it's way worst.
Everything is "pop"y including when I'm not talking; i.e. sending messages.

As well when that used to happen, pulseaudio used to consume all the CPU.
...I don't even get that far anymore :(

---

### Post by tudor117 on 2009-08-11
bump

So does any one know what I can do or try?
I also found out that vlc doesn't want to work properly anymore. When I use the "Default" setting for sound output it says
 "[[COLOR=Lime]0x1ba7358[/COLOR]] alsa audio output error: [COLOR=Red]cannot write: Broken pipe[/COLOR]"

I suppose that it has something to do with my problem...
I didnt have that before skype broke either.

---

### Post by tudor117 on 2009-08-13
bump

---

### Post by TheBuzzSaw on 2009-08-13
Pulseaudio blows chunks. I'm wondering if eradicating it altogether would fix this.

---

### Post by tudor117 on 2009-08-14
i beleive its skype's fault
thanks for your replies anyways
hope skype updates and makes it work
till then.... i'll wait....

---

