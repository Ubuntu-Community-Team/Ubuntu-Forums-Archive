---
title: "[SOLVED] Flash 64bit"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by claymater on 2008-12-06
Hey I know this has probably been asked a million times, but does anyone know how to get flash to work in ubuntu 64-bit (8.04)?

Would be great, thanks guys :)

---

### Post by 2hot6ft2 on 2008-12-06
This should help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by zika on 2008-12-06
> **claymater said:**
> Hey I know this has probably been asked a million times, but does anyone know how to get flash to work in ubuntu 64-bit (8.04)?

Would be great, thanks guys :)

Beware that there is a 64-bit Aplha Flash plugin.

Below is the way it works in Intrepid. I did not try it in Hardy.

```

sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
(create plugins dir if it doesn't exist)
```

---

### Post by claymater on 2008-12-06
> **zika said:**
> Beware that there is a 64-bit Aplha Flash plugin.

Below is the way it works in Intrepid. I did not try it in Hardy.

```

sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
(create plugins dir if it doesn't exist)
```

So I upgraded to imtrepid and tried that code, but it doesnt seem to have done anything :(

---

### Post by zika on 2008-12-06
> **claymater said:**
> So I upgraded to imtrepid and tried that code, but it doesnt seem to have done anything :(

Sorry, what do You mean by "it doesnt seem to have done anything"?

Did You get any errors ... did You copy the file? 

If everything went well but You do not get flash working in Firefox try copying libflashplayer.so to /usr/lib64/mozilla/plugins/ dir instead to ~/.mozilla/plugins.

Either I was busy or You were very quick in uprading from Hardy to Intrepid ... :)

---

### Post by claymater on 2008-12-06
> **zika said:**
> Sorry, what do You mean by "it doesnt seem to have done anything"?

Did You get any errors ... did You copy the file? 

If everything went well but You do not get flash working in Firefox try copying libflashplayer.so to /usr/lib64/mozilla/plugins/ dir instead to ~/.mozilla/plugins.

Either I was busy or You were very quick in uprading from Hardy to Intrepid ... :)

It did seem like a very quick upgrade, because last time I upgraded it, it took a  good hour or 2... oh well :P 

But what I got back from the command was... 

```
claymater@claymater-desktop:~$ sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
claymater@claymater-desktop:~$ wget http://download.macromedia.com/pub/l...6_64.so.tar.gz
--2008-12-06 15:21:47--  http://download.macromedia.com/pub/l...6_64.so.tar.gz
Resolving download.macromedia.com... 96.6.35.191
Connecting to download.macromedia.com|96.6.35.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-12-06 15:21:47 ERROR 404: Not Found.

claymater@claymater-desktop:~$ tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
tar: libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
claymater@claymater-desktop:~$ sudo mv libflashplayer.so ~/.mozilla/plugins/
mv: cannot stat `libflashplayer.so': No such file or directory
claymater@claymater-desktop:~$ (create plugins dir if it doesn't exist)

```

---

### Post by zika on 2008-12-06
You do not need first 3 lines of the code below since You are done with them ...

```
sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
(go to the directory that You have designated as a download directory, using command cd _here_goes_that_directory_)<----------------------I've assumed this ... sorry
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
(create plugins dir if it doesn't exist)
```

I hope that, now, it will work.

---

### Post by claymater on 2008-12-06
yea I got it to work, thanks :)

---

