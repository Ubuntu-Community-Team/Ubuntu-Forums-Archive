---
title: "how to install IBM Symphony on 64-bit systems"
date: 2008-10-13
forum: x86 64-bit Users
---

### Post by linuxed on 2008-10-13
I was able to get IBM Symphony v1.3 installed on Ubuntu 8.10 64-bit by using the steps listed below.  [_You can download Symphony 1.3 here._](http://www14.software.ibm.com/webapp/download/preconfig.jsp?id=2008-09-02+15%3A54%3A56.990888R&S_TACT=104CBW71&S_CMP=)


[list=1]
[*]First off you will need to install the following packages.
```

sudo apt-get install libstdc++5 ia32-libs ia32-sun-java6-bin

```
[*]Next download [_this package_](http://mirrors.kernel.org/ubuntu/pool/main/libx/libxkbfile/libxkbfile1_1.0.4-1_i386.deb) to your desktop.
[*]Open the libxkbfile package with file-roller (make sure to use sudo)
```

sudo file-roller ./libxkbfile1_1.0.4-1_i386.deb

```
[*]Open the data.tar.gz file in file-roller.  You should be able to simply double click on the file to open it in file-roller.  If you are prompted to select an application to open it with just type file-roller in the Application box and click Open.
[*]Double click the . folder then the usr folder then the lib folder.
[*]Select the following files:
```

libxkbfile.so.1
libxkbfile.so.1.0.2

```
[*]Click extract and extract those files to /usr/lib32.
[*]Close both file-roller windows
[*]Type the following:
```

sudo dpkg --force-architecture -i symphony*.deb

```
[/list]

After the installation is completed you'll have a new Symphony menu item on you Applications > Office menu.  The first time you run it you'll be asked to accept a software license from a terminal window.  Just type 1 and then enter to continue.

---

### Post by arch0njw on 2008-11-25
I have not done extensive testing (yet), but this similar process seems to work with Symphony 1.2.  The only difference being that a DEB is downloaded and you need to install it with "sudo dpkg -i --force-architecture symphony_1.2-1hardy1_i386.deb"

The "chown" steps do not appear to be necessary when installing this DEB.

Thanks for this!  It was a big help; I wouldn't have figured out the .so file/s.

---

### Post by ubun_two on 2008-11-25
I know IBM Symphony and OpenOffice are related.  How is the performance with Symphony?  Is it worth for me to get this instead of/in addition to OpenOffice 3?

The reason I am considering this is because OpenOffice 2/3 performance is reeeeaaaaaally sluggish when the document has many objects.  I am hoping to find an alternative that's hopefully better.

FYI, my computer is not that old (intel quadcore + 4GB RAM).

---

### Post by linuxed on 2008-11-28
Unfortunately Symphony seems to be just as slow as OpenOffice.  Neither application seems to outperform the other.  I currently have both apps installed on my system and frequently switch between the two.

---

### Post by plr4ever on 2008-12-30
That link just takes me to a download page with Lotus symphony 1.2, and there is no generic binary, just a deb, which does not work with these instructions.

---

### Post by arch0njw on 2008-12-30
> **plr4ever said:**
> That link just takes me to a download page with Lotus symphony 1.2, and there is no generic binary, just a deb, which does not work with these instructions.

pl/ -- quoting myself from above in this thread:
[I]
I have not done extensive testing (yet), but this similar process seems to work with Symphony 1.2. The only difference being that a DEB is downloaded and you need to install it with "**sudo dpkg -i --force-architecture symphony_1.2-1hardy1_i386.deb**"

The "chown" steps do not appear to be necessary when installing this DEB.

Thanks for this!  It was a big help; I wouldn't have figured out the .so file/s.[/I]

---

### Post by mehaga on 2009-03-09
Thank you both (OP and arch0njw) very much.

---

### Post by linuxed on 2009-03-22
I've updated the instructions above for use with the v1.2 deb package.  The deb package has simplified the installation quite a bit.  Let me know if you encounter any problems with the new instructions.  Thanks.

---

### Post by cogitordi on 2009-06-27
I can confirm that these steps work on Ubuntu Hardy Heron AMD64 with IBM Symphony 1.3.

---

### Post by maturin on 2009-06-28
Sorry - no luck here.  Same setup as cogitordi (64 bit & hardy and symphony 1.3).

About the only difference is that I already had all the prerequisite packages installed, and had to move libxkbfile.so.1 and libxkbfile.so.1.0.2 into lib32 manually from regular old lib.

It doesn't install on the menu, and trying to start it from the command line leads to "permission denied".  

Tracking down the recalcitrant file and changing the permissions eventually leads to numerous complaints about missing operating system libraries.  I'm assuming something's wrong with the 32 bit library setup but have no clue.

---

### Post by cogitordi on 2009-06-29
It may have something to do with the existing condition of the OS. I did not have the libraries installed but I attempted to install Symphony. The installation would not run.

I then installed the libraries as described: libxkbfile.so.1 and libxkbfile.so.1.0.2. 

I ran the installation once more and it was successful.

---

### Post by cogitordi on 2009-07-18
Just did the same installation successfully in Heron-64 on an Intel Core 2 Duo box. Follow the instructions and it works.

---

### Post by konungursvia on 2009-09-14
I tried this but now the version on IBM's website is 1.3 and it's a 180Mb RPM not a deb now. So I tried alien to make a deb but it froze my system, creating a subdirectory tree called symphony but no deb.

---

### Post by linuxed on 2009-09-14
[You can download the v1.3 deb package here.](http://www14.software.ibm.com/webapp/download/preconfig.jsp?id=2008-09-02+15%3A54%3A56.990888R&S_TACT=104CBW71&S_CMP=)

---

### Post by konungursvia on 2009-09-14
Thanks.

---

### Post by theZoid on 2009-09-15
Cool....installed Symphony 1.3 deb......trying to decide how I like it....:)

---

### Post by theZoid on 2009-09-22
Anyone know how to uninstall Symphony?  I like it, but I think OO.o might work better for me in the long haul....it seems like IBM isn't putting much work into it from what I gather from the forums.  They aren't addressing simple, cosmetic issues, some going back for 2 years.

---

### Post by linuxed on 2009-09-23
Check the control file in the symphony deb package.  I don't have symphony installed at the moment so I can't tell you what the actual package name is.  Open the deb package in file-roller, double click the control.tar.gz file, double click the "." folder, double click control and open with gedit.  The first line in the file should begin with "Package:".  Write down whatever package name is listed on that line.  Once you have the package name type "sudo dpkg -r nameOfPackage".

---

### Post by virgil_machine on 2009-10-28
Works to the last step on karmic-64..after I changed permissions on usr/lib to 777, but the install process fails: 

> 2009-10-28 09:42:02 -- Begin pre-install...
2009-10-28 09:42:02 -- rcplauncher.properties: /opt/ibm/lotus/Symphony/framework/rcp/rcplauncher.properties
2009-10-28 09:42:02 -- can not find file rcplauncher.properties
2009-10-28 09:42:02 -- End pre-install...
2009-10-28 09:42:18 -- Begin post-install...
2009-10-28 09:42:18 -- Install action is: configure ...
2009-10-28 09:42:18 -- Preparing for .ini file merge...
2009-10-28 09:42:19 -- Merging .ini files...
2009-10-28 09:42:19 -- Running provisioning with the following command:
2009-10-28 09:42:19 -- ./rcplauncher -data /tmp/.lotus/symphony -provManifest -rcpLauncherWait -noSplash -product NULL -provisioningOperation install -vmargs -DprovisioningOperation=install
2009-10-28 09:42:20 -- Provisioning failed to launch, or terminated unexpectedly
2009-10-28 09:42:20 -- Platform may have been running when upgrade/uninstall/hotfix was attempt

Anyone have an idea?

---

### Post by virgil_machine on 2009-10-29
Success!

I found [this link at lotus]("http://symphony.lotus.com/software/lotus/symphony/help.nsf/GeneralFAQ#15").  It's not completely correct for karmic, but neither is this posting (at least I attribute the differences to karmic).
First, it's not libstdc++5, it's libstd++6, which is installed by default with karmic (at least in my version)--that's in both places.  

The Lotus version had a slightly different way of dealing with libxkbfile1:
> Download and extract libxkbfile1, and make use of them.

    * Make a directory to save libs.

      sudo mkdir /libxkb
    * Download libxkbfile1 to /libxkb/*.deb (Do not install! Will extract the package manually later):

      [http://ftp.us.debian.org/debian/pool/main/libx/libxkbfile/libxkbfile1_1.0.5-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/libx/libxkbfile/libxkbfile1_1.0.5-1_i386.deb)
    * Extract the deb package.

      cd to /libxkb

      sudo dpkg -X libxkb*.deb ./

      Folder /libxkb/usr/lib will be created, the libs located in this folder.
    * Create symbol link of libxkb.

      sudo ln -s /libxkb/usr/lib/libxkbfile.so.1.0.2 /usr/lib32/libxkbfile.so.1

Since I couldn't get it to work with the directions here, I followed the Lotus directions.

The last step in the lotus version says to download ISMP installer, which from what I can tell is not correct. In any case, I can't find the ISMP Installer or the IBM_Lotus_Symphony_linux.bin it refers to.  [update: IBM has acknowledged this error and says they'll fix their documentation]

So, I took the last step in this OP (sudo dpkg --force-architecture -i symphony*.deb), and all is well.

Since the difference between the two approaches [taking into account the acknowledged IBM error] is in how to handle libxkbfile1, I'd say that's the solution, at least for karmic...at least for my system: 	

    ASUS M3A78-CM  Motherboard
    AMD Athlon X2 4850e Processor
    karmic koala vm under virtualbox 3.0.8 on jaunty host

---

### Post by dwasifar on 2009-11-16
> **linuxed said:**
> I was able to get IBM Symphony v1.3 installed on Ubuntu 8.10 64-bit by using the steps listed below.  

This worked for me in Karmic, except that libstdc++5 is not in the Karmic repos.  I substituted libstdc++6 and everything worked fine.

Thanks for the howto.  :)

---

