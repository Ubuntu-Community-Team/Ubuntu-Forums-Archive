---
title: "thief 2 and hyper threading commands not working properly"
date: 2008-10-05
forum: Wine
---

### Post by Griffin Bain on 2008-10-05
ok guys i need help, I have read the posted stuff on the taskset and schedtool programs in order that I may run thief 2 in wine with the multi threading turned off. I have followed what the forums and help files have said and I still cannot get the program to even launch. 

this is what happened when I tried the taskset way:

nate@nate-desktop:~$ taskset -c 1 wine thief2.exe
wine: could not load L"C:\\windows\\system32\\thief2.exe": Module not found
nate@nate-desktop:~$ sudo taskset -c 1 wine thief2.exe
[sudo] password for nate: 
wine: /home/nate/.wine is not owned by you

and this is what happens when I try the schedtool way:

nate@nate-desktop:~$ sudo schedtool -a 0x2 -e wine thief2.exe
wine: /home/nate/.wine is not owned by you

I don't know what to do, friends, i remeber seeing something else about not being able to run wine as a sudo or a root but I know no other commands to get around the wine not being owned by me stuff.

thank you for any help

---

### Post by Griffin Bain on 2008-10-05
by the way I am using the latest development version 1.1.5 I believe

---

### Post by Hobo Joe on 2008-10-06
Try this instead:

```

taskset -c 0 wine thief.exe

```

---

### Post by asdfoo on 2008-10-06
> **Griffin Bain said:**
> ok guys i need help, I have read the posted stuff on the taskset and schedtool programs in order that I may run thief 2 in wine with the multi threading turned off. I have followed what the forums and help files have said and I still cannot get the program to even launch. 

this is what happened when I tried the taskset way:

nate@nate-desktop:~$ taskset -c 1 wine thief2.exe
wine: could not load L"C:\\windows\\system32\\thief2.exe": Module not found
nate@nate-desktop:~$ sudo taskset -c 1 wine thief2.exe
[sudo] password for nate: 
wine: /home/nate/.wine is not owned by you

and this is what happens when I try the schedtool way:

nate@nate-desktop:~$ sudo schedtool -a 0x2 -e wine thief2.exe
wine: /home/nate/.wine is not owned by you

I don't know what to do, friends, i remeber seeing something else about not being able to run wine as a sudo or a root but I know no other commands to get around the wine not being owned by me stuff.

thank you for any help

do not use sudo.

read the error message: wine: could not load L"C:\\windows\\system32\\thief2.exe": Module not found

You need to change your current directory to the place that thief is installed, something similar to: cd ~/.wine/drive_c/Program\ Files/Thief2

---

### Post by Griffin Bain on 2008-10-06
thanks hobo joe and asdfoo, it appears to work great, now the thieving can commence once again.

i did it using the taskset command once the terminal was set to look in the correct directery.

it is still taking some time to readjust and learn the proper terminal commands, i feel like i'm better off than what i was in the dos days but my terminal skills have a lot to be desired but i digress, every problem that has come up so far somebody has been able to help me with and I have been using ubuntu with NO windows now since April . . . its been a trip let me tell you . . .

---

### Post by Griffin Bain on 2008-10-06
i would issue a thank you command but I do not know how to perform that function yet

---

### Post by asdfoo on 2008-10-06
> **Griffin Bain said:**
> i would issue a thank you command but I do not know how to perform that function yet

good to hear it's working :)  The thank you button is to the right of the Quote and Reply buttons

---

### Post by Hobo Joe on 2008-10-07
I'm just jealous you got it to run. :(


Runs like 1FPS whenver I try to play it, I still can't figure out what's up with it.

---

### Post by Griffin Bain on 2008-10-08
there you both should have gotten thank yous.

thanks again

---

