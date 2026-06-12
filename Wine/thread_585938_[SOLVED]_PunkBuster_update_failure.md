---
title: "[SOLVED] PunkBuster update failure"
date: 2007-10-21
forum: Wine
---

### Post by drunken_sapo on 2007-10-21
I've just finished installing Gutsy, and downloaded the pbsetup.run executable from PunkBuster's web site. When I try to run it, it just exits. Making an echo $? shows an error code of 127. It is weird, because it is a statically linked binary, and my guess what that shouldn't be a problem in Gutsy.
Can anyone confirm this or give me a hint?
Thanks in advance.
Best Regards,
                    Juan

---

### Post by drunken_sapo on 2007-10-21
I've tried to run it back on a feisty box and worked. If you do a 'file pbsetup.run' in both boxes you get the same:
-----------
pbsetup.run: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
-----------
Is there some sort of compatibility mode or something?

---

### Post by drunken_sapo on 2007-10-22
Well, I still don't know what the problem is or how to solve it. However I find a workaround to avoid it.
If you go to the folder where PB is located, in my case, /usr/local/games/enemy-territory/pb you will find a binary called pbweb.x86.
if you do a 
chmod u+x pbweb.x86
and then 
./pbweb.x86
it will update your game.
in the case of enemy territory, you have to copy pbweb.x86 to ~/.etwolf and run it there.
after that you are done.

---

### Post by drunken_sapo on 2007-10-22
The punkbuster team answered me. They have suggested to run upx -d pbsetup.run and that fixed the executable.
Now it works neatly.
I hope this helps someone else apart from me.
Regards,
            Juan

---

### Post by groovomata on 2007-11-04
Hey Juan, I have the same issue but with Call of Duty and punkbuster and Gutsy. I downloaded the same file from punkbuster and can't install it either. I tried 'upx -d pbsetup.run' however I get a 'command not found' error. Is there anything I'm doing wrong?

---

### Post by drunken_sapo on 2007-11-04
> **groovomata said:**
> Hey Juan, I have the same issue but with Call of Duty and punkbuster and Gutsy. I downloaded the same file from punkbuster and can't install it either. I tried 'upx -d pbsetup.run' however I get a 'command not found' error. Is there anything I'm doing wrong?

Well, when you get an command not found, mean that the command you've just tried to run doesn't exists. As the only command you ran is 'upx' (1), it is possible that you don't have upx installed.
to install it:
```
sudo apt-get install upx-ucl
```
Next time, if you don't have an executable you can do a 
```
apt-file search upx
```
to see in which package upx is located.
Let me know what happened.
Best regards,
                   Juan

notes:
(1) in 'upx -d pbsetup.run' the 'upx' part is the command and '-d pbsetup.run' are the argumetns for the command.

---

### Post by groovomata on 2007-11-08
Ah yes, you've helped to solve my problem! To recap, if you download pbsetup.run from evenbalance.com, you need to install upx-ucl as per the instructions above. Then run 'upx -d pbsetup.run'. Then I did (as per instructions from evenbalance.com):chmod +x pbsetup.run, and then: ./pbsetup.run. Use sudo for all the commands. I finally got the application to run and was able to update punkbuster for both Enemy Territory and Call of Duty. I'm gonna try them both and post back on whether or not I get kicked for not using punkbuster.
Thanks!
Erik.

---

### Post by 1/0 on 2007-12-18
> **groovomata said:**
> Ah yes, you've helped to solve my problem! To recap, if you download pbsetup.run from evenbalance.com, you need to install upx-ucl as per the instructions above. Then run 'upx -d pbsetup.run'. Then I did (as per instructions from evenbalance.com):chmod +x pbsetup.run, and then: ./pbsetup.run. Use sudo for all the commands. I finally got the application to run and was able to update punkbuster for both Enemy Territory and Call of Duty. I'm gonna try them both and post back on whether or not I get kicked for not using punkbuster.
Thanks!
Erik.

That helped me!!

---

### Post by drunken_sapo on 2007-12-18
> **1/0 said:**
> That helped me!!

nice to hear that!

---

### Post by kuscsik on 2007-12-24
> **drunken_sapo said:**
> The punkbuster team answered me. They have suggested to run upx -d pbsetup.run and that fixed the executable.
Now it works neatly.
I hope this helps someone else apart from me.
Regards,
            Juan
excelent, thanx

---

### Post by H3adshot on 2008-12-27
Aloha, 

I am having problems with punkbuster kicking me from cod4 servers.  please help.  Where or how do i install the upx -d pbsetup.run

---

### Post by 1/0 on 2008-12-28
> **H3adshot said:**
> Aloha, 

I am having problems with punkbuster kicking me from cod4 servers.  please help.  Where or how do i install the upx -d pbsetup.run

Download pbsetup.run from [Evenbalance's homepage](http://www.evenbalance.com/index.php?page=pbsetup.php). Then do the following:

```
cd to/dir/with/pbsetup.run
chmod +x pbsetup.run
./pbsetup.run

```

That opens the GUI, which is pretty self explaining.

---

### Post by fermulator on 2009-02-15
And what if there's no GUI?

(i.e. Console Only Headless Box.  Trying to run CoD4 dedicated)

---

### Post by hikaricore on 2009-02-15
> **fermulator said:**
> And what if there's no GUI?

(i.e. Console Only Headless Box.  Trying to run CoD4 dedicated)

I don't see any instructions here whatsoever that would require a GUI.

You may want to be more specific with your question.

---

### Post by gwoodard on 2009-05-23
Okay, I did the second step...what did I do wrong?

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
baiter@GMW-Laptop:~$ upx -d pbsetup.run
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
upx: pbsetup.run: FileNotFoundException: pbsetup.run

Unpacked 0 files.

---

