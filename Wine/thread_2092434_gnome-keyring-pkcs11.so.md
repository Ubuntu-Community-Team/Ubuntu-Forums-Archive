---
title: "gnome-keyring-pkcs11.so"
date: 2012-12-07
forum: Wine
---

### Post by shaolin77 on 2012-12-07
Hello Community, 
   Need help!!!   I'm getting the following error when attempting to run and configure wine:

WINEPREFIX=~/.wine32_Dota2/ WINEARCH=win32 winecfg
wine: created the configuration directory '/home/shaolin/.wine32_Dota2'
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0xffe8d0, overlapped 0xffe8dc): stub
wine: configuration in '/home/shaolin/.wine32_Dota2' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory


I've google searching and reading multiple posts on Wine HQ forums, ubuntu forums and ask ubuntu forms and I can't see to find clear cut way on how to fix the issue.

I'm currently Running Ubuntu 12.04 LTS 64bit, the last few bits I've read is that this is an issue with the 64bit version.   The info was dated sometime in May 2012.   

Has this issue been resolved or is it still on going.   

And yes I'm trying to get Dota2 working on my box but that will be the focus after I find a solution the error above.

Please help!!!

---

### Post by shaolin77 on 2012-12-08
I have resolved the following issue with Wine not finding gnome-keyring-pkcs11.so

---

### Post by Tweak42 on 2012-12-08
> **shaolin77 said:**
> I have resolved the following issue with Wine not finding gnome-keyring-pkcs11.so

I have the same issue, it doesn't affect anything I do, but how did you resolve it?

---

### Post by shaolin77 on 2012-12-09
> **Tweak42 said:**
> I have the same issue, it doesn't affect anything I do, but how did you resolve it?

Yeah, I'm not sure what the impact of the error is but my steam ran fine either way.

You can fix by doing the following:

1.  Install getlibs
wget [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
sudo dpkg -i getlibs_2.06-0ubuntu1~ppa2_all.deb

2. Install the 32bit library:
sudo getlibs -p gnome-keyring:i386

3. Make symbolic link:

sudo mkdir -p /usr/lib/i386-linux-gnu/pkcs11/ 
sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

Then run steam...you'll notice the error is gone after do you the following above. 

Like I mentioned before I didn't notice any difference before and after but the error is gone :p

Hope this helps...Sharing is caring :p

---

### Post by NoCyberDom on 2012-12-10
The keyring isn't installing correctly now, just 13 hours after you replied above I get this in the terminal:

[I]The following i386 packages will be installed: gnome-keyring:i386
Continue [Y/n]? y
Downloading ...
[COLOR=Red]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install
[/COLOR][/I]
Issue with the mirrors? Not sure... I'll try again in the morning since it seems to have worked for you just 13 hours ago. Perhaps the mirrors are down temporarily.

---

### Post by Tweak42 on 2012-12-10
Well the bug doesn't really affect anything I do so far, it's just annoying so I'll leave it alone. 

I did find the bug report that addresses it though:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600)

---

### Post by shaolin77 on 2012-12-10
> **NoCyberDom said:**
> The keyring isn't installing correctly now, just 13 hours after you replied above I get this in the terminal:

[I]The following i386 packages will be installed: gnome-keyring:i386
Continue [Y/n]? y
Downloading ...
[COLOR=Red]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install
[/COLOR][/I]
Issue with the mirrors? Not sure... I'll try again in the morning since it seems to have worked for you just 13 hours ago. Perhaps the mirrors are down temporarily.

I think I see the problem here..for some odd reason the URL in step #1 is being displayed really weird in the posting which could be leading to some confusion.

Try this the actual URL:

'https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb'


**Remove single quotes in the url it should work now.**

---

### Post by NoCyberDom on 2012-12-10
No joy. I colour coded the terminal output to make it easier to read but the entire terminal op is here:

ncd@diablo:~$[COLOR=SeaGreen] wget [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)[/COLOR]
--2012-12-10 21:40:40--  [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb) [following]
--2012-12-10 21:40:41--  [https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7316 (7.1K) [application/x-debian-package]
Saving to: `getlibs_2.06-0ubuntu1~ppa2_all.deb.2'

100%[======================================>] 7,316       --.-K/s   in 0.003s  

2012-12-10 21:40:42 (2.34 MB/s) - `getlibs_2.06-0ubuntu1~ppa2_all.deb.2' saved [7316/7316]

ncd@diablo:~$ [COLOR=SeaGreen]sudo getlibs -p gnome-keyring:i386[/COLOR]
[sudo] password for ncd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=SeaGreen]ia32-libs is already the newest version.[/COLOR]
The following packages were automatically installed and are no longer required:
  wine-mono0.0.4 wine-gecko1.7 wine-gecko1.7:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
The following i386 packages will be installed: gnome-keyring:i386
[COLOR=SeaGreen]Continue [Y/n]? y[/COLOR]
Downloading ...
[COLOR=DarkOrange]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install[/COLOR]
ncd@diablo:~$

---

### Post by shaolin77 on 2012-12-11
> **NoCyberDom said:**
> No joy. I colour coded the terminal output to make it easier to read but the entire terminal op is here:

ncd@diablo:~$[COLOR=SeaGreen] wget [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)[/COLOR]
--2012-12-10 21:40:40--  [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb) [following]
--2012-12-10 21:40:41--  [https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpadlibrarian.net/38736204/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7316 (7.1K) [application/x-debian-package]
Saving to: `getlibs_2.06-0ubuntu1~ppa2_all.deb.2'

100%[======================================>] 7,316       --.-K/s   in 0.003s  

2012-12-10 21:40:42 (2.34 MB/s) - `getlibs_2.06-0ubuntu1~ppa2_all.deb.2' saved [7316/7316]

ncd@diablo:~$ [COLOR=SeaGreen]sudo getlibs -p gnome-keyring:i386[/COLOR]
[sudo] password for ncd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=SeaGreen]ia32-libs is already the newest version.[/COLOR]
The following packages were automatically installed and are no longer required:
  wine-mono0.0.4 wine-gecko1.7 wine-gecko1.7:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
The following i386 packages will be installed: gnome-keyring:i386
[COLOR=SeaGreen]Continue [Y/n]? y[/COLOR]
Downloading ...
[COLOR=DarkOrange]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install[/COLOR]
ncd@diablo:~$

Sorry to hear your still having issues with this.  I'm sure the issue with the issue with the mirror will be resolve...question is when.  I wonder if this can be reported somehow.

---

### Post by NoCyberDom on 2012-12-21
This remains unsolved but I found a workaround... I installed 12.04 32 bit in another partition and ran the program off that.

---

### Post by danfly on 2013-01-05
> **NoCyberDom said:**
> This remains unsolved but I found a workaround... I installed 12.04 32 bit in another partition and ran the program off that.

That is not a solution ¬¬

Otherwise, if i try install gnome-keyring:i386 from repositorys, synaptic advertise to me that are many dependecy conflicts =S

---

