---
title: "Marble drop shows its title opening forever..."
date: 2008-10-12
forum: Wine
---

### Post by Hyper Tails on 2008-10-12
Hi i run ubuntu hardy heron and i bought a game marble drop in a book fair when i was in grade 2 and 7 years old and i thought it was the best marble game ever.

things haven't changed i still love marble drop and i installed it under wine and the setup was sucessful and i started it up and the marble drop opening showed up and it just stays there and i thought when is this going to start and it did behind it (used the compiz fusion cube) so i got that thing out of the way by using the expo plugin and i tryed playing it and it won't do anything and even close out

please help

thank you

---

### Post by Hyper Tails on 2008-10-13
.................................................................

---

### Post by david_kt on 2008-10-13
> **Hyper Tails said:**
> Hi i run ubuntu hardy heron and i bought a game marble drop in a book fair when i was in grade 2 and 7 years old and i thought it was the best marble game ever.

things haven't changed i still love marble drop and i installed it under wine and the setup was sucessful and i started it up and the marble drop opening showed up and it just stays there and i thought when is this going to start and it did behind it (used the compiz fusion cube) so i got that thing out of the way by using the expo plugin and i tryed playing it and it won't do anything and even close out

please help

thank you

Is it DOS game? If yes, try dosbox:
```

sudo apt-get install dosbox
```

And then read below to use it:

[https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)

DK

---

### Post by Hyper Tails on 2008-10-13
it's was meant to be ran on windows 95

---

### Post by david_kt on 2008-10-13
> **Hyper Tails said:**
> it's was meant to be ran on windows 95

Then most likely it is DOS games. Could you give me where I could download it? I will give it a try.

If you want to use wine, at least change the windows version to windows 95.

DK

---

### Post by Hyper Tails on 2008-10-13
I don't know where you can download it but i know a spot that you can see pictures of it

[http://au.gamespot.com/pc/puzzle/marbledrop/index.html](http://au.gamespot.com/pc/puzzle/marbledrop/index.html)

---

### Post by david_kt on 2008-10-13
> **Hyper Tails said:**
> I don't know where you can download it but i know a spot that you can see pictures of it

[http://au.gamespot.com/pc/puzzle/marbledrop/index.html](http://au.gamespot.com/pc/puzzle/marbledrop/index.html)

Unfortunately I could not troubleshoot a software by looking at the picture of the program :)
Than just try to emulate windows 95 using winecfg, but I think the best bet is try to use dosbox instead of wine.

DK

---

### Post by Hyper Tails on 2008-10-14
how do i try that?

under dosbox?

---

### Post by david_kt on 2008-10-14
> **Hyper Tails said:**
> how do i try that?

under dosbox?

1. enable the Universe repositories
2. sudo apt-get install dosbox
3. make a c drive:
```
mkdir ~/dos/c 
```
4. Copy your marble drop program to ~/dos/c 
(you can use nautilus for step 3 and 4) 
5. Open terminal and type dosbox <enter>
6. Mount drive c:
```
mount c /home/your_user_name/dos/c 
```
7. Run your program/installer

DK

---

### Post by david_kt on 2008-10-14
Finally I got the Marble Drop and try to install it.
It will not install on windows xp, require old windows. As such, I need to set to windows 98 to work.

As you said, it shows title opening forever. Changing to emulate a virtual desktop (with desktop size 800 X 600)  could pass the title opening.

After that, it ask for user name, and marble drop only shows the title bar, have to minimize and than double click to restore it. It could shows similar to the screen shoot you give me, but still could not play (or I do not know how to play).

I tried dosbox, it could not be played at all, It is not a dos game.

May be need to apply patch to solve below problem:

fixme:MCIAVI_mciRealize (0002, 00000000, 0x32f16c) : stub
fixme:MCIAVI_mciRealize (0002, 00000000, 0x32f5a4) : stub

DK

---

### Post by david_kt on 2008-10-16
You could try to emulate windows 95, and then download dcom95 from Microsoft website:

[http://www.microsoft.com/downloads/details.aspx?FamilyID=d7a4de78-81a9-4db7-beb6-84ff99342172&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=d7a4de78-81a9-4db7-beb6-84ff99342172&displaylang=en)

install dcom95 and run marble drop again. Hopefully it help.

DK

---

### Post by Hyper Tails on 2008-10-17
I don't know how to runs these un zip things

any other advice?

---

### Post by david_kt on 2008-10-17
> **Hyper Tails said:**
> I don't know how to runs these un zip things

any other advice?

I have not tried to install dcom95 on latest wine, looks like it is not easy. What you could do is install old wine, may be wine 0.9.43, and upon unzipping dcom95 run below command:

```
WINEDLLOVERRIDES="ole32=n" wine c:/windows/tmp/x86/DCom95.exe 
```

Adjust the path and name according to your actual file extraction. But if your wine is latest wine, most likely it would still fail. To install old wine (and multiple wines) on custom directory and how to use it, see my post below:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

Using that installer, you could have many versions of wine to suit your applications. But read carefully so that you know how to use it properly.

Alternatively the easy one, try dcom98. But dcom98 require windows 98 license although you could download freely from internet (something like: I put my money on the street, but please do not steal it :) ).

To install dcom98, set your windows version to windows 98, open terminal and run below command:

```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
sh winetricks dcom98
```

After that, try again to run marble drop and let me know the outcome.

DK

---

### Post by Hyper Tails on 2008-10-18
this is my results

```
liam@liam-desktop:~$ cd /usr/bin
liam@liam-desktop:/usr/bin$ sudo ln -s '$home/wine-X.X.X/bin/wine-X.X.X'
liam@liam-desktop:/usr/bin$ Properties> Open with > Add > wine-x.x.x > click "Add" button.
bash: Open: Permission denied
liam@liam-desktop:/usr/bin$ 

```

---

### Post by david_kt on 2008-10-19
> **Hyper Tails said:**
> this is my results

```
liam@liam-desktop:~$ cd /usr/bin
liam@liam-desktop:/usr/bin$ sudo ln -s '$home/wine-X.X.X/bin/wine-X.X.X'
liam@liam-desktop:/usr/bin$ mjklopiuhgnb
bash: mjklopiuhgnb: command not found
liam@liam-desktop:/usr/bin$ Properties> Open with > Add > wine-x.x.x > click "Add" button.
bash: Open: Permission denied
liam@liam-desktop:/usr/bin$ 

```

First of all, which version of wine have you install? Sure it is not version X.X.X. So, if you install wine-0.9.59, then you should issue command:

```
sudo ln -s '$home/wine-0.9.59/bin/wine-0.9.59
```

And for the Properties> Open with > Add > wine-x.x.x > click "Add" button is not for command line, but gui.

Please let me know what you want to do in more details.

DK

---

### Post by Hyper Tails on 2008-10-19
I got wine 1.1.6 and this is what i got.
```
liam@liam-desktop:~$ sudo ln -s '$home/wine-0.9.59/bin/wine-0.9.59
> 
```



I not sure if i'm doing anything right or something.

---

### Post by david_kt on 2008-10-19
> **Hyper Tails said:**
> I got wine 1.1.6 and this is what i got.
```
liam@liam-desktop:~$ sudo ln -s '$home/wine-0.9.59/bin/wine-0.9.59
> 
```



I not sure if i'm doing anything right or something.

There are 3 mistakes. But before I point out those mistake, please answer below question first:

Did you install wine 1.1.6 using Multiple Wine installer?

DK

---

