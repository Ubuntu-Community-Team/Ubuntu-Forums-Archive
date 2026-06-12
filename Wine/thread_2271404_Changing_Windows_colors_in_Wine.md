---
title: "Changing Windows colors in Wine"
date: 2015-03-29
forum: Wine
---

### Post by dora5 on 2015-03-29
Instructions I could find (multiple copies of) online on how to change your Windows colors that programs running in Wine use, all tell how to change the colors to black, white and gray.   Does anyone here actually use only black, white and gray?   Well, evidently millions of Ubuntu users, but since they can't be human we won't count them....

I use the Windows basic blue scheme in Windows 7, with some alterations.   I copied my own values from my own Windows registry.   

Now, there are contradictory and vague instructions all over the place about how to find the set of color instructions Windows 7 actually uses....  LOL.  NOT hard.   They are in [COLOR=windowtext][FONT=Consolas] 
[/FONT][/COLOR][COLOR=windowtext][FONT=Consolas][FONT=inherit]HKEY_CURRENT_USER\Control Panel\Colors - I varified this is the actual colors my computer is using.

The nearby color scheme in 

[COLOR=windowtext][FONT=Segoe UI][COLOR=windowtext][FONT=Consolas][FONT=inherit]HKEY_CURRENT_USER\Control Panel\Desktop\Colors
is not the color scheme my computer is using; in fact it appears to be your basic gray color scheme.   

I also like my window a different color than White Glare.

Don't forget to put in the quotes and the equal signs.  Oops - the thread I'm responding to is closed, leaving all of the information behind ... brother!

Alright.   You edit ~/.wine/user.reg  , using your text editor like gedit.    Insert this code following by all the below lines, with quotes and the equal sign.

[Control Panel\\Colors] string of ten numbers, the first six of seems like it should be consistent with the numbering scheme the other entries use
"ActiveBorder="182 204 241"
"ActiveTitle"="0 128 64"
....
"WindowText"="0 0 0"   

[/FONT][/FONT][/COLOR][/FONT][/COLOR]
[FONT=Tahoma]My own registry values.[/FONT]
[FONT=Tahoma]
[/FONT]
[FONT=Tahoma]ActiveBorder  182 204 241    [/FONT]
[FONT=Tahoma]ActiveTitle  0 128 64             [/FONT]
[FONT=Tahoma]AppWorkspace 63 121 218     [/FONT]
[FONT=Tahoma]Background  0 0 0                   [/FONT]
[FONT=Tahoma]ButtonAlternativeFace 0 0 0     [/FONT]
[FONT=Tahoma]ButtonDkShadow 105 105 105    [/FONT]
[FONT=Tahoma]ButtonFace 182 204 241           [/FONT]
[FONT=Tahoma]ButtonHiliht 219 231 249[/FONT]
[FONT=Tahoma]ButtonLight 182 204 241[/FONT]
[FONT=Tahoma]ButtonShadow  63 121 218[/FONT]
[FONT=Tahoma]ButtonText  0 0 0[/FONT]
[FONT=Tahoma]GradientActiveTitle  215 228 242[/FONT]
[FONT=Tahoma]GradientInactiveTitle   215 228 242[/FONT]
[FONT=Tahoma]GrayText  63 121 218[/FONT]
[FONT=Tahoma]Hilight  51 153 255[/FONT]
[FONT=Tahoma]HilightText  255 255 255[/FONT]
[FONT=Tahoma]HotTrackingColor 0 102 204[/FONT]
[FONT=Tahoma]InactiveBorder  182 204 241[/FONT]
[FONT=Tahoma]InactibeTitle 63 121 218[/FONT]
[FONT=Tahoma]InactiveTitleText  67 78 84[/FONT]
[FONT=Tahoma]InfoText 0 0 0[/FONT]
[FONT=Tahoma]InfoWindow   255 255 225[/FONT]
[FONT=Tahoma]Menu  182 204 241[/FONT]
[FONT=Tahoma]MenuBar   240 240 240[/FONT]
[FONT=Tahoma]MenuHilight 51 153 255[/FONT]
[FONT=Tahoma]MenuText  0 0 0[/FONT]
[FONT=Tahoma]Scrollbar   219 231 249[/FONT]
[FONT=Tahoma]Title Text 0 0 0[/FONT]
[FONT=Tahoma]Window 241 220 192  (deep orangy off white color)[/FONT]
[FONT=Tahoma]WindowFrame   100 100 100[/FONT]
[FONT=Tahoma]WindowText  0 0 0[/FONT]
[FONT=Tahoma]
[/FONT]
I put this in my Windows registry in Wine, and behold, Rootsmagic now runs with the same colors it does on my Windows 7 computer!
[COLOR=windowtext][FONT=Segoe UI][COLOR=windowtext][FONT=Consolas][FONT=inherit]
[/FONT][/FONT][/COLOR][/FONT][/COLOR]
[COLOR=windowtext][FONT=inherit] [/FONT][/COLOR]
[/FONT][/FONT][/COLOR]

---

### Post by dora5 on 2015-03-29
Look out for typos above, for instance, "Inactibe" is Inactive".

---

