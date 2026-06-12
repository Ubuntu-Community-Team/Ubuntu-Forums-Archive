---
title: "Need help with installing &quot;libfreetype&quot; dependencies for LoL"
date: 2013-07-12
forum: Wine
---

### Post by samiscool30 on 2013-07-12
Not sure where to post this.. 

I followed this guide to installing League of Legends on wine:

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=19141](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=19141)

And when running         "sh Install-LoL-on-Wine.sh
I get: "libfreetype" not installed.
Some dependencies are not met. Please install them and try again

So I went to Synaptic and download the package as I did with the other dependencies which were no met and download the "libfreetype6" package.  When running         "sh Install-LoL-on-Wine.sh"again I still get the error.  So I decided to do "sudo apt-get install libfreetype and it said that the they were unable to locate the package.

Can anyone help me with this please?

---

### Post by DeathByDenim on 2013-07-12
Ah, it's because the script is looking for that library in a rather dumb way. It expects the library to be in /usr/lib, but that's not where Ubuntu put is. Open the Install-LoL-on-Wine.sh script in your favourite text editor and change line 110 from
```
if ! ls /usr/lib/ | grep libfreetype > $? 2>&1 ; then
```
to
```
if ! ls /usr/lib/x86_64-linux-gnu/ | grep libfreetype > $? 2>&1 ; then
```

This is assuming you have a 64-bit install of Ubuntu by the way. You can use the following command to find where your libfreetype is installed:
```
dpkg -L libfreetype6
```
The last line of that should show you where libfreetype.so.6 or something like that is installed.

Alternatively, you can just comment out lines 110 to 113 entirely. That is, change those lines in the Install-LoL-on-Wine.sh script to:
```
#if ! ls /usr/lib/ | grep libfreetype > $? 2>&1 ; then 
#  echo "\"libfreetype\" not installed.";
#  DEP_FAIL_FLAG=1;  #set the unmet dependency flag to "missing dep(s) found"
#fi
```

---

### Post by samiscool30 on 2013-07-12
Thank you so much!  I used the alternative and it worked :)

---

### Post by samiscool30 on 2013-07-12
So I got another problem.. When running the "Play_LeagueOfLegends.sh" they give me 4 options: display, cancel, run, run in terminal.  Did "run" didn't do anything. Then did run in terminal, terminal shows up and the quickly disappears.  Don't know what "display" does but clicked it anyways and still got nothing.

---

### Post by DeathByDenim on 2013-07-12
Oh, hmm, it does say on the top of the guide:
> ">">">NOTE: This script works for almost any distro, but some people reported problems with Ubuntu on 64bit machines. If you use it, scroll a little down and follow the Ubuntu-specific guide :)
Do you have a 64-bit install? If so, you should probably follow the Ubuntu-specific guide they mention. It seems pretty complicated to me though.

Anyway, you return to your question: Can you start a terminal yourself and start the Play_LeagueOfLegends.sh script from there? So:
```
cd ~/Desktop
./Play_LeagueOfLegends.sh
```

That way the terminal shouldn't close up on you if you press Run and you can see the error messages hopefully.

---

