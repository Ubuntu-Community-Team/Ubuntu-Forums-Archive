---
title: "New WoW problem"
date: 2006-08-24
forum: Wine
---

### Post by AJLChase on 2006-08-24
I was trying to update my mx500 to get all the buttons working, well while going through the suggested commands I had to restart X..when doing so X was unable to reboot, and I had to use the live cd to get back on and learn what needed to be done to reconfigure X. Well, I got it X reconfigured and am back to my regular GUI. But now when I try to run WoW I get this error wich I never had before.

--

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:B7D1EDA0

The instruction at "0xB7D1EDA0" referenced memory at "0x00000000".
The memory could not be "read".

Any suggestions? Or a link to a thread already designated to this problem? I may have missed it. Thanks in advance.

---

### Post by reverend1313 on 2006-10-23
I am also getting this problem. Installed Ubuntu upgraded to 6.10rc and everything is running fine. I installed automatix used that to grab the nvidia drivers listed in their. Tested with glxgears and got the little gears in motion. Then installed Crossover office beta. I installed the game just fine. Copied over the patch from my zip drive patched just fine. But when I try to run the game it gives me the same error. 

I also reformatted and reinstalled and then copied the WOW folders over from my windows install and removed the WTF and WTB folders it got the same error message. Also I have the game folder sitting in /home/me/games/WOW.


Any suggestions would be great. I am new to Linux and so far completely love Ubuntu just wish I could get this to work. 

Using an Asus Z71v laptop 
1gb ram Intel 2.4 Pent M
Nvidia 6600go

---

### Post by reverend1313 on 2006-10-23
Just wanted to let anyone that has this issue know I solved it. Talked to a friend and they told me to add the 
(SET gxApi "opengl") into the config file in the WTF folder. 

Works fine now with a little messing with the graphics.

---

### Post by DraeLee on 2006-10-25
I had an error#131  what i did to fix it was go to blizzard.com technical support site.  There it told me to run the repair utility in the WoW folder if found and reverted WoW back to an older version.  Then I redownloaded the patch again.  I havnt had an error since.

Hope that helps

---

### Post by Achube on 2008-03-27
The Error 132 is a vague error message that is reported when something went wrong that was unexpected and not previously documented. This error can exist due to the actual code being faulty or system instability. This was the first type of error that was created when WoW was made. The other types of errors in this thread were once Error 132s before they were isolated and separated as to their individual causes.

It is important to separate an Error 132 that happens before recent patches against those that happen after.

As an example please note this particular Error 132 that can occur before WoW is patched:

    Q u o t e:
    ERROR #132 (0x85100084)
    Program: C:\Program Files\World of Warcraft\WoW.exe
    Exception: 0xC0000005 (ACCESS_VIOLATION) at 001B:00604D73

    The instruction at "0x00604D73" referenced memory at "0x00000054".
    The memory could not be "read"."



After recent patches this error will appear as:

    Q u o t e:
    World of Warcraft was unable to start up 3D acceleration



Through research and troubleshooting the error reports that contain this code "0x00000054" means that there are issues using DirectX and/or the video card/drivers.

Please follow the steps listed here: [http://us.blizzard.com/support/article.xml?articleId=21027](http://us.blizzard.com/support/article.xml?articleId=21027) to begin troubleshooting the Error 132.

There is also information regarding this error documented in another sticky located here: [http://forums.worldofwarcraft.com/thread.aspx?fn=wow-tech-support&t=308254&p=1&tmp=1#post308254](http://forums.worldofwarcraft.com/thread.aspx?fn=wow-tech-support&t=308254&p=1&tmp=1#post308254) .

If you are still encountering this error we will need to see the complete error log. The error will have created a text file in the World of Warcraft\Errors folder. Please locate the most recent error file there and copy and paste the contents in a new thread below.

but i do not know how its working in the ubuntu

---

