---
title: "Upgrading wine, no audio, winetricks GUI missing from dash"
date: 2013-04-19
forum: Wine
---

### Post by IdoSC on 2013-04-19
Hello, 3 problems with Wine:
1. "$ wine --version" returns 1.5.20. I'm trying to install v1.5.28 from the PPA, though "$ sudo apt-get install wine1.5" states that "wine 1.5 is already installed". How do I upgrade wine? (would rather not build from source, but I'll do that if there's no other choice).
2. My wine installation doesn't play sound. How do I fix that?
3. Since upgrading to Ubuntu 13.04, I can only access winetricks' GUI using the terminal command; it's missing from the Dash. Any way to fix that?

Thanks in advance, if any info is missing please let me know.

---

### Post by dino99 on 2013-04-22
wine1.5 is only an empty metapackage to point to the latest release (1.5.28)

for ease, install & use synaptic
about sound, test it inside winecfg
about dash app: [http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps](http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps)

---

### Post by IdoSC on 2013-04-27
> **dino99 said:**
> wine1.5 is only an empty metapackage to point to the latest release (1.5.28)

for ease, install & use synaptic
about sound, test it inside winecfg
about dash app: [http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps](http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps)
I installed it (using Synaptic) but winecfg still shows it's version 1.5.20.
I tested it inside winecfg but there's no output and I only have "(System default)" as options in all of the lists there.
You misunderstood me about the dash app, I want the dash app for winetricks (like it used to be in 12.10), not for a Windows (Wine) app.

---

### Post by VietCanada on 2013-04-29
Open the Terminal.
type:
cd /usr/bin
This where the winetricks program should be. You can navigate there by clicking on 'files' and then 'computer' then usr and bin of course, just to be sure.
Then type:
winetricks --gui
That should open winetricks. If you close the terminal winetricks will close as well since the terminal is running it. So don't close the terminal until you are finished doing what you want with winetricks.

---

