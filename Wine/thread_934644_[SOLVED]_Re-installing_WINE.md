---
title: "[SOLVED] Re-installing WINE"
date: 2008-09-30
forum: Wine
---

### Post by DougieFresh4U on 2008-09-30
I have removed wine and re-installed it twice(or thought I did)
Now when I install wine, it does not show up in Applications>Wine.
It shows up under Applications>Other then it only says 'Windows Program Loader' before in my origanal  Wine install it went like this Applications>Wine, then it broke wine down into config and a couple of other things. How do I get that back to the way it was when I first put wine on machine. Also, what are the lines I can add to sources list(Intrepid). I tried a wget through terminal and got a '404 not found' error messege. 
Please help, I really screwed this up. I have gone into files and deleted the .wine file also.
Thanks

---

### Post by david_kt on 2008-10-01
> **DougieFresh4U said:**
> I have removed wine and re-installed it twice(or thought I did)
Now when I install wine, it does not show up in Applications>Wine.
It shows up under Applications>Other then it only says 'Windows Program Loader' before in my origanal  Wine install it went like this Applications>Wine, then it broke wine down into config and a couple of other things. How do I get that back to the way it was when I first put wine on machine. 

For the menu, open applications.menu and see what happen inside:

```
 gedit ~/.config/menus/applications.menu

```

DK

---

### Post by DougieFresh4U on 2008-10-06
> **david_kt said:**
> For the menu, open applications.menu and see what happen inside:

```
 gedit ~/.config/menus/applications.menu

```

DK

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/dougie/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<AppDir>/home/dougie/.local/share/applications</AppDir>
		<Layout>
			<Merge type="menus"/>
			<Filename>application-browser.desktop</Filename>
			<Filename>mount-archive.desktop</Filename>
			<Filename>nautilus-autorun-software.desktop</Filename>
			<Filename>bluefish-project.desktop</Filename>
			<Filename>bmp-play-2.0.desktop</Filename>
			<Filename>compiz.desktop</Filename>
			<Filename>seahorse-pgp-encrypted.desktop</Filename>
			<Filename>seahorse-pgp-keys.desktop</Filename>
			<Filename>gmenu-simple-editor.desktop</Filename>
			<Filename>metacity.desktop</Filename>
			<Filename>nautilus-folder-handler.desktop</Filename>
			<Filename>openjdk-6-java.desktop</Filename>
			<Filename>cxassoc-cxchromium-0:application_x-crossover-exe::run.desktop</Filename>
			<Filename>displayconfig-gtk.desktop</Filename>
			<Filename>sun-java6-java.desktop</Filename>
			<Filename>gnome-theme-installer.desktop</Filename>
			<Filename>userapp-wine-FAIEHU.desktop</Filename>
			<Filename>seahorse-pgp-signature.desktop</Filename>
			<Filename>wine.desktop</Filename>
			<Filename>xmms-pl.desktop</Filename>
			<Merge type="files"/>
		</Layout>
		<Exclude>
			<Filename>userapp-wine-FAIEHU.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>xmms-pl.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>wine.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>wine-1.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<Include>
			<Filename>paman.desktop</Filename>
		</Include>
		<AppDir>/home/dougie/.local/share/applications</AppDir>
		<Include>
			<Filename>gnome-volume-control.desktop</Filename>
		</Include>
		<Include>
			<Filename>pavumeter-record.desktop</Filename>
		</Include>
		<Include>
			<Filename>pavumeter.desktop</Filename>
		</Include>
	</Menu>
</Menu>

---

### Post by david_kt on 2008-10-06
> **DougieFresh4U said:**
> <!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/dougie/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<AppDir>/home/dougie/.local/share/applications</AppDir>
		<Layout>
			<Merge type="menus"/>
			<Filename>application-browser.desktop</Filename>
			<Filename>mount-archive.desktop</Filename>
			<Filename>nautilus-autorun-software.desktop</Filename>
			<Filename>bluefish-project.desktop</Filename>
			<Filename>bmp-play-2.0.desktop</Filename>
			<Filename>compiz.desktop</Filename>
			<Filename>seahorse-pgp-encrypted.desktop</Filename>
			<Filename>seahorse-pgp-keys.desktop</Filename>
			<Filename>gmenu-simple-editor.desktop</Filename>
			<Filename>metacity.desktop</Filename>
			<Filename>nautilus-folder-handler.desktop</Filename>
			<Filename>openjdk-6-java.desktop</Filename>
			<Filename>cxassoc-cxchromium-0:application_x-crossover-exe::run.desktop</Filename>
			<Filename>displayconfig-gtk.desktop</Filename>
			<Filename>sun-java6-java.desktop</Filename>
			<Filename>gnome-theme-installer.desktop</Filename>
			<Filename>userapp-wine-FAIEHU.desktop</Filename>
			<Filename>seahorse-pgp-signature.desktop</Filename>
			<Filename>wine.desktop</Filename>
			<Filename>xmms-pl.desktop</Filename>
			<Merge type="files"/>
		</Layout>
		<Exclude>
			<Filename>userapp-wine-FAIEHU.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>xmms-pl.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>wine.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>wine-1.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<Include>
			<Filename>paman.desktop</Filename>
		</Include>
		<AppDir>/home/dougie/.local/share/applications</AppDir>
		<Include>
			<Filename>gnome-volume-control.desktop</Filename>
		</Include>
		<Include>
			<Filename>pavumeter-record.desktop</Filename>
		</Include>
		<Include>
			<Filename>pavumeter.desktop</Filename>
		</Include>
	</Menu>
</Menu>

Remove the <Deleted/> become as below and see whether it help.

DK


<!DOCTYPE Menu
PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
<Name>Applications</Name>
<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
<Menu>
<Name>wine-wine</Name>
<DirectoryDir>/home/dougie/.local/share/desktop-directories</DirectoryDir>
</Menu>
<Menu>
<Name>Other</Name>
<AppDir>/home/dougie/.local/share/applications</AppDir>
<Layout>
<Merge type="menus"/>
<Filename>application-browser.desktop</Filename>
<Filename>mount-archive.desktop</Filename>
<Filename>nautilus-autorun-software.desktop</Filename>
<Filename>bluefish-project.desktop</Filename>
<Filename>bmp-play-2.0.desktop</Filename>
<Filename>compiz.desktop</Filename>
<Filename>seahorse-pgp-encrypted.desktop</Filename>
<Filename>seahorse-pgp-keys.desktop</Filename>
<Filename>gmenu-simple-editor.desktop</Filename>
<Filename>metacity.desktop</Filename>
<Filename>nautilus-folder-handler.desktop</Filename>
<Filename>openjdk-6-java.desktop</Filename>
<Filename>cxassoc-cxchromium-0:application_x-crossover-exe::run.desktop</Filename>
<Filename>displayconfig-gtk.desktop</Filename>
<Filename>sun-java6-java.desktop</Filename>
<Filename>gnome-theme-installer.desktop</Filename>
<Filename>userapp-wine-FAIEHU.desktop</Filename>
<Filename>seahorse-pgp-signature.desktop</Filename>
<Filename>wine.desktop</Filename>
<Filename>xmms-pl.desktop</Filename>
<Merge type="files"/>
</Layout>
<Exclude>
<Filename>userapp-wine-FAIEHU.desktop</Filename>
</Exclude>
<Exclude>
<Filename>xmms-pl.desktop</Filename>
</Exclude>
<Include>
<Filename>wine.desktop</Filename>
</Include>
</Menu>
<Menu>
<Name>System</Name>
<Include>
<Filename>wine-1.desktop</Filename>
</Include>
</Menu>
<Menu>
<Name>Multimedia</Name>
<Include>
<Filename>paman.desktop</Filename>
</Include>
<AppDir>/home/dougie/.local/share/applications</AppDir>
<Include>
<Filename>gnome-volume-control.desktop</Filename>
</Include>
<Include>
<Filename>pavumeter-record.desktop</Filename>
</Include>
<Include>
<Filename>pavumeter.desktop</Filename>
</Include>
</Menu>
</Menu>

---

### Post by kilian_wasmer on 2008-10-06
Hi.

I have a similar problem. Actually my "applications.menu" is the following:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/kilian/.local/share/applications</AppDir>
		<Exclude>
			<Filename>wine-browsedrive.desktop</Filename>
		</Exclude>
		<Menu>
			<Name>wine-Programs</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Menu>
			<Name>wine-Programme</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Include>
			<Filename>wine-uninstaller.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-winecfg.desktop</Filename>
		</Include>
	</Menu>
</Menu>
```

Although there is no "</Delete>" left, "wine" is nowhere to find in the menu bar!? I also tried uninstalling and reinstalling before but nothing changed..

Any ideas!?

Kilian

---

### Post by david_kt on 2008-10-06
> **kilian_wasmer said:**
> Hi.

I have a similar problem. Actually my "applications.menu" is the following:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/kilian/.local/share/applications</AppDir>
		<Exclude>
			<Filename>wine-browsedrive.desktop</Filename>
		</Exclude>
		<Menu>
			<Name>wine-Programs</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Menu>
			<Name>wine-Programme</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Include>
			<Filename>wine-uninstaller.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-winecfg.desktop</Filename>
		</Include>
	</Menu>
</Menu>
```

Although there is no "</Delete>" left, "wine" is nowhere to find in the menu bar!? I also tried uninstalling and reinstalling before but nothing changed..

Any ideas!?

Kilian

Could you try to remove <Exclude> and </Exclude> as below, see whether it is help. If still problem, try to put <Include> and </Include> enclosing the menu that does not show up.

Backup your file first as I am not sure whether these steps will hlep you or not.

DK

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		<AppDir>/home/kilian/.local/share/applications</AppDir>
				<Filename>wine-browsedrive.desktop</Filename>
			<Menu>
			<Name>wine-Programs</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Menu>
			<Name>wine-Programme</Name>
			<DirectoryDir>/home/kilian/.local/share/desktop-directories</DirectoryDir>
		</Menu>
		<Include>
			<Filename>wine-uninstaller.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-winecfg.desktop</Filename>
		</Include>
	</Menu>
</Menu>
```

---

### Post by kilian_wasmer on 2008-10-07
Hi.

At first it did'nt work. Then I've deleted all "wine"-entries un- and reinstalled wine. Now wine is there again! :)

But I wonder! Now I can see some old entries (of software that's been uninstalled long ago!?)? How can I get rid of them? :mad:

Cheers

Kilian

---

### Post by kilian_wasmer on 2008-10-07
Solved!
[HTML]http://ubuntuforums.org/archive/index.php/t-815333.html[/HTML]


> **kilian_wasmer said:**
> Hi.

At first it did'nt work. Then I've deleted all "wine"-entries un- and reinstalled wine. Now wine is there again! :)

But I wonder! Now I can see some old entries (of software that's been uninstalled long ago!?)? How can I get rid of them? :mad:

Cheers

Kilian

---

### Post by DougieFresh4U on 2008-10-08
Thanks for ALL replies. Got it, thanks so much. Getting rid of 'Delete' fixed the problem

---

