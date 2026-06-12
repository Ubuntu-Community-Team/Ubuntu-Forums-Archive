---
title: "Error while installing wine on Debian[4.0]"
date: 2008-03-14
forum: Wine
---

### Post by Aliyans on 2008-03-14
[B]hi
    Anybody help to fix this error...i have tried to install the wine on my new debian server..i think it was old version installed n keep getting error while installing programmes on vncserver..i tried to upgrade it latest version..but still error[cant overwrtie it]..i removed it..tried with latest package..still error.i'm using putty if u r getting me commands please in nano.  sudo commands not taking in ..[/B]
[PHP] 
apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  msttcorefonts
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B/10.3MB of archives.
After unpacking 47.9MB of additional disk space will be used.
(Reading database ... 19572 files and directories currently installed.)
Preparing to replace wine 0.9.25-2.1 (using .../wine_0.9.57~winehq0~debian~4.0-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: error processing /var/cache/apt/archives/wine_0.9.57~winehq0~debian~4.0-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/wine/msacm32.drv.so', which is also in package libwine
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.9.57~winehq0~debian~4.0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

---

### Post by Aliyans on 2008-03-15
hi
   nobody able to figure it out ...poor...support..

---

### Post by Aliyans on 2008-03-15
hi
    i figured it out myself n solved...i dont need any those reputed guys[ who think they r the best] over here help who didnt even show some kindness. **[COLOR="SeaGreen"]]...if knowlegde is power its most power lies in where there is  ability to share it[/COLOR]**

---

### Post by kerry_s on 2008-03-15
> **Aliyans said:**
> hi
    i figured it out myself n solved...i dont need any those reputed guys[ who think they r the best] over here help who didnt even show some kindness. i have only 1 thing to say to them  **"go n f**k urself"[/B[B][COLOR="SeaGreen"]]...if knowlegde is power its most power lies in where there is  ability to share it[/COLOR]**

i never saw your post, i would have tried to help. :(
did you run>
su
apt-get -f install

to fix those 12 errors?

also there is a console gui for adding/removing packages, just like synaptic in the gui.

su
aptitude

it takes a little getting use to, to learn the keyboard controls, but after that it's easy, you'll be finding(/) and installing(+) or removing(-) like a pro.

---

### Post by Aliyans on 2008-03-15
hi
    i ran that command which fixed evry errors...but i cant set ftp...i cant do openssl commands which says command not found...kerry  r u there to help me

---

### Post by kerry_s on 2008-03-15
> **Aliyans said:**
> hi
    i ran that command which fixed evry errors...but i cant set ftp...i cant do openssl commands which says command not found...kerry  r u there to help me

Sorry, just got up.
can you be a little more specific.

ftp?
openssl commands? what commands?

i'm here!

---

### Post by Aliyans on 2008-03-16
hi
   u donno FTP[file transfer protocol]...to set up vsftp[i donno correct name] u need to run openssl -------   ------ etc...comand..on terminal it wont accpet...is it different for debian..i aslo want to know how to config **firewall  n NIC** on vnc server

---

### Post by kerry_s on 2008-03-16
i'm sorry, what i meant was, what are you using for ftp?
there are many ways to go, different programs to use, you might prefer 1 over another.

here, top of the list from google.
[http://www.debian-administration.org/articles/228](http://www.debian-administration.org/articles/228)

also you said you were running a server, is it gui or no gui?

try here, has links to several things, including firewall how to-> [http://www.debianhelp.co.uk/debianserver.htm](http://www.debianhelp.co.uk/debianserver.htm)

---

### Post by Aliyans on 2008-03-17
hi
    thanx kerry...i will check it out...i have to go its st.patrick's day....byeee

---

### Post by Aliyans on 2008-03-17
hi
   one more kerry...i want to encrypt hdd ..so i ran **umount /dev/sda2** command.. but drive is busy is what i'm getting...i have installed neccessary tool b4..i havent logged into server with my user or vncserver is not running..then how can there be activity?? also i want to know instead of "sudo" command what is the alternative command for debian??

---

### Post by kerry_s on 2008-03-17
> **Aliyans said:**
> hi
   one more kerry...i want to encrypt hdd ..so i ran **umount /dev/sda2** command.. but drive is busy is what i'm getting...i have installed neccessary tool b4..i havent logged into server with my user or vncserver is not running..then how can there be activity?? also i want to know instead of "sudo" command what is the alternative command for debian??

my friend used this method for his kiosk->
[http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

debian uses "su", but you can install sudo and set it up.

su
apt-get install sudo

then add your "user" to sudoers.

visudo

user    ALL=(ALL) ALL

just in case you want to know
.
disable root-> sudo passwd -l root
enable root-> sudo passwd -u root

on mine, root is disabled and i use sudo.

---

### Post by Aliyans on 2008-03-18
hi
   Look like my problems .. n questions not going to end..i want u to look at the NIC setting from my server n tell me is there anything wrong..
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth0
iface eth0 inet static

```

     I'm experincing a very low outgoing speed..n i'm getting almost max incoming speed..is there anything u see to slow up speed..or what should i do to get equal up/down speed..i was told its 100mbt up/down..

also i need to know how to install flash plug in n other plug ins as well....i'm so sorry to disturb u  coz u r the only one who showed some kindness to help me here...

---

### Post by Aliyans on 2008-03-20
Hi
    hope u come back here kerry...or anybody who can sort this one please

---

