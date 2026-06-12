---
title: "Ubuntu 14.04 Office 2010 on wine Greek without accents"
date: 2014-04-19
forum: Wine
---

### Post by luca11 on 2014-04-19
Hi Everyone, 
this is my first post, so apologies for any mistake I might make.

I am running Office 2010 on Wine (1.6.2) with Ubuntu 14.04. Everything works flawlessly, but when I switch to Greek Polytonic layout (on ubuntu using Ibus) and try to type on Office 2010 - Wine, I cannot get the accents.
To clarify, if I want to type &#7940; I can only type &#945;.
The dead keys just don't work. 

It is more or less the problem already experienced by this person:

[http://ubuntuforums.org/showthread.php?t=1677890](http://ubuntuforums.org/showthread.php?t=1677890)

but his post never received a reply.

So far, I have noticed that:

1. it is not a problem of fonts: pasting Greek text from, say, libreoffice to wine/office works well, and accents are displayed.

2. It works perfectly well in Xubuntu (for the life of me this is driving me crazy)

Please, could anyone help?

L.

---

### Post by yunxao on 2014-06-26
Hi

I have the same problem but with spanish layaout. I have insalled the office using a Play On linux script and with Crossover 12.5.1 and 13.X.X. I have asked in Crossover offical forum and they have said me that it is a ubuntu 14.04 (or wine) problem and they are solving in this moment. 

The post in codeweavers page (Crossover): [http://www.codeweavers.com/support/forums/general/?t=26;msg=163070](http://www.codeweavers.com/support/forums/general/?t=26;msg=163070)

---

### Post by engtomas on 2014-07-07
> **yunxao said:**
> Hi

I have the same problem but with spanish layaout. I have insalled the office using a Play On linux script and with Crossover 12.5.1 and 13.X.X. I have asked in Crossover offical forum and they have said me that it is a ubuntu 14.04 (or wine) problem and they are solving in this moment. 

The post in codeweavers page (Crossover): [http://www.codeweavers.com/support/forums/general/?t=26;msg=163070](http://www.codeweavers.com/support/forums/general/?t=26;msg=163070)



[B]Hello, 
 
Disable IBUS on system configuration.  Set to default or none input  method from System Settings >> Language Support >> Default  input method. 
 
Restart the computer. All done.

Best regards,[/B]

---

### Post by brunojcm on 2015-04-23
Disable IBus on system config may affect other applications, I had a bad experience doing this.

I changed all the launcher files to disable IBus individually, like this one:

     .cxoffice/Microsoft\ Office\ 2010/desktopdata/cxmenu/StartMenu.C\^5E3A_users_crossover_Start\^2BMenu/Programs/Microsoft+Office/Microsoft+Word+2010.lnk

Just include a line like the below, right before the "exec" command:

      export XMODIFIERS=""

---

### Post by andrei90 on 2015-05-17
If your *dual-booting* Windows just go in your **C:\Windows\Fonts **dir and copy/paste them in **~/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/Fonts/**

I've had a similar issue but with Romanian diacritics, wrote an [article on how to fix it]("https://ubuntulinuxx.wordpress.com/2015/05/17/fix-romanian-fonts-diacriticediacritics-on-office-2010-xubuntu-14-04-2-lts"), try it and see if it works.

You may need to get the Greek Updated letters package from Windows, then Update Windows Fonts and now copy/paste the ***.ttf** & ***.TTF** fonts to your Ubuntu Office2010 Fonts installation.

Be sure to **backup your fonts** before doing this.

Regards,
*Daniel*

---

### Post by luca11 on 2015-08-17
First off, let me thank all of you for your time and replies, and please accept my apologies for not replying any earlier. Indeed, I managed to solve the problem by installing the fonts I had on a windows partition using font-manager, and then changing the input method from Ibus no none on the language support page. All was fine until I switched to Ubuntu-Gnome (which I very much prefer to Ubuntu-Unity). Now I have the same problem, and the past steps no longer seem to work! 
I have noticed that gnome 3.14 does not come with the Language Support page (only Regional Language) so I installed it myself (gnome-language-selector if I am not mistaken) but it still does not work. I have noticed that if I install Ubuntu and then gnome-shell it works, but the solution is not optimal (the shell by itself seems to cause some random crashes).
Does anyone have any idea?

Thank you very much, and again sorry for vaishing into thin air (simply lost touch of the email connected to Ubuntu Forum)

Cheers!

---

### Post by luca11 on 2015-08-17
Well, I am happy to say that I have solved the issue, thanks to a bit of granu salis and to all the answers I have received above. 
The problem with Gnome is that the input method is bound to Ibus (that is why there is no language support, I assume), and even trying to change it via "input method" GUI did not really change anything.
So I opted for the hard way: I opened up Synaptic and completely removed the Ibus package (I wasn't going to use it anyway). Then I used the system-settings to set the input method to 'none', rebooted et voila the accents were where they should have been.

In short:

1. install font manager (sudo apt-get install font-manager)
2. use font manager to install the windows fonts (this step requires fonts from a windows partition)
3. install & open synaptic (sudo apt-get install synaptic)
4. find the Ibus package, right click and "remove completely". Apply and see Ibus being flushed out
5. Open "input method"
6. click 'Ok' then 'Yes' and select 'none' from the list
7. Reboot
Use Office!

PS
Sorry for the long and verbose instructions. I am sure quite many would not need them but I tried to place myself from the perspective of a complete IT illiterate (such as myself).

---

