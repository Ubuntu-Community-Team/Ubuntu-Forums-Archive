---
title: "[SOLVED] Can't change preferences in Synaptic"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-02-21
Yesterday, I decided I wanted to change some settings in Synaptic.  Specifically, i wanted it to clear out the cached packages once they are installed.

The problem is that when I either click Apply or OK, the desktop locks, and I have to restart the X server to regain usage.

Recently, I installed Cinerella(sp) for video editing.  I installed by adding a repository that did the work for me.  I developed a problem during the install, because the same repository also carried a newer version of DVDStyler and it tried to update my install version but failed on unpacking one of the .so files.

In order to fix the problem i Googled up a command that did a force install --all or something like that from the terminal.

then I did a sudo apt-get install -f and all seemed to complete normally.

Everything seems to be stable and working fine, EXCEPT that I can't change my settings for Synaptic.

I don't know if one is related to the other, I've never tried to change the settings before, I just wanted to provide all informaion available.

I did find ONE other person with the same problem by searching the forums, but he didn't get any replies.

Thanks for any help...

---

### Post by gsmanners on 2008-02-21
Adding repos indiscriminately can mess up your system, especially when installing multimedia apps that depend on so many libraries. You're not fixing anything by using "force install". Rather you are forcing apt to ignore the problems with its own database.

I think you would be best to remove those repos and remove whatever you got out of them.

---

### Post by crjackson on 2008-02-21
> **gsmanners said:**
> Adding repos indiscriminately can mess up your system, especially when installing multimedia apps that depend on so many libraries. You're not fixing anything by using "force install". Rather you are forcing apt to ignore the problems with its own database.

I think you would be best to remove those repos and remove whatever you got out of them.

Well, I don't feel it was indscriminately added.  It's from their official website which points directly to the Ubuntu Gutsy install section.  I didn't find the package in Synaptic, did I miss it or something?

```
7.10 Gutsy Gibbon
for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb http://repository.akirad.net akirad-gutsy main
Notes:
- Installations from this repository need an authentication key. Add it by typing the following command in your terminal: 
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
- Cinelerra package is available in 5 variants:
cinelerra (no opengl) - cinelerra-generic (with opengl) - cinelerra-k8 (with opengl) - cinelerra-k7 (no opengl)
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to akir4d at gmail dot com

for i386 (not working on amd 32 bits), by Valentina Messeri:
deb http://giss.tv/~vale/ubuntu32 ./

for AMD64 (and also Core Duo Intel64), by Valentina Messeri:
deb http://giss.tv/~vale/ubuntu64 ./
Note:
- If your package manager complains that it does not have the right version of libfaac (1.25) you can try installing libfaac0
```

None the less, do you think that uninstalling this app. is going to fix my preferences setting?  I've tested it out only a bit, and this app. is the best video editing app. for linux I can find, and something I really need.  Otherwise I must stick to Windows for video editing.

---

### Post by gsmanners on 2008-02-21
You said yourself that you needed to force install, so it obviously isn't suitable.

---

### Post by crjackson on 2008-02-21
> **gsmanners said:**
> You said yourself that you needed to force install, so it obviously isn't suitable.

I didn't have to force install that package.  It was an update to a different package that was already installed that caused the problem.  It just occurred at the same time.  I'm just not sure that the problem wasn't preexisting.  I'm going to test it out.  I have full backup images of the system before and after.  If the installation didn't cause this, then what?

---

### Post by crjackson on 2008-02-22
Well, I can confirm it had nothing to due with my recent installation of Cinelerra.  I restored my system to before the install and it has the same problem.  Furthermore, I have the same problem on 2 more (that I've tested so far) of my systems, and they have pretty much only basic installs with only updates from synaptic added.  I'll probably be filing a bug report on this.

---

### Post by crjackson on 2008-02-22
Bug report filed here [https://bugs.launchpad.net/ubuntu/+bug/194299]("https://bugs.launchpad.net/ubuntu/+bug/194299")

---

### Post by crjackson on 2008-02-22
I've now tried on 5 different system and they all exibit the same behavior.

---

### Post by crjackson on 2008-02-22
Since I can't get this setting to work, can someone tell me how to do the same thing by CLI, or the location of the files so I can delete them with a file manager?

---

### Post by gsmanners on 2008-02-22
Should work with:

sudo apt-get clean

Or remove anything in:

/var/cache/apt/archives/ and /var/cache/apt/archives/partial/

apt-get autoclean will clear out old packages

Fedora's yum has the behavior you describe by default, but I really don't understand what the point is. I never even come close to filling my /var partition.

---

### Post by crjackson on 2008-02-23
> **gsmanners said:**
> Should work with:

sudo apt-get clean

Or remove anything in:

/var/cache/apt/archives/ and /var/cache/apt/archives/partial/

apt-get autoclean will clear out old packages

Fedora's yum has the behavior you describe by default, but I really don't understand what the point is. I never even come close to filling my /var partition.

Thanks for your help.  It's just something I want to do...

---

### Post by crjackson on 2008-07-02
Issue was solved by upgrading to 8.04

---

