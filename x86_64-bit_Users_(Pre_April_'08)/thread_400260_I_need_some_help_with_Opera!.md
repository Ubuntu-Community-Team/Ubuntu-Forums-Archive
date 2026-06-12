---
title: "I need some help with Opera!"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rotaj on 2007-04-03
How do I force the install of Opera on an Edgy AMD64 machine. I have the deb file on my desktop. 

I have looked in a few of the previous postings regarding this issue. Many of the links on those pages were outdated. 
I am still weak with the CLI, so please walk me though it.

---

### Post by kuja on 2007-04-03
> **Rotaj said:**
> How do I force the install of Opera on an Edgy AMD64 machine. I have the deb file on my desktop. 

I have looked in a few of the previous postings regarding this issue. Many of the links on those pages were outdated. 
I am still weak with the CLI, so please walk me though it.

dpkg --install --force-architecture somefilename.deb

Oh, and you may also want to install ia32-libs ia32-libs-kde and lib32asound2. 
sudo apt-get install ia32-libs ia32-libs-kde lib32asound2

If it gives you any trouble afterwards you may also need certain things from ia32-libs-gtk and ia32-libs-openoffice.org.
sudo apt-get install ia32-libs-gtk ia32-libs-openoffice.org

---

### Post by Rotaj on 2007-04-05
I was able to install the 32 bit libraries, but Opera was a no go. Below are the results.

sudo dpkg --install --force-architecture Opera_9.10-20061214.6-shared-qt_en_i386.deb
Password:
dpkg: error processing opera_9.10-20061214.6-shared-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_9.10-20061214.6-shared-qt_en_i386.deb

Do I need to incude some path info?

---

### Post by kuja on 2007-04-05
You've got me stumped, the only thing I can see that puts me off is the caps in the "sudo dpkg ..." line. That's just plain weird.

---

### Post by Kamco on 2007-04-05
Be sure to download the static version of the .deb file. Then use the forced install.

Ken

---

### Post by Rotaj on 2007-04-05
Thank you. 

How or more accurately, where do I find a static version version of Opera?

---

### Post by Colonel Kilkenny on 2007-04-06
There is no need for static version. Or at least shared version worked perfectly for me (month ago, edgy 64-bit).
Are you sure that you're pointing dpkg to right file?
If the file is in your desktop try using "sudo dpkg -i --force-architecture ~/Desktop/*insertherefilename*.deb.

Just use tab-button after writing that ~/Desktop/ and it finds you the correct file if it's the only deb-file on your desktop..

---

### Post by Rotaj on 2007-04-07
hI appreciate all the assistance, but stil a no go for Opera. 

dpkg: error processing /home/xxxxxx/Desktop/sudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force-architecture (--install):
 cannot access archive: No such file or directory
dpkg-split: error reading /home/xxxxxx/Desktop/: Is a directory
dpkg: error processing /home/xxxxxx/Desktop/ (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 /home/xxxxxx/Desktop/sudo
 dpkg
 -i
 --force-architecture
 /home/xxxxxx/Desktop/


I have a dual boot sysytem. "xxxxxx" is on sda4. Does that make a difference?

---

### Post by Colonel Kilkenny on 2007-04-08
That looks like you haven't specified which deb-file to install or something.
If your opera*.deb file is in desktop, use command "sudo dpkg -i --force-architecture ~/Desktop/opera*.deb". And replace opera*.deb with the correct file name.
For me that error looks like you have problem with the install command and not with Opera.

And dual boot makes no difference nor does partition.

---

### Post by pearlie on 2007-04-11
Errrm... I installed the 32bit libraries, force-installed the 32bit Opera .deb, and got no errors back.

Then I tried to start it from the terminal, and I got this:

*/usr/lib/opera/9.20-20070409.6/opera: error while loading shared libraries: libaudio.so.2: wrong ELF class: ELFCLASS64*

What's an ELF class? Is that where pointy-eared children go?

---

### Post by John Jason Jordan on 2007-04-11
> **pearlie said:**
> Then I tried to start it from the terminal, and I got this:

*/usr/lib/opera/9.20-20070409.6/opera: error while loading shared libraries: libaudio.so.2: wrong ELF class: ELFCLASS64*

What's an ELF class? Is that where pointy-eared children go?
I got a similar error after installing Adobe Reader 7.08, which is also a 32-bit app. Someone else told me to install ia32-libs, and that corrected the problem.

Only problem is I may have lied. I can't remember exactly which library it was. I *think* it was an ia32 library, but I may be mistaken. I have installed:

ia32-libs
ia32-libs-gtk
ia32-libs-kde
ia32-libs-scim
ia32-libs-sdl
ia32-sun-java5-bin

I know if you search the forums for a thread started by me about Adobe Reader on amd64 you will find where someone gave me the answer. (I'm in a hurry at the moment or I'd do it for you.)

---

### Post by pearlie on 2007-04-13
Sadly, that didn't solve my problem - I installed everything you have, everything I could think of, and everything that has libaudio somewhere in the name or description of it.  But thanks for the assist anyhow - I now know what I need if I install Adobe Reader :D

---

### Post by kuja on 2007-04-13
As far as I know, all you need to run Adobe Reader is libstdc++5. Oh, and pearlie, the 32-bit libaudio.so.2 file is in the ia32-libs-openoffice.org package. (In feisty it has been to the ia32-libs package).

---

