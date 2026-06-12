---
title: "Java"
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr_koboi on 2006-03-20
Hi,
     anybody know how to install Java for Breezy?

---

### Post by TLE on 2006-03-20
I did a simple search on the wiki for "java" and found [this page]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-68565ae07a003332e82c9f23706638777396c249")

---

### Post by mr_koboi on 2006-03-20
I tried that already. Didn't work. Im not sure what I did wrong.followed those instructions step by step.

---

### Post by TLE on 2006-03-20
Where in the procedure did it go wrong ?

---

### Post by mr_koboi on 2006-03-20
Went to JavaPPC page.
Could'nt execute second command.
<fakeroot alien fakeroot alien ibm-java2-ppc-jre-5.0-0.0.ppc.rpm>

says cant locate fakeroot.

---

### Post by will.first on 2006-03-21
Try using sudo instead of fakeroot.

---

### Post by TLE on 2006-03-21
But are you supposed to be using the PPC version ?

---

### Post by funkyade on 2006-03-29
[QUOTE=will.first]Try using sudo instead of fakeroot.[/QUOTE]

sudo is NOT the same as fakeroot!

sudo gives a regular user superuser priviledges.

fakeroot replicates the root directory structure so a regular user can make .deb packages etc... without the requisite write priviledges.

if you follow the instructions in the wiki you will find the IBM java installs in /opt, not /usr/lib as stated. If you replace the paths in the export command with the path in /opt and reboot before setting the alternative java then it should work okay. Also when running the alien command try setting the --scripts option if it doesn't work first time round.

hth

---

### Post by nazish on 2006-03-29
hi everybody,

it actually very easy to install java on your ubuntu machine.It can b done with a  few clicks.

First ,

you didnt specify whether you need JRE or Java Compiler (to run java programs) so I assume that you need JRE.

Also assuming that you know how to use Synaptic package manager,

goto System->Administration->Synaptic Package Manager

after entering ur password click the search button

there type **Blackdown** and press enter it will show u the relevant options.ASSUMING THAT U HAVE ALL THE REPOSITORIES UPDATED.the blackdown version of java is JRE 1.4.2.

If u need the **latest version visit of JRE or J2EE SDK **then visit the following links,
for **J2SE 5.0 Update 6 with Netbeans IDE it has JRE bundled with it too**
[https://sdlc5b.sun.com/ECom/EComActionServlet;jsessionid=EF3323FD8F5007EC1BEB992825DEB9B4#](https://sdlc5b.sun.com/ECom/EComActionServlet;jsessionid=EF3323FD8F5007EC1BEB992825DEB9B4#)

for downloading JRE only

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

---

### Post by jdp on 2006-03-29
The JavaPPC page says that Blackdown doesn't work with Mozilla browsers, and it's only at 1.3.1 for PPC.

---

