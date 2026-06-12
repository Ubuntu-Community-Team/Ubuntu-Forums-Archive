---
title: "Installing Mathematica in 64bit Feisty Fawn"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by kmir on 2007-08-20
Hello Everyone!

I am trying to install Mathematica 6.0 in a 64bit Feisty Fawn. I have read several threads and websites that cover Mathematica installation, e.g. 

[http://help.ubuntu.com/community/Mathematica]("http://help.ubuntu.com/community/Mathematica")

or here:

[http://ubuntuforums.org/showthread.php?t=348002&highlight=mathematica]("http://ubuntuforums.org/showthread.php?t=348002&highlight=mathematica")
[http://documents.wolfram.com/mathematica/GettingStarted/SettingUp/InstallingMathematica.html]("http://documents.wolfram.com/mathematica/GettingStarted/SettingUp/InstallingMathematica.html")

Each time I try to install it another way (logged in as root, in another directory, etc.), it starts installing, but when it is supposed to create the scripts, I the I get the following error message:

"Now Installing...
[******************************************************************]

Type the directory path in which the Mathematica script(s) will be created, or press ENTER to select /usr/local/bin:
>


Error: The installer was unable to check for a valid password file. Your Mathematica installation may be incomplete or corrupted."



What is happening? What do I need to do? I am a little new to all this, please help and give me an idea where I need to look! 

Thanks!

---

### Post by kmir on 2007-08-20
Ok, so if anyone will ever be interested: I just talked to a very helpful Mathematica Tech Support person. I am just going to post what happened in case this information might be helpful for anyone else later.

The first thing he advised me to do was to find a file called "MathPass" in the 
/usr/local/Wolfram/Mathematica/6.0.1/Configurations/Licensing or the 
/usr/share/Mathematica/Licensing directories and delete it in case it was there. It was not there and then he made me install c++ packages (libstdc++), versions 5 & 6. After that, it worked.

---

### Post by paulita on 2007-09-18
Hi, I'm trying to run Mathematica in Kubuntu Feisty. The installation did ok, but when i run Mathematica everything freezes. I can run the math kernel in the konsole with no problem but i can't run it with the windows.
Does anyone know how to fix this? :confused:
Please, i need some help...

---

### Post by USBuntu on 2007-10-29
@kmir
I am new to Ubuntu and Linux in general.Thank you for sharing your experience and explanations. I used them in my XUbuntu install with 7.04 version.
In 7.10 version libstdc++6 has been already installed but it was not enough. I used GUI version of Applications->System->Synaptic Package Manager and installed libstdc++5 which reqested for gcc... to be installed as well. After this everything worked as you described.

What I do not like about my install is that *.nb files are not regestered with mathematica by default and cannot be opened automatically. Mathematica also did not placed itself in some Location which can be accessed through GUI. Let say Applications->Mathematica

---

### Post by USBuntu on 2007-10-29
I had additional setup with Ubuntu 7.10 amd64 and I checked what happened if I installed gcc-3.3-base which was required for libstdc++5 and it was not enough. libstdc++5 is must

---

