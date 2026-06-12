---
title: "Patching Wine so that I can run Diablo 3"
date: 2012-05-15
forum: Wine
---

### Post by aaeamdar on 2012-05-15
So I'm trying to &quot;patch&quot; Wine so that I can resolve some issues I'm having with the D3 installer. Anyway, I have the patch files; I just need a step-by-step walkthrough of how to &quot;patch&quot; wine. REALLY step-by-step. I've searched this online and mostly what I've found is 3-4 year old forum posts that just don't apply anymore. Thanks in advance for any help and to re-iterate I really do need detailed help. For example until a few minutes ago I didn't know where Wine was located on my computer, so saying something like &quot;open up your Wine directory&quot; without providing detail might just get me stuck again.  Thanks, Paul

---

### Post by Lisiano on 2012-05-15
Won't it be easier to just use PlayOnLinux? I think it had Diablo 3 in it, it's basically a Wine wrapper, it installs and configures wine so the games work 100% or as much as possible.
And to use .diff files, just execute ```
patch < file.diff
```
To read more about the patch command, execute ```
man patch
```

---

### Post by aaeamdar on 2012-05-15
Gonna itemize to keep this organized:  1. I do use PlayOnLinux; it isn't working. That's why I'm trying to patch. And I just updated it to the latest version and it still doesn't explicitly support D3.  2. The patch files I have are labeled as .patch. If I mis-labeled them and they should be .diff let me know. But I did find a source that referred to them as .patch files.  3. When you say "Just execute x" that doesn't give me enough information; execute it from where; where should the file be; etc.

---

### Post by Lisiano on 2012-05-15
Sorry. 
[LIST=1]
[*]Didn't know, don't play Diablo 3
[*].diff - .patch same thing in this case (Diff comes from Difference, or difference between the original file and the new file, patching means modifying the original file to be the new file using the difference we know between them, so in this case, they can be called the same)
[*]Open a terminal (Ctrl+Alt+T), type ```
cd *dir*
``` where dir is where the source code is, for example ~/src/wine (~ is a shortcut for /home/*username*/), then type ```
patch < file.patch
``` though usually the instructions should be given with the patch.
[/LIST]

---

### Post by aaeamdar on 2012-05-15
OK I'm more with you now BUT I don't know where the source code is.  EDIT: So I guess what I need here is instructions for how to locate the source code, either on my computer or not, and then how to navigate there, and also once I am there how to know I'm there (i.e. what type of file(s) I am looking for).  Thanks

---

### Post by Lisiano on 2012-05-15
Okay. Do you have the Wine source code? If not, please download it from [WineHQ.org](WineHQ.org)

---

### Post by aaeamdar on 2012-05-15
Update: I got Wine from GitWine... not sure if that's right. Anyway, I copied the patch files in ran them like you said and it says "File to patch:" what should I put in?

---

### Post by Lisiano on 2012-05-15
Please post the output from the *username*@*hostname*:~/src/wine$ line to the very last one, put it in code tags (The hash (#) button above), also it would be best if you put a link to the patch files you found so I can take a look and make it so we both are on the same page.

---

### Post by aaeamdar on 2012-05-15
Here is the link to the patch files. They're the four links about halfway down the page.   

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953) 

Maybe now that I have NoScript disabled it won't delete my newline characters?


And I'm sorry if this makes me sound like a complete moron but "output from the *username*@*hostname*:~/src/wine$ line to the very last one" I don't know what that means. At all. Should be able to use code-tags though... ```
Code?
```

---

### Post by Lisiano on 2012-05-15
Like this ```
lisiano@Lisiano-Ubuntu:~/src$ ls
abgx360-1.0.5
abgx360gui-1.0.2
Accelerated C++
aegisub-2.1.8
aegisub-2.1.8.tar.gz
android-sdk-linux
angrytux
a.out
asterisk-gui
banshee-remote-plugin
banshe-remote-plugin.tar.gz
blender-2.54-beta-linux-glibc27-x86_64
blender-2.54-beta-linux-glibc27-x86_64.tar.bz2
blender-2.56a-beta-linux-glibc27-x86_64
bm
ccsm
cinelerra-4.2
client.cfg
compiz
compizconfig-python
crark
CUDA-Multiforcer-Linux-0.72
cudart
cudatoolkit_3.2.9_linux_64_ubuntu10.04.run
cudatoolkit_4.0.17_linux_64_ubuntu10.10.run
deluge
droid-VNC-server
duplicate-source
empathy
exploits
fah6
FAHlog.txt
ferret
ffmpeg
ffmpeg_0.6.2-1ubuntu1_amd64.deb
ffmpeg-dbg_0.6.2-1ubuntu1_amd64.deb
ffmpeg-doc_0.6.2-1ubuntu1_all.deb
flare_src_v011.zip
fuppes-0.660
geogebra-4.0.6.0
gpucomputingsdk_3.2_linux.run
gpucomputingsdk_4.0.17_linux.run
grabber
hamster
htmlparser1_6
hydra-5.4-src
hydra-5.4-src.tar.gz
imagination-3.0
imule
IronAHK
k10ctl
Learning_C
libav-0.6.2
libav_0.6.2-1ubuntu1_amd64.changes
libav_0.6.2-1ubuntu1.diff.gz
libav_0.6.2-1ubuntu1.dsc
libav_0.6.2.orig.tar.gz
libavcodec52_0.6.2-1ubuntu1_amd64.deb
libavcodec-dev_0.6.2-1ubuntu1_amd64.deb
libav-dbg_0.6.2-1ubuntu1_amd64.deb
libavdevice52_0.6.2-1ubuntu1_amd64.deb
libavdevice-dev_0.6.2-1ubuntu1_amd64.deb
libav-doc_0.6.2-1ubuntu1_all.deb
libavfilter1_0.6.2-1ubuntu1_amd64.deb
libavfilter-dev_0.6.2-1ubuntu1_amd64.deb
libavformat52_0.6.2-1ubuntu1_amd64.deb
libavformat-dev_0.6.2-1ubuntu1_amd64.deb
libav-source_0.6.2-1ubuntu1_all.deb
libavutil50_0.6.2-1ubuntu1_amd64.deb
libavutil-dev_0.6.2-1ubuntu1_amd64.deb
libcompizconfig
libpostproc51_0.6.2-1ubuntu1_amd64.deb
libpostproc-dev_0.6.2-1ubuntu1_amd64.deb
libswscale0_0.6.2-1ubuntu1_amd64.deb
libswscale-dev_0.6.2-1ubuntu1_amd64.deb
libvpx
libvpx0_0.9.6-1_amd64.deb
libvpx-0.9.6
libvpx_0.9.6-1_amd64.changes
libvpx_0.9.6-1.debian.tar.gz
libvpx_0.9.6-1.dsc
libvpx_0.9.6.orig.tar.bz2
libvpx0-dbg_0.9.6-1_amd64.deb
libvpx-dev_0.9.6-1_amd64.deb
libvpx-doc_0.9.6-1_all.deb
lives-1.3.10
metadata.anidb.net
minitube
mjpg-streamer
mpiexec
mplayer
mplayer-1.0~svn33464~natty
mplayer_1.0~svn33464~natty.dsc
mplayer_1.0~svn33464~natty.tar.gz
mplayer2
mplayer_oc
MyFolding.html
nanozip
natchck
natcheck
natcheck.c
NeXposeSetup-Linux64.bin
oclHashcat+-0.03
oclHashcat-0.25
oclHashcat-lite-0.05
pacpl-4.0.5.tar.gz
pascal
plugins-extra
plugins-main
plugins-unsupported
projectM-complete-2.0.1-Source
pyrit
rapt-6.13.11.0
rar
rarcrack-0.2
rarcrack-0.2.tar.bz2
slcreator
sleepshell
sqlitebrowser
sslstrip-0.7
stkeys
testing
wine-1.3.14
wxWidgets-2.9.1
x264
x264-0.106.1741
x264_0.106.1741-3.diff.gz
x264_0.106.1741-3.dsc
x264_0.106.1741.orig.tar.gz
xbmc-anidb
lisiano@Lisiano-Ubuntu:~/src$
```
I'll take a look at the patches in a second.

---

### Post by aaeamdar on 2012-05-15
ok I see that list; I don't understand how you generated that. I need the console command to generate it. I tried typing in what it looks like you typed in but it didn't seem similar to your output. Anyway here was the result from opening a terminal and typing LS (lowercase)

```
d3patch1.patch       Install Dragon Age Origins.log  StarCraft II
d3patch2.patch       Music                           Templates
d3patch3.patch       My Games                        Ubuntu One
d3patch4.patch       netbeans-7.1                    Videos
Desktop              newwine                         wine-git
Documents            Pictures                        wine-patched
Downloads            PlayOnLinux's virtual drives    winetricks
examples.desktop     POL-POM-4
hs_err_pid20817.log  Public

```

---

### Post by Lisiano on 2012-05-15
Took a look at the patches, made this [http://paste.ubuntu.com/988687/](http://paste.ubuntu.com/988687/), save it where you put the wine source and call it Wine.Diablo3.patch
Okay so just copy paste all this into a terminal once you cd to where you put wine
```
patch -p1 < Wine.Diablo3.patch
./tools/make_requests
./tools/wineinstall
``` At the last part, reply no, then you can run ```
./wine "~/.wine/drive_c/Program Files/Diablo3/Diablo.exe"
``` or replace that location with wherever you installed Diablo 3.


EDIT: The list I showed you is just a demonstration, it's what I have in my src directory. I wanted to see what you got when you tried to run your patch.

---

### Post by aaeamdar on 2012-05-15
OK so I did that; right now my terminal is still executing ./tools/wineinstall which has a massive text output - I'm a little concerned that it's stuck in an infinite loop. I'm gonna grab some groceries; be back in about 20 and if it's not any different I'll assume it's somehow bugged. However in the meantime two things:

1. I haven't yet successfully installed D3. So I guess the .exe I want to run is d3setu.exe (it has a longer title but w/e).

2. Ideally I'd like to tie this all back through PlayOnLinux - is there a way to point POL back towards this new patched version of Wine?

Thanks

---

### Post by Lisiano on 2012-05-15
[LIST=0]
[*]It's compiling Wine, go watch a movie after you finish your groceries
[*]I don't know, try
[*]Yes, but let's see if we can first get Diablo 3 to work.
[/LIST]

---

### Post by aaeamdar on 2012-05-15
OK! This is the farthest I've actually gotten getting D3 to run on Linux, so yippee! However, still stuck. Ran that ./wine "D3setup.exe" thing, and the d3 installer came up, which is as I said, further than I've gotten before. (Oh Wine finished compiling obviously). However, now it says "insufficient space". Now, I checked when it first said that, it says that it requires 15 gigs. I used GParted to check my available space (sadly the only way I know how) and at that point it said I had 14 and change available but I've since deleted some stuff and now it says 17, but even after restarting the D3 installer still ain't happy. I'm gonna try restarting the computer after this post so hopefully that works. If not I'll come back and update.

---

### Post by aaeamdar on 2012-05-15
OK still stuck on "not enough space". Any tips for getting around that? Including any tips on freeing up space? I feel like I've deleted most everything except WoW and Linux and still that somehow takes up 85 gigs. Anyway, thoughts?

---

### Post by Hairy_Palms on 2012-05-15
you can try running sudo apt-get clean this removes downloaded packages from /var/cache/apt which can be a lot of space if you havent cleaned it since installing as every update is a new package

---

### Post by aaeamdar on 2012-05-15
That did clear up about 250MB, so thanks! However at this point I'm getting increasingly convinced it's not actually a problem with not having enough space; it's a problem with the installer not having permission or not thinking there's enough space.

EDIT: Turns out I had around 30 Gigs of stuff in the trash. Kinda explains a lot.

EDIT 2: Actually after getting rid of that 30 gigs it's moving forward. I'll post again with the next bug cause I'm sure there will be one =). Thanks for all the help so far!

---

### Post by Lisiano on 2012-05-15
Random stuff hapens, oh and FYI, if you use EXT3/4 then there is some reserved space available only to root so that system important apps can still run like log writing, updates can proceed and so on. So it might've been that not letting you install. I think it was 5% out of all the space you have. Also a good way to see what uses up what is to use [Filelight]("apt://filelight")

---

### Post by aaeamdar on 2012-05-15
So again I just wanted to thank you for your help; because of all this I actually got the game to install. Logged into the game. made a character. Started act 1. Only problem now? the graphic for the mouse got stuck so this makes the game unplayable. Anyway, I'll be playing around with various options but if you have any suggestions either direct help or suggestions of where to get help they would be appreciated.

-Paul

P.S.: Amen to "random stuff happens"

EDIT: OK two steps backwards: Now I can't even get it to run. Maybe I'm unfamiliar with manually running things on Wine. I've tried doing the ./wine command a few different ways now; each time it says "cannot find that". 

Let me paste in an example:

```

paul@abacus:~/.wine/drive_c/Program Files/Diablo III$ dir
BattlenetAccount.url       fmodex.dll          Manual.url
Bnet               icudt44.dll          Microsoft.VC90.CRT.manifest
D3Debug.txt           icuin44.dll          msvcp90.dll
d3.exe               icuuc44.dll          msvcr90.dll
Data_D3               ijl15.dll          SetupWin.mpq
Diablo\ III\ Launcher.exe  InspectorReporter  TechSupport.url
Diablo\ III.mfil       Launcher.db          Updates
Diablo\ III.tfil       Logs
paul@abacus:~/.wine/drive_c/Program Files/Diablo III$ ./wine d3.exe
bash: ./wine: No such file or directory
paul@abacus:~/.wine/drive_c/Program Files/Diablo III$ ./wine "d3.exe"
bash: ./wine: No such file or directory
paul@abacus:~/.wine/drive_c/Program Files/Diablo III$ ./wine "~/.wine/drive_c/Program Files/Diablo III/d3.exe"
bash: ./wine: No such file or directory
paul@abacus:~/.wine/drive_c/Program Files/Diablo III$ 

```


I feel like I need to get this set up in PlayOnLinux but I don't really know how to do that.

---

### Post by Lisiano on 2012-05-15
Well... First off, you can try disabling the in-game mouse look so while your mouse will not look like it did in Windows, there won't be any stuck textures. Though the best place to look for information is in the Wine subforum here, wine forums anywhere and WineHQ itself.

---

### Post by spiralofhope on 2012-05-16
I could give detailed instructions, but so far I cannot get the actual game to work.

So right now I'll spare you the suffering until I can find the mystical diablo3-wine PPA people are talking about.

---

### Post by uRock on 2012-05-16
Moved to the *Wine* sub-forum.

---

### Post by Lisiano on 2012-05-16
The ./wine command means the following
[LIST]
[*]Execute program "wine" located in the current directory
[/LIST]
Since it can't find it in your Diablo 3 folder, you need to tell Bash where it is, (I'm assuming you downloaded wine to wine-git)
```
~/wine-git/wine d3.exe
```
Which would translate to the following
[LIST]
[*]Execute program "wine" located in ~/wine-git with the argument d3.exe
[/LIST]

---

### Post by spiralofhope on 2012-05-16
I found the solution.  My notes are here:

[http://eu.battle.net/d3/en/forum/topic/4065186688?page=1](http://eu.battle.net/d3/en/forum/topic/4065186688?page=1)

---

### Post by brainwash on 2012-05-16
There is already an alternative patch set ([http://bugs.winehq.org/show_bug.cgi?id=28898#c106](http://bugs.winehq.org/show_bug.cgi?id=28898#c106)).

Rebuilding the current wine1.5 package from the offcial wine ppa and using "quilt" to apply the needed patches does also work.

---

### Post by woefulwabbit on 2012-05-17
> **spiralofhope said:**
> I could give detailed instructions, but so far I cannot get the actual game to work.

So right now I'll spare you the suffering until I can find the mystical diablo3-wine PPA people are talking about.

[https://launchpad.net/~cheako/+archive/packages4diabloiii](https://launchpad.net/~cheako/+archive/packages4diabloiii)

---

### Post by buzzmandt on 2012-05-17
playonlinux also has the diablo3 wine patch available.

---

