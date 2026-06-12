---
title: "Lost disk space"
date: 2008-07-31
forum: x86 64-bit Users
---

### Post by painterh on 2008-07-31
Hi all;
     First off, let me just say I use Ultimate edition 1.8 which is Hardy x64. I have a separate linux drive (160 gig Seagate Barricuda) in a dual boot system w/WinXP.  My Ubuntu OS was set to access my Windows home network for printing and file sharing using samba. Up till now everything has been just fine. Now, I don't know what was the root of the problem, but I suddenly lost the ability to print to the printer located on my wife's Win XP box (both our boxes are connected to our router via ethernet).  In searching and posting this problem on Ultimate edition forums, and finding one of the regulars had just having the same issue, I received a suggestion to install my printer via LDP/LPR Host or Printer, and was told how to do this using the ip address of my wife's computer. So far so good, I got my printing back.
     This was now only the beginning of a series of nightmares from which I don't know how to recover.  Somehow, by linking these computers together in this manner, My computer started generating 2 very large log files which are normally in most (or maybe all ) Ubuntu systems.  One is called daemon.log.0, and the other is syslog.0.  These log files quickly grew to about 48 GBs each and consumed all but 1.7 GBs of this drive.  I found this out after bootup the next morning after setting up the printer in the manner described above.  On bootup I received a message that I was running out of disk space on my Ubuntu drive.  I started searching the filesystem and soon found these 2 files.  Unsure of what to do with them, I asked on the Ultimate forum about this and was given the suggestion to just erase them.  Seeming logical to me, I did just that using gedit (as root). This however did not solve the problem because I next found that upon removal I somehow now had 2 backup log files with the same name and the same size.  I then deleted them (as root), and thought everything was going to return to normal.  I now, however am left with no more disk space than I had before.  I used the disk usage analyzer, and found that indeed the files and backups were gone and I should have more space, but the drive is still reported to have only 1.7 GBs free.  I don't know what has happened, but I would appreciate anyone's help to find my missing space.

---

### Post by gsmanners on 2008-07-31
You might try checking /root and see if they ended up there.

sudo du /root -hx --max-depth 1

---

### Post by Yannick Le Saint kyncani on 2008-07-31
> **painterh said:**
> I don't know what has happened, but I would appreciate anyone's help to find my missing space.

Hi painterh, the easiest way to find what is using disk space is to use "sudo du -ksx /some/directory | sort -n".

You should start with / : "sudo du -ksx / | sort -n" and work your way up until you've found which file / directory is using all this space.

Hope it helps.

---

### Post by painterh on 2008-07-31
Hey all;
I ran the command sudo  du /root -hx --max-depth 1.  It appears I have 97GB in /root/.local, and it shows further down in the list 97GB in /root.  I'm guessing that the files showing in root are the same ones showing in /root/.local.  Now what to do next? How come that isn't visible within nautilus? see below

97G	/root/.local
4.0K	/root/.gnome2_private
140K	/root/.gnome2
652K	/root/.tremulous
3.1M	/root/usr
4.0K	/root/.wapi
24K	/root/.gnupg
484K	/root/.loki
4.0K	/root/.gconfd
4.0K	/root/.gvfs
1.2M	/root/.synaptic
200K	/root/.gconf
8.0K	/root/.nautilus
16K	/root/.dbus
7.0M	/root/.cache
8.0K	/root/Desktop
4.0K	/root/.mozilla
4.0K	/root/.aptitude
97G	/root

---

### Post by painterh on 2008-07-31
Thanks for all the help guys.  I was finally able to isolate the folder in the root directory and delete it. As always, it's nice to have folks who will help.  Thanks again:\\:D/

---

### Post by painterh on 2008-08-02
:D
Thanks for all the help everyone.  Great job.

---

