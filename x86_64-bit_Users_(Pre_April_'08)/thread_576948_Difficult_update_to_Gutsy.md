---
title: "Difficult update to Gutsy"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by fraCPH on 2007-10-15
After messing up my system I tried to solve everything by upgrading to Gutsy.
The update has been difficult but now my system is almost working.
However there are several key parts of the system that refuse to work:
```
fra@fra-desktop:~/Desktop$ gnome-panel
gnome-panel: symbol lookup error: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: pango_font_description_get_gravity
fra@fra-desktop:~/Desktop$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgtkmm-2.4.so.1: undefined symbol: gtk_builder_error_quark
fra@fra-desktop:~$ sudo gedit
gedit: symbol lookup error: gedit: undefined symbol: gtk_widget_set_tooltip_text
```
You would say that the libs are wrong but look at this:
```
fra@fra-desktop:~$ apt-cache policy libpango1.0-0
libpango1.0-0:
  Installato: 1.18.2-0ubuntu1
  Candidato: 1.18.2-0ubuntu1
  Tabella versione:
 *** 1.18.2-0ubuntu1 0
        500 http://it.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
fra@fra-desktop:~$ apt-cache policy libgtkmm-2.4-1c2a
libgtkmm-2.4-1c2a:
  Installato: 1:2.12.0-0ubuntu1
  Candidato: 1:2.12.0-0ubuntu1
  Tabella versione:
 *** 1:2.12.0-0ubuntu1 0
        500 http://it.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
```
As you see the libraries are perfectly compliant with the version present in Gutsy.
I'm lost, isn't there any way to solve my problems a part from the fresh install ? :(

---

### Post by saru411 on 2007-10-15
what were you issues that made you go through all of this? according to your post history youn had a nvidia video card driver issue. there were much simplier ways to fix the problem apart from upgrading to a beta gutsy. when you do finally get your install stable install your nvidia driver from this site([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) . it will do it for you!

---

### Post by fraCPH on 2007-10-16
The issues were related to a wrong library I had installed and stopped my X session. Now that library is removed and my graphical session restored, no problems at all with nvidia drivers.

---

### Post by fraCPH on 2007-10-17
I made a small step forward:

```
ldd /usr/bin/gnome-panel
```
I found out that it was using the libpangocairo located in /usr/local/lib rather than the one in /usr/lib
therefore I made:

```
export LD_LIBRARY_PATH=/usr/lib
gnome-panel
```
and it worked! :)
Same with gedit and gnome-system-monitor
Now I'm trying to apply the same trick to all the other apps that do not work.
However this is a temporary solution as it expires each time you close the programs.
How can I tell them to always use the libraries in the right path ?

---

### Post by michael37 on 2007-10-17
> **fraCPH said:**
> I made a small step forward:
Same with gedit and gnome-system-monitor
Now I'm trying to apply the same trick to all the other apps that do not work.
However this is a temporary solution as it expires each time you close the programs.
How can I tell them to always use the libraries in the right path ?

Let me ask you.  How did libpango or anything else ended up in /usr/local?  Did you intentionally install it?  Did it come in any package?  Test with "dpkg -S /path/to/file" -- it will tell you whether a rogue .deb installed these library, or you just happened to copy it there.  If earlier, consider removing this .deb.  If latter, just delete those libraries.

---

### Post by fraCPH on 2007-10-17
They have probably gone there after the installation of a .deb
I will test as per your suggestion and see what I find out.
Thanks.

---

### Post by go_beep_yourself on 2007-10-17
> **fraCPH said:**
> I made a small step forward:

```
ldd /usr/bin/gnome-panel
```
I found out that it was using the libpangocairo located in /usr/local/lib rather than the one in /usr/lib
therefore I made:

```
export LD_LIBRARY_PATH=/usr/lib
gnome-panel
```
and it worked! :)
Same with gedit and gnome-system-monitor
Now I'm trying to apply the same trick to all the other apps that do not work.
However this is a temporary solution as it expires each time you close the programs.
How can I tell them to always use the libraries in the right path ?

man ldconfig

---

### Post by javello on 2007-10-29
I got a similar problem after upgrading to Gutsy. Didn't get the gnome-panel on startup. Your post help me to begin with.

Then I replaced the text in file /etc/ld.so.conf which was
include /etc/ld.so.conf.d/*.conf

for
# Begin /etc/ld.so.conf
/lib
/usr/lib
/usr/X11R6/lib
# End /etc/ld.so.conf

et voilà.

I suspect this problem arose because I compiled pango libraries from source at some point.

I still have a minor problem. update-notifier icon has gone.

---

### Post by Gotblade on 2007-12-07
I had this problem with Inkscape not starting.
Your quick fix worked so then I needed a way to make it work every time so I made a sh file with this in it " export LD_LIBRARY_PATH=/usr/lib inkscape" & made it executable.
Thank you for such a great tip!!

---

