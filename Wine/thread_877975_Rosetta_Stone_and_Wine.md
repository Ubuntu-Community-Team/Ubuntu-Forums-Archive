---
title: "Rosetta Stone and Wine"
date: 2008-08-02
forum: Wine
---

### Post by steem on 2008-08-02
Hello!

I try to run The Rosetta Stone language Programm to learn a little bit Thai. But it won't work. The Chinese Language pack runs without problems, but the Thai language pack doesn't work. It says fellowing errors when I open a lesson: 

Error: Unkown CXT file ths0103.cxt
Error: TXTs font used over LangDB font
Error: Bad parameters in getFontProb
And last:
String expected
(member 1 of castLib 14)
Script Error Continue 
yes/no ?


This is what the Terminal says:

max@max-desktop:~$ wine /media/cdrom0/Application/TheRosettaStone.exe
Warning: could not find DOS drive for current working directory '/home/max', starting in the Windows directory.
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp2DBC4.FOT",L"C:\\windows\\temp\\AAXcbcb.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp6EBC4.FOT",L"C:\\windows\\temp\\AAXcbe2.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp01CC4.FOT",L"C:\\windows\\temp\\AAXcc06.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp83CC4.FOT",L"C:\\windows\\temp\\AAXcc21.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp06CC4.FOT",L"C:\\windows\\temp\\AAXcc5b.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp58CC4.FOT",L"C:\\windows\\temp\\AAXcc7f.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpDACC4.FOT",L"C:\\windows\\temp\\AAXcca4.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp1CCC4.FOT",L"C:\\windows\\temp\\AAXccbd.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpEECC4.FOT",L"C:\\windows\\temp\\AAXcce3.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp20DC4.FOT",L"C:\\windows\\temp\\AAXccff.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpA4DC4.FOT",L"C:\\windows\\temp\\AAXcd39.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp72EC4.FOT",L"C:\\windows\\temp\\AAXce1d.tmp",(null)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
----> Here I selected "no" in the question "Script error continue?"
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:DllCanUnloadNow stub

Does anyone have an idea whats the problem there? Seems that there are some fonts missing.. but I am not shure.

---

### Post by tamoneya on 2008-08-02
looks like some feature that isnt fully implemented.  Are you using the version from the repositories or the version from winehq.  The repo version is always lagging slightly so it is best to get from winehq when you can.

---

### Post by steem on 2008-08-02
Thank you for this very quick reply!
I use the wine version 1.0 wich is availiable in the Ubuntu 8.04 software sources. 
It seems that this verion comes from WineHQ.
What is this repositories version exactly?

---

### Post by tamoneya on 2008-08-02
software sources is the repositories.  While the version you have does ultimately come from winehq it is not the most up to date version.  Follow this guide: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

It will allow you to still uses the software sources/synaptic interface but will use a more up to date version of wine.  Also take a look here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043)

There are several tricks which they talk about on that page that have helped to get wine working with rosetta stone.

---

### Post by atoc on 2008-08-02
FYI Wine in the repos is 1.0
Following the instructions [here]("http://www.winehq.org/site/download-deb") will get you 1.1.2 (called the "unstable" version, but for me has proven otherwise to be stable)

---

### Post by Rainstride on 2008-08-03
i just tryed my copy of rosetta stone with 1.1.2 and it work perfectly. it never worked on 1.1.0 and down. if you use 1.1.2 you should be fine.

---

### Post by finlost on 2008-09-22
> **tamoneya said:**
> Also take a look here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043)

I am still having issues getting Rosetta Stone to run under Wine.  I have read the link quoted above and it references a script to run.  

Newbie question:  How do I execute this script: [Wine Tricks]("http://www.kegel.com/wine/winetricks")?

---

### Post by aoanla on 2008-09-22
> **finlost said:**
> I am still having issues getting Rosetta Stone to run under Wine.  I have read the link quoted above and it references a script to run.  

Newbie question:  How do I execute this script: [Wine Tricks]("http://www.kegel.com/wine/winetricks")?

I'm not sure why you're having problems with this - the post you read which includes that link also tells you how to run it!

To quote from it:

"If you don't have any xml parsers or whatever installed on your system, the installation will end as it starts to copy files from the CD, so if that is the case, you need to download this script:

[www.kegel.com/wine/winetricks](www.kegel.com/wine/winetricks)

and run it with 'sh winetricks msxml4' "

So... download the script.

Then, in a terminal, type:

sh winetricks msxml4

making sure that winetricks is in your home directory.

---

### Post by finlost on 2008-09-26
Easy there chief...as stated, I am a newbie seeking to learn more.

Thanks for the help as that was the piece I was missing to execute the script.

---

### Post by potterzot on 2008-09-30
if you downloaded the winetricks script you will need to do the following to actually get it working:

```
chmod +x winetricks
```

This makes the script executable.  Then from a terminal navigate to the location of hte script and type

```
sh ./winetricks
```

Then follow the directions.  It should work well.

---

### Post by jcb081584 on 2009-05-15
I tried the above tricks and the sh files listed at [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
and nothing works.  I've also tried mounting though the command line but I get errors.  I'm using Wine 1.1.21 and Ubuntu 9.04 but I still can't get anything to mount the languages so that Wine can read them.  I don't have a cd or dvd drive so I can't insert an actual disk.  Any help would be greatly appreciated.  Thanks in advance.

---

### Post by executorvs on 2009-09-25
I don't know if you've solved this, but gmount has a gui in the repos which is easy to use.

---

