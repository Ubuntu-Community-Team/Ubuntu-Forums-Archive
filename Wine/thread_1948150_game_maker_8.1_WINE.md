---
title: "game maker 8.1 WINE"
date: 2012-03-27
forum: Wine
---

### Post by gandalf3 on 2012-03-27
I'm new to Linux, (Ubuntu 11.10) and was attempting to install game maker 8.1 with wine (i couldn't find any earlier versions with working download links) unfortunately, when i try to open the game maker EXE with wine, nothing happens.
i have tried lateralgm, but the lack of ability to run the gmk file is a major problem..
is there anyway to run the executables with lateralgm? or get gamemaker working? (assuming you can run the .gmk using gamemaker through wine)
any help appreciated..:neutral:

---

### Post by uRock on 2012-03-27
Moved to *Wine*

---

### Post by Toz on 2012-03-27
Have you tried following the HOWTO at this page? [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23252]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23252")

---

### Post by gandalf3 on 2012-03-31
yes.. it works okay until i try to run the game.. then there's an error dialog box "there is something seriously wrong with the program helloworldgame.exe or a problem with wine the program will shut down now." then wine is stuck open, because gamemaker keeps trying to save before wine closes, but it doesn't work.. ](*,)

---

### Post by Toz on 2012-04-01
Yes. According to that same link, running your created games doesn't work. You might want to create a bug report over at wineappdb and see if the wine devs will consider fixing it.

As an alternative, you could consider using virtualbox to create a Window VM and running the program in there.

---

### Post by gandalf3 on 2012-04-07
to do that, i would have to mess with windows..
hmm.. i thought there might be some "add on" or something to run games created with lateralgm, but i never actually found anything..
oh well..
i guess i'll have to learn a real programming language. (i was planing to do that anyway, but..)

---

### Post by gandalf3 on 2012-05-17
well.. i found this page sort of by accident the other day..
[http://enigma-dev.org/docs/Wiki/Install:Git](http://enigma-dev.org/docs/Wiki/Install:Git)

and it looks like it will run the exe (i hope)
but i can't make much sense out of the "git client" and everything else..:confused:
could somebody explain how i go about installing this?
Thanks.
(sorry to be such a noob..):oops:

---

### Post by Toz on 2012-05-17
To get the linux dev port installed, do the following:

1. Install git:
```
sudo apt-get install git
```

2. Pull the git code:
```
mkdir ~/enigma_git
cd ~/enigma_git
git clone git://github.com/enigma-dev/enigma-dev.git
```

3. Obtain additional dependencies:
```
cd enigma-dev
python install.py
```

4. Run enigma:
```
cd ~/enigma_git/enigma-dev
java -jar lgm16b4.jar
```
...Note: on the first run, it will compile the necessary library code (took a couple of minutes on my system).

5. Try to load a project and see if it works. I'm sorry but I don't have any projects to test.

----------------------------------

Other notes: To update the git source code (to get the latest source updates):
```
cd ~/enigma_git/enigma-dev
git pull
```

---

### Post by gandalf3 on 2012-05-18
when i did ```
python install.py
```
i got

```
~/enigma_git/enigma-dev$ python install.py
Enigma package manager
Traceback (most recent call last):
  File "install.py", line 5, in <module>
    webFile = urllib.urlopen(url)
  File "/usr/local/lib/python2.7/urllib.py", line 86, in urlopen
    return opener.open(url)
  File "/usr/local/lib/python2.7/urllib.py", line 204, in open
    return self.open_unknown(fullurl, data)
  File "/usr/local/lib/python2.7/urllib.py", line 216, in open_unknown
    raise IOError, ('url error', 'unknown url type', type)
IOError: [Errno url error] unknown url type: 'https'

```
was that supposed to happen? (something tells me it wasn't..)

---

### Post by Toz on 2012-05-18
How have you installed python 2.7? It seems to be located in your /usr/local tree. The default python 2.7 install just goes in the /usr tree. 

What does the following return:
```
apt-cache policy python2.7
```

I think you may need to have python-httplib2 installed or python compiled with ssl support.

---

### Post by gandalf3 on 2012-05-19
```
python2.7:
  Installed: 2.7.2-5ubuntu1
  Candidate: 2.7.2-5ubuntu1
  Version table:
 *** 2.7.2-5ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Toz on 2012-05-19
Interesting. I'm also using oneiric and not getting this problem.

What does the following return?
```
which python
```
...and
```
which python2.7
```
...and
```
apt-cache policy python-httplib2
```

---

### Post by gandalf3 on 2012-05-19
```
which python
/usr/local/bin/python
```
```
which python2.7
/usr/local/bin/python2.7
```
```
apt-cache policy python-httplib2
python-httplib2:
  Installed: 0.7.2-1ubuntu2~0.11.10.1
  Candidate: 0.7.2-1ubuntu2~0.11.10.1
  Version table:
 *** 0.7.2-1ubuntu2~0.11.10.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main i386 Packages
        100 /var/lib/dpkg/status
     0.7.1-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
```

---

### Post by Toz on 2012-05-19
Why is your python in /usr/local/bin? Here is mine:
```
which python
/usr/bin/python
```

```
ls -l /usr/bin/python
lrwxrwxrwx 1 root root 9 2011-12-02 10:05 /usr/bin/python -> python2.7
```

Do you have python2.7-minimal installed?
```
apt-cache policy python2.7-minimal 
python2.7-minimal:
  Installed: 2.7.2-5ubuntu1
  Candidate: 2.7.2-5ubuntu1
  Version table:
 *** 2.7.2-5ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by gandalf3 on 2012-05-19
```
apt-cache policy python2.7-minimal 
python2.7-minimal:
  Installed: 2.7.2-5ubuntu1
  Candidate: 2.7.2-5ubuntu1
  Version table:
 *** 2.7.2-5ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status

```
```

ls -l /usr/bin/python
lrwxrwxrwx 1 root root 9 2012-03-02 16:00 /usr/bin/python -> python2.7

```
> 
Why is your python in /usr/local/bin?

no idea..
would it make a difference because i have IDLE (using python 3.2) installed?

---

### Post by Toz on 2012-05-20
For step #3, try this instead:
```
cd enigma-dev
/usr/bin/python install.py
```

If that still doesn't work, try to rename the python executables in /usr/local/bin:
```
sudo mv /usr/local/bin/python /usr/local/bin/python.BAK
sudo mv /usr/local/bin/python2.7 /usr/local/bin/python2.7.BAK
```

---

### Post by gandalf3 on 2012-05-20
```


/usr/bin/python install.py
Enigma package manager
Traceback (most recent call last):
  File "install.py", line 5, in <module>
    webFile = urllib.urlopen(url)
  File "/usr/lib/python2.7/urllib.py", line 84, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 435, in open_https
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 951, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 811, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 773, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 1154, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out

```
i don't know much about this.. i may be wrong, but to me it looks like that worked (except there was a network error)
so haven't tried ```
 sudo mv /usr/local/bin/python /usr/local/bin/python.BAK
sudo mv /usr/local/bin/python2.7 /usr/local/bin/python2.7.BAK 
```
yet..
also, when ever i try to load a web page by clicking on link, i get "aw, snap!" from chrome. (this just started happening now)do you think this is related?

---

### Post by Toz on 2012-05-20
> **gandalf3 said:**
> ```


/usr/bin/python install.py
Enigma package manager
Traceback (most recent call last):
  File "install.py", line 5, in <module>
    webFile = urllib.urlopen(url)
  File "/usr/lib/python2.7/urllib.py", line 84, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 435, in open_https
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 951, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 811, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 773, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 1154, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out

```
i don't know much about this.. i may be wrong, but to me it looks like that worked (except there was a network error)
I don't think so, because the install program downloads some patch files from a secure link and updates the program. Since it's crashing, I don't believe its completed successfully. And I believe your problem is that you have this secondary python install (that we are unsure of how it was installed), it is the default python, and it appears not to be able to handle secure network links.

> so haven't tried ```
 sudo mv /usr/local/bin/python /usr/local/bin/python.BAK
sudo mv /usr/local/bin/python2.7 /usr/local/bin/python2.7.BAK 
```
yet..
Maybe give it a try. You can always restore it by renaming the BAK files back to their original names. This will make the proper python the default python.

> also, when ever i try to load a web page by clicking on link, i get "aw, snap!" from chrome. (this just started happening now)do you think this is related?
I don't see how since you haven't really done anything other that try to build a program. How did you install chrome? Chroumium is in the repositories. Try running chrome from a terminal window to see if any error messages pop up.

---

### Post by gandalf3 on 2012-05-20
i restarted, and the "aw, snap!"s went away.
i ran it again:
```


/usr/bin/python install.py
Enigma package manager
Installing main please wait...
INFO: no dependencies for jnaJar
INFO: no dependencies for lgm
Finished updating main

```
is this right?
if not, i will try ```
  sudo mv /usr/local/bin/python /usr/local/bin/python.BAK
sudo mv /usr/local/bin/python2.7 /usr/local/bin/python2.7.BAK 
```
.
> 
I don't see how since you haven't really done anything other that try to build a program. How did you install chrome? Chroumium is in the repositories. Try running chrome from a terminal window to see if any error messages pop up. 
i thought it might be the cause, and not the effect.
i installed chrome from an apt link i got from clicking a "install chrome" button.
(now it's listed as a repository in the software center)
and i think there's a line for it in /etc/apt/sources.list now.

---

### Post by Toz on 2012-05-20
> **gandalf3 said:**
> i restarted, and the "aw, snap!"s went away.
i ran it again:
```


/usr/bin/python install.py
Enigma package manager
Installing main please wait...
INFO: no dependencies for jnaJar
INFO: no dependencies for lgm
Finished updating main

```
is this right?
Yes! It worked. Try step #4 to see if the program starts and works.

---

### Post by gandalf3 on 2012-05-20
YES! it did work!
started fine, but when i tried to run a game, (just a single object in a room with no events for a quick test) i got 
"```
 Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0x9246120
File version: -1

Incorrect version. File is too old for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [1]
Copying sound names [0]
Copying background names [0]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [1]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
1 Objects:
 obj_0: 12 events: 
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[3, 1.
Checking for default code in ev[8, 0.
Checking for default code in ev[100000, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm7728527283959174856.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
mkdir -p .eobjs/Linux/Linux/Run
mkdir -p .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL
mkdir -p .eobjs/Linux/Linux/Run/Collision_Systems/BBox
mkdir -p .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL
mkdir -p .eobjs/Linux/Linux/Run/Platforms/xlib
mkdir -p .eobjs/Linux/Linux/Run/Universal_System
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths
mkdir -p .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines
mkdir -p .eobjs/Linux/Linux/Run/Widget_Systems/None
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o Universal_System/Extensions/DataStructures/data_structures.cpp
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o Universal_System/Extensions/DateTime/date_time.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o Universal_System/Extensions/MotionPlanning/mp_movement.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o Universal_System/Extensions/MotionPlanning/motion_planning_struct.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o Universal_System/Extensions/MotionPlanning/motion_planning.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o Universal_System/Extensions/Paths/paths.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o Universal_System/Extensions/Timelines/timelines.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o Universal_System/Extensions/Alarms/alarmcode.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/zlib.o Universal_System/zlib.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o Universal_System/var4_lua.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/var4.o Universal_System/var4.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o Universal_System/transform_object.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o Universal_System/terminal_io.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o Universal_System/spritestruct.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o Universal_System/spriteinit.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o Universal_System/soundinit.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o Universal_System/simplecollisions.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o Universal_System/roomsystem.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o Universal_System/resource_data.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o Universal_System/reflexive_types.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o Universal_System/rectpack.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o Universal_System/planar_object.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o Universal_System/pathstruct.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o Universal_System/pathinit.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o Universal_System/path_functions.cpp
Universal_System/path_functions.cpp: In function &#8216;bool path_update()&#8217;:
Universal_System/path_functions.cpp:106:38: warning: unused variable &#8216;inst&#8217; [-Wunused-variable]
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/object.o Universal_System/object.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o Universal_System/multifunction_variant.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o Universal_System/move_functions.cpp
Universal_System/move_functions.cpp:102:49: fatal error: ..\Collision_Systems\BBox\coll_impl.h: No such file or directory
compilation terminated.
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o Universal_System/mathnc.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/loading.o Universal_System/loading.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o Universal_System/instance_system.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/instance.o Universal_System/instance.cpp
Universal_System/instance.cpp: In function &#8216;void instance_activate_object(int)&#8217;:
Universal_System/instance.cpp:75:93: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o Universal_System/IMGloading.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o Universal_System/highscore_functions.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o Universal_System/graphics_object.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o Universal_System/globalupdate.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o Universal_System/fontstruct.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o Universal_System/fontinit.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/fileio.o Universal_System/fileio.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/events.o Universal_System/events.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/estring.o Universal_System/estring.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o Universal_System/ENIGMA_GLOBALS.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o Universal_System/dynamic_args.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o Universal_System/depth_draw.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/darray.o Universal_System/darray.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o Universal_System/collisions_object.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o Universal_System/CallbackArrays.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o Universal_System/backgroundstruct.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o Universal_System/backgroundinit.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o Widget_Systems/None/nowidget_impl.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o Collision_Systems/BBox/placeholderlinks.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o Collision_Systems/BBox/coll_util.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o Collision_Systems/BBox/coll_impl.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o Collision_Systems/BBox/coll_funcs.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o Audio_Systems/OpenAL/wrap_oal.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o Audio_Systems/OpenAL/as_basic.cpp
Audio_Systems/OpenAL/as_basic.cpp:32:22: fatal error: AL/alure.h: No such file or directory
compilation terminated.
gcc -Wall -s -O3  -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o Graphics_Systems/OpenGL/glew.c
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o Graphics_Systems/OpenGL/OPENGLStd.cpp
Graphics_Systems/OpenGL/OPENGLStd.cpp: In function &#8216;void enigma::graphicssystem_initialize()&#8217;:
Graphics_Systems/OpenGL/OPENGLStd.cpp:36:12: warning: unused variable &#8216;err&#8217; [-Wunused-variable]
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o Graphics_Systems/OpenGL/GStextures.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o Graphics_Systems/OpenGL/GSsurface.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o Graphics_Systems/OpenGL/GSstdraw.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o Graphics_Systems/OpenGL/GSsprite.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o Graphics_Systems/OpenGL/GSscreen.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o Graphics_Systems/OpenGL/GSprmtvs.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o Graphics_Systems/OpenGL/GSmiscextra.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o Graphics_Systems/OpenGL/GSfont.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o Graphics_Systems/OpenGL/GSenable.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o Graphics_Systems/OpenGL/GSd3d.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o Graphics_Systems/OpenGL/GScurves.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o Graphics_Systems/OpenGL/GScolors.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o Graphics_Systems/OpenGL/GSblend.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSbackground.o Graphics_Systems/OpenGL/GSbackground.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBwindow.o Platforms/xlib/XLIBwindow.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBthreads.o Platforms/xlib/XLIBthreads.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBmain.o Platforms/xlib/XLIBmain.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBdialog.o Platforms/xlib/XLIBdialog.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/LINUXjoystick.o Platforms/xlib/LINUXjoystick.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Platforms/xlib/file_manip.o Platforms/xlib/file_manip.cpp
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:121:0:
Universal_System/instance_create.h: In function &#8216;void instance_change(int, bool)&#8217;:
Universal_System/instance_create.h:73:27: warning: variable &#8216;ob&#8217; set but not used [-Wunused-but-set-variable]
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/libEGMstd.o libEGMstd.cpp
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o Universal_System/move_functions.cpp
Universal_System/move_functions.cpp:102:49: fatal error: ..\Collision_Systems\BBox\coll_impl.h: No such file or directory
compilation terminated.
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o Audio_Systems/OpenAL/as_basic.cpp
Audio_Systems/OpenAL/as_basic.cpp:32:22: fatal error: AL/alure.h: No such file or directory
compilation terminated.
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
make: *** [Game] Error 2 
```"
and a "compile failed at c++ level".... :(

---

### Post by Toz on 2012-05-21
> AL/alure.h: No such file or directory
compilation terminated.
Do you have the alure libraries installed?
```
sudo apt-get install libalure-dev
```

---

### Post by Toz on 2012-05-21
Having a closer look at this. Have a look at this page: [http://enigma-dev.org/docs/Wiki/Linux#Dependencies]("http://enigma-dev.org/docs/Wiki/Linux#Dependencies"). Towards the bottom it lists the development dependencies that you need:
```
sudo apt-get install g++ zlib1g-dev libglu1-mesa-dev libalure-dev
```

However, after installing, I get some more error messages:
1. Error not finding "..\Collision_Systems\BBox\coll_impl.h"
Notice the backslashes in the error message. You need to edit line #102 of ...../enigma-dev/ENIGMAsystem/SHELL/Universal_System/move_functions.cpp and change the line to read:
```
#include "../Collision_Systems/BBox/coll_impl.h"
```

2. error about missing ldumb library. Apparently, you also need to install libaldmb1-dev
```
sudo apt-get install libaldmb1-dev
```

Now, I'm testing with the Balloon Pop example, and everything compiles properly, something pops up quickly, but I can't tell what it is. Anyways, the compilation works. 

I just tried a couple of examples, and they're doing the same. Found this error message:
```
*** glibc detected *** /tmp/egm3933348192477337969.tmp: malloc(): memory corruption: 0x08cb7e98 ***
```

I'll see what I can find.

---

### Post by Toz on 2012-05-21
Okay, I solved my problem for not being to able to run these games. It was related to the built in accelerometer in my HP laptop (for hard drive protection). Found the answer here: [http://enigma-dev.org/forums/index.php?topic=958.0]("http://enigma-dev.org/forums/index.php?topic=958.0").

In a nutshell:
```
sudo rm /dev/input/js0
```

And now everything works for me.

---

### Post by gandalf3 on 2012-05-21
after doing

```
sudo apt-get install libalure-dev
```

```
sudo apt-get install g++ zlib1g-dev libglu1-mesa-dev libalure-dev
```

> edit line #102 of ...../enigma-dev/ENIGMAsystem/SHELL/Universal_System/move_functions.cpp and change the line to read:

```
#include "../Collision_Systems/BBox/coll_impl.h"
```

```
sudo apt-get install libaldmb1-dev
```

i get
```
Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0x92e7520
File version: -1

Incorrect version. File is too old for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [1]
Copying sound names [0]
Copying background names [0]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [1]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
1 Objects:
 obj_0: 12 events: 
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[3, 1.
Checking for default code in ev[8, 0.
Checking for default code in ev[100000, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm9021464206644805234.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:121:0:
Universal_System/instance_create.h: In function ‘void instance_change(int, bool)’:
Universal_System/instance_create.h:73:27: warning: variable ‘ob’ set but not used [-Wunused-but-set-variable]
g++  -o /tmp/egm9021464206644805234.tmp .eobjs/Linux/Linux/Run/libEGMstd.o .eobjs/Linux/Linux/Run/SHELLmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/file_manip.o .eobjs/Linux/Linux/Run/Platforms/xlib/LINUXjoystick.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBdialog.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBthreads.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBwindow.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSbackground.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o .eobjs/Linux/Linux/Run/Universal_System/darray.o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o .eobjs/Linux/Linux/Run/Universal_System/estring.o .eobjs/Linux/Linux/Run/Universal_System/events.o .eobjs/Linux/Linux/Run/Universal_System/fileio.o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o .eobjs/Linux/Linux/Run/Universal_System/instance.o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o .eobjs/Linux/Linux/Run/Universal_System/loading.o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o .eobjs/Linux/Linux/Run/Universal_System/object.o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o .eobjs/Linux/Linux/Run/Universal_System/var4.o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o .eobjs/Linux/Linux/Run/Universal_System/zlib.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o  -lz -lpthread -lX11 -lGL -lGLU -lopenal -lalure -lvorbisfile -lvorbis -ldumb -lz
/usr/bin/ld: cannot find -lvorbisfile
/usr/bin/ld: cannot find -lvorbis
collect2: ld returned 1 exit status
make[1]: *** [/tmp/egm9021464206644805234.tmp] Error 1
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
make: *** [Game] Error 2

```
it seems it wants some 

"```
-lvorbis
```"

file/directory thing?
(lib?)
i haven't tried ```
sudo rm /dev/input/js0
``` because this sounds like a different problem..

---

### Post by Toz on 2012-05-21
Try:
```
sudo apt-get install libvorbis-dev
```

We're close...

---

### Post by gandalf3 on 2012-05-22
very close.
something popped up for second, then went away..
```
Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0x951c8d0
File version: 810

Incorrect version. File is too new for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [1]
Copying sound names [0]
Copying background names [0]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [1]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
1 Objects:
 obj_0: 12 events: 
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[3, 1.
Checking for default code in ev[8, 0.
Checking for default code in ev[100000, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm4305027386881877745.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:121:0:
Universal_System/instance_create.h: In function ‘void instance_change(int, bool)’:
Universal_System/instance_create.h:73:27: warning: variable ‘ob’ set but not used [-Wunused-but-set-variable]
g++  -o /tmp/egm4305027386881877745.tmp .eobjs/Linux/Linux/Run/libEGMstd.o .eobjs/Linux/Linux/Run/SHELLmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/file_manip.o .eobjs/Linux/Linux/Run/Platforms/xlib/LINUXjoystick.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBdialog.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBthreads.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBwindow.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSbackground.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o .eobjs/Linux/Linux/Run/Universal_System/darray.o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o .eobjs/Linux/Linux/Run/Universal_System/estring.o .eobjs/Linux/Linux/Run/Universal_System/events.o .eobjs/Linux/Linux/Run/Universal_System/fileio.o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o .eobjs/Linux/Linux/Run/Universal_System/instance.o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o .eobjs/Linux/Linux/Run/Universal_System/loading.o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o .eobjs/Linux/Linux/Run/Universal_System/object.o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o .eobjs/Linux/Linux/Run/Universal_System/var4.o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o .eobjs/Linux/Linux/Run/Universal_System/zlib.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o  -lz -lpthread -lX11 -lGL -lGLU -lopenal -lalure -lvorbisfile -lvorbis -ldumb -lz
+++++Make completed successfully.++++++++++++++++++++++++++++++++++++
Built to /tmp/egm4305027386881877745.tmp
1 Adding Sprites to Game Module: make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'

Done writing sprites.
Finalized sprites.
0 Sounds:
Done writing sounds.
0 Adding Backgrounds to Game Module: 
Done writing backgrounds.
1 Adding Fonts to Game Module: 
Done writing fonts.
0 Adding Paths to Game Module: 
Done writing paths.
Closing game module and running if requested.
Running "/tmp/egm4305027386881877745.tmp" 
Game returned 0
```

---

### Post by Toz on 2012-05-22
Same thing happened to me. The fix (for me) was:
```
sudo rm /dev/input/js0
```

The internal accelerometer on my laptop was being recognized as a joystick and crashing the app.

---

### Post by gandalf3 on 2012-05-22
hmm..
i do have a joystick connected..
is this the problem?
and after 
```

sudo rm /dev/input/js0 
```
will i still be able to use it with flightgear and other applications?

---

### Post by Toz on 2012-05-22
That command disables the built-in accelerometer, if you have one. AFAIK, it shouldn't affect the joystick. When you reboot your computer, the js0 interface will be re-created.

---

### Post by gandalf3 on 2012-05-22
well it worked!!
THANKS!
:)
will i have to sudo rm /dev/input/js0 every time after restarting the computer?

EDIT:
strange.. didn't think i had a acceleration.. custom build with older mobo... (system specs below)

---

### Post by Toz on 2012-05-22
> **gandalf3 said:**
> well it worked!!
THANKS!
:)Glad to hear.

> will i have to sudo rm /dev/input/js0 every time after restarting the computer?
Yes. Or, to do it permanently every time you boot your computer, add:
```

rm /dev/input/js0
```
...to **/etc/rc.local** _before_ the *exit 0* command. 

> EDIT:
strange.. didn't think i had a acceleration.. custom build with older mobo... (system specs below)
I knew I had it, but luckily someone in the enigma forums posted it as a fix to the crashing problem - so kudos to them.

---

### Post by gandalf3 on 2012-05-23
i don't have an accelerometer apparently..
it *was* my joystick that was causing the problem (after rm /dev/input/js0, my joystick seems to disappear) hmm.. do you have any idea
why this causes it not to run the game?

---

### Post by Toz on 2012-05-23
I'm sorry, but I don't know how to solve this problem since it's related directly to the code. Perhaps you should post this in the enigma-dev.org forums and see if the developers can offer some solutions.

---

### Post by gandalf3 on 2012-05-27
okay..
i also had problems running more complicated games..
is it something i did? or something else? (i can't figure it out..)

```

Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0x96de6f8
File version: 810

Incorrect version. File is too new for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [14]
Copying sound names [0]
Copying background names [2]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [12]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
12 Objects:
 wall1: 12 events: 
 you: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `you::create... Done. Parse... Done.
  Event[2]:   Parsing 1 sub-events:
Check `you::alarm_1... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `you::step... Done. Parse... Done.
  Event[4]:   Parsing 1 sub-events:
Check `you::collision_0... Done. Parse... Done.
  Event[5]:   Parsing 4 sub-events:
Check `you::keyboard_65... Done. Parse... Done.
Check `you::keyboard_68... Done. Parse... Done.
Check `you::keyboard_83... Done. Parse... Done.
Check `you::keyboard_87... Done. Parse... Done.
  Event[6]:   Parsing 1 sub-events:
Check `you::globalleftpress... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `you::keyrelease_87... Done. Parse... Done.
 enemy1: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `enemy1::step... Done. Parse... Done.
  Event[4]:   Parsing 1 sub-events:
Check `enemy1::collision_3... Done. Parse... Done.
 shell: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `shell::create... Done. Parse... Done.
  Event[1]:   Parsing 1 sub-events:
Check `shell::destroy... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `shell::step... Done. Parse... Done.
  Event[4]:   Parsing 2 sub-events:
Check `shell::collision_0... Done. Parse... Done.
Check `shell::collision_2... Done. Parse... Done.
 hole: 12 events: 
 turret: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `turret::step... Done. Parse... Done.
 object6: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object6::animationend... Done. Parse... Done.
 boom: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `boom::animationend... Done. Parse... Done.
 shrapnel: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `shrapnel::animationend... Done. Parse... Done.
 object9: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object9::animationend... Done. Parse... Done.
 enemybullit: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `enemybullit::create... Done. Parse... Done.
  Event[1]:   Parsing 1 sub-events:
Check `enemybullit::destroy... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `enemybullit::step... Done. Parse... Done.
  Event[4]:   Parsing 1 sub-events:
Check `enemybullit::collision_0... Done. Parse... Done.
 object12: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object12::animationend... Done. Parse... Done.
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[2, 1.
Checking for default code in ev[7, 7.
Checking for default code in ev[3, 1.
Checking for default code in ev[4, 0.
Checking for default code in ev[0, 0.
Checking for default code in ev[1, 0.
Checking for default code in ev[8, 0.
Checking for default code in ev[6, 53.
Checking for default code in ev[5, 87.
Checking for default code in ev[10, 87.
Checking for default code in ev[100000, 0.
Checking for default code in ev[3, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm4059029416915525350.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:100:0:
Preprocessor_Environment_Editable/IDE_EDIT_resourcenames.h:67:10: error: conflicting declaration &#8216;hole&#8217;
Preprocessor_Environment_Editable/IDE_EDIT_resourcenames.h:37:3: error: &#8216;hole&#8217; has a previous declaration as &#8216;<anonymous enum> hole&#8217;
Preprocessor_Environment_Editable/IDE_EDIT_resourcenames.h:68:11: error: conflicting declaration &#8216;shell&#8217;
Preprocessor_Environment_Editable/IDE_EDIT_resourcenames.h:36:3: error: &#8216;shell&#8217; has a previous declaration as &#8216;<anonymous enum> shell&#8217;
make[1]: *** [.eobjs/Linux/Linux/Run/SHELLmain.o] Error 1
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
make: *** [Game] Error 2 
```
"compile failed at C++ level"
and this:

```

Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0xb52b9d8
File version: 810

Incorrect version. File is too new for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [20]
Copying sound names [0]
Copying background names [2]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [22]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
22 Objects:
 object0_island1: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object0_island1::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object0_island1::step... Done. Parse... Done.
 object1_island2: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object1_island2::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object1_island2::step... Done. Parse... Done.
 object2_island3: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object2_island3::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object2_island3::step... Done. Parse... Done.
 obj_enterprise: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `obj_enterprise::create... Done. Parse... Done.
  Event[2]:   Parsing 1 sub-events:
Check `obj_enterprise::alarm_0... Done. Parse... Done.
  Event[5]:   Parsing 4 sub-events:
Check `obj_enterprise::keyboard_37... Done. Parse... Done.
Check `obj_enterprise::keyboard_38... Done. Parse... Done.
Check `obj_enterprise::keyboard_39... Done. Parse... Done.
Check `obj_enterprise::keyboard_40... Done. Parse... Done.
  Event[6]:   Parsing 1 sub-events:
Check `obj_enterprise::globalrightbutton... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `obj_enterprise::outsideroom... Done. Parse... Done.
 object4: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object4::create... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `object4::outsideroom... Done. Parse... Done.
 object5: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object5::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object5::step... Done. Parse... Done.
  Event[4]:   Parsing 2 sub-events:
Check `object5::collision_3... Done. Parse... Done.
Check `object5::collision_4... Done. Parse... Done.
 object6_blow1: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object6_blow1::animationend... Done. Parse... Done.
 object7_blowx: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object7_blowx::animationend... Done. Parse... Done.
 mastermind: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `mastermind::create... Done. Parse... Done.
  Event[2]:   Parsing 1 sub-events:
Check `mastermind::alarm_0... Done. Parse... Done.
 plasma: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `plasma::animationend... Done. Parse... Done.
 xwing: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `xwing::create... Done. Parse... Done.
  Event[2]:   Parsing 5 sub-events:
Check `xwing::alarm_0... Done. Parse... Done.
Check `xwing::alarm_2... Done. Parse... Done.
Check `xwing::alarm_3... Done. Parse... Done.
Check `xwing::alarm_4... Done. Parse... Done.
Check `xwing::alarm_5... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `xwing::step... Done. Parse... Done.
  Event[5]:   Parsing 6 sub-events:
Check `xwing::keyboard_32... Done. Parse... Done.
Check `xwing::keyboard_65... Done. Parse... Done.
Check `xwing::keyboard_68... Done. Parse... Done.
Check `xwing::keyboard_83... Done. Parse... Done.
Check `xwing::keyboard_87... Done. Parse... Done.
Check `xwing::keyboard_88... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `xwing::outsideroom... Done. Parse... Done.
  Event[9]:   Parsing 2 sub-events:
Check `xwing::keypress_66... Done. Parse... Done.
Check `xwing::keypress_86... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `xwing::keyrelease_87... Done. Parse... Done.
 star_destroyer: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `star_destroyer::step... Done. Parse... Done.
 saturnV: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `saturnV::step... Done. Parse... Done.
  Event[5]:   Parsing 3 sub-events:
Check `saturnV::keyboard_37... Done. Parse... Done.
Check `saturnV::keyboard_38... Done. Parse... Done.
Check `saturnV::keyboard_39... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `saturnV::outsideroom... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `saturnV::keyrelease_38... Done. Parse... Done.
 object13: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object13::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object13::step... Done. Parse... Done.
 photontrailer: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `photontrailer::animationend... Done. Parse... Done.
 lasers_xwing: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `lasers_xwing::create... Done. Parse... Done.
 missile: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `missile::create... Done. Parse... Done.
  Event[2]:   Parsing 2 sub-events:
Check `missile::alarm_0... Done. Parse... Done.
Check `missile::alarm_1... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `missile::step... Done. Parse... Done.
 misle_3: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `misle_3::animationend... Done. Parse... Done.
 X_engine_gook: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `X_engine_gook::animationend... Done. Parse... Done.
 object19: 12 events: 
  Event[2]:   Parsing 1 sub-events:
Check `object19::alarm_11... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object19::step... Done. Parse... Done.
 flcon: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `flcon::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `flcon::step... Done. Parse... Done.
  Event[5]:   Parsing 3 sub-events:
Check `flcon::keyboard_37... Done. Parse... Done.
Check `flcon::keyboard_38... Done. Parse... Done.
Check `flcon::keyboard_39... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `flcon::keyrelease_38... Done. Parse... Done.
 object22: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object22::animationend... Done. Parse... Done.
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[2, 11.
Checking for default code in ev[7, 7.
Checking for default code in ev[3, 1.
Checking for default code in ev[4, 4.
Checking for default code in ev[0, 0.
Checking for default code in ev[8, 0.
Checking for default code in ev[6, 51.
Checking for default code in ev[5, 39.
Checking for default code in ev[9, 86.
Checking for default code in ev[10, 38.
Checking for default code in ev[100000, 0.
Checking for default code in ev[7, 0.
Checking for default code in ev[3, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm2710485197265476392.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:121:0:
Universal_System/instance_create.h: In function &#8216;void instance_change(int, bool)&#8217;:
Universal_System/instance_create.h:73:27: warning: variable &#8216;ob&#8217; set but not used [-Wunused-but-set-variable]
background.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o .eobjs/Linux/Linux/Run/Universal_System/darray.o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o .eobjs/Linux/Linux/Run/Universal_System/estring.o .eobjs/Linux/Linux/Run/Universal_System/events.o .eobjs/Linux/Linux/Run/Universal_System/fileio.o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o .eobjs/Linux/Linux/Run/Universal_System/instance.o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o .eobjs/Linux/Linux/Run/Universal_System/loading.o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o .eobjs/Linux/Linux/Run/Universal_System/object.o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o .eobjs/Linux/Linux/Run/Universal_System/var4.o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o .eobjs/Linux/Linux/Run/Universal_System/zlib.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o  -lz -lpthread -lX11 -lGL -lGLU -lopenal -lalure -lvorbisfile -lvorbis -ldumb -lz
g++  -o /tmp/egm2710485197265476392.tmp .eobjs/Linux/Linux/Run/libEGMstd.o .eobjs/Linux/Linux/Run/SHELLmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/file_manip.o .eobjs/Linux/Linux/Run/Platforms/xlib/LINUXjoystick.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBdialog.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBthreads.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBwindow.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSbackground.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o .eobjs/Linux/Linux/Run/Universal_System/darray.o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o .eobjs/Linux/Linux/Run/Universal_System/estring.o .eobjs/Linux/Linux/Run/Universal_System/events.o .eobjs/Linux/Linux/Run/Universal_System/fileio.o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o .eobjs/Linux/Linux/Run/Universal_System/instance.o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o .eobjs/Linux/Linux/Run/Universal_System/loading.o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o .eobjs/Linux/Linux/Run/Universal_System/object.o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o .eobjs/Linux/Linux/Run/Universal_System/var4.o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o .eobjs/Linux/Linux/Run/Universal_System/zlib.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o  -lz -lpthread -lX11 -lGL -lGLU -lopenal -lalure -lvorbisfile -lvorbis -ldumb -lz
+++++Make completed successfully.++++++++++++++++++++++++++++++++++++
20 Adding Sprites to Game Module: 
Subimages of sprite `sprite23' have zero size.
Built to /tmp/egm2710485197265476392.tmp
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
Built to /tmp/egm2710485197265476392.tmp
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'

``` "error occurred. see scroll back for details
all help appreciated..

---

### Post by Toz on 2012-05-29
Yes, I ran into similar problems with some of the demo games I tried. I believe the problem is with the game and needs to be fixed in the code. 

Which games/programs are they? Can you post links to the code?

---

### Post by gandalf3 on 2012-05-30
i don't think so.. i made these ones..
but i did find some errors, and when i fixed them, i got a window to pop up for a second, but then it went away..

a lot like what happened before i removed the js0 input thing.
here's the output:
```

Building for mode (0)
Cleaning up from previous executions
Location in memory of structure: 0x9d30db0
File version: 810

Incorrect version. File is too new for this compiler. Continuing anyway, because this number is always wrong.COPYING SOME F*CKING RESOURCES:
Copying sprite names [19]
Copying sound names [0]
Copying background names [2]
Copying path names [0]
Copying script names [0]
Copying font names [1]
Copying timeline names [kidding, these are totally not implemented :P] [0]
Copying object names [20]
Copying room names [1]
SYNTAX CHECKING AND PRIMARY PARSING:
0 Scripts:
"Linking" scripts
`Linking' 0 scripts in 0 passes...
Completing script "Link"
Done.
20 Objects:
 object2_island3: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object2_island3::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object2_island3::step... Done. Parse... Done.
 obj_enterprise: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `obj_enterprise::create... Done. Parse... Done.
  Event[2]:   Parsing 1 sub-events:
Check `obj_enterprise::alarm_0... Done. Parse... Done.
  Event[5]:   Parsing 4 sub-events:
Check `obj_enterprise::keyboard_37... Done. Parse... Done.
Check `obj_enterprise::keyboard_38... Done. Parse... Done.
Check `obj_enterprise::keyboard_39... Done. Parse... Done.
Check `obj_enterprise::keyboard_40... Done. Parse... Done.
  Event[6]:   Parsing 1 sub-events:
Check `obj_enterprise::globalrightbutton... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `obj_enterprise::outsideroom... Done. Parse... Done.
 object4: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object4::create... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `object4::outsideroom... Done. Parse... Done.
 object5: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object5::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object5::step... Done. Parse... Done.
  Event[4]:   Parsing 1 sub-events:
Check `object5::collision_4... Done. Parse... Done.
 object6_blow1: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object6_blow1::animationend... Done. Parse... Done.
 object7_blowx: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object7_blowx::animationend... Done. Parse... Done.
 mastermind: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `mastermind::create... Done. Parse... Done.
  Event[2]:   Parsing 1 sub-events:
Check `mastermind::alarm_0... Done. Parse... Done.
 plasma: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `plasma::animationend... Done. Parse... Done.
 xwing: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `xwing::create... Done. Parse... Done.
  Event[2]:   Parsing 5 sub-events:
Check `xwing::alarm_0... Done. Parse... Done.
Check `xwing::alarm_2... Done. Parse... Done.
Check `xwing::alarm_3... Done. Parse... Done.
Check `xwing::alarm_4... Done. Parse... Done.
Check `xwing::alarm_5... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `xwing::step... Done. Parse... Done.
  Event[5]:   Parsing 6 sub-events:
Check `xwing::keyboard_32... Done. Parse... Done.
Check `xwing::keyboard_65... Done. Parse... Done.
Check `xwing::keyboard_68... Done. Parse... Done.
Check `xwing::keyboard_83... Done. Parse... Done.
Check `xwing::keyboard_87... Done. Parse... Done.
Check `xwing::keyboard_88... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `xwing::outsideroom... Done. Parse... Done.
  Event[9]:   Parsing 2 sub-events:
Check `xwing::keypress_66... Done. Parse... Done.
Check `xwing::keypress_86... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `xwing::keyrelease_87... Done. Parse... Done.
 star_destroyer: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `star_destroyer::step... Done. Parse... Done.
 saturnV: 12 events: 
  Event[3]:   Parsing 1 sub-events:
Check `saturnV::step... Done. Parse... Done.
  Event[5]:   Parsing 3 sub-events:
Check `saturnV::keyboard_37... Done. Parse... Done.
Check `saturnV::keyboard_38... Done. Parse... Done.
Check `saturnV::keyboard_39... Done. Parse... Done.
  Event[7]:   Parsing 1 sub-events:
Check `saturnV::outsideroom... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `saturnV::keyrelease_38... Done. Parse... Done.
 object13: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `object13::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object13::step... Done. Parse... Done.
 photontrailer: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `photontrailer::animationend... Done. Parse... Done.
 lasers_xwing: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `lasers_xwing::create... Done. Parse... Done.
 missile: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `missile::create... Done. Parse... Done.
  Event[2]:   Parsing 2 sub-events:
Check `missile::alarm_0... Done. Parse... Done.
Check `missile::alarm_1... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `missile::step... Done. Parse... Done.
 misle_3: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `misle_3::animationend... Done. Parse... Done.
 X_engine_gook: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `X_engine_gook::animationend... Done. Parse... Done.
 object19: 12 events: 
  Event[2]:   Parsing 1 sub-events:
Check `object19::alarm_11... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `object19::step... Done. Parse... Done.
 flcon: 12 events: 
  Event[0]:   Parsing 1 sub-events:
Check `flcon::create... Done. Parse... Done.
  Event[3]:   Parsing 1 sub-events:
Check `flcon::step... Done. Parse... Done.
  Event[5]:   Parsing 3 sub-events:
Check `flcon::keyboard_37... Done. Parse... Done.
Check `flcon::keyboard_38... Done. Parse... Done.
Check `flcon::keyboard_39... Done. Parse... Done.
  Event[10]:   Parsing 1 sub-events:
Check `flcon::keyrelease_38... Done. Parse... Done.
 object22: 12 events: 
  Event[7]:   Parsing 1 sub-events:
Check `object22::animationend... Done. Parse... Done.
Creating room creation code scope and parsing
"Linking" scripts into the objects...
"Link" complete.
Tabulating maximum argument passes to each script
Finished
Writing modes and settings
Writing object switch
Writing resource names and maxima
Writing events
Checking for default code in ev[2, 11.
Checking for default code in ev[7, 7.
Checking for default code in ev[3, 1.
Checking for default code in ev[4, 4.
Checking for default code in ev[0, 0.
Checking for default code in ev[8, 0.
Checking for default code in ev[6, 51.
Checking for default code in ev[5, 39.
Checking for default code in ev[9, 86.
Checking for default code in ev[10, 38.
Checking for default code in ev[100000, 0.
Checking for default code in ev[7, 0.
Checking for default code in ev[3, 0.
Linking globals
Running Secondary Parse Passes
Writing object data
Writing local accessors
Writing font data
Writing room data
Running make from `make'
Full command line: make Game GMODE=Run GRAPHICS=OpenGL AUDIO=OpenAL COLLISION=BBox WIDGETS=None PLATFORM=xlib CXX=g++ CC=gcc COMPILEPATH=Linux/Linux EXTENSIONS=" Universal_System/Extensions/Alarms Universal_System/Extensions/Timelines Universal_System/Extensions/Paths Universal_System/Extensions/MotionPlanning Universal_System/Extensions/DateTime Universal_System/Extensions/DataStructures" OUTPUTNAME="/tmp/egm1769194842232591405.tmp" eTCpath=""
/usr/bin/make -C ENIGMAsystem/SHELL
make[1]: Entering directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
g++ -Wall -s -O3 -IPlatforms/xlib/Info -IGraphics_Systems/OpenGL/Info -IAudio_Systems/OpenAL/Info -ICollision_Systems/BBox/Info -IWidget_Systems/None/Info -IUniversal_System/Info -I.  -MMD -MP -c -o .eobjs/Linux/Linux/Run/SHELLmain.o SHELLmain.cpp
In file included from SHELLmain.cpp:121:0:
Universal_System/instance_create.h: In function &#8216;void instance_change(int, bool)&#8217;:
Universal_System/instance_create.h:73:27: warning: variable &#8216;ob&#8217; set but not used [-Wunused-but-set-variable]
g++  -o /tmp/egm1769194842232591405.tmp .eobjs/Linux/Linux/Run/libEGMstd.o .eobjs/Linux/Linux/Run/SHELLmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/file_manip.o .eobjs/Linux/Linux/Run/Platforms/xlib/LINUXjoystick.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBdialog.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBmain.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBthreads.o .eobjs/Linux/Linux/Run/Platforms/xlib/XLIBwindow.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSbackground.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSblend.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScolors.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GScurves.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSd3d.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSenable.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSfont.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSmiscextra.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSprmtvs.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSscreen.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsprite.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSstdraw.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GSsurface.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/GStextures.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/OPENGLStd.o .eobjs/Linux/Linux/Run/Graphics_Systems/OpenGL/glew.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/as_basic.o .eobjs/Linux/Linux/Run/Audio_Systems/OpenAL/wrap_oal.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_funcs.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_impl.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/coll_util.o .eobjs/Linux/Linux/Run/Collision_Systems/BBox/placeholderlinks.o .eobjs/Linux/Linux/Run/Widget_Systems/None/nowidget_impl.o .eobjs/Linux/Linux/Run/Universal_System/backgroundinit.o .eobjs/Linux/Linux/Run/Universal_System/backgroundstruct.o .eobjs/Linux/Linux/Run/Universal_System/CallbackArrays.o .eobjs/Linux/Linux/Run/Universal_System/collisions_object.o .eobjs/Linux/Linux/Run/Universal_System/darray.o .eobjs/Linux/Linux/Run/Universal_System/depth_draw.o .eobjs/Linux/Linux/Run/Universal_System/dynamic_args.o .eobjs/Linux/Linux/Run/Universal_System/ENIGMA_GLOBALS.o .eobjs/Linux/Linux/Run/Universal_System/estring.o .eobjs/Linux/Linux/Run/Universal_System/events.o .eobjs/Linux/Linux/Run/Universal_System/fileio.o .eobjs/Linux/Linux/Run/Universal_System/fontinit.o .eobjs/Linux/Linux/Run/Universal_System/fontstruct.o .eobjs/Linux/Linux/Run/Universal_System/globalupdate.o .eobjs/Linux/Linux/Run/Universal_System/graphics_object.o .eobjs/Linux/Linux/Run/Universal_System/highscore_functions.o .eobjs/Linux/Linux/Run/Universal_System/IMGloading.o .eobjs/Linux/Linux/Run/Universal_System/instance.o .eobjs/Linux/Linux/Run/Universal_System/instance_system.o .eobjs/Linux/Linux/Run/Universal_System/loading.o .eobjs/Linux/Linux/Run/Universal_System/mathnc.o .eobjs/Linux/Linux/Run/Universal_System/move_functions.o .eobjs/Linux/Linux/Run/Universal_System/multifunction_variant.o .eobjs/Linux/Linux/Run/Universal_System/object.o .eobjs/Linux/Linux/Run/Universal_System/path_functions.o .eobjs/Linux/Linux/Run/Universal_System/pathinit.o .eobjs/Linux/Linux/Run/Universal_System/pathstruct.o .eobjs/Linux/Linux/Run/Universal_System/planar_object.o .eobjs/Linux/Linux/Run/Universal_System/rectpack.o .eobjs/Linux/Linux/Run/Universal_System/reflexive_types.o .eobjs/Linux/Linux/Run/Universal_System/resource_data.o .eobjs/Linux/Linux/Run/Universal_System/roomsystem.o .eobjs/Linux/Linux/Run/Universal_System/simplecollisions.o .eobjs/Linux/Linux/Run/Universal_System/soundinit.o .eobjs/Linux/Linux/Run/Universal_System/spriteinit.o .eobjs/Linux/Linux/Run/Universal_System/spritestruct.o .eobjs/Linux/Linux/Run/Universal_System/terminal_io.o .eobjs/Linux/Linux/Run/Universal_System/transform_object.o .eobjs/Linux/Linux/Run/Universal_System/var4.o .eobjs/Linux/Linux/Run/Universal_System/var4_lua.o .eobjs/Linux/Linux/Run/Universal_System/zlib.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Alarms/alarmcode.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Timelines/timelines.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/Paths/paths.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/motion_planning_struct.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/MotionPlanning/mp_movement.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DateTime/date_time.o .eobjs/Linux/Linux/Run/Universal_System/Extensions/DataStructures/data_structures.o  -lz -lpthread -lX11 -lGL -lGLU -lopenal -lalure -lvorbisfile -lvorbis -ldumb -lz
+++++Make completed successfully.++++++++++++++++++++++++++++++++++++
19 Adding Sprites to Game Module: 
Done writing sprites.
Finalized sprites.
0 Sounds:
Done writing sounds.
2 Adding Backgrounds to Game Module: 
Done writing backgrounds.
1 Adding Fonts to Game Module: 
Done writing fonts.
0 Adding Paths to Game Module: 
Done writing paths.
Closing game module and running if requested.
Running "/tmp/egm1769194842232591405.tmp" 
Built to /tmp/egm1769194842232591405.tmp
make[1]: Leaving directory `/home/ellwood/enigma_git/enigma-dev/ENIGMAsystem/SHELL'
Game returned 0 
```

---

### Post by Toz on 2012-05-31
The log file looks mostly okay except for the last statement - its like the game is closing itself. Perhaps it would be best to ask on the enigma forums. I don't have any experience with actually coding in this environment.

---

### Post by gandalf3 on 2012-06-02
well... after a lot of Googleing, i found this: [URL="http://enigma-dev.org/forums/index.php?topic=550.0"]http://enigma-dev.org/forums/index.php?topic=550.0
[/URL]but I'm not even sure if that is like the problem I'm having.. but "If the game seems to compile but closes immediately on run, it probably segfaulted" sounds like it to me.
only i have no clue what they are talking about at all...:confused:

---

