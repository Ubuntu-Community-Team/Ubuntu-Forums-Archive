---
title: "Warcraft III (via wine) Scrolling/alt-tab/cube WITH Compiz-fusion"
date: 2008-09-01
forum: Wine
---

### Post by Ng Oon-Ee on 2008-09-01
Hey guys,

Spent the whole morning figuring this out, figured I'd just post how I got this working on my setup. Any stuff marked ADDITIONAL EXPLANATIONS (in a quote box) is merely some background, not needed to get things working. Also explained in the 2nd last quote box is workarounds for the cube rotate behaviour turned off by this guide. Finally, the last quote box has some random stuff about creating a desktop shortcut to WC3 if it is not in your .wine directory (for example, if you're running it from a shared drive with a windows partition, as in my case).

Firstly, the problems enumerated:-

1. Warcraft III via wine runs full-screen, alt-tab does not work.
2. Warcraft III via wine runs full-screen, alt-tab works but returning to WC3 you have artifacts and/or a black screen.
3. Warcraft III via wine runs in windowed mode, alt-tab does not work.
4. Warcraft III via wine runs in windowed mode, alt-tab works, but scrolling is difficult/impossible.
5. Warcraft III via wine runs full-screen but scrolling is buggy (this last one has to do with the compiz cube).

The solution which I have found involves both wine's own configuration and Compiz's configuration. In a terminal, run
```
winecfg
```
Go to the Graphics tab, select the options "Allow the window manager to control the windows" and "Emulate a virtual desktop". Make sure the size of the virtual desktop is the same as the size of your screen.

> ADDITIONAL EXPLANATIONS: This allows WC3 to run in such a way that alt-tab works, as well as cube rotation, since your window manager (the one that comes with Compiz) handles it, as it is a window (the full-screen desktop is virtualized by wine). However, the gnome-panel and AWN (if you use it) will still appear as usual, and this interferes greatly with the game.

To ensure true full-screen running, you need the CompizConfig Settings Manager (System->Preferences->Advanced Desktop Settings Effect). Install it from synaptic, or Google to find out more about getting it working. You're looking for the 'Window Rules' settings, under the 'Window Management' category. Click on 'Window Rules', and add this line to the fullscreen line.
```
class=Wine
```

EDIT: Ecna informs me that this line works better. It only maximizes windows with the title Warcraft III. Of course, I only use wine for that, so I use the above, but not everyone would be like that. Thanks Ecna.
```
title=^Warcraft III$ 
```

> ADDITIONAL EXPLANATIONS: Since Compiz's window manager is handling the wine desktop, it sees it as just another window. This rule makes that window appear fullscreen, which is desirable because it hides the panels/docks you have on your regular desktop, only on the workspace WC3 is running in, and only if WC3 currently has focus. For example, if you alt-tab to your Firefox instance, the panels and docks reappear.

Finally, you'll find that WC3 run this way doesn't scroll reliably. To fix that, go to the 'Rotate Cube' settings, under 'Desktop' in the CompizConfig Settings Manager. Under the 'Bindings' tab, expand the 'Rotate cube' options if its not already expanded (via the small triangle) and set the 'Rotate Flip Left' and 'Rotate Flip Right' to 'None' (you do this by clicking on the currently assigned sides to turn them off).

> ADDITIONAL EXPLANATIONS: It seems Compiz reserves a small (probably 1 or 2 pixels) of the screen edges for its flipping behaviours. To compensate for these reserved pixels, the 'actual' screen edge is moved a bit closer in. Thus, any applications which rely on screen edges for some behaviour (for example, scrolling in WC3) would have to use the screen edges defined by Compiz, but the mouse pointer can easily travel right past that edge to the reserved Compiz edge, which would obviously not trigger any scrolling at all.

With all this done, you should have, as promised, a full-screen WC3 which is fully scrollable, useable alt-tab, and useable cube rotation via Ctrl-Alt-Mouse Drag or Ctrl-Alt-Arrow Keys. Read the quote box below for a few additional notes if this is not satisfactory.

> FINAL NOTES: Unfortunately, this disables the edge-flip cube rotate behaviour. In other words, you can't flip the cube using only mouse movements, you can't drag windows between workspaces, and you can't drag objects between workspaces. A small workaround is to set the 'Rotate Flip Left' and 'Rotate Flip Right' to the bottom-left and bottom right corners, respectively. Thus, when wanting to flip the cube, or move windows/objects, simply aim for the bottom corner on whichever side you wish. Not very intuitive, and not ideal, but for me, a small price to pay for being able to play WC3 in wine without worrying about not being able to read IMs through alt-tab.

> DESKTOP SHORTCUT USING WINE OUTSIDE ~/.WINE: This was surprisingly hard to figure out, but if you can run a typical windows executable using
```
wine "executable path/name"
```
launchers created using that line wouldn't launch the same executable. I created my WC3 launcher using the slightly modified
```
wine start /Unix "executable path/name" -opengl
```
The 'start' is crucial, it seems, and /Unix specifies that the path to the executable is a standard Unix path (ie. /home/...). Finally, the -opengl runs WC3 using OpenGL instead of DirectX, always a good idea for performances issues.

Phew, what a long post. Please let me know through replies if there's any mistakes or any better ways of doing what's shown above.

---

### Post by Ecna on 2008-09-02
I realized today that class=Wine is a bit too broad, it makes all wine apps fullscreen if they support it. Instead use this:

> title=^Warcraft III$ 

And only apps named exactly: "Warcraft III" will be fullscreen. 

Thanks for putting this all together in one place.

---

### Post by Ecna on 2008-09-04
This isn't really a technical concern, but my shortcut didn't have an icon, so I grabbed one of these snazzy ones:
[http://customize.org/icons/19636]("http://customize.org/icons/19636")

One of these days I'm gonna stop tweaking my War3 install and actually play it...

---

### Post by shae on 2008-09-05
May I suggest looking into using my patched version of wine.  It is available in my ppa (see link in signature).

---

### Post by llh11456 on 2008-09-06
mmonice provider[AOC Gold](http://www.mmonice.com/) service. My favorite bottled sauce is Maull's, out of St. Louis, and here are some ideas on how to doctor it. Start by simmering a bottle of sauce over low heat. Add 1/4 to 1/3 cup of cider vinegar or rice vinegar.[AOC powerleveling](http://www.mmonice.com/) A lot of people use Pepsi, which gives a sweet, caramel flavor. Add a tablespoon of granulated or fresh garlic. Throw in a little chili powder for an outdoorsy quality. Maybe add a tablespoon of Worcestershire sauce.[Age of Conan Gold](http://www.mmonice.com) A tablespoon of butter or prepared mustard tastes good, too. [Buy AOC Gold](http://www.mmonice.com/)

---

### Post by Valok on 2008-09-15
I'm having a couple problems after following these directions.  I do have the Wine that you made specifically for WC3, but when I open up WC3 a couple of things go wrong.

1. The screen 'grays out' after about 10 seconds.
2. The Wine window is in full screen, but the WC3 part of it is only in the top left corner.

But when I uncheck the 'emulate a virtual desktop' my game will play fullscreen, and will not gray out.  The graying out things only happens with the special version of Wine, and not the regular one.

Any tips on how to fix this?

---

### Post by Ng Oon-Ee on 2008-09-15
W.R.T the second part of that (disclaimer, I do not use the patched version), I believe that I got that sort of behaviour before when the virtual WINE desktop is of a certain resolution but Warcraft III itself is of a different resolution (or, alternatively, is running in windowed mode).

So, either check your in-game resolution through the Video Options, or make sure you're not starting your WC3 in windowed mode.

---

### Post by Valok on 2008-09-15
Thanks for the tip!  Once I have wine, my desktop, and the game all set to the same resolution it works!  Thanks again!

---

### Post by k1ngb0b0 on 2008-09-19
> **Ng Oon-Ee said:**
> Hey guys,

Spent the whole morning figuring this out, figured I'd just post how I got this working on my setup. Any stuff marked ADDITIONAL EXPLANATIONS (in a quote box) is merely some background, not needed to get things working. Also explained in the 2nd last quote box is workarounds for the cube rotate behaviour turned off by this guide. Finally, the last quote box has some random stuff about creating a desktop shortcut to WC3 if it is not in your .wine directory (for example, if you're running it from a shared drive with a windows partition, as in my case).

Firstly, the problems enumerated:-

1. Warcraft III via wine runs full-screen, alt-tab does not work.
2. Warcraft III via wine runs full-screen, alt-tab works but returning to WC3 you have artifacts and/or a black screen.
3. Warcraft III via wine runs in windowed mode, alt-tab does not work.
4. Warcraft III via wine runs in windowed mode, alt-tab works, but scrolling is difficult/impossible.
5. Warcraft III via wine runs full-screen but scrolling is buggy (this last one has to do with the compiz cube).

The solution which I have found involves both wine's own configuration and Compiz's configuration. In a terminal, run
```
winecfg
```
Go to the Graphics tab, select the options "Allow the window manager to control the windows" and "Emulate a virtual desktop". Make sure the size of the virtual desktop is the same as the size of your screen.



To ensure true full-screen running, you need the CompizConfig Settings Manager (System->Preferences->Advanced Desktop Settings Effect). Install it from synaptic, or Google to find out more about getting it working. You're looking for the 'Window Rules' settings, under the 'Window Management' category. Click on 'Window Rules', and add this line to the fullscreen line.
```
class=Wine
```

EDIT: Ecna informs me that this line works better. It only maximizes windows with the title Warcraft III. Of course, I only use wine for that, so I use the above, but not everyone would be like that. Thanks Ecna.
```
title=^Warcraft III$ 
```



Finally, you'll find that WC3 run this way doesn't scroll reliably. To fix that, go to the 'Rotate Cube' settings, under 'Desktop' in the CompizConfig Settings Manager. Under the 'Bindings' tab, expand the 'Rotate cube' options if its not already expanded (via the small triangle) and set the 'Rotate Flip Left' and 'Rotate Flip Right' to 'None' (you do this by clicking on the currently assigned sides to turn them off).



With all this done, you should have, as promised, a full-screen WC3 which is fully scrollable, useable alt-tab, and useable cube rotation via Ctrl-Alt-Mouse Drag or Ctrl-Alt-Arrow Keys. Read the quote box below for a few additional notes if this is not satisfactory.





Phew, what a long post. Please let me know through replies if there's any mistakes or any better ways of doing what's shown above.


This was immensely helpful and fixed all my problems but one.

For some reason the scrolling problem still happens with the bottom of my screen.  It doesn't happen with top, left or right sides but the bottom still has this problem.


Any idea why?

---

### Post by Ng Oon-Ee on 2008-09-19
> **k1ngb0b0 said:**
> This was immensely helpful and fixed all my problems but one.

For some reason the scrolling problem still happens with the bottom of my screen.  It doesn't happen with top, left or right sides but the bottom still has this problem.


Any idea why?

I'd look through all your Compiz effects for something which uses the bottom part of the screen as activation.

If you have the time, keep WC3 open on one workspace of your cube and Advanced Desktop Effect Settings on another, switching back and forth. Try turning off the effects one-by-one (just untick the checkboxes by them) and see if that fixes anything. If you've found the effect that uses the bottom side of the panel, go into that effect's settings and check which specific command is binded (bound?) to that part of the screen.

Off the top of my head, the 'Desktop Wall' has edge flipping by default, as well as 'Rotate Cube'. Some people use 'Expo' with a single edge to activate as well. As a general rule, check all the effects under 'Desktop' first, before checking the rest, its more likely that the problem is there.

Let me know how it turns out =).

---

### Post by bwaskiew on 2008-09-29
I've got everything working well, except for one caveat:

When holding on the alt key (to view the life of units on the screen), I can't right-click anything because it brings up the Gnome context menu (Minimize, Maximize, Resize, etc.).

There is probably a really obvious way to disable that, either by toggling it before I start up War3, or having it switch it off and on automatically depending if Wine is running, but I can't seem to figure out how to do so.

Any ideas? :)

EDIT:

Realized the main Wine page has it right in front of my face:
System > Preferences > Windows

---

### Post by Sanix on 2008-10-02
I've still got the alt tab issue. If I alt + tab, I have graphics problems afterwards. The interesting thing is, when I quit the game (not the program) it displays the colors more or less correctly. I tried all your stuff but it's not working.

---

### Post by Ng Oon-Ee on 2008-10-03
Ah, I'm sorry its not working for you. Maybe a bit more details would help? Which steps have you taken, and what's the difference those steps make (or don't make)?

---

### Post by mtphr on 2008-11-17
hi.

> **Sanix said:**
> I've still got the alt tab issue. If I alt + tab, I have graphics problems afterwards. The interesting thing is, when I quit the game (not the program) it displays the colors more or less correctly. I tried all your stuff but it's not working.

Sanix you're probably having the graphics problem because your Compiz Window Rule setting is as :

title=^Warcraft III$

if you're using "Emulate Desktop" in you WINE settings then this won't work.
So I suggest use the other solution stated in the post.

class=Wine

this will make all your Wine software run fullscreen, but you won't have graphics problems anymore.

cheers.

---

### Post by dubhear on 2008-11-18
alt+tab shotcuts(and many other shortcuts) can be modified or tunred off from system->Preferences->**Keyboard shortcuts**


I run fullscreen war3 just fine, after i found out that i should choose wineconfigures->graphix... just by checking:

"allow window manager to control windows". also should check the 
"directx to stop mouse leaving window" thingy too (otherwise it might lock your keyboard and you will have to to everything with mouse if i remember it right)

I used these settings for most of the games (including warcraft3) and my wine is version 1.00 
Also if movies don't play or chrashes your game: just name the Movies folder to something else, anything will do the trick. you won't see any movies, but atleast the game works. you can play movies later if you want to see them.


there is one other thing worth to mention. some say that you should use windows 98, some say windows2K. windows 95 is too old, for atleast installation.

only problem that remains for me is saving games. now thinking about tweaking or upgrading my wine. it's a shame to unistall it all.


this is my third day trying to get my war3 working under wine. Maybe i can get it to run perfectly sooner than i thought, thanks for help.

---

### Post by elitenoobboy on 2008-12-07
I don't mind running the game in a window. In fact I sorta prefer it because I have a widescreen monitor, and running fullscreen stretches everything. What I'd like to see is wine present an option to allow directx apps to force the mouse from leaving the screen (while still allowing keyboard shortcuts so you can alt-tab out). This would solve alot of other game problems at the same time as well. Maybe they could fix the saving the game crashes warcraft3 glitch at the same time.

---

### Post by Ng Oon-Ee on 2008-12-08
> **elitenoobboy said:**
> I don't mind running the game in a window. In fact I sorta prefer it because I have a widescreen monitor, and running fullscreen stretches everything. What I'd like to see is wine present an option to allow directx apps to force the mouse from leaving the screen (while still allowing keyboard shortcuts so you can alt-tab out). This would solve alot of other game problems at the same time as well. Maybe they could fix the saving the game crashes warcraft3 glitch at the same time.

I run WC3 in a widescreen, stretched graphics, since its cartoon graphics anyhow I don't see much of a degradation in the experience. Your mileage may vary, of course.

About the option, its already there in winecfg, the first option under the graphics tab. The thing is, I prefer running WC3 in Wine under OpenGL for the performance benefits. Not an issue if you have a faster CPU and are ONLY running your game, but I tend to run tons of apps at the same time....

---

### Post by hotweiss on 2009-01-07
Thanks for the tip! You wouldn't know how to make it fully maximize at the bottom, would you:

[[IMG]http://img211.imageshack.us/img211/9795/bottomre1.png[/IMG]](http://imageshack.us)
[[IMG]http://img211.imageshack.us/img211/bottomre1.png/1/w800.png[/IMG]](http://g.imageshack.us/img211/bottomre1.png/1/)

---

### Post by Ng Oon-Ee on 2009-01-07
To me it looks like your virtual desktop (in winecfg) is missing a few pixels. Did you set it to 1280x768 instead of 1280x800?

You also need to do the same in regedit for Warcraft III's resolution, as by default it doesn't support wide-screen. I find that better than using 'full-screen' mode, for some reason or other.

---

### Post by hotweiss on 2009-01-08
> **Ng Oon-Ee said:**
> To me it looks like your virtual desktop (in winecfg) is missing a few pixels. Did you set it to 1280x768 instead of 1280x800?

You also need to do the same in regedit for Warcraft III's resolution, as by default it doesn't support wide-screen. I find that better than using 'full-screen' mode, for some reason or other.

If I enable virtual desktop, I get this:

[[IMG]http://img353.imageshack.us/img353/5080/69553160at8.png[/IMG]](http://imageshack.us)
[[IMG]http://img353.imageshack.us/img353/69553160at8.png/1/w1920.png[/IMG]](http://g.imageshack.us/img353/69553160at8.png/1/)

And yes I have edited the registry for the "widescreen support", but that has changed nothing.

---

### Post by Ng Oon-Ee on 2009-01-08
You need to use the exact resolution you have set, in your registry. The picture you posted up indicates that you've set 1280x800 in what looks like a 1920x1200 virtual desktop.

What's your system resolution?

---

### Post by hotweiss on 2009-01-09
> **Ng Oon-Ee said:**
> You need to use the exact resolution you have set, in your registry. The picture you posted up indicates that you've set 1280x800 in what looks like a 1920x1200 virtual desktop.

What's your system resolution?

I have the problem fixed. I had the correct resolution, but I was still using the -window extension. I also had turn off all of wine desktop integration features...

---

### Post by Ng Oon-Ee on 2009-01-09
Ah, glad you got it fixed. Enjoy your gaming.

---

### Post by slapspants on 2009-01-10
[IMG]http://www.gearfuse.com/wp-content/uploads/andrew/6_may07/chuck._wow.jpg[/IMG]

---

### Post by shaolinmilk on 2009-01-19
Hey, can someone help me with full screening my Frozen Throne?

I tried the class=Wine way and it just did not work. So I manually went into regedit and changed the resolution to 1680x1050. When I did that, I got fullscreen capabilities, but the fonts were smaller and everything seemed stretch. When I play it, the scrolling isn't smooth at all and it seems very choppy. It's much better when the resolution is say 1280x1050, but it's not full screen when it is. Can someone help me?

---

### Post by hotweiss on 2009-01-19
> **shaolinmilk said:**
> Hey, can someone help me with full screening my Frozen Throne?

I tried the class=Wine way and it just did not work. So I manually went into regedit and changed the resolution to 1680x1050. When I did that, I got fullscreen capabilities, but the fonts were smaller and everything seemed stretch. When I play it, the scrolling isn't smooth at all and it seems very choppy. It's much better when the resolution is say 1280x1050, but it's not full screen when it is. Can someone help me?

Make sure your wine config looks like this:

[IMG]http://img176.imageshack.us/img176/1386/winecfgeu8.png[/IMG]

---

### Post by Ng Oon-Ee on 2009-01-19
> **shaolinmilk said:**
> Hey, can someone help me with full screening my Frozen Throne?

I tried the class=Wine way and it just did not work. So I manually went into regedit and changed the resolution to 1680x1050. When I did that, I got fullscreen capabilities, but the fonts were smaller and everything seemed stretch. When I play it, the scrolling isn't smooth at all and it seems very choppy. It's much better when the resolution is say 1280x1050, but it's not full screen when it is. Can someone help me?
You've got to expect some stretching when using WC3 in widescreen mode, because the game itself does not expect a widescreen monitor. In Windows it looks better because of anti-aliasing done, so I'm sure if you google "Wine Nvidia anti-aliasing" or ATI if that's your GC, you'll find some help there. My nvidia-settings contains a setting which forces AA for all apps, but unsure how that works out for Wine.

It seems playable for me, even with a bit messed up fonts. Another idea is to search around for ways to add all the normal Windows fonts to Wine, I've always had the suspicion that most are missing.

---

### Post by shaolinmilk on 2009-01-19
> **Ng Oon-Ee said:**
> You've got to expect some stretching when using WC3 in widescreen mode, because the game itself does not expect a widescreen monitor. In Windows it looks better because of anti-aliasing done, so I'm sure if you google "Wine Nvidia anti-aliasing" or ATI if that's your GC, you'll find some help there. My nvidia-settings contains a setting which forces AA for all apps, but unsure how that works out for Wine.

It seems playable for me, even with a bit messed up fonts. Another idea is to search around for ways to add all the normal Windows fonts to Wine, I've always had the suspicion that most are missing.
When I enable AA, it becomes way too laggy. Is there any other way you can help me?

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> When I enable AA, it becomes way too laggy. Is there any other way you can help me?

1. Go to: Hkey_Current_User --> Software --> Blizzard Enterteinment --> Warcraft III --> Video

2. Edit refreshrate and enter your correct refresh rate, you now should have no more tearing

3. Edit reswidth and resheight to match your actual screen resolution, your graphic's should now be a little sharper

---

### Post by shaolinmilk on 2009-01-20
> **hotweiss said:**
> 1. Go to: Hkey_Current_User --> Software --> Blizzard Enterteinment --> Warcraft III --> Video

2. Edit refreshrate and enter your correct refresh rate, you now should have no more tearing

3. Edit reswidth and resheight to match your actual screen resolution, your graphic's should now be a little sharper
The problem still persist after editing my refresh rate. I already did set my reswidth and resheight to 1680x1050.

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> The problem still persist after editing my refresh rate. I already did set my reswidth and resheight to 1680x1050.

What video card do you have?

---

### Post by shaolinmilk on 2009-01-20
I told you in the other thread. A Geforce 6200 256 mb and it definitely cannot be my video card. Warcraft doesn't require a good graphics card in order for it to be run properly.

---

### Post by Ng Oon-Ee on 2009-01-20
> **shaolinmilk said:**
> I told you in the other thread. A Geforce 6200 256 mb and it definitely cannot be my video card. Warcraft doesn't require a good graphics card in order for it to be run properly.
WC3 may not, but it takes a load off your processor if you have a good card and its being used. Therefore a good graphics card will help, no matter what the game, as long as its using non-simplistic graphics.

The fact that AA slows things down is to be expected, I believe, since it does take up a lot more graphical processing power. Do you have Compiz running? May want to try without, search synaptic for compiz-fusion and use that icon to temporarily run Metacity.

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> I told you in the other thread. A Geforce 6200 256 mb and it definitely cannot be my video card. Warcraft doesn't require a good graphics card in order for it to be run properly.

Warcraft 3 does require an OK video card, especially when you are playing at a resolution of 1680x1050.

---

### Post by shaolinmilk on 2009-01-20
> **Ng Oon-Ee said:**
> WC3 may not, but it takes a load off your processor if you have a good card and its being used. Therefore a good graphics card will help, no matter what the game, as long as its using non-simplistic graphics.

The fact that AA slows things down is to be expected, I believe, since it does take up a lot more graphical processing power. Do you have Compiz running? May want to try without, search synaptic for compiz-fusion and use that icon to temporarily run Metacity.
When I search for compiz-fusion in synaptic package manager, the only ones that are selected is compiz-fusion-plugins-extra and compiz-fusion-plugins-main. Do I deselect those or something?

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> When I search for compiz-fusion in synaptic package manager, the only ones that are selected is compiz-fusion-plugins-extra and compiz-fusion-plugins-main. Do I deselect those or something?

Leave those alone... You can go into Preferences and Appearance and try to play Warcraft 3 with all effects disabled.

---

### Post by shaolinmilk on 2009-01-20
Yeah, it's already set to none. I just don't understand how it can be so choppy like this. Prior to accidentally installing Ubuntu over my Windows, it was perfectly fine. I know Wine isn't suppose to be a simulator, but still... lol

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> Yeah, it's already set to none. I just don't understand how it can be so choppy like this. Prior to accidentally installing Ubuntu over my Windows, it was perfectly fine. I know Wine isn't suppose to be a simulator, but still... lol

What Nvidia driver are you using?

---

### Post by shaolinmilk on 2009-01-20
> **hotweiss said:**
> What Nvidia driver are you using?
I'm using the newest one. 1.80.22

---

### Post by hotweiss on 2009-01-20
> **shaolinmilk said:**
> I'm using the newest one. 1.80.22

Well then I think you might need a better video card to play Warcraft 3 on Linux. You can get an 8800 GT for nothing now...

---

### Post by shaolinmilk on 2009-01-21
I think it has something to do with my refresh rate. It's so choppy.

---

### Post by hotweiss on 2009-01-21
> **shaolinmilk said:**
> I think it has something to do with my refresh rate. It's so choppy.

OK, so let me see if you have did everything:

1. Edited the registry?

2. added -opengl extension

3. Changed sound to OSS?

4. Enabled sound driver emulation?

The only cause of my choppyness was due to me running the game in DirectX mode. Adding the -opengl extenstion made it perfectly smooth.

Do you still get any choppyness when you run Warcraft 3 from terminal:

> wine .wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

PS-is the choppyness still around when you set resolution to 800x600 and set all of the detail to low?

---

### Post by shaolinmilk on 2009-01-21
Yes, I have done all those. I tried running it from terminal and still the same result. I put everything on low settings and still the same result. When I move my mouse, it's not smooth and its very choppy. When I scroll with my keyboard and start moving my mouse, it's even uglier. I'm so sure that it's my fps or refresh rate. Something doesn't seem right.

EDIT:

When I don't set my resolution to 1680x1050 in regedit and try to full screen in 1280x1024 res, vertically its full, but horizontally its not. And it's MUCH smoother playing like that. I want to stretch it the whole way, but when I do stretch it the whole way, it's so choppy.

---

### Post by hotweiss on 2009-01-22
> **shaolinmilk said:**
> Yes, I have done all those. I tried running it from terminal and still the same result. I put everything on low settings and still the same result. When I move my mouse, it's not smooth and its very choppy. When I scroll with my keyboard and start moving my mouse, it's even uglier. I'm so sure that it's my fps or refresh rate. Something doesn't seem right.

EDIT:

When I don't set my resolution to 1680x1050 in regedit and try to full screen in 1280x1024 res, vertically its full, but horizontally its not. And it's MUCH smoother playing like that. I want to stretch it the whole way, but when I do stretch it the whole way, it's so choppy.

I don't know what to tell you at this moment... everything seems fine. Are you using the 64 bit version of Ubuntu by any chance?

Try this running this from terminal:

> wine .wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl -swtnl

---

### Post by shaolinmilk on 2009-01-22
I don't think I'm using the 64 bit. How do I check?

---

### Post by hotweiss on 2009-01-22
> **shaolinmilk said:**
> I don't think I'm using the 64 bit. How do I check?

...then you aren't using the 64 bit version. Did the -swtnl switch help you?

PS-looking at these benchmarks:

[http://www.tomshardware.com/reviews/ready-winter-games,687-27.html](http://www.tomshardware.com/reviews/ready-winter-games,687-27.html)

It doesn't seem like the 6200 is much of a performer when it comes to Warcraft 3... You probably need a little bit more power under Linux.

---

### Post by shaolinmilk on 2009-01-22
No it didn't do much. I just don't understand how when I run it without stretching, it's much MUCH smoother. Maximizing the screen shouldn't make it that bad, should it?

---

### Post by hotweiss on 2009-01-22
> **shaolinmilk said:**
> No it didn't do much. I just don't understand how when I run it without stretching, it's much MUCH smoother. Maximizing the screen shouldn't make it that bad, should it?

I'm out of ideas :(

---

### Post by Ng Oon-Ee on 2009-01-22
> **shaolinmilk said:**
> No it didn't do much. I just don't understand how when I run it without stretching, it's much MUCH smoother. Maximizing the screen shouldn't make it that bad, should it?
Well, there's a lot more load calculating bigger screen sizes, unfortunately. Its technically linear with the number of pixels calculated, so on your big screen obviously that's a much bigger load. What more if interpolation has to be done.

And as hotweiss said, I'm out of ideas. I do know that the overhead for stretched WC3 in Wine is much larger than it is in Windows, somehow (and I'm only using 1280x800).

---

### Post by shaolinmilk on 2009-01-23
Thanks for trying to help though.

umm, when I go to System > Preferences > Screen Resolution, my monitor says unknown. Maybe it's not detecting my monitor correctly? I also noticed another thing. When I watch videos and there's a part where it moves very quickly, it becomes really choppy and it looks like the refresh rate is messed up.

---

### Post by hotweiss on 2009-01-23
> **shaolinmilk said:**
> Thanks for trying to help though.

umm, when I go to System > Preferences > Screen Resolution, my monitor says unknown. Maybe it's not detecting my monitor correctly? I also noticed another thing. When I watch videos and there's a part where it moves very quickly, it becomes really choppy and it looks like the refresh rate is messed up.

That isn't important. What is important is what is stated in the Nvidia settings manager.

---

### Post by shaolinmilk on 2009-01-23
I see.

Is there any other way that I can full screen my WC3 without having to manually edit it in regedit? I just noticed something else. When I set my resolution to 1280x1024, the screen maximizes vertically and not horizontally and the color depth gets way uglier. And when I ult tab, the screen is still like that and I'm only using 2/3 of my screen.

---

### Post by hotweiss on 2009-01-23
> **shaolinmilk said:**
> I see.

Is there any other way that I can full screen my WC3 without having to manually edit it in regedit? I just noticed something else. When I set my resolution to 1280x1024, the screen maximizes vertically and not horizontally and the color depth gets way uglier. And when I ult tab, the screen is still like that and I'm only using 2/3 of my screen.

Enable virtual desktop and set your current screen resolution.

---

### Post by Ng Oon-Ee on 2009-01-23
> **shaolinmilk said:**
> Thanks for trying to help though.

umm, when I go to System > Preferences > Screen Resolution, my monitor says unknown. Maybe it's not detecting my monitor correctly? I also noticed another thing. When I watch videos and there's a part where it moves very quickly, it becomes really choppy and it looks like the refresh rate is messed up.
If there's choppiness even in watching videos, either your graphics card isn't up to snuff or you need newer/older drivers. If you have an older card (I seem to remember you saying something to that effect) you may try using legacy nvidia drivers. Try uninstalling your current restricted drivers and using Envy to find which is recommended for you and install that. If you're on Intrepid, though, there's no GUI, its text-based. Very easy to do, however.

---

### Post by shaolinmilk on 2009-01-24
> **hotweiss said:**
> Enable virtual desktop and set your current screen resolution.
I tried that and it doesn't work. There is no 1680x1050 resolution in Warcraft. I have to set it manually.

> **Ng Oon-Ee said:**
> If there's choppiness even in watching videos, either your graphics card isn't up to snuff or you need newer/older drivers. If you have an older card (I seem to remember you saying something to that effect) you may try using legacy nvidia drivers. Try uninstalling your current restricted drivers and using Envy to find which is recommended for you and install that. If you're on Intrepid, though, there's no GUI, its text-based. Very easy to do, however.
Yeah. They recommended the 1.77 version and I tried it already. Same result unfortunately. :(

---

### Post by elitenoobboy on 2009-03-12
Excellent guide that helped me solve many of my war3 problems. thanks for it.

Instead of just leaving compiz edge flipping off all the time, I set up a script that would switch out profiles when I launch the game so that I can have edge flipping when I'm not playing the game. It goes something like:
```
enb@compy:~/bin$ cat compiznoedgeflip 
sed -i s/current/noedgeflip/g ~/.config/compiz/compizconfig/config
sleep 3s
env WINEPREFIX="/home/enb/.wine" wine "C:\Program Files\Warcraft III\Warcraft III.exe"

```
And then I just have that "noedgeflip" profile set with no flip left or right bindings and a regular one that does have the bindings set. I would add in a "sed -i s/noedgeflip/current/g ~/.config/compiz/compizconfig/config" to the end of that, but when launching wine programs, the prompt returns prematurely and it gets turned right back on, so I just have to have a quick launch icon for that at the top of my screen.

---

### Post by Ng Oon-Ee on 2009-03-13
You could just put a loop which checks every 5-10 seconds whether wineserver is running.

Something like:-

```
if [ pidof wineserver]; then
   sleep 5s
else
   sed -i s/noedgeflip/current/g ~/.config/compiz/compizconfig/config
fi
```

Of course, put this into a while loop or something, maybe having a variable that you set yourself. I also believe there's a way for the bash process to wait for your process to finish, but am not very sure on how to go about that, this is the easiest stop-gap, for me.

---

### Post by florianderouck on 2009-07-15
This has been more then helpfull. Excellent guide and pointers !
Keep up the good work !
Editing in Regidit and following ur tips made everything work fine. 

Thanks !

---

### Post by Constantinff on 2011-06-11
> **k1ngb0b0 said:**
> This was immensely helpful and fixed all my problems but one.

For some reason the scrolling problem still happens with the bottom of my screen.  It doesn't happen with top, left or right sides but the bottom still has this problem.


Any idea why?

> **Ng Oon-Ee said:**
> I'd look through all your Compiz effects for something which uses the bottom part of the screen as activation.

If you have the time, keep WC3 open on one workspace of your cube and Advanced Desktop Effect Settings on another, switching back and forth. Try turning off the effects one-by-one (just untick the checkboxes by them) and see if that fixes anything. If you've found the effect that uses the bottom side of the panel, go into that effect's settings and check which specific command is binded (bound?) to that part of the screen.

Off the top of my head, the 'Desktop Wall' has edge flipping by default, as well as 'Rotate Cube'. Some people use 'Expo' with a single edge to activate as well. As a general rule, check all the effects under 'Desktop' first, before checking the rest, its more likely that the problem is there.

Let me know how it turns out =).

Same trouble here. I see that the threat is quite old but still i have the problems with black window or windows not responding when alt-tab.
The configuration from the first post didnt work for me at all. The only way to get nice alt-tabing is by useing "-window" trigger at the end of the command. So in windowed mode to get it as fullscreen in the wine config i select:
"Allow the window manager to decorate windows"
and
"Allow the window manager to control the windows"
AND DESELECT the "Emulate virtual desktop" option

Also in the 'Window Rules' I set "Fullscreen:" "class=Wine"
to get the Warcraft in fullscreen

So ... like this the configuration works perfect except 
1. At first i had problems with scrolling left and right - fixed as in the first post described
2. Still i have problems with the scrolling down
(actually this is the only problem atm)

I got a black offset like 10px which bugs the bottom scrolling.
I have tested almost every option - nothing.

Also i have World of Warcraft - there is the same black offset on the bottom but no problems there because there is no scrolling. In the WoW video options i have selected to be run in Windowed mode and there is one option "Maximized" which fixes the bottom offset.
Unfortunately no such option in Warcraft III
I hope that someone has a solution.  I searched the whole www for running an application in maximized mode - and noting that works in this case.

EDIT:Also I'm running Ubuntu 10.4 and Wine 1.2.2 (from the Ubuntu Software Center). On what versions this configuration is tested?

---

### Post by elitenoobboy on 2011-06-12
Try a newer version 1.3 wine. The option to allow games to capture the mouse works in my version, making all the hacks in this thread unnecessary. The only problem I have is that the mouse stays bound to the game when alt-tabbing or switching virtual desktops. I have to do the show desktop hotkey to get mouse control back. This may not happen on compiz though.

---

### Post by Constantinff on 2011-06-12
> **elitenoobboy said:**
> Try a newer version 1.3 wine. The option to allow games to capture the mouse works in my version, making all the hacks in this thread unnecessary. The only problem I have is that the mouse stays bound to the game when alt-tabbing or switching virtual desktops. I have to do the show desktop hotkey to get mouse control back. This may not happen on compiz though.
Everything is totally the same with Wine 1.3

---

### Post by elitenoobboy on 2011-06-12
> **Constantinff said:**
> Everything is totally the same with Wine 1.3

If you have the automatically capture the mouse in fullscreen windows option set, and it still doesn't capture it, then you might want to file a bug report, as it is supposed to be working now (and it at least works for me).

---

### Post by Constantinff on 2011-06-15
Not sure if this is the actual bug to report it.
Also still looking for a way to run Warcraft III in maximized window like the option in the video options of WoW

---

