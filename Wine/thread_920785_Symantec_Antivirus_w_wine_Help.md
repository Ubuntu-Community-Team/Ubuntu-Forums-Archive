---
title: "Symantec Antivirus w/ wine Help"
date: 2008-09-15
forum: Wine
---

### Post by SGundamZro on 2008-09-15
Hi, recently I switched from Windows XP to ubuntu and I'm trying to install Symantec Antivirus using Wine, however I'm unable to install it and I don't know why.  This is what I got from using terminal:

> sgundamzro@GaoGaiGar:~$ cd desktop
bash: cd: desktop: No such file or directory
sgundamzro@GaoGaiGar:~$ cd Desktop
sgundamzro@GaoGaiGar:~/Desktop$ wine SAV_32bit.exe
fixme:advapi:LookupAccountNameW (null) L"sgundamzro" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"sgundamzro" 0x12c448 0x33f7fc 0x12ff28 0x33f800 0x33f7f4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 19 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 19 ignored L"Upgrade" table values
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err:msi:ITERATE_Actions Execution halted, action L"PrepareInstallCcSettingsTables.03FE01CF_295E_4354_A292_7DC4A810E0DA" returned 1603
sgundamzro@GaoGaiGar:~/Desktop$ 

BTW I need the symantec because I'm returning back to school at Drexel University where we're required to have Symantec Antivirus install in order to use the internet.  

Thanks

---

### Post by fiddler616 on 2008-09-15
First of all, you really don't need an anti-virus program for Ubuntu.
Second of all, if you're paranoid, you need an Ubuntu-specific anti-virus program. Not Norton.
Third of all, Drexel *probably* has different rules for non-Windows users.
Fourth of all, if they don't, it's something to talk to the IT department about.

---

### Post by Thelasko on 2008-09-16
As they allow Mac users, so they should allow Ubuntu.  I also doubt they actually check to see if you have Norton installed.  I think they just [cut off your connection]("http://www.drexel.edu/IRT/support/virusinfo/") if your computer starts behaving like a bot.

---

### Post by fiddler616 on 2008-09-16
> **Thelasko said:**
> As they allow Mac users, so they should allow Ubuntu.  I also doubt they actually check to see if you have Norton installed.  I think they just [cut off your connection]("http://www.drexel.edu/IRT/support/virusinfo/") if your computer starts behaving like a bot.
Yeah, now that I think about it, I find it hard to believe that they'll remotely check for Norton each time you connect to the Internet, and that a lot of that is scare tactics.
If you *do* experience problems (which I sincerely doubt), then, as I said, then explain to the IT people that you're running Linux, and that Norton Anti-Virus is completely and utterly useless for Linux.

---

### Post by SGundamZro on 2008-09-16
Thank you.  Actually I do recall someone was streaming a video off of the veoh website using a linux system before.  Maybe I shouldn't have to worry, but thanks for the advice.

---

### Post by Thelasko on 2008-09-16
Be prepared to have the fastest computer on campus.  [Symantec AV uses a lot of resources.]("http://slashdot.org/comments.pl?sid=965781&cid=25026961")

---

### Post by fiddler616 on 2008-09-16
> **Thelasko said:**
> Be prepared to have the fastest computer on campus.  [Symantec AV uses a lot of resources.]("http://slashdot.org/comments.pl?sid=965781&cid=25026961")
And so does Windows in general.
Ubuntu: Making the term 'new computer' last for years, not months.

---

### Post by Twitch6000 on 2008-09-16
> **fiddler616 said:**
> And so does Windows in general.
Ubuntu: Making the term 'new computer' last for years, not months.

Amen I have had this laptop with 1gb ram 1.6 ghz intel processer and a 945 intel graphics card.
It still runs freaking great on ubuntu or PCLinuxOS :).

Oh btw @OP if you want a anti virus just for laughs or kicks just in case of that .01% of getting a Linux virus or windows virus get clanvm it is a good Linux Anti Virus :).

---

### Post by fiddler616 on 2008-09-16
> **Twitch6000 said:**
> Amen I have had this laptop with 1gb ram 1.6 ghz intel processer and a 945 intel graphics card.
It still runs freaking great on ubuntu or PCLinuxOS :).
Me? 1000 mhz, 512 MB RAM, four years old, runs like a champ.
I can't wait to get back home (I'm away for six months), dig Windows 98/ME computers out of the basement, and pop Xubuntu onto them.

---

### Post by Twitch6000 on 2008-09-16
> **fiddler616 said:**
> Me? 1000 mhz, 512 MB RAM, four years old, runs like a champ.
I can't wait to get back home (I'm away for six months), dig Windows 98/ME computers out of the basement, and pop Xubuntu onto them.
I want my friends old windows 98/2000 computer,but he won't let me have it :(.

I wanna put DSL in it lol.

---

### Post by fiddler616 on 2008-09-16
> **Twitch6000 said:**
> I want my friends old windows 98/2000 computer,but he won't let me have it :(.

I wanna put DSL in it lol.
Also, after reading KMandla's [blog]("http://kmandla.wordpress.com"), I've been inspired to do something like take the 10-year old computer, put a very lightweight distro on it, and turn it into a jukebox. Much easier than CDs, and much nicer use a separate machine than run it off the main computer.
---------
@OP (Original Poster. Now you know, OP (if you didn't already): The things that happen when you don't keep tight control on your thread :) People storm in and start digressing like mad :)

---

