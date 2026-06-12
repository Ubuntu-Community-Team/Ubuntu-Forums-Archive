---
title: "anti-virus for x64 feisty/gutsy?"
date: 2008-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by The_Jesus on 2008-01-31
im wondering if there is a virus scanner for gutsy gibbon or feisty fawn. i have the feisty fawn cd, btu somehow got the bad burn i think. considering .i386 and .tar.gz .rpm and .deb files wont work, period.

im wanting to do a virus scan and make sure nothing si wrong with my computer so could someoen please tell me?> im kind of concerned becaus ea link i clicked about an hour ago has a known virus, that my friend got that took about 80gigs of memory before he got rid of it.
some assistance pplzkthx~Locke`/The_Jesus~

---

### Post by Kilz on 2008-01-31
> **The_Jesus said:**
> im wondering if there is a virus scanner for gutsy gibbon or feisty fawn. i have the feisty fawn cd, btu somehow got the bad burn i think. considering .i386 and .tar.gz .rpm and .deb files wont work, period.

im wanting to do a virus scan and make sure nothing si wrong with my computer so could someoen please tell me?> im kind of concerned becaus ea link i clicked about an hour ago has a known virus, that my friend got that took about 80gigs of memory before he got rid of it.
some assistance pplzkthx~Locke`/The_Jesus~

Linux has no known viruses in the wild, none. Windows viruses can not infect a Linux computer. Anti virus is useless on a Linux computer. You do not need it. Just delete the file so it doesnt get passed by you to someone else. You would actually have to manually give it to someone.
Viruses attack the poor security and code of Windows. Linux has none of those flaws. The only people who run a form of Linux that could have any use for anti virus is if you run a **mail server** that Windows users connect to to send email. It would only be useful then because people who send would be blocked from sending viruses.

---

### Post by Fechter on 2008-01-31
First, you should read this 
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)
And, I have to say, If you are not using your system as a mail server, you won't need an antivirus at all. Anyway, if you are in a hostile environment, you can configure your firewall and you will have no 
problems. MAC and Win viruses don't work on Unix-based systems, so you needn't worry. Anyway,
it is not true that there aren't any viruses for Linux, but they are not a serious threat.

---

### Post by jamesford on 2008-01-31
f-prot  works well

---

### Post by tad1073 on 2008-01-31
you can try clamav and chkrootkit

---

### Post by crjackson on 2008-01-31
Have a look here [http://www.howtoforge.com/avg_antivirus_ubuntu_feisty]("http://www.howtoforge.com/avg_antivirus_ubuntu_feisty")

---

### Post by Kilz on 2008-01-31
> **Fechter said:**
> First, you should read this 
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)
And, I have to say, If you are not using your system as a mail server, you won't need an antivirus at all. Anyway, if you are in a hostile environment, you can configure your firewall and you will have no 
problems. MAC and Win viruses don't work on Unix-based systems, so you needn't worry. Anyway,
**it is not true that there aren't any viruses for Linux, **but they are not a serious threat.

What was said was there are no viruses in the wild. There are proof of concept viruses, and ones that would work if you ran as root. But there is nothing attacking Linux installs.

---

### Post by MageOrchid on 2008-02-01
ahh yes i see hmm, well i was worried bout the same thing. noting its a 64 bit system and im a new linux user as well

---

### Post by Kilz on 2008-02-01
> **MageOrchid said:**
> ahh yes i see hmm, well i was worried bout the same thing. noting its a 64 bit system and im a new linux user as well

Dont worry, linux is safe without anti virus.

---

### Post by frankos44 on 2008-02-01
Linux is safe but you can pass on virus to another windows user. AVG now has a free virus checker for Linux.

Its also useful for fixing infected windows machine, sometimes the only way to fix them. You will need to mount the windows hard drive with write permissions though.

---

### Post by Kilz on 2008-02-01
> **frankos44 said:**
> Linux is safe but you can pass on virus to another windows user. AVG now has a free virus checker for Linux.

Its also useful for fixing infected windows machine, sometimes the only way to fix them. You will need to mount the windows hard drive with write permissions though.

How are you going to pass a virus to a windows user? Are you going to manually send someone a virus. Since viruses cant infect a Linux os they cant copy or send themselves to anyone on the off chance that one may get on your system. They cant infect other files on your linux system. So it would take you actually sending a unknown attachment to someone, or a file you downloaded. Secondly if they have windows, odds are they have antivirus. They should be scanning everything that comes in their system. If not they are dead meat anyway.
If you do rescue work, use the [System Rescue CD]("http://www.sysresccd.org/Main_Page"). It has anti virus installed and available. Its a Linux distribution on a live cd that is setup to rescue down systems, even windows. This way you can rescue the system and not have anti virus on your desktop system to drain resources.

---

### Post by frankos44 on 2008-02-01
Yes I agree but what about this, I have a customers windows PC in for repair and I cant persuade them to use Linux.

Step 1
Backup the users files from the infected PC to my Ubuntu computer.

Step 2
Scan these files using AVG so when I copy the files back again later they will not contain viruses.

Step 3
Often by the time I get to work on the repair the PC's barely boots up! There is no chance of installing Anti-virus software and removing the viruses. Often I decide I to nuke the damm thing and cerate a new windows system.

Step 4
Copy users files back to the windows PC again.

I do indeed need a virus checker on Linux to do this, I don't give a ####! if the files have viruses or not but the customer does.

---

### Post by Kilz on 2008-02-01
> **frankos44 said:**
> Yes I agree but what about this, I have a customers windows PC in for repair and I cant persuade them to use Linux.

Step 1
Backup the users files from the infected PC to my Ubuntu computer.

Step 2
Scan these files using AVG so when I copy the files back again later they will not contain viruses.

Step 3
Often by the time I get to work on the repair the PC's barely boots up! There is no chance of installing Anti-virus software and removing the viruses. Often I decide I to nuke the damm thing and cerate a new windows system.

Step 4
Copy users files back to the windows PC again.

I do indeed need a virus checker on Linux to do this, I don't give a ####! if the files have viruses or not but the customer does.

Ok, you may have another reason for running a anti virus, its business related. But the average desktop user who does not back up customers data and reinstalls the data has no need of anti virus for Linux.

---

### Post by frankos44 on 2008-02-01
> **Kilz said:**
> Ok, you may have another reason for running a anti virus, its business related. But the average desktop user who does not back up customers data and reinstalls the data has no need of anti virus for Linux.

I agree, once you make the step you don't have a virus issue. Some home users may have a samba / windows file share to contend with though.

---

### Post by Kilz on 2008-02-01
> **frankos44 said:**
> I agree, once you make the step you don't have a virus issue. Some home users may have a samba / windows file share to contend with though.

Home users are better off installing Avast or AVG to the Windows machines on their home network imho.

---

### Post by MageOrchid on 2008-02-01
alright so how would one go about configuring the firewall?

---

### Post by frankos44 on 2008-02-01
Does your router have one?

Normally the default setting would suffice.

You might want to open up port 22 if you want to us SSH.

If you intend to host a web server, port 80 and possible port 443 for SSL would need also need to be open.

You sound as if you are an ex paranoid windows user, you can relax now, youve seen the light at last.

---

### Post by Kilz on 2008-02-01
Linux comes with iptables (a firewall) and all inbound ports closed. You can install an application like firestarter (in the repositories) to configure the firewall if you want. But imho you will only make it less secure by opening ports.

---

### Post by Fechter on 2008-02-01
Hey Kilz why not look here [http://www.linux.com/feature/125548](http://www.linux.com/feature/125548) I think some precautions are never
surplus; anyway, if you are not using your computer in a very hostile environment, you won't need antivirus. Seems a firewall is excellent /firestarter or guarddog/. If you want antivirus, clam is specially written for Unix-systems, but there are also AntiVir, Panda, Kaspersky, Avg, Avast.. If I were you, I wouldn't waste my time, but it is your choice, so you can try it out.:)

---

### Post by Kilz on 2008-02-01
> **Fechter said:**
> Hey Kilz why not look here [http://www.linux.com/feature/125548](http://www.linux.com/feature/125548) I think some precautions are never
surplus; anyway, if you are not using your computer in a very hostile environment, you won't need antivirus. Seems a firewall is excellent /firestarter or guarddog/. If you want antivirus, clam is specially written for Unix-systems, but there are also AntiVir, Panda, Kaspersky, Avg, Avast.. If I were you, I wouldn't waste my time, but it is your choice, so you can try it out.:)

I am aware of that story. Notice the title. "**Mystery** infestation strikes Linux/Apache Web sites"
They have no idea how this is happening, go ahead, read it. 
I run a lamp server and have no anti virus installed, and my server is not infected. Your story does not prove that anti-virus would have solved the issue or prevented it. Since we dont know how the servers became compromised its not a good idea to install applications that may not help.
Linux has 0, thats right 0 viruses in the wild. Those that exist are proof of concept viruses made by the antivirus companies to prove that Linux needs antivirus. They require you to run as root (something Windows dose) or copy them into place as root.
The anti virus applications you mention scan for Windows viruses, Clam is mainly used by email servers. More as a courtesy to the Windows users who connect to the server. The Linux email server cant get infected by a Windows virus.
Users who recently change over to Linux from Windows sometimes feel the need to install antivirus because they are so used to it on windows. But it isnt needed. A virus is a piece of code that exploits the huge holes in Windows and its sad security. Neither are a problem on Linux.
Be glad it isnt needed and put the extra resources to good use. Running applications you enjoy.

I dont miss Windows and anti virus one bit.

---

### Post by Fechter on 2008-02-02
Here I agree with you. Even if you ever get infected in linux, the virus can't spread because it hasn't the same environment as in Windows and you jst delete the infected file and it cannot spread any more. Also, if not given root privileges /chmod +x I think/  , it has acess only to the desktop and home directory, but he system is untouched.Anyway, at Virusbtn and ICSA Labs there are some antivirus for lInux tested, but there really is no point. Linux and other Unix-based systems are the most secure
and stable. :)

---

### Post by Kilz on 2008-02-19
> **stooshbunutu said:**
> There is a very reliable and free virus scan that now has a .deb all inclusive file for download. AVG anti-virus. it can be useful for scanning files even though the threats are low

[click here]("http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb") to download

Hope this helps:)

**Threats are not low**, **[COLOR="Red"]they dont exist. [/COLOR]** People who install anti virus on desktop Linux are only wasting resources. Most of them are new users who have just come over from Windows and think anti virus is needed as part of running any operating system. They are sadly misinformed and hopefully will learn in time to just say no to people who suggest it.

---

### Post by pixel :-) on 2008-02-19
Hem,guys,i think you should have read more carefullyi :lolflag: ,the real problem of the thread was

 "btu somehow got the bad burn i think. considering .i386 and .tar.gz .rpm and .deb files wont work, period."

This don't make a lot of sence :popcorn: .his problem are not viruses:

I'll try to simplify and summarize,i don't make any assumptions:
in ubuntu you can only install .deb filles.with "dpkg" if you have it on your computer and with "apt-get" if you whant to downlod it from the repositories.
,rpm and .tar.gz, can be installed but there no garentie,with "alien"

you can only install .deb FOR 64 bit in a 64 bit ubuntu.
if you are on a 32 bit linux you can only install 32 bit .deb paqueges
you can be on a 64 bit hardware and install 32 bit linux,type "uname -m" in a terminal ,it will tell you on what you are.If you really are on 64 ubuntu,i recomend to install a 32 bit,there are needless complications with 64 bit for noobs.
You can install 32 bit programms on 64 bit linux,but it's not streat forword,and not garentied.

more precicelly:
 .i386, means that it's a 32 bit paquege,you are(i presume) on 64 bit, thats not suprizing that he complains.What would you feel like if you had to where a dress

.tar.gz,it's a compressed fille,i guess that it's the source ,you have too uncompresse ,then compille it,and then install it.So just forget it for know. 

.deb:i hope that you didn't just clik on it.It have to be of the good architecture and of the good flavor.

---

### Post by MageOrchid on 2008-05-31
same person as the original poster. how can one find the file if they dont know what the file is or where?

---

### Post by MageOrchid on 2008-05-31
also to tag onto that, .zip .deb .tar.gz and  a  well basically all other formats dont work  jsut got rpm to downlaod, and install properly.. yet i ant get myjava to work.

---

