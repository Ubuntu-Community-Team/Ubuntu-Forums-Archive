---
title: "associated programs."
date: 2015-03-02
forum: Wine
---

### Post by dead-line on 2015-03-02
hello forums.

im new to wine, i have latest ubuntu and wine version wine-1.6.2 .
everything works fine. i even tried an windows application called pdftoMusic and the setup/run works very fine under wine.

the issue here is  1.
i have a windows CD and when i run the setup seems it works fine but during setup process it complains that
there is no "windows media player" and there is no "pdf" installed.

its educational CD so it requires pdf and windows media player. after the setup finishes seems the cd works but at some points
i get black screen because it cannot play the tutorial videos it has or display the pdf files that cd has under wine.

the question is (and sorry if its a newbie question)
what to do now?
do i need to install pdf under wine? what about WMP ? and then how to tell wine to open the pdf/WMP and associate the files to CD.

kindly a detailed answer as im so new to wine and ubuntu, but expert in BSD.

issue 2.
the installed and working windows programs under wine doesnot show in wine programs directory.
Yes. its in programs folder, and i have to manualy go programs folder and run the installed app i need.
is this normal ?

thank you very much
-Marwan

---

### Post by Fincer on 2015-03-02
**Issue 1:**

Have you tried

```
winetricks wmp10
``` (installs Windows Media Player 10 on Wine)

or alternatively

```
winetricks wmp9
``` (installs Windows Media Player 9 on Wine)

?

If you don't have [winetricks](http://wiki.winehq.org/winetricks), run
```
wget http://winetricks.org/winetricks && \
sudo mv winetricks /usr/bin/ && \
sudo chmod +x /usr/bin/winetricks
``` To PDF issue, you *may* need to install Windows version of Adobe reader (I don't know the details of the requirements your program has)

Check [Wine Application Database - Adobe Acrobat Reader 11.X]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=27093")

The database claims it's installable but I've seen several discussions around where people deny this claim and say they can't install Reader XI. If that's the case, you may have only two options left:

[LIST]
[*]Install older Reader version 
[*]Read this: [Winetricks - Install Adobe Acrobat XI with Wine - Ask Ubuntu]("http://askubuntu.com/questions/560560/install-adobe-acrobat-xi-with-wine/586407#586407") 
[/LIST]
  **Issue 2:**

[LIST]
[*]Have you checked the contents of *.local/share/applications/wine* folder? This hidden folder path locates at your home directory. If Wine application shortcuts exist, that's the place where they should be. 
[*]Have you checked you've set Wine menu visible in your application launcher? 
[/LIST]
  Personally, I don't use Unity and I'm not experienced with the Unity desktop. I apologize, but I can't help you any further with this issue. You may try some googling or maybe someone who knows better tells you a direct solution.

Regards,
Fincer

---

