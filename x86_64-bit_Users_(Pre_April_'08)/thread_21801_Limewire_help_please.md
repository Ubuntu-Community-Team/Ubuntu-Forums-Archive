---
title: "Limewire help please"
date: 2005-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by boxxxx117 on 2005-03-24
I am trying to install limewire. i installed the SUN JRE following thier instructions to a T and i get this msg when i try and start limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = Kaffe]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/local/jre1.5.2_02/bin/: No such file or directory
OOPS, unable to locate java exec in  /usr/local/jre1.5.0_02/bin//  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

iv also tried it with the 1.4.2

now when i run 'java -version'
i get this 
Kaffe Virtual Machine

Copyright (c) 1996-2004 Kaffe.org project contributors (please see
  the source code for a full list of contributors).  All rights reserved.
Portions Copyright (c) 1996-2002 Transvirtual Technologies, Inc.

The Kaffe virtual machine is free software, licensed under the terms of
the GNU General Public License.  Kaffe.org is a an independent, free software
community project, not directly affiliated with Transvirtual Technologies,
Inc.  Kaffe is a Trademark of Transvirtual Technologies, Inc.  Kaffe comes
with ABSOLUTELY NO WARRANTY.

Engine: Interpreter   Version: 1.1.x-cvs   Java Version: 1.1

i dont understand. HELP PLEASE

---

### Post by kubla on 2005-03-24
You need to do two things:

1) get the Sun Java compiled for AMD64 by adding this to your /etc/apt/sources list

#for Java
deb [ftp://ftp.tux.org/java/debian/](ftp://ftp.tux.org/java/debian/) unstable non-free

2) make sure you haven't set a different home for your Java VM. What do you get when you type "echo $JAVA_HOME" from your shell?

Ian

---

### Post by boxxxx117 on 2005-03-24
i added that line to my sources.list 
and this is what i get
justin@MelfortMenace:~ $ echo $JAVA_HOME

justin@MelfortMenace:~ $
 
it doesnt give anything

---

### Post by kubla on 2005-03-25
[QUOTE=boxxxx117]i added that line to my sources.list 
and this is what i get
justin@MelfortMenace:~ $ echo $JAVA_HOME

justin@MelfortMenace:~ $
 
it doesnt give anything[/QUOTE]
 
After changing your sources file did you run apt-get update and apt-get upgrade?

Ian

---

### Post by krusk on 2005-03-26
I have the same problem when starting azureus....

My output:

> rasmus@ubuntumus:~/programmer/pakker$ azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/java/jre1.5.0_02/bin/
OOPS, you don't seem to have a valid JRE  [/usr/java/jre1.5.0_02/bin/java = ]
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
rasmus@ubuntumus:~/programmer/pakker$ 

I get no output when typing "echo $JAVA_HOME".

i have no ideas...

---

### Post by FluffyElmo on 2005-03-27
I have Azureus and Eclipse running under Hoary using the 64bit IBM 1.4.x JDK. Azureus may just be having problems with 1.5? Eclipse had an issue with the 64bit Sun 1.5 JVM, which is why I'm now using the IBM one, but I can't remember whether I had Azureus running back then or not. May be worth a try.
[http://www-128.ibm.com/developerworks/java/jdk/linux140/](http://www-128.ibm.com/developerworks/java/jdk/linux140/)

I haven't tried Limewire. But it seems to be finding the wrong JVM. After installing, place the [*path to jvm*]*/bin/* directory in your PATH variable. When you type *java -version* you should see a more current JVM. I think I set mine in the ~/.bashrc file, but it has been a while so Google is probably your  best bet for PATH modification tips...

---

### Post by boxxxx117 on 2005-03-28
#for Java
deb [ftp://ftp.tux.org/java/debian/](ftp://ftp.tux.org/java/debian/) unstable non-free

i added this to my sources file now i get this when i try to run apt-get update

E: Malformed line 23 in source list /etc/apt/sources.list (dist)

---

### Post by boxxxx117 on 2005-03-28
ok so i fixed the sources.list. i had it added wrong, but after i run the apt-get update and the other one i still get nothing with my echo $JAVA_HOME

---

### Post by boxxxx117 on 2005-03-29
okay so i have limewire working. i had to remove that kaffe stuff and then install the sun JRE.
so does anyone know how to create a desktop shortcut for limewire now?

---

### Post by bored2k on 2005-03-29
[QUOTE=boxxxx117]okay so i have limewire working. i had to remove that kaffe stuff and then install the sun JRE.
so does anyone know how to create a desktop shortcut for limewire now?[/QUOTE]
 create a scrip like this for example:

> 
#!/bin/sh
cd /home/boxxxx117/Limewire; sh runLime.sh

Let's say we name it lime.sh and put it in $Home dir.

Then we create the launcher so it will run
sh lime.sh [if its in your $Home, it will pick it up] .

Thats how I did mine -sort of- .

---

### Post by Liz on 2005-03-30
when i go to install LimeWire..i get 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

so i did java -version and i get
liz@dragynhart:~/Desktop/download $ java -version
java version "1.5.0_02"

and echo $JAVA_HOME gives me 
liz@dragynhart:~/Desktop/download $ echo $JAVA_HOME
/usr/java/jre1.5.0_02

anyone got any ideas on the next step?
i didnt have any problems with limewire in warty. but since upgrading to hoary, (3rd installation since my other hdd died on me) im not sure which way to go now.

any help would be gladly appreciated. 
thanks

oh, i should mention that i am using AMD athlon 2000+ chip.

---

### Post by eena on 2005-08-17
ok. so i have limewire. but the thing keeps on freezing on me.. :mad: something about my computer's firewall prevents me from going into the program. i need mucho help.

---

