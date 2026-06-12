---
title: "Play full screen with emulate virtual desktop"
date: 2007-12-31
forum: Wine
---

### Post by Faud on 2007-12-31
This post is a how to on playing a game in WINE such as World of Warcraft or Everquest 2 with emulate virtual desktop checked off in full screen.

[COLOR="Red"]*NOTE* A link to your terminal on  your desktop required[/COLOR]

Download the "nothing" metacity theme from gnome-look.org
[http://www.gnome-look.org/content/show.php/Nothing?content=32164](http://www.gnome-look.org/content/show.php/Nothing?content=32164)
If you haven't installed a theme like this before you just go to system-->preferences-->appearance and then click install. Then go to a theme you like and hit the customize button. Go to window and click "nothing" then save as a different theme name.

In winecfg you want to have "emulate virtual desktop" enabled and set the virtual desktop resolution to the same as your non-virtual desktop resolution.

Ok, so

Apply your "nothing" theme. This will take the title bars off of your windows.
*Note* Use ```
Alt+:Left mouse button
``` to move your windows around the screen.
Next you take away your gnome panel, which is why a link to your terminal on your desktop is essentail :lolflag: 
Use
```
gnome-session-remove gnome-panel
```
to remove your gnome panel.
Now you should have NO title bar and NO gnome panel.
Start your game as normal. Your WINE virtual desktop should now take up your entire desktop.
You can use```
ctrl+right(or left)arrow
``` to switch desktops and you can use your terminal to open things like firefox.

To get your gnome panel back simply open a terminal window and type
```
gnome-panel
```
and to get your title bars back just switch your metacity theme to whatever you want.

I know this may sound a wee bit complex at first but it only takes me a few seconds to do and Im sure there is someone out there that would know how to write a script to make it a one step process.
I also hope that this can help anyone else that has wondered if it was possible at all. It works perfectly for me with both World of Warcraft and Everquest 2.

Good luck

Faud

---

### Post by Ertai87 on 2008-01-02
OK, so I did that, and now I can do CTRL-ALT-LArrow/RArrow, but I have a couple problems:

1) I can't get fullscreen in a virtual desktop, even when I set all the things you said.

2) When I switch desktop and then switch back, it minimizes my window and I can't get it back.  The program is still running (I can hear the sounds and see the job using ps -ef), but won't let me see it.

3) I can't seem to get my title bars back :'( (nevermind on this one: I had to restart all my programs to get them back...annoying but doable)

Thanks.

---

### Post by Faud on 2008-01-04
Sorry you had some problems. My first how-to and I apologize if my step by step assumed some things.
You will know if you've done it correctly if you open a terminal and type winefile and it takes up your entire desktop.
To get your title bars back bring your gnome panel back first and then go back to system-->preferences-->appearance and click on your normal theme.
Ive never had it minimze on me when switching desktops unless I was using alt-tab and that was only when I did NOT have emulate virtual desktop checked.
Im gonna go home and make a quick movie of me doing it and see if I can get it up on you tube for you. I'll just download some video editing software real quick.

---

### Post by Faud on 2008-01-08
Ok, made the video for you and it can be found here

[http://www.youtube.com/watch?v=V_Fjx7lcqxg](http://www.youtube.com/watch?v=V_Fjx7lcqxg)

Sorry it took so long to get the video. Been coming home and crashing after work pretty-much,

In the video my desktop res is set to 1024x768 and my virtual desktop size in WINE is also set to 1024x768.
I go into winefile just so that you can see that wine is now taking up 100% of my screen with no borders or title bars. Good luck

---

### Post by Ertai87 on 2008-01-08
Ah.  I see that puts the program in the upper-left corner...if possible, I'd like the program to be centered on my screen.  I'd draw it out but I don't know how to do images on webforums and for some reason ASCII art doesn't work here.  Basically the idea is to center the program on the screen, having it maintain aspect ratio and fit to the screen vertically, with black bars on either side (of course, I don't insist upon black, but that's how it was in Win XP, so w/e).

---

### Post by Faud on 2008-01-08
The only way that i know to get your window centered is to use something like compiz and then use the window placement plug in. While winefile is in the upper left of my screen it is actually taking up the entire desktop so that when I start my game it starts taking up my entire desktop. But if you just want a window in the center, compiz will do the trick for you.

---

### Post by Ertai87 on 2008-01-09
Oh wait...why was I pointed here in the first place...I forgot :(

Right now it works decently; I can play in fullscreen with skewed aspect ratio.  Was it the ALT-TAB thing or the aspect ratio thing that I came here for? XD

---

