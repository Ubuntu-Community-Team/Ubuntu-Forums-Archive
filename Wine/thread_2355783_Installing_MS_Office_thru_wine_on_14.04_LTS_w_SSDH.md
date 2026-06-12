---
title: "Installing MS Office thru wine on 14.04 LTS w SSD/HD drives"
date: 2017-03-16
forum: Wine
---

### Post by mhs999 on 2017-03-16
Hi, I am currently running 14.04 LTS installed on a 16GB SSD and the laptop also has a 750GB HD.  I used wine from the ubuntu sw center.  I initially installed excel and word but it put it all on the SSD so i could not install ppt. [note, i need these apps for client compatibility].  i tried to uninstall the existing installations by simply deleting the files.  i then also uninstalled wine and re-installed it.  i attempted to direct the .wine folder to the HD using some other set of directions.  now, when i try to install MSO again, the installer disk rejects it due to either not being able to see the space or not having enough space (i'm not sure which it is).  Anyways, does anyone know a Bulletproof Version of instructions to do what i'm trying to do?  specifically, run ubuntu from the SSD and install the program files for MS Office 2010 on the HD.

Many Thanks,
Mark

---

### Post by howefield on 2017-03-16
Welcome to the forums.

Your thread has been moved to the "*Wine*" forum for a better fit.

---

### Post by mastablasta on 2017-03-17
first it depends which office version you are installing. also powerpoint (in my experience) has more issues than Excel and Word, but is still kin dof working. if oyu need it only to read or porcess the files it should be OK. alternatively explore latest Libre office (via PPA) or WPS office (AKA Kingsolft office). what i tested regarding ppt, libre office had best, but still not 100% compatibility.

second, how did you direct .wine folder to HDD? normally it is in home but you can have it elsewhere. here is one solution: [http://askubuntu.com/questions/576888/how-to-change-the-directory-wine-of-wine-to-a-different-directory](http://askubuntu.com/questions/576888/how-to-change-the-directory-wine-of-wine-to-a-different-directory)

third - the install. you can use wine to do the install for that but you might also want to explore frontned such as Playonloinux or if you are prepared to invest a bit of money into it - Crossover (i think they have a trial version).

---

### Post by mhs999 on 2017-03-17
Thanks. I was having a lot of problems with libre office screwing up the formatting in existing ppt files.  it has to be MS Office because I'm always shipping files back and forth to a client who uses office proper.

1. MS office 2010 Professional
2. I had a friend walk me thru it and then I tried another set of directions but I will try your link too [just looked at your link, those were the ones i tried, i must have done it wrong.  i am a noob to ubuntu]
3. I will trial crossover

Thanks again for the tips!

---

