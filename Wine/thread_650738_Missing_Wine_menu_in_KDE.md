---
title: "Missing Wine menu in KDE"
date: 2007-12-26
forum: Wine
---

### Post by constchar* on 2007-12-26
I installed KDE ontop of Ubuntu and I've been using it insted of Gnome for some time
and a few weeks ago I got into a bad mood with somebody and deleted my Wine
menu to prove a point and now I want it back and I can't figure out how lol.

So to the point; how do I get back the "Wine" menu in my K Menu?

Thanks!

---

### Post by jrusso2 on 2007-12-26
Use the kdemenu editor and browse to each of the progrms you want to add to the menu.  Be sure to save you settings before closing

You can also try running kappfinder and see if it finds them.

---

### Post by constchar* on 2007-12-26
> **jrusso2 said:**
> Use the kdemenu editor and browse to each of the progrms you want to add to the menu.  Be sure to save you settings before closing

You can also try running kappfinder and see if it finds them.

I already know about the menu editor but before Wine would automatically
create the menu items during an installation and now it doesn't do that anymore
and the Wine menu is gone altogether as I mentioned earlier, perhaps for that reason.

---

### Post by mc4man on 2007-12-27
i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing

---

### Post by constchar* on 2007-12-28
> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing

for 7.04 only
try revert in gutsy

Thanks, I tried your suggestion and it I was able to get my Wine menu back with KDE, even on Gutsy Gibbon.

---

### Post by Linux Lurker on 2008-02-03
> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing



THANK YOU!!!
This problem was driving me crazy.
Your solution worked great on KDE 7.10gg
=D>=D>=D>=D>=D>=D>=D>=D>

---

### Post by Nakoma on 2008-03-07
EDIT: This is for GNOME. Not tested on KDE

This is swell and all, But what you're really looking for is not to have the Alacarte menu undeleted. It seems doing this doesn't re-associate the menu system with the new configuration of wine and therefore when you install anther wine app it doesn't show up (at least for me) in the menu. To remove everything you must remove the files and folders associated with wine in both:

~/.local/share/applications/
~/.local/share/desktop-directories/

and removing the wine xml menu data from the previously mentioned file:

~/.config/menus/applications.menu

Do this all after a :

sudo apt-get remove --purge wine
rm ~/.wine -R    (or be leet and do " yes | rm ~/.wine -R " to be rid of all the questions)

This should remove everything you care about so far as wine is concerned. Don't fret -- all is reconfigured (menus, .wine dir, cfg, etc...) when you:

sudo apt-get install wine
winecfg

Tested under Gusty

Enjoy!

---

### Post by anjilslaire on 2008-03-07
cool. noted for next time ;)

---

### Post by yugan on 2008-05-22
thanks a lot broo

---

### Post by BryanFRitt on 2008-06-19
> **Nakoma said:**
> EDIT: This is for GNOME. Not tested on KDE

This is swell and all, But what you're really looking for is not to have the Alacarte menu undeleted. It seems doing this doesn't re-associate the menu system with the new configuration of wine and therefore when you install anther wine app it doesn't show up (at least for me) in the menu. To remove everything you must remove the files and folders associated with wine in both:

~/.local/share/applications/
~/.local/share/desktop-directories/

and removing the wine xml menu data from the previously mentioned file:

~/.config/menus/applications.menu

Do this all after a :

sudo apt-get remove --purge wine
rm ~/.wine -R    (or be leet and do " yes | rm ~/.wine -R " to be rid of all the questions)

This should remove everything you care about so far as wine is concerned. Don't fret -- all is reconfigured (menus, .wine dir, cfg, etc...) when you:

sudo apt-get install wine
winecfg

Tested under Gusty

Enjoy!

This sounds like it destroys everything I've ever installed/done in wine, and I'll have to install everything installed with wine again, not something I want to do.

---

### Post by simptechmike on 2008-08-10
> **Nakoma said:**
> EDIT: This is for GNOME. Not tested on KDE

Tested under Gusty

Works under Hardy as well!  Thanks as this fixed my problem.  Not a big deal reinstalling my software as its all just for writing tutorials :)

Ran into one small problem, the newly installed programs were not being populated into the menu.  To fix this, instead of removing just the applications.menu, I removed the entire menus folder.

Updated list of things to do from terminal (in order):

sudo apt-get remove --purge wine

sudo rm ~/.wine -R
sudo rm ~/.local/share/applications/ -R
sudo rm ~/.local/share/desktop-directories/ -R

sudo rm ~/.config/menus/ -R

sudo apt-get install wine
winecfg

---

### Post by neostead on 2008-10-19
> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing
thx, ubuntu has great support and great community ^^

---

### Post by BryanFRitt on 2008-11-09
I had this error a while back and played with editing the menus and somehow it came back, played with editing the menu some more and it went away again, and the pattern continued... I think it affected more than the wine folder, but I'm not sure.

It's been a while since I've messed with this, don't even remember which files, I edited, any patterns, etc... (probably edited some file mentioned somewhere on the forum(s))

...

Now I remember I backuped and deleted the K menu info (I got prepared to put the info back in from the command line if I needed to), and when I rebooted everything was Ok... Start menu became alphabetized and any entries I made got put in the Lost & Found menu within the K menu (even if they started/were elsewhere), and icons were set to their default, or first icon they had.

---

### Post by -jay- on 2009-01-30
wow thanks i couldnt remove call of duty 4 thanks for the steps i was able to remove wine & reinstall it

---

### Post by spike_naples on 2009-07-21
>  ubuntu has great support and great community ^^

It surely does and THAT is the reason why I don't want to ever go back to Windows even if they paid me for it!

I'm not a Linux genius. I'm just a total beginner but I am loving this.

---

### Post by arjmage on 2009-10-22
Accurate and apt! Thanks again Mr.Ubuntu-Person-Anonymous... you help me once again.

Worked on Jaunty Jackalope

---

### Post by andycastille on 2009-10-23
What about for Ubuntu 9.04 Desktop GNOME?

---

### Post by arashiko28 on 2009-11-30
> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing

Thank you, this was giving me a head ache!

---

### Post by corevalue on 2010-02-21
Finally, I  found a trick that worked. I had uninstalled Wine after a bad windows exe that hung on installation. After re-installing Wine, although it worked, I had command line only. SimptechMike's trick worked. Thanks!

---

### Post by Mills00013 on 2010-03-09
> **Nakoma said:**
> EDIT: This is for GNOME. Not tested on KDE

This is swell and all, But what you're really looking for is not to have the Alacarte menu undeleted. It seems doing this doesn't re-associate the menu system with the new configuration of wine and therefore when you install anther wine app it doesn't show up (at least for me) in the menu. To remove everything you must remove the files and folders associated with wine in both:

~/.local/share/applications/
~/.local/share/desktop-directories/

and removing the wine xml menu data from the previously mentioned file:

~/.config/menus/applications.menu

Do this all after a :

sudo apt-get remove --purge wine
rm ~/.wine -R    (or be leet and do " yes | rm ~/.wine -R " to be rid of all the questions)

This should remove everything you care about so far as wine is concerned. Don't fret -- all is reconfigured (menus, .wine dir, cfg, etc...) when you:

sudo apt-get install wine
winecfg

Tested under Gusty

Enjoy!

Worked perfect on karmic.

Thank you so much.

---

### Post by licotto on 2010-07-31
[COLOR=Blue]**MY SOLUTION:**[/COLOR][COLOR=Black]

This is what my applications.menu file stated for Wine:
    <Name>wine-wine</Name>
        <DirectoryDir>/home/kevin/.local/share/desktop-directories</DirectoryDir>

As you can see, I had no 'Deleted' line...however, when I went to the directory listed, I had 4 files listed under 'desktop-directories' but no /DirectoryDir folder, so I just made a new folder named that and added all the files except the .directory file and it works!!
[/COLOR]

---

### Post by hempanicker on 2010-08-13
Yep ! This fixes it. Thanks a bunch !

---

### Post by julri764 on 2010-08-27
Great support, worked on 10.04 Lucid.

---

### Post by nekizi on 2011-01-14
> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
        <DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
        <Deleted/>
```remove the <Deleted/>
maybe kde does the same thing

what? can you please explain me what to write, where to write etc, because i am not undestanding what to do. 
Thanks in advance

---

### Post by cogadh on 2011-01-14
He did explain it fairly perfectly but some clarification might help:

1. Find the applications.menu file in "/home/<your username>/.config/menus/applications.menu". The .config directory is a hidden directory, so you will need to show hidden files and folders in the file browser in order to find it.

2. Open the applications.menu with a text editor and find a section that looks something like this:```
<Name>wine-wine</Name>
        <DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
        <Deleted/>
```

3. Remove the <Deleted/> line but leave the rest as it is

That's it. If you had previously manually deleted the Wine menu, it should now come back, though you may need to log out/back in to see the changes.

---

### Post by nekizi on 2011-01-15
Thank you!

---

### Post by NMALP on 2011-03-23
> **cogadh said:**
> He did explain it fairly perfectly but some clarification might help:

1. Find the applications.menu file in "/home/<your username>/.config/menus/applications.menu". The .config directory is a hidden directory, so you will need to show hidden files and folders in the file browser in order to find it.

2. Open the applications.menu with a text editor and find a section that looks something like this:```
<Name>wine-wine</Name>
        <DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
        <Deleted/>
```

3. Remove the <Deleted/> line but leave the rest as it is

That's it. If you had previously manually deleted the Wine menu, it should now come back, though you may need to log out/back in to see the changes.


Sorry but I still dont get it.

Under Menus
I have applications.menus
then Amplications.menus.Undo-10
all the way to undo-15 

In applications.menu

I have:

!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Graphics</Name>
		<Include>
			<Filename>evince.desktop</Filename>
		</Include>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Deleted/>
		</Menu>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Games</Name>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
		<Include>
			<Filename>gnome-sudoku.desktop</Filename>
		</Include>
		<Include>
			<Filename>quadrapassel.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnomine.desktop</Filename>
		</Include>
		<Include>
			<Filename>mahjongg.desktop</Filename>
		</Include>
		<Include>
			<Filename>gbrainy.desktop</Filename>
		</Include>
		<Include>
			<Filename>sol.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
		<Include>
			<Filename>evolution.desktop</Filename>
		</Include>
	</Menu>
</Menu>
 

I am not sure of which "deleted" to remove.


Thanks

---

### Post by cogadh on 2011-03-23
Looks like you deleted both the Wine menu and the programs sub-menu separately, creating two separate <deleted/> entries, both of which need to be removed.
> **NMALP said:**
> Sorry but I still dont get it.
!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Graphics</Name>
		<Include>
			<Filename>evince.desktop</Filename>
		</Include>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Deleted/>[COLOR="Red"]<<< THIS ONE RIGHT HERE[/COLOR]
		</Menu>
		<Deleted/>[COLOR="red"]<<< AND THIS ONE RIGHT HERE[/COLOR]
	</Menu>
	<Menu>
		<Name>Games</Name>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
		<Include>
			<Filename>gnome-sudoku.desktop</Filename>
		</Include>
		<Include>
			<Filename>quadrapassel.desktop</Filename>
		</Include>
		<Include>
			<Filename>gnomine.desktop</Filename>
		</Include>
		<Include>
			<Filename>mahjongg.desktop</Filename>
		</Include>
		<Include>
			<Filename>gbrainy.desktop</Filename>
		</Include>
		<Include>
			<Filename>sol.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<AppDir>/home/nicholas/.local/share/applications</AppDir>
		<Include>
			<Filename>evolution.desktop</Filename>
		</Include>
	</Menu>
</Menu>

I am not sure of which "deleted" to remove.


Thanks

---

