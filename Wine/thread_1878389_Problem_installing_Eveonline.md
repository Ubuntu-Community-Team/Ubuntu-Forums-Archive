---
title: "Problem installing Eveonline"
date: 2011-11-09
forum: Wine
---

### Post by jockyburns on 2011-11-09
Hi there. I've been trying to download and install eveonline tonight but am struggling. First of all I downloaded and installed Wine and then the eve installation file for windows from CCP (eveonline.com)
Right click the downloaded file then select the option to install using wineinstaller. The Eve installer then opens but after a few minutes comes back with Failed, and a message about python.dll missing. 
Had a look at downloading dll's using wine but python.dll doesn't appear on the list. Tried downloading the offline version of eve (download eve installer and 2 x packs from eveonline.com , but still doesn't appear to work (same problem) 
Anyone out there help me?

Latest version of Wine 1.3 ?? and currently running Ubuntu 11.04 Natty. 

Thanks in advance  JB

---

### Post by ergo-proxy on 2011-11-10
You must install it ussing offline files, check wineeq for details.

---

### Post by jockyburns on 2011-11-10
Have tried installing using offline files but still no joy. I get the message
Error, Module not found,,, Load library (pythondll) failed.

---

### Post by jockyburns on 2011-11-12
Bump. Still unable to install Eve in online or offline mode. Am I missing something that's really simple?

---

### Post by ergo-proxy on 2011-11-12
Did you follow winehq instructions?

---

### Post by jockyburns on 2011-11-12
I followed all instructions on Winehq to no avail. Still getting the message that "Module not found, Load Library (pythondll) failed. 
Ive tried downloading the files again from eveonline.com, thinking they may be corrupted, but still the same. If all else fails I'll have to load Windoze just to play my favourite game. :(:(

---

### Post by ergo-proxy on 2011-11-13
Ok, you did download EVE_Premium_Setup_306979.exe and two payload files, right?

---

### Post by jockyburns on 2011-11-13
Yep that's the one's I downloaded, but when I try to install, the Eve install screen starts then after about 30 seconds I get the error message as above. I have made sure both the .exe file and the  payload files are located within the same folder too, but no joy yet.

---

### Post by ergo-proxy on 2011-11-14
Check here: [https://forums.eveonline.com/default.aspx?g=posts&t=24436&find=unread](https://forums.eveonline.com/default.aspx?g=posts&t=24436&find=unread)

perhaps reinstall all vcrun installations.

---

### Post by Nigel Lyon on 2011-11-14
hey there, 

complete No0b to Linux here 
I too play eve and just the other day (Saturday) decided to have a play round with another O/s so Ubuntu 11.04 got installed along with the wine 1.3 after some reading tho i didn't realise its labled as beta version even down graded to 1.2 as a just in case , so after many installs and deletions and many readings of "how to" i came to the conclusion 11.04 didn't have the capability just yet to run eve (just something that popped into my mind) so today i down graded Ubuntu to 10.04 used wine 1.2 to no avail, I got it to work with a program called wine-doors which is a 7day free trail software then £40+ for continued use (which I be-grudge paying) i did however enjoy the fact that it ran my steam account with portal running , 

so with a downgrade and without wine-doors installed
only problems I have right now running 10.04 are

i cant wrap my head around installing the correct graphics driver as eve is seeing my geforce 105m (laptop) as a 8600 0_o and captains quarters looks pretty ugly but a quick click to hanger spinning and it looks fairly decent, but wine (atleast for me) wont run the nvidia .exe install file, an error comes up after double clicking telling me ""an unknown error has occurred""  and an OK button to close so thats something to work on

on the EULA scroll down page (before user name and password) the text was not present so i had to install the font file to the wine folder 

the function keys do not seem to work including the escape key so forget safely logging out

will keep at it on my end , hope this is of help in some way

---

### Post by jockyburns on 2011-11-14
I have downloaded the vcrun2008 and 2010 files and installed them. Eve has now installed, but when I try to run it , there's a message "Eve.exe has encountered a serious problem and needs to close.

This may be due to some deficiency in Wine, check appdb at wine.org for further help. So I'm going there now to check it out. 
Fingers crossed it may just be running in time to shoot down Santa Claus. :D:D

---

### Post by jockyburns on 2011-11-14
Ahh success at last:guitar: I downloaded the corefonts and vcrun2005 for winetricks, installed them and it now works. Seems to be the corefonts that were missing though. Now to set up another account on Eve before returning to my main account. (just so I can check out if everything is working. Last thing I want is losing an expensive ship to some Sansha blaggers. ):D:D:D

---

### Post by jockyburns on 2011-11-14
My endless thanks to Ergo Proxy for the invaluable help and the links. Cheers.

---

### Post by ergo-proxy on 2011-11-15
Great, enjoy! :)

---

### Post by jockyburns on 2011-11-15
Thanks again Ergo Proxy. Just a couple of issues,,, I had to set graphics options to a lower quality (in game) Seemed rather laggy with graphics  all on high (but had this problem with Windoze too, but not as bad). Sometimes when entering a station, it took a long while to load the station environment and hung a few times, but bearable. ;);)

---

### Post by ergo-proxy on 2011-11-15
Check for the tips/tricks in winehq, decreasing shadows might be helpful too. I had jsut a few glitches in captain's quaters.

---

