---
title: "regedit bash"
date: 2008-03-25
forum: Wine
---

### Post by Sandsound on 2008-03-25
I'm trying to write a bash script to simplify the installation of wineasio, but I'm stuck at the regedit :-(

I need to change and/or verify the audio driver within the script, but can't find any documentation on how to do it.

[HKEY_CURRENT_USER\Software\Wine\Drivers]
"Audio"="alsa"

My gues would be something like this :
wine regedit /D "HKEY_CURRENT_USER\Software\Wine\Drivers\Audio=alsa"

But I'm not in a "trial and error" kind'a mood today, and I'd like to understand what I'm doing.

Any ideas would be welcome.

---

### Post by finer recliner on 2008-03-25
```

string1 == string2
    True if the strings are equal. `=' may be used in place of `=='.

```

[http://www.faqs.org/docs/bashman/bashref_68.html#SEC75](http://www.faqs.org/docs/bashman/bashref_68.html#SEC75)

---

### Post by Sandsound on 2008-03-25
> **finer recliner said:**
> ```

string1 == string2
    True if the strings are equal. `=' may be used in place of `=='.

```

[http://www.faqs.org/docs/bashman/bashref_68.html#SEC75](http://www.faqs.org/docs/bashman/bashref_68.html#SEC75)

Thanks for the answer and the link, but maybe I should have explained that I'm a total noob at this :oops:
I do however understand that I'll have to make some kind'a if-then statment, but before i plunge into this, I need to know how to make a simple change in the registry with a bash script.

tried :
wine regedit /D "HKEY_CURRENT_USER\Software\Wine\Drivers\Audio=alsa"

but that did'nt work.

I could make a .reg-file but doesnt it seams a bit excessive just to change a parameter in the registry ?

---

### Post by happyhamster on 2008-03-25
> **Sandsound said:**
> I could make a .reg-file but doesnt it seams a bit excessive just to change a parameter in the registry ?
Making a temporary .reg file is probably a good way of doing this. There are a few other ideas on this page:

[http://wiki.jswindle.com/index.php/Wine_Registry](http://wiki.jswindle.com/index.php/Wine_Registry)

---

### Post by Sandsound on 2008-03-25
> **happyhamster said:**
> Making a temporary .reg file is probably a good way of doing this. There are a few other ideas on this page:

[http://wiki.jswindle.com/index.php/Wine_Registry](http://wiki.jswindle.com/index.php/Wine_Registry)

Thanks :-)

I think I got it now. this is the script so far :

> #!/bin/bash
# by Sandy Sandgreen
# Install wineasio 0.7.3 on Ubuntu 8.04
#
# Thanks to Jacklab for the wineasio source
# but also to David Hayes and AlanPoPo who both made a great howto
#
echo "This script will download and install wineasio" ;
echo "This might take awhile, please be patient" ;
echo "First it will install the latest wine, jack and some other usefull stuff" ;
sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential
echo "Configuring wine" ;
wineprefixcreate -w
mkdir -p ~/wineasio_tmp
cd ~/wineasio_tmp
echo "REGEDIT4" >> alsa.reg
echo "[HKEY_CURRENT_USER\Software\Wine\Drivers]" >> alsa.reg
echo '"Audio"="alsa"' >> alsa.reg
wine regedit alsa.reg
echo "Then it will download the wineasio driver and place it in your wine-folder" ;
wget [http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so](http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so)
chmod u+rwx wineasio.dll.so
sudo mv wineasio.dll.so /usr/lib/wine/
rm -Rf ~/wineasio_tmp
regsvr32 wineasio.dll
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
echo "All done :-) ... Now you can use the win-version of EnergyXT2 (or Reaper) with wineasio" ;
echo "Press [ENTER] to close the shell"
read

Now I "only" need to check if wine already have alsa set to default.

---

