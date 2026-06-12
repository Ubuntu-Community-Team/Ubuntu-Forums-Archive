---
title: "Google Earth authenticate error code 29"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by bravo331 on 2008-05-21
Hello all
I am new to Ubuntu and love it! I installed Google Earth but when I run it from the deskto icon I get an error message "google earth detected an error while trying to authenticate; check internet connection (can you get to google. com?) check firewall settings (are you blocking /home/username/google-earth-bin?) Error code 29
I can connect to Google.com just fine and dont have a firewall as far as I know and how do I check if i do have a firewall and how to check if its blocking google earth if there is a firewall. Does Ubuntu 8.04 install its own firewall? My system: amd athalon 64x2 (64 bit); 2gb ram; GeForce 7600gt

I've been searching forums for 2 nights now looking for cure for this problem; found a few references to it but no solutions as of yet.](*,):confused:

---

### Post by gsmanners on 2008-05-21
Could you open a terminal and load it that way?

googleearth

You may be missing "lib32nss-mdns" (so install that if you haven't already).

---

### Post by philinux on 2008-05-21
I'd reboot and try again. Probably your isp having a hiccup.

---

### Post by bravo331 on 2008-05-21
> **gsmanners said:**
> Could you open a terminal and load it that way?

googleearth

You may be missing "lib32nss-mdns" (so install that if you haven't already).
How do I open terminal and load it? And how do I install "lib32nss-mdns"? Thanks for reply! I should also mention that I did try rebooting and reloading several times over a couple hours

---

### Post by gsmanners on 2008-05-21
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Melk79 on 2008-05-21
I had this too and did this:

1. Install GE 4.3 via Synaptic Package Manager (rather than from Google)

2. At this point, I get Error 29 and no connection

3. Run sudo apt-get install lib32nss-mdns (thanks acope) (For 64bit anyways)

4. Error 29 is gone, but no earth appears as user. Only sudo googleearth works.

5. Remove .config/Google and .googleearth from my home directory and restart googleearth (thanks phoolish)

6. Everything works great.

---

### Post by DoritosBR on 2008-05-22
Yay, installing the "lib32nss-mdns" worked for me.
Thanks

---

### Post by bravo331 on 2008-05-23
thanks to you all; inlstalling the "lib32nss-mdns" did the trick!:)

---

### Post by soldersplash on 2008-05-24
Is it essential to get GE 4.3 through Synaptic? I can't find it in Synaptic, which repo does it come from?:confused:

Looking forward to getting GE working on Hardy AMD64.:)
Thanks,
Daniel.

---

### Post by pixel :-) on 2008-05-24
@soldersplash
it in medubuntu
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

then try this in a terminal

sudo apt-get install googleearth-4.3 lib32nss-mdns

and remome the old config directory of googleearth ,a hiden directory in home

---

### Post by lizzard on 2008-05-24
> **soldersplash said:**
> Is it essential to get GE 4.3 through Synaptic? I can't find it in Synaptic, which repo does it come from?:confused:



It's in the medibuntu repos. Check this out: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Of course you can download GE from its homepage and run the install-script as well.

---

### Post by markbuntu on 2008-05-24
You need to have the third party repos enabled in synaptics and you need to reload. Then the search for google earth will get you results. 

Do not forget to make sure you have lib32nss-mdns though it may be included in the package by now. I already had it installed so I can't tell you.

---

### Post by soldersplash on 2008-05-25
Pixel, Lizzard, Markbuntu,
Thanks for info. I'm adding the medibuntu repo to my apt-mirror mirror.lst file so tonight I should sync the required packages for install tommorrow.

I had tried GE from the Google web site, it installed OK but when run gives the error 29 code. I had tried removing the ~/.config/Google and ~/.googleearth stuff, didn't help, still no earth. That is why I was asking if it is important to get GE 4.3 from repo _not_ GE web site.

Anyhow, I'll post back tomorrow after I've installed from medibuntu repo mirror, let you'll know how I get on. :)

---

### Post by soldersplash on 2008-05-25
Hi Guys,
I couldn't wait..... synced my mirror this afternoon during off peak time.:twisted:

(If you use Virgin ADSL in UK _BEWARE_ their "Traffic Management Policy" :cry:) 

Just installed GE 4.3 from medibuntu repo and \\:D/ it works just fine! :guitar:

Does anyone know how that package differs from the one on GE web site? -curiosity...

GE rocks on Hardy AMD64 :guitar:

Thanks again everyone!

---

### Post by balak on 2008-06-22
Thanks everybody! 

I had the same situation after upgrading to hardy and found the solution in this thread. Installing lib32nss-mdns and removing the config directories did the trick for me. I am using the GE from google's website w/o any issues.

---

### Post by Waltomatic on 2008-09-26
Thanks for all the help on this subject. I'm a new convert, and I'm grateful that such a resource exists. I managed to get Google Earth working by deleting the ~/.config and the ~/.googleearth folders.

I'm still having one minor issue, however. The ~/.config folder was moved to my trash can. When I try to delete it from the trash, it says I don't have the proper permission. I'm sure there is a way to delete it through the terminal. However, I do not know the correct command or the correct path to the trash can.

---

### Post by Waltomatic on 2008-09-28
> **Waltomatic said:**
> I'm still having one minor issue, however. The ~/.config folder was moved to my trash can. When I try to delete it from the trash, it says I don't have the proper permission. I'm sure there is a way to delete it through the terminal. However, I do not know the correct command or the correct path to the trash can.
With some assistance, I was able to solve the problem. Thanks again for the help with the installation.

---

### Post by DeMus on 2009-02-08
> **Melk79 said:**
> I had this too and did this:

1. Install GE 4.3 via Synaptic Package Manager (rather than from Google)

2. At this point, I get Error 29 and no connection

3. Run sudo apt-get install lib32nss-mdns (thanks acope) (For 64bit anyways)

4. Error 29 is gone, but no earth appears as user. Only sudo googleearth works.

5. Remove .config/Google and .googleearth from my home directory and restart googleearth (thanks phoolish)

6. Everything works great.

I did just that and receive the following error when starting the program:

./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

I installed it in my home folder and I am owner. I use the symbolic link to start.
I use Hardy 8.0.4.2-64 bits.
The program starts, I see the first splash screen, then the real window with a grey (looks like error) window inside and it all disappears again.
When I start again, I get this:

Unable to create prefs directory '/home/jan/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

What to do?

Found the solution here:
[http://ubuntuforums.org/showthread.php?t=1058081](http://ubuntuforums.org/showthread.php?t=1058081)
It's a strange solution but it works.

---

### Post by harrykar on 2009-08-09
Ok here's my GE adventure LOL. I install GE from official Google's *.bin installer and like others  have no Google servers connection. So after some reading time i deinstall** lib32nss-mdns (NSS module for Multicast DNS name resolution (32-bits version)**. I have a Core2Duo 64 bit on jaunty amd64 PC anyway) and then reinstall it through Synaptic. That's it now GE go. What the heck the simplicity here's an option?:(

---

### Post by joshjh on 2009-08-15
Great this worked for me too. i may never use my Vista again if i can get the sound to work on my video player. You guys are great

---

### Post by Parvo on 2009-08-21
sudo apt-get install lib32nss-mdns

worked for me. can't thank you enough.

---

### Post by grokk on 2009-08-26
Thanks folks, fixed my error in seconds by installing lib32nss-mdns.  didnt need to delete anything or reinstall

---

