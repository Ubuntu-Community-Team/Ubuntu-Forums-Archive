---
title: "Citrix XenApp Presentation Server Client Version 11.0 on Jaunty 9.04"
date: 2009-05-19
forum: x86 64-bit Users
---

### Post by DanglingPointer on 2009-05-19
Hi I am completely new to Ubuntu and very rusty with unix/linux.  Could someone give me a hand installing the Citrix XenApp Client version 11 on my newly installed Jaunty?

I tried running the setup file but got the following repeatedly:
"Downloads/linuxx86-11.0.140395/linuxx86/echo_cmd: not found"

I have been using MS Windows for the most part of my life and expected the setup file to just run like an exe installer in Windows.

Could someone guide me?  The client is found [here]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.citrix.com%2FEnglish%2FSS%2Fdownloads%2Fresults.asp%3FproductID%3D186%26c1%3Dsot2755&ei=wMUSSrSzLpbqswOu8vHpDQ&usg=AFQjCNEsd2iXhNNMGMCMbJWWM_n9QHuWzA&sig2=gYM2JrywiygQXXvxrxGlHQ")

---

### Post by maheshasolkar on 2009-05-19
I followed these steps to install this client. This is on Jaunty (Ubuntu 9.04):

[LIST]
[*] Installed motif, which this client requires:


```
  % sudo aptitude install libmotif3
```

  [*] Downloaded the .tar.gz file from (to the Desktop):

  [http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755)

  [*] Extracted it in a temporary directory:

```
  % cd ~/Desktop
  % mkdir tmp
  % cd tmp
  % tar -zxvf ../linuxx86-11.0.140395.tar.gz
```

  [*] Used the installer to install the client:

```
  % sudo ./setupwfc
```

  [*] Follow the prompts. It will install the client in /usr/lib/ICAClient directory.

  [*] You can find the 'Citrix Receiver' menu item under Applications -> Internet. If the client does not launch with that menu, it is probably missing the libXm.so.4 shared library. Do the following and try again:

```
  % cd /usr/lib/
  % sudo ln -s libXm.so.3.0.2 libXm.so.4
```
[/LIST]
Hopefully this should do it.

---

### Post by Rede on 2009-05-19
I have the ICA client working but have found it slow to launch.

I've found this to be very slow to launch via a Citrix web interface. I can run 'top' and see the wfica process has started but don't receive any on-screen feedback.

Ideas?

---

### Post by DanglingPointer on 2009-05-20
Thanks maheshasolkar

I followed your steps one at a time but when I run "sudo ./setupwfc" I get the following...

```
fernando@Vanguard-Support:~/Downloads/tmp$ sudo ./setupwfc
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4045: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
No target hinst.msg found under  for en_AU.UTF-8
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4073: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4074: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4075: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4076: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4103: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4103: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4103: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
/home/fernando/Downloads/tmp/./linuxx86/hinst: 4103: /home/fernando/Downloads/tmp/./linuxx86/echo_cmd: not found
^C
fernando@Vanguard-Support:~/Downloads/tmp$ 

```libmotif3 installed ok.
These are the contents of the temp directory after extracting...
```
fernando@Vanguard-Support:~/Downloads/tmp$ ls -lrt
total 8
drwxr-xr-x 5 fernando fernando  4096 2009-02-26 20:22 nls
-r-xr-xr-x 1 fernando fernando 19582 2009-02-26 20:22 setupwfc
-r--r--r-- 1 fernando fernando   689 2009-02-26 20:22 PkgId
drwxr-xr-x 3 fernando fernando  4096 2009-02-26 20:22 linuxx86
fernando@Vanguard-Support:~/Downloads/tmp$ 

```Have you seen this scenario before?

---

### Post by maheshasolkar on 2009-05-20
Can you try what is mentioned here:

[http://ubuntuforums.org/showpost.php?p=4059815&postcount=11](http://ubuntuforums.org/showpost.php?p=4059815&postcount=11)

---

### Post by DanglingPointer on 2009-05-21
Thanks for your time and support maheshasolkar!

I followed your lead which lead on to this guide:[URL="http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml"]
http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml[/URL]

And it worked!

I just need to get used to the norms of Unix/linux/ubuntu.  Like file locations the purpose of each directory, etc.

As for the previous Rede's question; my broadband has been shaped for this month so I am running at 65kbps full duplex.  I throttled my remote desktop to dial-up speed and it worked great.
Speed so far is not a problem whether with launching the ica through the plugin, nor through the connection while doing work.

Problem solved.

---

### Post by charon79m on 2009-05-22
> **maheshasolkar said:**
> Can you try what is mentioned here:

[http://ubuntuforums.org/showpost.php?p=4059815&postcount=11](http://ubuntuforums.org/showpost.php?p=4059815&postcount=11)


This was the fix for me.  Thanks for pointing in the right direction.

!!!!  EDIT !!!!

While this allowed the package to install, I still am not able to get the plugin to run properly.  

Mike K.

---

### Post by barksten on 2009-05-22
Thanks this worked for me too. (But ECHO was on another line..)

---

### Post by BigRod on 2009-05-23
I was able to get the client installed, but wfica just doesn't seem to do anything when I try to open a link in Citrix.  Has anyone experienced this?  I tried installing it as root to /usr/lib/ICAClient as well as as myself to my home directory and neither one works.

---

### Post by bmalpas on 2009-05-24
like the above poster i did all the above steps got it installed but when i click the ICA Links and select open with /usr/lib/ICAClient/wfica and also tried wfcmgr with no luck nothing opens. 

also when i try to just run the wfica nothing happens either no error message or anything pops up.

any ideas ?

---

### Post by maheshasolkar on 2009-05-24
> **bmalpas said:**
> like the above poster i did all the above steps got it installed but when i click the ICA Links and select open with /usr/lib/ICAClient/wfica and also tried wfcmgr with no luck nothing opens. 

also when i try to just run the wfica nothing happens either no error message or anything pops up.

any ideas ?

Setting the symbolic link to libXm.so.4 as mentioned in my earlier comment fixed similar issues for me.

The fact that wfica does not report any errors when invoked from terminal does not leave us with any clue :(

---

### Post by bmalpas on 2009-05-26
> **maheshasolkar said:**
> Setting the symbolic link to libXm.so.4 as mentioned in my earlier comment fixed similar issues for me.

The fact that wfica does not report any errors when invoked from terminal does not leave us with any clue :(

i tried this already but after restarting and trying it again it worked !!

---

### Post by BigRod on 2009-05-27
That is really strange.  I know I had done that step at least once or twice, but this time it worked for me too.  Oh well.  Thanks to all!

---

### Post by BigRod on 2009-05-29
Okay, well I had to reinstall for an unrelated reason, and now I'm back to the same problem I was having before.  I have tried creating the symbolic link and restarting several times to no avail.  When I try to run the Citrix Receiver program under Applications > Internet, I get an error that says: 

[I]Could not launch 'Citrix Receiver'

Failed to execute child process "/usr/lib/ICAClient/wfcmgr" (No such file or directory)[/I]

When I try to open a link through FireFox, I don'd get any kind of error, it just doesn't do anything.  The file referenced in the error above definitely exists, and I have made sure that I have full permissions to both it and the wfica process.

Any ideas out there?  I hate it that I had it working and now am out of luck again.

---

### Post by hesjnet on 2009-06-02
> **maheshasolkar said:**
> I followed these steps to install this client. This is on Jaunty (Ubuntu 9.04):

[LIST]
[*] Installed motif, which this client requires:


```
  % sudo aptitude install libmotif3
```

  [*] Downloaded the .tar.gz file from (to the Desktop):

  [http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/SS/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755)

  [*] Extracted it in a temporary directory:

```
  % cd ~/Desktop
  % mkdir tmp
  % cd tmp
  % tar -zxvf ../linuxx86-11.0.140395.tar.gz
```

  [*] Used the installer to install the client:

```
  % sudo ./setupwfc
```

  [*] Follow the prompts. It will install the client in /usr/lib/ICAClient directory.

  [*] You can find the 'Citrix Receiver' menu item under Applications -> Internet. If the client does not launch with that menu, it is probably missing the libXm.so.4 shared library. Do the following and try again:

```
  % cd /usr/lib/
  % sudo ln -s libXm.so.3.0.2 libXm.so.4
```
[/LIST]
Hopefully this should do it.

Thanks! This worked for me:popcorn:

---

### Post by tns09 on 2009-06-11
Just wanted to say following these instructions and some other how-tos on the web, I did get Citrix working on Jaunty. Works great except for one problem. With visual effects turned on while connected to my company server via citrix, it causes all sorts of buggy behaviour. I found that if I turn off all visual effects that solves the buggy problems within citrix. Kinda of annoying to have to do this everytime I need to use citrix. Anyone have any suggestions on a fix for this or just have to live with it. Thanks

---

### Post by techstop on 2009-06-14
> **tns09 said:**
> Just wanted to say following these instructions and some other how-tos on the web, I did get Citrix working on Jaunty. Works great except for one problem. With visual effects turned on while connected to my company server via citrix, it causes all sorts of buggy behaviour. I found that if I turn off all visual effects that solves the buggy problems within citrix. Kinda of annoying to have to do this everytime I need to use citrix. Anyone have any suggestions on a fix for this or just have to live with it. Thanks

Bit of a known problem with compiz and CitrixICA. Open ccsm and under workarounds, tick "Legacy Fullscreen Support". See if that fixes it, does for me...

---

