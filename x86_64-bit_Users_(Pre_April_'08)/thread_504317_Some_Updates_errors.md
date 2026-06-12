---
title: "Some Updates errors"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by dryder on 2007-07-19
Hi,
Feisty 64 bit

I just re-installed Feisty 64 bit on a separate drive and there were 89 updates. I immediately started the update process.

During the installing of the updates I got these errors:
```
E: ttf-opensymbol: subprocess post-installation script returned error exit status 66
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
```

Then I tried to install ia32-libs, a32-libs-gtk, ia32-kde from synaptic for something I need and received these errors:
```
E: ttf-opensymbol: subprocess post-installation script returned error exit status 66
E: openoffice.org-core: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
```

The errors seem to revolve around ttf-opensymbol and openoffice.org... which I don't think is just a coincidence.

And this install of feisty 64 bit is quite considerably slower than previously (same drive)

Many thanks,
David

---

### Post by PaulFr on 2007-07-19
Could this be a timezone or time setting issue ? Did you change timezone after installation, or enter a future time while installing and correct it later ?
Please run the command ```
sudo fc-cache -v
``` and see if it gives any failures (**failed to write cache**). If yes, then
1. Make sure you have set the right time and timezone.
2. The following should fix it (please replace <list> to reflect the directories being reported as failures by fc-cache):```
touch /tmp/current_time
sudo find <list> -newer /tmp/current_time -exec touch {} \;

``` Then again run **sudo fc-cache -v** to see if you have any remaining errors. Now try your update. Hope this helps.

---

### Post by dryder on 2007-07-19
Hi PaulFr,

I didn't change the time settings or time at all - I am using local time, not UTC, in the BIOS, XP, Ubuntu (32 bit) and for this 64 bit installation.

The output of sudo fc-cache -v is:
```
/usr/share/fonts: skipping, 0 fonts, 3 dirs
/usr/share/fonts/X11: skipping, 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: skipping, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: skipping, 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: skipping, 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: skipping, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: skipping, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: skipping, 0 fonts, 0 dirs
/usr/share/fonts/X11/util: skipping, 0 fonts, 0 dirs
/usr/share/fonts/truetype: skipping, 0 fonts, 21 dirs
/usr/share/fonts/truetype/arphic: skipping, 2 fonts, 0 dirs
/usr/share/fonts/truetype/baekmuk: skipping, 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: skipping, 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: skipping, 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: skipping, 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: skipping, 27 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: skipping, 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: skipping, 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: skipping, 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: skipping, 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-devanagari-fonts: skipping, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gentium: skipping, 4 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gujarati-fonts: skipping, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: skipping, 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: skipping, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: skipping, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-mgopen: skipping, 16 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: skipping, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: skipping, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: skipping, 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: skipping, 2 fonts, 0 dirs
/usr/share/fonts/type1: skipping, 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: skipping, 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, 0 fonts, 6 dirs
/usr/share/X11/fonts/100dpi: skipping, 0 fonts, 0 dirs
/usr/share/X11/fonts/75dpi: skipping, 0 fonts, 0 dirs
/usr/share/X11/fonts/Type1: skipping, 8 fonts, 0 dirs
/usr/share/X11/fonts/encodings: skipping, 0 fonts, 1 dirs
/usr/share/X11/fonts/encodings/large: skipping, 0 fonts, 0 dirs
/usr/share/X11/fonts/misc: skipping, 0 fonts, 0 dirs
/usr/share/X11/fonts/util: skipping, 0 fonts, 0 dirs
/usr/local/share/fonts: skipping, 0 fonts, 0 dirs
/home/david64/.fonts: skipping, no such directory
/var/lib/defoma/fontconfig.d: skipping, 0 fonts, 24 dirs
/var/lib/defoma/fontconfig.d/A: skipping, 8 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: skipping, 11 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/C: skipping, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: skipping, 24 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/E: skipping, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/F: skipping, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/G: skipping, 12 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: skipping, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: skipping, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/K: skipping, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/L: skipping, 10 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/M: skipping, 19 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/N: skipping, 25 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/O: skipping, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/P: skipping, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/R: skipping, 3 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/S: skipping, 7 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/T: skipping, 22 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: skipping, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/V: skipping, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: skipping, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/j: skipping, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: skipping, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: skipping, 1 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/david64/.fontconfig: cleaning cache directory
fc-cache: succeede

```
David

---

### Post by PaulFr on 2007-07-20
1. The postinst function for ttf-opensymbol seems to be calling the command **fc-cache -fs**.
2. The only difference between ttf-opensymbol_2.2.0-0ubuntu2_all.deb and ttf-opensymbol_2.2.0-1ubuntu4_all.deb is that in the post-installation of the latest ttf-opensymbol_2.2.0-1ubuntu4_all.deb package, the command being run is ```
if [ "$1" = "configure" ] && [ -x /usr/bin/fc-cache ] && [ -e /etc/fonts/fonts.conf ]; then
        echo "Updating fontconfig cache..."
        fc-cache -fs
fi
``` whereas in ttf-opensymbol_2.2.0-0ubuntu2_all.deb, the postinst is```
if [ "$1" = "configure" ] && [ -x /usr/bin/fc-cache ] && [ -e /etc/fonts/fonts.conf ]; then
        echo "Updating fontconfig cache..."
        fc-cache -f
fi
```. Note the difference in the arguments. The -s indicates that the font cache should be only be created for the system-wide directories only.

***Update:*** -s in the fc-cache command implies run only in the system directories rather than running it for both system and user directories. This should not matter. So the difference pointed out above may not be your problem.

***Suggestion:*** If you have the time, maybe you can try ```
cd /var/cache/apt/archives
sudo dpkg -i ttf*deb
``` to see if you get the same error message. If so, the error is in the ttf package itself (check the version of the package). Then ```
sudo strace -f -o /tmp/pkgcall.log dpkg -i ttf*deb
``` will put all the system calls in /tmp/pkg_inst.log (which will be a large file). The error will be reflected in the last 1000 or so lines.

On the other hand, if some one else has already diagnosed this problem, please help.

---

### Post by styracosaurus on 2007-07-20
I am not running Ubuntu 64 bit, I am running Kbuntu on an x86 machine, I just installed and got very similar errors, however after trying 

sudo fc-cache -v

I got "failed to write to cache" errors. PaulFr, you said to insert a list of directories instead of <list> but there are many directories that have this error. Can I point it to a file or something? Or should they just come one after another on the command line?

Thanks!

---

### Post by PaulFr on 2007-07-20
Instead of doing all the directories you can take the parent directory. For example, in my machine, these are the  recognizable parent directories:
[LIST=1]
[*]/usr/share/fonts
[*]/usr/share/X11/fonts
[*]/var/lib/defoma/fontconfig.d
[*]/var/cache/fontconfig
[*]~/.fonts
[*]~/.fontconfig
[/LIST]
So I would issue the command ```
touch /tmp/current_time
sudo find /usr/share/fonts /usr/share/X11/fonts /var/lib/defoma/fontconfig.d ~/.fonts ~/.fontconfig  -newer /tmp/current_time -exec touch {} \;
``` FYI, this command is safe - it just makes sure that any file in these font directories that has a time stamp in the future is touched so that the timestamp is slightly in the past. It will not touch any file whose timestamp is already in the past.

---

### Post by PaulFr on 2007-07-20
Since dryder mentioned local timezone, please see **[http://ubuntuforums.org/showpost.php?p=1049744&postcount=7](http://ubuntuforums.org/showpost.php?p=1049744&postcount=7)** for another possibility - Linux puts the BIOS in UTC by default

---

### Post by lerum on 2007-07-20
Thanks PaulFr, got it working eventually :)
Just did a clean install of the x86 version.

---

### Post by dryder on 2007-07-20
> Since dryder mentioned local timezone, please see [http://ubuntuforums.org/showpost.php...44&postcount=7](http://ubuntuforums.org/showpost.php...44&postcount=7) for another possibility - Linux puts the BIOS in UTC by default

Umm ... no, at least not in Feisty 64 bit Alternative. My BIOS clock is left unchanged at local time, NOT been changed to UTC.

It's default prompts assume UTC but if one says 'no' then it leaves (my) the BIOS clock alone.

David

---

### Post by dryder on 2007-07-20
> Suggestion: If you have the time, maybe you can try
Code:

cd /var/cache/apt/archives
sudo dpkg -i ttf*deb

to see if you get the same error message


Did this without errors. However, I can't get the updates to download again and they show installed in Synaptic. Is the a terminal command that will force the re-download and install of the updates?

Many thanks,
David

David

---

### Post by Anandavala on 2007-07-30
**This post could be related to an Ubuntu bug filed at**: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg400606.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg400606.html) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem but since coming to this page it all seems to be working well.

I'm running Feisty 7.04 and many packages wouldn't install because of ttf-opensymbol.

I ran ```
sudo fc-cache -v
``` and got nothing but errors. But after following PaulFr's advice I then ran ```
sudo apt-get install ttf-opensymbol
``` and the whole openoffice package installed fine - since then everything is *sweet*...            Thanks guys :)

---

