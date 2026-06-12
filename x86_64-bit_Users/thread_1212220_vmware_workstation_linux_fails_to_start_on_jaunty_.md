---
title: "vmware workstation linux fails to start on jaunty amd64"
date: 2009-07-13
forum: x86 64-bit Users
---

### Post by SOULTE on 2009-07-13
hey there;

fellas, i've jaunty amd64. i've just downloaded vmware workstation 6.5 x86_64 bundle file and installed it successfully. but when i try to start it just appears and disappears on task panel and fails to start without any error message. i also tried to start it with super user privileges but no chance. could anyone please tell me what's wrong with that?

edit: Solved;

[QUOTE=doas777]did you follow all the instructions here (with your downloaded version)?
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

the dependency packages are important [/QUOTE]

---

### Post by darco on 2009-07-13
run it from the terminal and post the output...

darco

---

### Post by SOULTE on 2009-07-13
> **darco said:**
> run it from the terminal and post the output...

darco
hi. here's the output. it says that some modules are missing. i don't know!


```
afshin@coldfusion:~$ /usr/bin/vmware
Logging to /tmp/vmware-alireza/setup-4901.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
/usr/bin/vmware: line 31:  4901 Segmentation fault      "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

```

---

### Post by doas777 on 2009-07-13
> **SOULTE said:**
> hi. here's the output. it says that some modules are missing. i don't know!


```
afshin@coldfusion:~$ /usr/bin/vmware
Logging to /tmp/vmware-alireza/setup-4901.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
/usr/bin/vmware: line 31:  4901 Segmentation fault      "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

```

did you reboot after install? anytime you add modules, you usually either need to manually load them, or reboot

---

### Post by jackaloper on 2009-07-13
where do i post my problem sorry for the interruptuon

---

### Post by SOULTE on 2009-07-13
> **doas777 said:**
> did you reboot after install? anytime you add modules, you usually either need to manually load them, or reboot
yes, of course.

---

### Post by SOULTE on 2009-07-13
> **jackaloper said:**
> where do i post my problem sorry for the interruptuon
you just need to select the proper forum for your problem and click on the "Submit new thread" button on the top.

---

### Post by Tanker Bob on 2009-07-13
> **SOULTE said:**
> hey there;

fellas, i've jaunty amd64. i've just downloaded vmware workstation 6.5 x86_64 bundle file and installed it successfully. but when i try to start it just appears and disappears on task panel and fails to start without any error message. i also tried to start it with super user privileges but no chance. could anyone please tell me what's wrong with that?
If you installed the bundle, then you may have to run the setup script. I usually convert the .rpm file to .deb using alien. Alien must be run as root with sudo and you need to use the -d and -c parameters.The command should look something like:

```
sudo alien -d -c VMware-Workstation-6.5.0-118166.i386.rpm
sudo dpkg -i VMware-Workstation-6.5.0-118166.i386.deb
```

where the first command creates the .deb file and the second installs it, and the file name will vary with the version that you are installing.

If you install using the bundle, it should have run the setup script automatically. If not, then you need to run:

```
sudo ./vmware-config.pl
```

If Ubuntu can't find vmware-config.pl in the path, you'll have to search for it. Then change to its directory and run it. That should build all the modules that are listed as missing in your follow-up post.

This should get you up and running.

---

### Post by SOULTE on 2009-07-14
> **Tanker Bob said:**
> If you installed the bundle, then you may have to run the setup script. I usually convert the .rpm file to .deb using alien. Alien must be run as root with sudo and you need to use the -d and -c parameters.The command should look something like:

```
sudo alien -d -c VMware-Workstation-6.5.0-118166.i386.rpm
sudo dpkg -i VMware-Workstation-6.5.0-118166.i386.deb
```

where the first command creates the .deb file and the second installs it, and the file name will vary with the version that you are installing.

If you install using the bundle, it should have run the setup script automatically. If not, then you need to run:

```
sudo ./vmware-config.pl
```

If Ubuntu can't find vmware-config.pl in the path, you'll have to search for it. Then change to its directory and run it. That should build all the modules that are listed as missing in your follow-up post.

This should get you up and running.
tnx for reply. i have got the .bundle archive and installed vmware using "sh" command. 
is there any other solution doesn't need to download that bulky rpm installation file?! my monthly transfer limit is near the end. it tells that some modules are missing. where are these modules? does the .bundle file include them or not? may i download and install them separately?

you see, i haven't any problem installing vmware bundle file and using it under my i386 jaunty but the problem is witch amd64 one.

---

### Post by Tanker Bob on 2009-07-14
The bundle should be complete. The .rpm package merely repackages the bundle. That said, I've not had good experiences with the bundle in the past, which is why I use alien to convert the .rpm to .deb. Did you run the bundle as root with sudo?

---

### Post by SOULTE on 2009-07-14
> **Tanker Bob said:**
> The bundle should be complete. The .rpm package merely repackages the bundle. That said, I've not had good experiences with the bundle in the past, which is why I use alien to convert the .rpm to .deb. Did you run the bundle as root with sudo?
yes. i ran it using "sudo sh".

---

### Post by SOULTE on 2009-07-14
is there anyone have the same experience about vmware in 64 bit jaunty?

---

### Post by jackaloper on 2009-07-14
thanks

---

### Post by doas777 on 2009-07-14
> **SOULTE said:**
> is there anyone have the same experience about vmware in 64 bit jaunty?


well, it installed smoothly for me. just downloaded it from VMWare, extracted it and ran the .run I think. I did find that the previous version i had downloaded to work with intrepid did not work with jaunty. be sure to get the latest version.

---

### Post by SOULTE on 2009-07-14
I've downloaded VMware-Workstation-6.5.1-126130.x86_64_2.bundle. This is the latest version but not works for me and i don't know why. :(

---

### Post by doas777 on 2009-07-14
did you follow all the instructions here (with your downloaded version)?
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

the dependency packages are important

---

### Post by Tanker Bob on 2009-07-14
> **SOULTE said:**
> I've downloaded VMware-Workstation-6.5.1-126130.x86_64_2.bundle. This is the latest version but not works for me and i don't know why. :(
That's not the latest version. I downloaded and installed VMware-Workstation-6.5.2-156735.x86_64.bundle dated 3/27/09 back in May. It was part of the .rpm package which I converted to .deb, and installed perfectly in a relatively clean 9.04 x86_64 setup.

---

### Post by Digitallysick on 2009-07-15
to fix it, do the following

# sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
# sudo vmware

---

### Post by SOULTE on 2009-07-15
well, I found the .bundle file that I have is the latest .bundle by check it out in vmware.com download section. maybe it's because of not updated .bundle file but .rpm ! i'm in office now. so when i gone back home i'll try two commands by Digitallysick and if it won't work i'll download the .rpm archive. hope it solve my problem.
thank you all for your guidences.

edit:
> **doas777 said:**
> did you follow all the instructions here (with your downloaded version)?
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

the dependency packages are important
> **Digitallysick said:**
> to fix it, do the following

# sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
# sudo vmware
i did them and i successfully managed to get it work. no need to download .rpm archive. thanks again all of you bros. :)

---

### Post by babygenius55 on 2009-07-31
It worked like a charm. Changing the library that is.

---

