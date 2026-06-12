---
title: "Flash installation error, Ubuntu 8.4 64bit."
date: 2009-08-02
forum: x86 64-bit Users
---

### Post by altometer on 2009-08-02
First let me say, I have been searching for several hours on this. I have attempted to follow the guide posted and I recieved the same error as when I use synaptic, or terminal 
```
sudo apt-get install flashplugin-nonfree
```I get the error...

```
Download done.
sha256sum mismatch install_flash_player_9.tar.gz
The Flash plugin is NOT installed.
```I get the same error on flash 10. Where should I submit this bug if this is not the correct section. 

I did find another user with this error, his resolution was not relative  to my problem, any help would be appreciated.

---

### Post by theremper on 2009-08-03
I followed these instructions on my 8.4 system and it worked. I feel like im a minister for these instructions but they are the only thing that worked for me 

[http://ubuntu64.today.com/](http://ubuntu64.today.com/)

---

### Post by altometer on 2009-08-03
Thanks for trying but that didn't work. I suspect it was the same error, but the terminal auto closed after completion of the script and I am unsure of how to stop that from happening. I checked about:plugins as well just in case, flash is still unlisted.

---

### Post by 3Miro on 2009-08-03
The version of Linux that you have is 8.04 (not 8.4). Perhaps that would help your Internet searches.

---

### Post by HavocXphere on 2009-08-03
I'm pretty sure v10 is out, although I think the x64 one is still in alpha/beta. Not sure whats in the repos.

The flash plugin needs to match the browser type, not the OS type.

i.e. If you grab FF 3.5 on the mozilla site you get the x86 version which works fine on a x64 system, but you then need the x86 version of the flash plugin. i.e. plugin type must much browser, not OS.

[http://ubuntuforums.org/showpost.php?p=7602453&postcount=4](http://ubuntuforums.org/showpost.php?p=7602453&postcount=4)

However, if you are using the 3.0 version of FF that is included by default in JJ then you need the x64 version of the plugin.

Not sure what type the shiretoko installs are.

I'd suggest downloading the plugin manually and dropping it in the relevant plugin folder as per link above.

And finally, the info presented under the about of FF is slightly misleading.
> Mozilla/5.0 (X11; U; Linux i686 (**x86_64**); en-US; rv:1.9.1.1) Gecko/20090715 Firefox/3.5.1
^Thats what is display on FF x86 but its showing x64 since the info is for the underlying OS.:rolleyes:

---

