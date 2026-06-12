---
title: "Wine will not install to Appplications Menu"
date: 2007-12-24
forum: Wine
---

### Post by 45acp on 2007-12-24
I had wine installed before but I deleted it for some reason. Now when I install wine it doesn't create a menu selection under the applications menu like before. Any ideas how I can get the menu selection back?

---

### Post by MaindotC on 2007-12-24
That is amazing - I had the same issue but it started about two weeks ago when I reinstalled 7.04.  There was just an update for wine released - a newer version I'm just not sure of the number b/c I'm in winblows right now - and I tried reinstalling Starcraft and not only did it create a menu but now SC crashes when I connect to battle.net.  Sorry I have nothing of value to contribute but I just thought it was funny how it happened to both of us :)

---

### Post by mc4man on 2007-12-24
1st. thing to check is to right click on applications and choose edit menus - see if wine is listed and if so check the box. You can also try revert but that affects the whole menu. Otherwise you can edit a file in /home/<user name>/.config/menus

---

### Post by MaindotC on 2007-12-25
Thanks for the reply.  I did check the menu configuration already and it doesn't show a Wine sub menu that I can enable :(  I know I can manually make my own menus, but I'm just concerned that before it did and now it doesn't.  7.04 should be 7.04 no matter how many times you install it, imho :(  What other steps could I take to troubleshoot this problem?

---

### Post by 45acp on 2007-12-25
Thanks for the replies. Still can't get wine reinstalled correctly.

---

### Post by mc4man on 2007-12-25
@strAlan  I'm not really sure what your asking but anyway I'm not using Feisty anymore so I'll defer to any one who is. In gutsy it's very hard not to have the menu (in applications) return from uninstall/ re install . Its in /etc/xdg/menus/applications-merged and if you do an uninstall it stays behind, a complete removal it goes but is (re)written when you install.
What you could check (feisty or gutsy) is if you had happened to delete the menu entry at some point then it won't return till you edit                                                                      
 /home/<user name>/.config/menus/applications.menu and remove the  <deleted/>  line in the wine entry. ( it's a hidden file and if it's not there then you never deleted ithe menu entry)
sorry couldn't be of more help

---

### Post by MaindotC on 2007-12-25
> **mc4man said:**
> if you do an uninstall it stays behind, a complete removal it goes but is (re)written when you install.

Are you referring to an unistall of a wine'd application, or wine itself?

> What you could check (feisty or gutsy) is if you had happened to delete the menu entry at some point

```
:~/.config/menus/applications-merged$ ls
wine-Programs-Starcraft.menu
```

Yep, it's there.  Still no Wine menu and no wine installed application menu :(

---

### Post by mc4man on 2007-12-26
The question of the thread was after having uninstalled _wine_ and then at some point reinstalling wine there was no entry ( for wine) in the drop down applications menu. while I don't have feisty there may have been an issue when removing the repo ver. and installing from winehq though i'm sure it was resolved as in post 3. If you have manually deleted the wine entry from the applications menu (right click, edit menus, ect.) an entry is written to 
/home/<user name>/.config/menus/applications.menu and by removing the <deleted/>  line the menu should return or will be able to return either immediately or when re installing wine

note; applications-merged is not the right file in this case

---

### Post by CypherHackz on 2008-01-09
im also having the same problem. had wine installed before but removed it because for some reason. but now, when i reinstall wine, there is no menu on the applications.

---

### Post by MaindotC on 2008-01-10
Yeah well don't ask mc4man - we're not on his level so we peasants dare not ask for help with this issue.

---

### Post by mc4man on 2008-01-11
@strAlan
sorry if i offended you or came across as an ******* - probably did, probably am.
As far as I can see any time you delete a menu item whether it's an individual item, directory, sub directory an entry is written to /home/<user name>/.config/menus/applications.menu . To get that menu, menu item back you need to remove the <deleted> 
example
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Multimedia</Name>
		<Include>
			<Filename>alacarte-made-2.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Menu>
				<Name>wine-Programs-System Shock 2</Name>
				<Deleted/>
			</Menu>
			<Exclude>
				<Filename>wine-Programs-Windows Media Player.desktop</Filename>
			</Exclude>
			<AppDir>/home/doug/.local/share/applications</AppDir>
		</Menu>
	</Menu>
	<Menu>
		<Name>Education</Name>
		<Deleted/>
	</Menu>
</Menu>
```

---

### Post by MaindotC on 2008-01-11
> **mc4man said:**
> @strAlan
sorry if i offended you or came across as an ******* - probably did, probably am.

That apology proves you aren't.  Actually I've been thinking about how almost everyone assumes everyone is a newb, and it actually has made me so angry that it drives me to learn more.  I guess it's better than just handing us the answers; sometimes it just seems like I hit a brick wall.  But anyway, I'm reading an O'Reilly book called "Understanding the Linux Kernel" and I'm almost done - then I'm taking a class in C and C++ in the spring so I hope to understand source code and how it interacts in Linux.  Thank you for apologizing :)

---

### Post by tjasko12 on 2008-09-24
> **mc4man said:**
> @strAlan  I'm not really sure what your asking but anyway I'm not using Feisty anymore so I'll defer to any one who is. In gutsy it's very hard not to have the menu (in applications) return from uninstall/ re install . Its in /etc/xdg/menus/applications-merged and if you do an uninstall it stays behind, a complete removal it goes but is (re)written when you install.
What you could check (feisty or gutsy) is if you had happened to delete the menu entry at some point then it won't return till you edit                                                                      
 /home/<user name>/.config/menus/applications.menu and remove the  <deleted/>  line in the wine entry. ( it's a hidden file and if it's not there then you never deleted ithe menu entry)
sorry couldn't be of more help

Actually, that works perfectly... Here's how to do it in a set of commands.

1) Open the Terminal
2) Type the following in:

```
sudo gedit ~/.config/menus/applications.menu
```

3) Type in your password if you weren't logged in as root already

3) A window should pop-up...

4) Find the entry that looks like this:

> 
<Menu>
		<Name>wine-wine</Name>
                [COLOR="Red"]**<deleted/>**[/COLOR]
	</Menu>


5) Deleted the text in red... Then click save at the top. 

6) Enjoy your (new) working WINE menu. :D


Hope this helps! :)

---

### Post by wyrless2002 on 2009-09-28
Thanks mc4man, nearly two years later your post is still helping.

---

