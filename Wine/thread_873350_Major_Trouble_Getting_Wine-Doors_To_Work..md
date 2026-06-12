---
title: "Major Trouble Getting Wine-Doors To Work."
date: 2008-07-28
forum: Wine
---

### Post by ModdTaco on 2008-07-28
Hey I'm fairly new to Ubuntu and Linux only using it for the past year. I decided  to give Wine-doors a try. Here's what happened. I installed Wine. Then Wine-Doors. The Wine-Doors First time user thingy popped up. I entered my name the checked the valid windows license box. I clicked proceed. (I'm going to call this proceeder "FirstDoors" because I refer to it many times here) It went along and crashed at the C++ install. I brought up terminal and put in "wine-doors --firstrun" The box came up again and I did FirstDoors. Then It crashed at the fonts. So T tried terminal again and did FirstDoors but I get to the same point. So I uninstalled Wine-Doors re-did everything and still. Same thing. Here's the terminal output.

ubuntu@ubuntu-desktop:~$ wine-doors --firstrun
Started logging session
Checking wine drive: /home/ubuntu/.wine/
Resolving dependencies for vc6 
Resolving dependencies for mozcontrol 
Resolving dependencies for winegecko 
Resolving dependencies for autohotkey 
Resolving dependencies for webdings 
Resolving dependencies for times_new_roman 
Resolving dependencies for courier_new 
Resolving dependencies for comicsans 
Resolving dependencies for arial_bold 
Resolving dependencies for arial 
Creating wine drive
wine.py: CreateDrive: Wine drive already exists, cowardly refusing to manage already installed apps
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0
wine.py: CreateDrive: Finished
Installing Application: arial
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/queue.py", line 145, in Execute
    app_pack = ApplicationPack( INSTALL, pack, version, repo )
  File "/usr/share/wine-doors/src/application.py", line 127, in __init__
    self.InstallApplication()
  File "/usr/share/wine-doors/src/application.py", line 346, in InstallApplication
    packlist.AddInstalled(self.app_pack['shortname'], majorversion)
  File "/usr/share/wine-doors/src/packlist.py", line 315, in AddInstalled
    self.DelInstalled( pack, version, None )
  File "/usr/share/wine-doors/src/packlist.py", line 336, in DelInstalled
    for pack_version in pack_a['versions']:
NameError: global name 'pack_a' is not defined

Any help would be great.

---

### Post by ModdTaco on 2008-07-29
Anyone?

---

### Post by SunnyRabbiera on 2008-07-29
what method did you install wine doors?

---

### Post by gjoellee on 2008-07-29
you should have WINE installed first....download a .deb from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

also download WINE DOORS .deb from here:
[http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb](http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb)

and use wine doors first time from the menu...should be located somewhere in Applications...you have to agree the Micrsoft's licenses

---

### Post by ModdTaco on 2008-07-29
@SunnyRabbiera
I installed via "wget http://www.wine-doors.org/releases/wine-doors_0.1-1_all.deb'"

@gjoellee
WINE has been installed before hand. I went to the Applications to try the first time. nothing happens when I click the Wine-Doors link. No network activity or CPU activity. So I uninstalled it and I tried via your link and it got me this far.

ubuntu@ubuntu-desktop:~$ wine-doors --firstrun
Started logging session
Checking wine drive: /home/ubuntu/.wine/
Resolving dependencies for vc6 
Resolving dependencies for mozcontrol 
Resolving dependencies for winegecko 
Resolving dependencies for autohotkey 
Resolving dependencies for webdings 
Resolving dependencies for times_new_roman 
Resolving dependencies for courier_new 
Resolving dependencies for comicsans 
Resolving dependencies for arial_bold 
Resolving dependencies for arial 
Creating wine drive
wine.py: CreateDrive: Wine drive already exists.
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0
wine.py: CreateDrive: Finished
Installing Application: arial
Warning: MD5 sum not found

Installing Application: arial_bold
Warning: MD5 sum not found

Installing Application: comicsans
Warning: MD5 sum not found

Installing Application: courier_new
Warning: MD5 sum not found

Installing Application: times_new_roman
tar: /home/edwin/.wine-doors/apppacks/times_new_roman-1.wdi: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/queue.py", line 165, in Execute
    app_pack = ApplicationPack( INSTALL, pack, version, repo )
  File "/usr/share/wine-doors/src/application.py", line 183, in __init__
    self.InstallApplication()
  File "/usr/share/wine-doors/src/application.py", line 306, in InstallApplication
    self.Parse()
  File "/usr/share/wine-doors/src/application.py", line 200, in Parse
    parser.parse( self.app_pack_xml )
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 102, in parse
    source = saxutils.prepare_input_source(source)
  File "/usr/lib/python2.5/xml/sax/saxutils.py", line 298, in prepare_input_source
    f = urllib.urlopen(source.getSystemId())
  File "/usr/lib/python2.5/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 459, in open_file
    return self.open_local_file(url)
  File "/usr/lib/python2.5/urllib.py", line 473, in open_local_file
    raise IOError(e.errno, e.strerror, e.filename)
IOError: [Errno 2] No such file or directory: '/home/ubuntu/.wine-doors/apppacks/times_new_roman-1/pack.xml'


NOTE: the Application link to wine-doors still does nothing.

PS: Thank you for your help so far

---

### Post by bodhi.zazen on 2008-07-29
wine-doors is a little err, difficult ?

[http://www.wine-doors.org/wordpress/?p=57](http://www.wine-doors.org/wordpress/?p=57)

You may have better luck filing a bug with the developers ...

---

### Post by ModdTaco on 2008-07-29
LOL, I'd say. I'll try filing a bug report. Wine-Doors is reminding me of Windows all over again. It's not a major thing because I have vista on boot but I'd like to NOT use windows as much as I can. Only for gaming. And even then......

PS is there anyway to erase the Wine-Doors log. So it starts from the.. well start. I really edont know how to make this NOT confusing.

---

### Post by kwpowers on 2009-06-30
just discovered this package in ubuntu tweak.  the application failed on 2 points 

1 autohotkey failed to install work around download latest from [http://www.autohotkey.com/](http://www.autohotkey.com/) and install manually this should be done after the first run of wine-doors to force a good install in the .wine folder

2 failed with following text

sh: --version: not found
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 137, in <module>
    ui.winedoors = ui.WineDoorsGUI()
  File "/usr/share/wine-doors/src/ui.py", line 1102, in __init__
    self.tree = PackTree( self.window['tv_packlist'], self.window )
  File "/usr/share/wine-doors/src/ui.py", line 597, in __init__
    packlist.UpdateAll()
  File "/usr/share/wine-doors/src/packlist.py", line 309, in UpdateAll
    self.TidyPacks()
  File "/usr/share/wine-doors/src/packlist.py", line 316, in TidyPacks
    wine.WineVersion().split(".") >= pack['versions'][0][0][1].split("."):
AttributeError: 'NoneType' object has no attribute 'split'



work around open file .wine/wine-doors/preferences.xml with text editor

i changed <prefix>/usr//share/wine-doors/</prefix> 
       to <prefix>/usr/share/wine-doors/</prefix> (changed // to /)
and <winebinary></winebinary>
 to <winebinary>/usr/bin/wine</winebinary> (added correct full path to wine binary)

NOTE both work arounds are necessary

---

### Post by Th3_uN1Qu3 on 2009-07-02
I dunno why you bother with that crap. Just the latest version of Wine is enough, it even creates its programs menu like on windoze. What could be easier?

Sure, not everything runs with it, but it's getting better. I tried wine-doors last year and it was way more difficult to figure out than using the terminal (!!!) so i removed it. Never needed it again.

---

### Post by Sef on 2009-07-02
Necromancing.  Locked.

---

