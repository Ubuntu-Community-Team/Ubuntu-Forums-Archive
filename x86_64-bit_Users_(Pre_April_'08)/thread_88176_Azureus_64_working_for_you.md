---
title: "Azureus 64 working for you?"
date: 2005-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by yohan on 2005-11-09
I installed the compilable azureus from azureus.sourceforge.com (The 64 bit version) but i have a problem. Ive got jre1.5 and azureus works fine usually but 90% of the time when i press tools->options i get this error:
> 
 yohan@yohan:/opt/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_05]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
**** DHT: Anti-spoof currently disabled for old clients ****
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00002aab0166cbd9, pid=10851, tid=46912501779168
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_05-b05 mixed mode)
# Problematic frame:
# C  [libuim.so.0+0x10bd9]
#
# An error report file with more information is saved as hs_err_pid10851.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
./azureus: line 107: 10851 Aborted                 ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.


The funny thing is that sometimes! Im not sure when...it works! What could be wrong? 

How did you guys install azureus? The guide on this forum didnt work for me, I get an error when doing the dpkg install.

Thank you!

---

### Post by jon_gunnar on 2005-11-10
[QUOTE=yohan]I installed the compilable azureus from azureus.sourceforge.com (The 64 bit version) but i have a problem. Ive got jre1.5 and azureus works fine usually but 90% of the time when i press tools->options i get this error:


The funny thing is that sometimes! Im not sure when...it works! What could be wrong? 

How did you guys install azureus? The guide on this forum didnt work for me, I get an error when doing the dpkg install.

Thank you![/QUOTE]

Used the 64AMD version for a long time. No problem at all. The install were just a matter of downloading the program from Azureus, extract it to a suitable directory and start using it.

---

### Post by yohan on 2005-11-10
That is exacly what I did, real simple installation and no errors when isntall.

But my question is, do i get this random errors because of jre? Has anyone experienced that java unstable on 64bit system? 

I get this error:
# Problematic frame:
# C [libuim.so.0+0x10bd9]
Is this because im using the wrong dependencies, should I reinstall something?

Thanks

---

### Post by ubernoob on 2005-11-11
My java seems unstable as well. I think it is my jvm that is the problem. Not azureus.

I can't start eclipse either. Installed it from synaptic.

---

### Post by Yagisan on 2005-11-11
[QUOTE=yohan]But my question is, do i get this random errors because of jre? Has anyone experienced that java unstable on 64bit system? 

I get this error:
# Problematic frame:
# C [libuim.so.0+0x10bd9]
Is this because im using the wrong dependencies, should I reinstall something?

Thanks[/QUOTE]There seems to be an occasional bad interaction between UIM (a japanese input method that I use, and you have installed on your system, thats what libuim comes from), and the sun jre. You can try upgrading the sun jre, downgrading the sun jre, or remove uim.

---

### Post by yohan on 2005-11-11
actually thats exacly what I have Yagisan! I have uim installed, thank you! Thats why nobody else had this issue. Its strange though how uim would disrupt my java.

Thanks, ill experiment a bit.

---

### Post by Yagisan on 2005-11-12
[QUOTE=yohan]actually thats exacly what I have Yagisan! I have uim installed, thank you! Thats why nobody else had this issue. Its strange though how uim would disrupt my java.

Thanks, ill experiment a bit.[/QUOTE] For some reason Java is trying to load uim, and it doesn't allways like it. It also breaks amule, but as scim is broken in breezy, there isn't much choice for Japanese input (without using 3rd party repos)

---

### Post by slavik on 2006-01-23
is the UIM listed as a package in something like synaptic or how can I remove it?

---

### Post by Aikinai on 2006-01-23
I was having this same problem (except with regular Azureus) and I can't believe I found this obscure an answer. I guess enough people use Japanese and Azureus though. I've got some input and a question.
I found that I can run azureus as long as I go into a terminal and type "azureus" (can't be "azureus &" or from Applications or anything else).
Also, I know it was awhile ago you guys found this problem. Did you ever find a solution to it or just delete UIM? Thanks a lot.

---

