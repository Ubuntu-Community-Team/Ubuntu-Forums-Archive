---
title: "Hardy problem with Plasma screen"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by debaser42 on 2008-05-08
I was running Gutsy for a while on my AMD64 and using an nvidia geforce6150 - getting 720p (1280x768 i think, but it might have been 1366x768). I upgraded and was having some problems so I did I clean install of Hardy. It went down to 800x600 After updating all software and enabling the nvidia driver I rebooted and it will only display now at 640x480. I've tried nvidia-settings, and it won't detect my display like it did before with xorg config in Gutsy. I can't seem to get it to use any other resolution with my plasma.

Additionally, if I plug it into my dell 20.1 widescreen and reboot it works fine - i can then put the resolution on to whatever I want, and then plug it back into my plasma and it will be fine (within viewable by the plasma) until I reboot. Then back to 640x480. This is obviously not a permanent solution.

My display is a Visio 42" Plasma and I'm running the VGA cable straight from the computer into the TV. It should detect it (as xorg did in Gutsy - came up with V42 or something and worked fine) - but now when I try to run xorg config it only goes through the questions for my keyboard and won't configure my monitor.

I figure either there's a fix out there or some way to roll back and use an older driver so I can run xorg config and force it to recognize my tv again. But I'm a n00b and have no idea what I'm doing past the basics. 

Thanks in advance for suggestions I really don't ever want to go back to xp to run my media server.

---

### Post by reidman on 2008-06-18
Having a similar problem. Installed Ubuntu Hardy on a Shuttle KPC K-4500-RS (which I believe has an Intel GMA 950 chipset) and I'm getting a crazy mishmash of junk on the screen (see picture below).

This is definitely a monitor issue -- I've had problems with this 42" Visio in the past. However, when I try to change the driver/monitor settings, the only options I get are to change the resolution. Can someone explain how to get back to the video driver settings in Hardy? I used to be able to access them from the System > Administration menu in Gutsy, but I can't find that option anymore...

[IMG]http://reidyoung.com/misc/shuttle+ubuntu+visio=dead.jpg[/IMG]

---

### Post by bufsabre666 on 2008-06-18
did you install the proprietary nvidia drivers?

---

