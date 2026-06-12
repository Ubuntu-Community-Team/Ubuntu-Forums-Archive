---
title: "Maxing out FPS"
date: 2007-12-18
forum: Wine
---

### Post by AJLChase on 2007-12-18
Hey all, I've noticed while sifting through all the posts that there are a lot of ones asking how to just install the game to even play it. Luckily, I am past that point and can actually play the games that I do like...those being CS:S and WoW. My question is this, is there a good link around that explains different things to do to possibly get better fps? It seems that when I dumb down the graphics on both games it does nothing to raise fps it just simply doesn't look as nice. 

In windows I could easily get up to 170+ fps on both games in certain areas for both games....but in Linux I seem to have taken a 30% or greater hit in FPS. I can't even go into major cities with out maxing at 17 FPS in WoW.

Any advice or links would be appreciated. Thx!

---

### Post by Beren Camlost on 2007-12-18
This may be a long shot by I found this on the Ryzom forums:

>  			 				Open a terminal window, (konsole/terminal/x terminal etc..) and type regedit. This will start the wine server     
     and the wine equivalent of the windows registry editor will be displayed. If your familiar with using the registry     
     editor under windows then this is pretty much the same.
      Find HKEY_CURRENT_USER\Software\Wine\     
    
     Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder     
    
     Click right on the wine folder and select [NEW] then [KEY]     
    
     Replace the text "New Key #1" with OpenGL     
    
     Click right in the right hand pane and select [NEW] then [String Value]     
    
     Replace "New Value #1" with "DisabledExtensions"     
     (Notice it's case sensitive)     
    
     Then double click anywhere on the line, a dialog box will open.     
     In the value field type "GL_ARB_vertex_buffer_object" (without the quotes).

No guarantees it will work, but worth a shot.

Source: [http://forums.ryzom.com/forum/showthread.php?t=30655&page=5](http://forums.ryzom.com/forum/showthread.php?t=30655&page=5) , post #46

---

### Post by AJLChase on 2007-12-18
Hey thx, but yes this was a post I found earlier when installing wow and have already done this command change. Hopefully there are so more ideas out there as to max fps on WoW

---

### Post by Ferrat on 2007-12-18
I think the problem is something that will be ironed out in time, the linux grafic drivers ain't as good as the once for windows, ATi drivers are really lacking and nVIDIA had a revert that lowered framerates on newer cards from what I've heard but a fix for that should come in the next release (hear say). 

Also for when running wine their "version" of directx (d3d to OpenGL) is still under construction, for ex. the GL_ARB_vertex_buffer_object trick is done because the wine development haven't got that working as good as it should, this function that is a openGL function that you disabled is really a preformance enhancing function that helps with the memory mapping of highend grafic memory.

So as you see there are some small problems, any given game running under wine for ex. will probably take a small preformance hit. 

But as linux itself if more efficient in many cases compaired to windows some of that will be canceled out, most people playing WoW via wine will take a 5-50% preformance drop, older systems that for ex. run AGP instead of PCI-E x16 will suffer the most as the gain of linux being more efficient probably is less apparent since ports ect. slow it down.

Some people (and AFAIK only people on real highend system) have reported that they acctually get better preformance under wine in ex. WoW than they do under windows, most likely cause the system itself is so good that the diffirence that "GL_ARB_vertex_buffer_object" and other stuff that is made to boost preformance is to small to make up for the gain the OS gives over all. 

I my self take about a 25-30% loss compaired to my brothers system that is more or less identical when playing WoW and that's when running ATi and on a old AGP system. 

It can also be your wine acctually, how you installed it and what packeges that are liked to it, the way that most often gives the best preformance is installing all the lib ect. that wine can use (more or less) and compiling wine directly under your system, that way wine will be as attuned to your system as possible. 

Added a script I've put together that installs needed libs ect and downloads the wine source as well as makes a .deb for you that is easy to install, its very easy to use, just run it in terminal =)

---

