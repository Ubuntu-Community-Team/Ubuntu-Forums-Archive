---
title: "No text in EVE Online"
date: 2007-11-07
forum: Wine
---

### Post by rudeboyskunk on 2007-11-07
I just downloaded EVE Online and after setting it up and entering the game for the first time, there is absolutely zero text.  Which font file do I need to install?  I have msttcorefonts installed.

---

### Post by rudeboyskunk on 2007-11-07
Really?  Nobody knows?  There aren't buttons or text. . .

---

### Post by mccord on 2007-11-07
are you using the official linux client/wrapper or are you using wine?
for wine, try copying arial.ttf to 'windows/fonts' in your wine drive_c directory

---

### Post by rudeboyskunk on 2007-11-07
I'm using the official linux version.  I copied arial.ttf (all the different arials) to the windows/fonts directory under the EVE directory (which is in .cedega).

---

### Post by rudeboyskunk on 2007-11-13
*bump*

---

### Post by element8 on 2007-11-13
did you try installing msttcorefonts? did you put the .ttf in the .cedega folder or the drive_c folder under that? (i think cedega has it like that, i've only currently got wine and i don't remember when i tried using the official wrapper thing)

or maybe try drive_c/windows/fonts?

---

### Post by rudeboyskunk on 2007-11-14
> **rudeboyskunk said:**
> I just downloaded EVE Online and after setting it up and entering the game for the first time, there is absolutely zero text.  Which font file do I need to install?  I have msttcorefonts installed.

> I'm using the official linux version. I copied arial.ttf (all the different arials) to the windows/fonts directory under the EVE directory (which is in .cedega).

Yes.

---

### Post by daengbo on 2007-12-16
I also have exactly the same problem, but I wonder if it is a result of my graphics card not being supported. The intro movie doesn't play, either. I linked all the MS fonts into the fonts directory, but it didn't help. Oh wel ...

---

### Post by daengbo on 2007-12-18
I solved this problem in Eve by turning off vertex shading in the configuration.

---

### Post by rudeboyskunk on 2008-01-13
I too did this, but it did not solve the problem.  I give up.  Too bad, EVE looked pretty cool (for the record, it does not work for me under WINE either).

---

### Post by prlewis on 2008-01-27
Just to say that I also solved this by turning off vertex shading, but I had to do it in the GUI, making the change in the config file didn't seems to do it.

---

### Post by Vadi on 2008-06-25
Download and install this: [http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)

---

### Post by napalm brain on 2008-06-25
The same thing is happening to me.

The License Agreement has no text, so I can't scroll down in order to advance any further in the game. There's other text, but none in there or the 'About EVE' tab in the options menu. Everything else is there. My card works because everything is fine on the Linux version (aside from a texture problem that isn't there when I start playing).

That download didn't lead me to a resolution though.. unfortunately. 

Any other suggestions?

---

### Post by Vadi on 2008-06-25
It was supposed to fix the font. Look on google for "no text in eve", you need to do something with a file named arial.ttf.

---

### Post by rudeboyskunk on 2008-07-28
Arial is installed and is in just about every folder under .wine that exists.  It's a hopeless cause.  Sorry, but the eve makers won't be getting my cash...

---

### Post by AgentZ86 on 2008-07-28
did you check to see if your video memory meets the game requirements I think min. is 128MB video card ? for this game ?

---

### Post by AgentZ86 on 2008-07-29
I"ve noticed something about my installation ?

I could not really use the Ubuntu client from the site it did not work and no text on the startup /login screen, and then it crashed almost instantly after that page came up and went down again.

Anyhow the windows install went well, however I can only play Eveonly sometimes, I've noticed a difference when compiz-fusion is running with visual effect and when there are no effects 

Here is the thing, when compiz-fusion is running the login screen for EVE looks good with some flashing in the upper right corner of the screen I can see thru my EVE screen and see a portion of the ubuntu panel flashing in and out of site. Not really a big deal as long as I can get into the game.

But I can't always get in sometimes the computer just freezes after I login and then the character screen starts loading, then I click enter game and then it almost starts, then freezes up.

I will work on it some more, however I've noticed that if I turn off all visual effects, that the login screen does not have the ubuntu panel flashing in and out anymore, however I cannot login. 

I try to type but there is no text, and the the cusor does not move.

It only works when compiz or visual effects are turned on, however I then get the freezing problem and flashing portion of the ubuntu panel in the upper right corner.
This would normally be where you would click quit game, so it's something graphical I think.

Any ideas ??
Please help
Thanks

---

### Post by AgentZ86 on 2008-07-29
So I've concluded on something here ?

When I configure wine, and select Graphics tab, and then check mark (Allow Windows Manager To Control The Windows, and Allow The Windows Manager To decorate the Windows,) Then I can login and the cursor works as it does when I enable compiz-fusion so at least I have that solved.

Basically this is regarding my windows install over wine, since I've had no luck at all with the Ubuntu client install from the EVE website.

Anyhow Once step closer, and the flashing of the upper ubuntu panel does not do that anymore, so I've basically turned off compiz-fusion buy installing the fusion button/manager, and using it that way, and then configured wine with those check marks mentioned above, and I get to the screen where the character selection status scroll starts loading.

Sometimes when I first start the computer it works fine, others it just freezes everything and I have to hit the hard boot reset etc. 

I'll work on this some more, but at least I got rid of the flashing part and I can now type in my login name etc.

---

### Post by AgentZ86 on 2008-07-29
I don't know what I did, but now I can't get the login screen to come up, I get the intro screen then just disappears like the ubuntu client of eve ?

I don't understand whats going on at all now, even after complete uninstall of all eve clients and windows via wine installations of eve. I reinstalled and it won't come up at all now ?

Very strange
back to the drawing board

---

### Post by AgentZ86 on 2008-07-30
Well, here is the status

also fyi I'm using 8.04 32bit install

I could not re-install Eve via wine, while the .exe file was inside a desktop folder, however when I moved it to my desktop it installed fine.

It took me back to the point where I start which is I can get to the login page, music and graphics look great.

Once I login it takes me to the character selection page where I can either (enter the game, or terminate my profile etc.) 
If I enter the game the status bar comes up for (Character Selection) goes about 3/4 and freezes the whole computer.

I hear a sort of phaser sound right at the moment that this happens.
I have to restart the computer and cannot get past this point now.

I tried to resort to the ubuntu client version from the eve website, however I've noticed that the Copy Protection portion of the configuration fails, not sure if this well effect things, but just FYI

Anyhow with the Ubuntu client I still get no text on the login screen and then it just disappears so I"m having less progress with the client then with the windows/wine installation.

Anyhow if someone knows of something else I could try ?

Please advise
Thanks

---

### Post by AgentZ86 on 2008-07-30
Ok

So here is where I am with my solutions so far

Turning off Vertex etc. Turning on and off anything with the Ubuntu client did not do anything for me.

I can now play eve
When I get to the character section where I either select my character or select the empty character.
I can create character and go right into the came no freeze or lockups nice and smooth
Of course I do have compiz-fusion turned off, and in wine configuration if have selected the options to allow windows to control windows and also decorations etc.

With this setup my wine installation of EVE works good.

I resorted to this since I could not get the client working.

Anyhow something during the character saved settings seems to be the freezup problem for me.

I'll post back if I can find out more

P.S don't forget to install the ariel fonts into the windows/fonts directory, the wine installation won't work without them,

---

### Post by NiksaVel on 2008-09-25
I used their installer to install on my mint which is essentialy tuned up gutsy...   first I got an error about a missing directory - created it manually and reinstalled and everything works perfectly.

Than I tried to install it on my Acer Aspire One with linpus, which is Fedora 8 based - and I got the same problem - no text at all....   

I guess it may be something I may have installed via wine on this gutsy comp???   I've had all kind of tools installed and such via wine-tools and winetricks but I have no idea what might result in getting text...   if at all this is the thing...

---

### Post by Grayvon on 2009-01-18
Solved this one by installing the arial.ttf found here. Hope that helps. 
[http://sourceforge.net/project/showfiles.php?group_id=34153&package_id=56408]("http://sourceforge.net/project/showfiles.php?group_id=34153&package_id=56408")

---

### Post by williane on 2009-02-16
> **Grayvon said:**
> Solved this one by installing the arial.ttf found here. Hope that helps. 
[http://sourceforge.net/project/showfiles.php?group_id=34153&package_id=56408](http://sourceforge.net/project/showfiles.php?group_id=34153&package_id=56408)

This worked for me too. I was getting the blank agreement screen.

8.1 intrepid
wine 1.1.14

---

### Post by jcmanley87 on 2010-06-05
Ok I understand that you need all of that to get the game going and stuff...So I downloaded the fonts that was suggested. Now where do I put. (I guess the fonts for microsoft under wine) but still no text. 

If someone could explain to me what I need to do so i can enjoy my game and break it down "retard" style for me.

Please forgive me too because I am a first time user.

p.s. everything works good so far till I get to the EULA. which you can probably guess has no text.

---

### Post by penalt on 2010-08-08
Same situation here, I have the arial font file.  But I need to know where to install it to.  Running Ubu 10.04 and Wine 1.1.42

EDIT:  Did some checking and as near as I can tell I already have all the True Type Fonts installed via the Ubuntu Software Center....

EDIT AGAIN:  PROBLEM SOLVED!!!!!!!  Downloaded winetricks and installed it.  After I did that all was well.
To get winetricks, go to Terminal and input:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Once that is done input:

sh winetricks corefonts vcrun6

Which does the install.  After those two steps were done I relaunched the game from Applications > Wine > Programs > Eve and she fired up.

---

### Post by Pietplaat on 2010-11-23
Solution for me was:

copy the ariel file to fonts folder in wine and double click it! 

It will install it and after that it worked.

Good luck!

---

