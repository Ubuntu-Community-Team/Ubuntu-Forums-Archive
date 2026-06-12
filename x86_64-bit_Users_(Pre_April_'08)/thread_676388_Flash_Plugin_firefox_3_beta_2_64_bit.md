---
title: "Flash Plugin firefox 3 beta 2 64 bit"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ronb94 on 2008-01-23
hello
i need the flash plugin for firefox 3 beta 2 in ubuntu 7.10 64bit.i saw here some links for 32 bit or for 64 but the link is broken,
Thanks

---

### Post by Kilz on 2008-01-23
> **ronb94 said:**
> hello
i need the flash plugin for firefox 3 beta 2 in ubuntu 7.10 64bit.i saw here some links for 32 bit or for 64 but the link is broken,
Thanks

You can install the the flash plugin and [nspluginwrapper with this script. ]("http://ubuntuforums.org/showthread.php?t=476924") then we can copy over the wrapped flash plugin to the plugin directory of the flash beta. Where do you have the firefox 3.0 beta 2 installed to?

---

### Post by ronb94 on 2008-01-23
the links before didnt worked:confused:
nevermind  amm i dont know where is my firefox is installed i didnt uninstalles the stable version of firefox so i have 2 firefoxes.

---

### Post by Kilz on 2008-01-23
I just double checked. links work.

---

### Post by jamesford on 2008-01-23
how do u install the new firefox anyway ?

---

### Post by ronb94 on 2008-01-23
i told that 30 min ago the link didnt worked now they works. i downloaded and installed.

---

### Post by potrzebie on 2008-01-27
I find myself also using Firefox 3 Beta 2 on Gutsy amd64. I installed it following the instructions [here]("http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710"), and it works very well. I installed flash using Kilz's script in the [big thread]("http://ubuntuforums.org/showthread.php?t=476924"), and it does work beautifully for Firefox 2, but not Firefox 3. I tried copying the wrapped plugin from /usr/lib/firefox/plugins to /usr/lib/firefox-3.0/plugins but flash still doesn't work in firefox 3, only 2. I haven't tried anything else yet, I'll be reading through the other thread (now at 72 pages!) and elsewhere in the forums but in case anyone knows if I'm missing something simple I'd like to know.

Neverthelss, the script works flawlessly for Firefox 2, and for that you're getting thanked, kilz.

**Inormations....**

Installed the newer Flash plugin via [nspluginwrapper-install-0-1.8.5-3.tar.gz]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz").

:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 sherman users    4096 2008-01-27 17:38 .
drwxr-xr-x 3 root    root     4096 2007-10-15 18:27 ..
-rwxr-xr-x 1 sherman users 8119784 2007-11-20 17:24 libflashplayer.so
lrwxrwxrwx 1 sherman users      36 2008-01-19 17:13 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 sherman users      37 2008-01-19 17:13 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 sherman users      34 2008-01-19 17:13 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 sherman users      35 2008-01-19 17:13 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 sherman users      36 2008-01-19 17:13 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 sherman users      37 2008-01-19 17:13 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 sherman users      42 2008-01-19 17:13 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 sherman users      43 2008-01-19 17:13 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 sherman users      60 2008-01-27 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 sherman users  4096 2008-01-27 17:38 .
drwxr-xr-x 5 root    root   4096 2008-01-19 23:49 ..
lrwxrwxrwx 1 sherman users    36 2008-01-19 17:13 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 sherman users    37 2008-01-19 17:13 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 sherman users    34 2008-01-19 17:13 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 sherman users    35 2008-01-19 17:13 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 sherman users    36 2008-01-19 17:13 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 sherman users    37 2008-01-19 17:13 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 sherman users    42 2008-01-19 17:13 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 sherman users    43 2008-01-19 17:13 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 sherman users 11456 2007-12-04 05:04 libunixprintplugin.so
lrwxrwxrwx 1 sherman users    60 2008-01-27 17:38 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

(the command "locate libflashplayer.so" returns nothing)

---

### Post by Kilz on 2008-01-27
Thanks. Since we know that it works in firefox 2 the results of the 2 usual commands dont give us a lot of information. We need to learn about firefox 3. What did you copy over, to firefox 3? Can you give me a listing of the firefox 3 plugin directory? please edit the path of this command to the path to the firefox3 plugin directory and use it.

ls -al /path/to/ff3/plugins

---

### Post by potrzebie on 2008-01-28
Actually, I should have thought of that. Here's what's in my ff3 plugins directory:

:~$ ls -al /usr/lib/firefox-3.0/plugins
total 40
drwxr-xr-x  2 sherman sherman  4096 2008-01-27 22:46 .
drwxr-xr-x 14 sherman sherman  4096 2008-01-27 18:14 ..
-rwxr-xr-x  1 sherman sherman 15600 2007-12-10 18:55 libnullplugin.so
lrwxrwxrwx  1 sherman sherman    36 2008-01-27 17:22 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx  1 sherman sherman    37 2008-01-27 17:22 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx  1 sherman sherman    34 2008-01-27 17:22 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx  1 sherman sherman    35 2008-01-27 17:22 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx  1 sherman sherman    36 2008-01-27 17:22 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx  1 sherman sherman    37 2008-01-27 17:22 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx  1 sherman sherman    42 2008-01-27 17:22 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx  1 sherman sherman    43 2008-01-27 17:22 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r--  1 sherman sherman 11456 2007-12-04 05:04 libunixprintplugin.so
lrwxrwxrwx  1 sherman sherman    60 2008-01-27 17:40 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

When I copied the flash plugin over, I also copied the rest of the plugins (the totem plugins), as the default Firefox 3 beta 2 plugins directory has only the 'libnullplugin.so'. On the off chance that the totem plugins being there is causing a problem I did a quick and dirty test by removing them, leaving only libnullplugin.so in place alongside the flash plugin. No flash in FF 3. I took away libnullplugin.so and left only the flash plugin. Still no flash in FF 3. So I put everything back and decided that was it for my experiments for now.

Installing Firefox 3 Beta 2 itself was a matter of installing the firefox-granparadiso package through synaptic and then downloading a copy of the beta from the mozilla site, unpacking it to /tmp, deleting the contents of /usr/lib/firefox-3.0, then copying over the unpacked beta from /tmp. I suppose the ubuntu team could have custom compiled the firefox 3.0 alpha in some way that leaves a stray directory someplace else, or it could be that the beta I downloaded isn't 64-bit (although I think it is), or something else is wrong and I'll just have to wait until march when ff 3 is supposed to be ready. Who knows, but it's fun to try all this.

---

### Post by Kilz on 2008-01-28
> **potrzebie said:**
> Actually, I should have thought of that. Here's what's in my ff3 plugins directory:


Click help, then about Firefox,  near the bottom of the little box that opens is a string that starts with Mozilla/5.0. Please copy that here.

---

### Post by potrzebie on 2008-01-28
That is exactly what I was relying on when I was wondering for certain if I have the 64-bit version or not. I guess I do...from the about box:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9b2) Gecko/2007121016 Firefox/3.0b2

And also for good measure, it's the same as the useragent string it's sending:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9b2) Gecko/2007121016 Firefox/3.0b2

---

### Post by Kilz on 2008-01-28
> **potrzebie said:**
> That is exactly what I was relying on when I was wondering for certain if I have the 64-bit version or not. I guess I do...from the about box:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9b2) Gecko/2007121016 Firefox/3.0b2

And also for good measure, it's the same as the useragent string it's sending:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9b2) Gecko/2007121016 Firefox/3.0b2

its 32bit, you only need the plugin in the plugin folder and not the wrapped one or symlink to it.

---

### Post by wawarren on 2008-01-28
In FF3 beta you can install Flash through the browser.  If you go to a site with Flash it ususally gives you a "Install missing plugins" popup.

---

### Post by potrzebie on 2008-01-28
Aha so it was something simple. I opened up /usr/lib/firefox-3.0/plugins, threw the link to the wrapped player in the trash, and copied the plugin from /usr/lib/mozilla/plugins. And now flash works in Firefox 3. So I guess it's the i686 in the useragent string that's significant, not the x86_64 in parentheses.

And you're right wawarren, I probably could have just installed it through the browser the first time I got the missing extensions popup. It just didn't occur to me, since even on windows doing that tends to have me accept a licence, download a file, and then inform me that it failed and give me an "install manually" button, which when clicked takes me to the Adobe site to download the plugin installer. I think the last time installing flash through the browser worked for me was back on Mac OS 9, so I guess I have a blind spot to the likely easy way.

---

