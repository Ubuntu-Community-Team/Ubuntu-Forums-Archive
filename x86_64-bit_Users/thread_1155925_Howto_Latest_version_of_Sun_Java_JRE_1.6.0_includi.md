---
title: "Howto: Latest version of Sun Java JRE 1.6.0 including Firefox Browser Plugin"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by slayer^_^ on 2009-05-11
Some choose to install the official Sun version of Java JRE (for a better compatibility with some websites), now it's possible to download and installa a good 64 bit version of it, including a nice plugin for Firefox Browser (and others like Opera), and set it as default. That's what I did (and I didn't encounter any problem).

**If you are using Ubuntu 9.04 Jaunty Jackalope**

Then the task is really simple... just write in the terminal:

```
sudo apt-get install sun-java6-plugin
```

to install Sun Java JRE 1.6.0 u13 and its plugin, and then:

```
sudo apt-get remove --purge icedtea-gcjwebplugin icedtea6-plugin icedtea-6-jre-cacao
```[/CODE]

to remove the IcedTea plugin that would prevent Firefox to use the Sun plugin.

By visiting the webpage [about:plugins]("about:plugins") on Firefox, you can see which Java plugin you're using (and if there are any other different Java plugins that you're using instead of the Sun one)

Then reboot Firefox and everything is done.


**If you are using older versions of Ubuntu (f.e. Ubuntu 8.10 Intrepid Ibex of Ubuntu 8.04 LTS Hardy Heron)**

This is very easy, let's go:

**Install Java SE Runtime Environment 6u13 and set is as default**

1) Download Java SE Runtime Environment 6u13

At the time of writing this howto, it is possible to download the .bin file (64 bit version) [here]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/VerifyItem-Start/jre-6u13-linux-x64.bin?BundledLineItemUUID=vXZIBe.pmWYAAAEhdCQkty.6&OrderID=SvBIBe.pUHoAAAEhXCQkty.6&ProductID=qWZIBe.o7LAAAAEfC3kcytQc&FileName=/jre-6u13-linux-x64.bin") or [here]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=29214") and put it on your Desktop.

2) Create the right directories (usually they're not present)

```
cd /opt
sudo mkdir java
cd java
sudo mkdir 64
```

3) Move the downloaded file to the created directory and make it executable:

```
sudo mv ~/Desktop/jre-6u13-linux-x64.bin /opt/java/64
sudo chmod 755 /opt/java/64/jre-6u13-linux-x64.bin
```

note: If you're using an Ubuntu non-english version, the path may be different. For example, the path in the italian version is different and the related code is: 

```
sudo mv ~/Scrivania/jre-6u13-linux-x64.bin /opt/java/64 
```

4) Execute the now-executable .bin file:

```
cd /opt/java/64
sudo ./jre-6u13-linux-x64.bin
```

Regardless of architecture, this should create a sub directory called jre1.6.0_13 .

5) Set JRE 1.6.0 u13 as Default

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_13/bin/java" 1
sudo update-alternatives --set java /opt/java/64/jre1.6.0_13/bin/java 
```

The above commands should give this output:

Using '/opt/java/64/jre1.6.0_13/bin/java' to provide 'java'.

6) Check if everything is OK:

```
java -version
```

The output should be like this one:

java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

Now everytime the java binary is needed, the one (more recent) you've installed should be used instead of the default one. 


**Now let's install the Firefox Plugin**:


1) Remove previous Java installations like IcedTea (if you&#8217;re upgrading from a previous JRE install, remove the old plugin first):

```
sudo apt-get remove --purge icedtea-gcjwebplugin icedtea6-plugin icedtea-6-jre-cacao
rm ~/.mozilla/plugins/libnpjp2.so
```

2) Install the new plugin. Do this _by creating a symbolic link_:

If you put the symbolic link in the /usr/lib/mozilla/plugins/ folder, it will be available for all the users:

```
sudo ln -s /opt/java/64/jre1.6.0_13/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
```

If you put the symbolic link in the ~/.mozilla/plugins/ folder, it will be available only for the current user:

```
sudo ln -s /opt/java/64/jre1.6.0_13/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

_Don't copy the file directly in the plugins folder, or Mozilla will crash any time you will try to ope a webpage with Java content !!_

4) Restart Firefox (or Opera)

5) The new installed plugin should result in the [about:plugins]("about:plugins") webpage


I am checking now and it works perfectly.

Any troubles? I'm here ^__^

---

### Post by jespdj on 2009-05-11
This is not necessary, because the Sun Java 6 update 13 64-bit browser plug-in is available in the Jaunty repository, so the only thing you have to do is install the package **sun-java6-plugin**:
```
sudo apt-get install sun-java6-plugin
```
It is not necessary to manually download and install it. You're making it seem much more complicated than necessary...

---

### Post by slayer^_^ on 2009-05-11
BUMP... I'm checking and you're right!

---

### Post by CooksWithFire on 2009-05-11
I received this at step 6. 

joe@joe-desktop:/opt/java/64$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: version. Program will exit.


I havent been able to get java set up, I have followed about 16 install guides to no avail

Any help would be appreciated, Joe

---

### Post by MakotoTheKnight on 2009-05-12
Try java -version, with the hyphen before the version, like so:

java -version

It should work.  The very fact that it spat out a NoClassDefFoundError should indicate that Java is installed.

---

### Post by jespdj on 2009-05-12
> **CooksWithFire said:**
> I havent been able to get java set up, I have followed about 16 install guides to no avail

Any help would be appreciated, Joe
Did you read what I wrote? :rolleyes:

Stop trying to do it the hard way and just install sun-java6-plugin:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by banduan on 2009-05-12
> **jespdj said:**
> This is not necessary, because the Sun Java 6 update 13 64-bit browser plug-in is available in the Jaunty repository, so the only thing you have to do is install the package **sun-java6-plugin**:
OTOH, not everyone has Jaunty

---

### Post by slayer^_^ on 2009-05-12
Indeed that's why I've written this HowTo, not everybody uses Jaunty...

Now I've specified that if you're using Jaunty you just got to install the package and if you're using older ubuntu versions you can follow the manual procedure.

Again, if a newer version of Java comes out (f.e. 1.6.0 **u14**), this howto will be useful for those who don't want to wait for the repositories to be updated.

Please notice that many people need **absolutely** a working-like-a-charm Java applet, for exaple for uploading pictures with the most common social network websites. It's hard for some to switch to Linux if their Firefox crashes doing things like these or simply doesn't allow them to upload pictures as-windows-does .

Sun Java JRE 1.6.0. **u13** solves most (not all) of this bugs, so please understand my efforts in providing it in the most simple way for 64-bit users _who don't use Jaunty Jackalope_.

Ok?

---

### Post by slayer^_^ on 2009-05-12
> **CooksWithFire said:**
> I received this at step 6. 

joe@joe-desktop:/opt/java/64$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: version. Program will exit.


I havent been able to get java set up, I have followed about 16 install guides to no avail

Any help would be appreciated, Joe


Dear Joe, this is the problem:

**joe@joe-desktop:/opt/java/64$ java version**

As specified above, the right command is:

```
java -version
```

Let us know if you still got troubles! :)

---

### Post by istblacken on 2009-05-12
works great ! although i am using Jaunty i still used the manual way because i like to do things on my own lol thanks for the guide :D

---

### Post by Ender985 on 2009-05-18
Worked like a charm for my Ibex distribution, lots of thanks!

---

### Post by slayer^_^ on 2009-05-18
...de nada :D

---

### Post by Daniel TL on 2009-05-21
Muchas gracias! Hice todo lo que explicás y ahora tengo Java en mi Firefox :p

Tengo Hardy Heron 64 bits (8.04.2) y Firefox 3.0.10


Sorry, I don't know type in English :(

---

### Post by slayer^_^ on 2009-05-21
no problemo amigo... es un plesir aiudarde :D

---

### Post by CooksWithFire on 2009-05-21
Yup, fixed the problem, Thanks!

BTW if I have to hit the 'Test' button in Sys>Pref>Sound>Capture everytime I start a flash player is that a problem with my flash or sound? 
Thanks, Joe

---

### Post by slayer^_^ on 2009-05-22
> **CooksWithFire said:**
> Yup, fixed the problem, Thanks!

BTW if I have to hit the 'Test' button in Sys>Pref>Sound>Capture everytime I start a flash player is that a problem with my flash or sound? 
Thanks, Joe

1) Flash player and Java are totally different softwares and take care of totally different kind of files...

2) If you're using (as yo ushould because this thread is in the 64-bit section) a 64-bit processor, try installing the 64 bit flash player for linux (you got to do it manually, elseway the automatic installation will install you a 32-bit version modified to work on 64 bit architecture, it works way too buggy..) following this guide I've written: [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

3)If installing the 64 bit version of flash player doesn't solve the trick, You should think about audio card bad configuration.

Cheers !!

---

### Post by OriTheEep on 2009-05-25
Oops!

Spot of trouble: my terminal window changed and I was instead presented with a windowed DOS-like screen and no obvious way of proceeding. There was an <OK> at the bottom of it but this wasn't a hot spot for the mouse nor did hitting <enter> help. Eventually I had to close the terminal window, despite protestations that there was still activity, and reboot.

Trying the "sudo apt-get install sun-java6-plugin" command again gave me:
[INDENT]tom@server:~$[COLOR=Red] sudo apt-get install sun-java6-plugin[/COLOR]
[sudo] password for tom: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/INDENT]Wondering if an interrupted installati0on could be reversed, I tried:
[INDENT]tom@server:~$[COLOR=Red] sudo apt-get remove sun-java6-plugin[/COLOR]
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/INDENT]so I did:
[INDENT]tom@server:~$ [COLOR=Red]sudo dpkg --configure -a[/COLOR]
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
[/INDENT]and followed, as per instructions, with:
[INDENT]tom@server:~$ [COLOR=Red]sudo apt-get remove icedtea-gcjwebplugin[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea-gcjwebplugin is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  sun-java6-jre: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-13-1) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/INDENT]and I think I'd better stop there and yell for help:
[INDENT]tom@server:~$ [SIZE=7][COLOR=Red]HELP![/COLOR][/SIZE]
[/INDENT]A look at the page that's all about plugins shows no mention of the word "java".

Looks like I wazzed up!

:(

---

### Post by pixel :-) on 2009-05-25
At the end of the last try it says

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

so 

sudo apt-get -f install

And don't follow what it says
just do

sudo apt-get install sun-java6-plugin ia32-sun-java6-bin

it will install java 32 bit from sun, and 64 bit plugin from sun. This gives the maximum compatibility right now

---

### Post by OriTheEep on 2009-05-25
> **pixel :-) said:**
> At the end of the last try it says

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

so 

sudo apt-get -f install

And don't follow what it says
just do

sudo apt-get install sun-java6-plugin ia32-sun-java6-bin

it will install java 32 bit from sun, and 64 bit plugin from sun. This gives the maximum compatibility right now

I can't show you terminal's response to "apt-get -f install" because it is all hidden behind the DOS-type screen attached. Any ideas how to get past this?

---

### Post by slayer^_^ on 2009-05-25
Yep you messed up something in terminal and the installation hasn't been completed (missing dependencies).

So, do this:

1) Once again...

```
sudo dpkg --configure -a
```

2) Now that everything should be fixed, try installing the package sun-java6-plugin from Synaptic Package Manager and tell us if there are any errors.. It should install dependencies automatically, in a maybe simpler way than terminal does :)

Feel free to post your experience here...

---

### Post by OriTheEep on 2009-05-25
> **slayer^_^ said:**
> Yep you messed up something in terminal and the installation hasn't been completed (missing dependencies).

So, do this:

1) Once again...

```
sudo dpkg --configure -a
```2) Now that everything should be fixed, try installing the package sun-java6-plugin from Synaptic Package Manager and tell us if there are any errors.. It should install dependencies automatically, in a maybe simpler way than terminal does :)

Feel free to post your experience here...

Thanks to pixel :-) :D and, slayer^_^, you did it again [IMG]http://www.smilies-and-more.de/pics/smilies/cool/054.gif[/IMG]

Real player next but I'm going to have a lie down first!

[IMG]http://www.smilies-and-more.de/pics/smilies/ill/022.gif[/IMG]

---

### Post by slayer^_^ on 2009-05-25
> **OriTheEep said:**
> Thanks to pixel :-) :D and, slayer^_^, you did it again [IMG]http://www.smilies-and-more.de/pics/smilies/cool/054.gif[/IMG]

Real player next but I'm going to have a lie down first!

[IMG]http://www.smilies-and-more.de/pics/smilies/ill/022.gif[/IMG]

Real Player?

Easy...

1) Add the Medibuntu ([www.medibuntu.org](www.medibuntu.org)) repository. This is valid if you're using Ubuntu 9.04 Jaunty Jackalope (if not visit: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) )

Open the terminal and paste this string:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

then this one:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

2) Now install realplayer (again, paste the following string in terminal):

```
sudo apt-get install realplayer
```

Easy, wasn't it?

---

### Post by julianp on 2009-05-25
Can I ask for some advice also regarding plugins and jre being a relative newbie here ...

I am using a video web server which runs an aplet and I can sucessfully run this in nasty internet explorer but not in firefox

I get the message applet not initialised and below is the java source if that helps:
 <applet
	name="application"
    code="application.class" 
        archive="application.jar"
        width=642
        height=600  >
                                <param name = label value =" This string was passed from the HTML host.">
    <param name = background value="FFFFFF">
    <param name = foreground value="FFFFFF">
    <param name = "732EUserName" value="*****            ">
    <param name = "732EPassWord" value="*****          ">
    <param name = "732EIP" value="86.170.37.192                                                   ">
    <param name = "732EPort" value="8000 ">
    <param name = "732EWidth" value="640">
    <param name = "732EHeight" value="552">
<param name = "732Estate" value="1">
    <param name = "732EFITWINDOW" value="0">
    
    <param name = "732Estate" value="1">
    <param name = "732ERES" value="1">
    <param name = "732EQUA" value="0">
    <param name = "732ECH" value="0">
    <param name = "732EHOTPOINT" value="1">
    <param name = "732ELIFESHOW" value="0">

I have obviously not included the username and password for obvious security reasons.

    </applet>
Any help that you can help me with would be appreciated as I do not want to go through the wine and ie4linux route although I have had it working there as well.

Many thanks in advance
regards
Julianp

---

### Post by slayer^_^ on 2009-05-26
> **julianp said:**
> Can I ask for some advice also regarding plugins and jre being a relative newbie here ...

I am using a video web server which runs an aplet and I can sucessfully run this in nasty internet explorer but not in firefox

I get the message applet not initialised and below is the java source if that helps:
 <applet
	name="application"
    code="application.class" 
        archive="application.jar"
        width=642
        height=600  >
                                <param name = label value =" This string was passed from the HTML host.">
    <param name = background value="FFFFFF">
    <param name = foreground value="FFFFFF">
    <param name = "732EUserName" value="*****            ">
    <param name = "732EPassWord" value="*****          ">
    <param name = "732EIP" value="86.170.37.192                                                   ">
    <param name = "732EPort" value="8000 ">
    <param name = "732EWidth" value="640">
    <param name = "732EHeight" value="552">
<param name = "732Estate" value="1">
    <param name = "732EFITWINDOW" value="0">
    
    <param name = "732Estate" value="1">
    <param name = "732ERES" value="1">
    <param name = "732EQUA" value="0">
    <param name = "732ECH" value="0">
    <param name = "732EHOTPOINT" value="1">
    <param name = "732ELIFESHOW" value="0">

I have obviously not included the username and password for obvious security reasons.

    </applet>
Any help that you can help me with would be appreciated as I do not want to go through the wine and ie4linux route although I have had it working there as well.

Many thanks in advance
regards
Julianp

Try removing IcedTea:

```
sudo apt-get remove --purge icedtea-gcjwebplugin icedtea6-plugin icedtea-6-jre-cacao
```

If necessary, reinstall Java as explained in the first post of this thread and let me know your results...

---

### Post by OriTheEep on 2009-05-26
> **slayer^_^ said:**
> Real Player?

Easy...

1) Add the Medibuntu ([www.medibuntu.org]("http://www.medibuntu.org")) repository. 
 
Already done, I hope. How could I confirm this? 
 
> **slayer^_^ said:**
> Now install realplayer (again, paste the following string in terminal):

```
sudo apt-get install realplayer
``` 
 
It's a bit untidy talking about RealPlayer in this thread but since I don't know where would be a better place (hint, hint)... 
 
In fact my flailing around unaided had included attempts to install both RealPlayer and Helix. I can find no trace of Helix but RealPlayer shows up in the Applications Menu. No sign of either in the plugins page of FF though. "apt-get remove" followed by "install" didn't help matters. I wouldn't bother with this except that I am addicted to Radio 4 (and now Radio 7) and the BBC i-Player insists on the blessed thing. Well done the BBC for supporting a proprietory, commercial format! 
 
> **slayer^_^ said:**
> Easy, wasn't it?
 
 
Don't be silly; very little is ever easy and most things that should work, don't!

:cry::cry::cry:

---

### Post by slayer^_^ on 2009-05-26
> **OriTheEep said:**
> Already done, I hope. How could I confirm this? 
 
 
 
It's a bit untidy talking about RealPlayer in this thread but since I don't know where would be a better place (hint, hint)... 
 
In fact my flailing around unaided had included attempts to install both RealPlayer and Helix. I can find no trace of Helix but RealPlayer shows up in the Applications Menu. No sign of either in the plugins page of FF though. "apt-get remove" followed by "install" didn't help matters. I wouldn't bother with this except that I am addicted to Radio 4 (and now Radio 7) and the BBC i-Player insists on the blessed thing. Well done the BBC for supporting a proprietory, commercial format! 
 
 
 
Don't be silly; very little is ever easy and most things that should work, don't!

:cry::cry::cry:

1) I forgot to tell you a thing... After correctly installing hte Medibuntu repository (as I explained you), but Before installing Real Player, you got to (of course !!!) update the package list with the new repositories...

You can do it easily from Synaptic package manager (simply "refreshing the packages list" and then searching for the "realplayer" package, or doing it in terminal:

```
sudo apt-get update
```

```
sudo apt-get install reaplayer
```

Be sure you correctly installed the Medibuntu repository...


2) You can simply download and install the realplayer .deb package from the website:

[http://packages.medibuntu.org/jaunty/realplayer.html](http://packages.medibuntu.org/jaunty/realplayer.html)

Just choose the architecture you need (It should be x64 I guess...

---

### Post by OriTheEep on 2009-05-26
> **slayer^_^ said:**
> 1) I forgot to tell you a thing... After correctly installing hte Medibuntu repository (as I explained you), but Before installing Real Player, you got to (of course !!!) update the package list with the new repositories...

You can do it easily from Synaptic package manager (simply "refreshing the packages list" and then searching for the "realplayer" package, or doing it in terminal:

```
sudo apt-get update
```

That seemed to work alright :)

> **slayer^_^ said:**
> ```
sudo apt-get reaplayer
```Be sure you correctly installed the Medibuntu repository...


Rather unexpectedly, gave me this:[INDENT]tom@server:~$ sudo apt-get realplayer
[sudo] password for tom: 
E: Invalid operation realplayer
[/INDENT]Is something broken?

:(


> **slayer^_^ said:**
>  2) You can simply download and install the realplayer .deb package from the website:

[http://packages.medibuntu.org/jaunty/realplayer.html](http://packages.medibuntu.org/jaunty/realplayer.html)

Just choose the architecture you need (It should be x64 I guess...


So I tried that as well and received a truly helpful error message (see att.).

I've not had much luck with this OS today. There is some sort of strange problem(s) with network access both in and out which I'm sure would be child's play to sort out if I only knew more about what I was doing. I'm just glad you all are here to help out.

Enough of this! I've got a whole week's worth of "Journey into Space" to listen to on my ten year old non-singing, non-dancing PC which, however, can run the i-Player! Next week (or whatever) they'll probably "upgrade" it so that my machine won't run it anymore. Will I be in time with my new one?

Hope you still have patience for me and thanks for all the help so far!

---

### Post by pixel :-) on 2009-05-26
the command is missing an option

sudo apt-get install reaplayer

---

### Post by OriTheEep on 2009-05-26
> **pixel :-) said:**
> the command is missing an option

sudo apt-get install reaplayer

Thanks, Pixel. The command now works but didn't cure the problem.

Any ideas about the second part of previous post?

---

### Post by pixel :-) on 2009-05-26
the command  ... had a second error

sudo apt-get install realplayer

---

### Post by OriTheEep on 2009-05-27
> **pixel :-) said:**
> the command  ... had a second error

sudo apt-get install realplayer

That one I did see, Pixel  ;)

I was thinking more of the error I got when I downloaded and attempted to install the .deb file using the default application "GDebi Package Installer".

In the screen attached, it indicates an extant installation. Clicking "Reinstall Package" leads to the error mentioned earlier. Clicking the "OK" button in that dialogue leaves a grey Installer window which just sits there waiting to be closed.

---

### Post by pixel :-) on 2009-05-27
You whant to do what? You want real player for bbc radio, this?
[http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

mozilla-mplayer should do the tric, uninstall all the rest realplayer helix and totem plugin.


if it works, ignore the rest, you'll need, a litle bit of configuring, when in a page with a "realplayer" right click and chose config, play around, but the one needed for BBC it's "play media directly from site". You can even rip it on your desktop.


if its about some mess with i-player, i don't know the details, i'm outside of the UK.

"I can find no trace of Helix but RealPlayer shows up in the Applications Menu"

Not all packages add them selves in the menu. You can simply run them from the terminal (you can edit the menus, to add commands)

try "helix" in the terminal

"No sign of either in the plugins page of FF"
Actually, i think they got installed correctly, but firefox isn't configured to use them. You still have the default video plugin(totem) that over rides them.

You can configure it, i don't now how.
the simplest, remove totem-mozilla.

---

### Post by slayer^_^ on 2009-05-27
> **pixel :-) said:**
> You whant to do what? You want real player for bbc radio, this?
[http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

mozilla-mplayer should do the tric, uninstall all the rest realplayer helix and totem plugin.


if it works, ignore the rest, you'll need, a litle bit of configuring, when in a page with a "realplayer" right click and chose config, play around, but the one needed for BBC it's "play media directly from site". You can even rip it on your desktop.


if its about some mess with i-player, i don't know the details, i'm outside of the UK.

"I can find no trace of Helix but RealPlayer shows up in the Applications Menu"

Not all packages add them selves in the menu. You can simply run them from the terminal (you can edit the menus, to add commands)

try "helix" in the terminal

"No sign of either in the plugins page of FF"
Actually, i think they got installed correctly, but firefox isn't configured to use them. You still have the default video plugin(totem) that over rides them.

You can configure it, i don't now how.
the simplest, remove totem-mozilla.

I definitely agree...

---

### Post by OriTheEep on 2009-05-27
> **pixel :-) said:**
> You whant to do what? You want real player for bbc radio, this?
[http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)


Yes. On [this page]("http://www.bbc.co.uk/programmes/b007js0f"), for the next seven days or so, if you click the word "Listen", an i-player window pops up and, if you are lucky, plays the requested programme with a fair margin of continuity chatter and surrounding programmes. I'm outside the UK too, now, but the radio service** isn't **restricted to the home, licence fee paying, audience.


> **pixel :-) said:**
>  mozilla-mplayer should do the tric, uninstall all the rest realplayer helix and totem plugin.

OK: Realplayer removed, helix wasn't there (?) and totem removed.
Deep breath: mozilla-mplayer installed.

All apparently without fuss or trouble :)


> **pixel :-) said:**
>   if it works, ignore the rest, you'll need, a litle bit of configuring, when in a page with a "realplayer" right click and chose config, play around, but the one needed for BBC it's "play media directly from site". You can even rip it on your desktop.


Ah! I'd better restart FF before trying that. Fizz! I want to paste the BBCode for this message into a text file for now but there doesn't seem to be a way.

Please don't reply to this message. I'll post up a report of what happened after I've tried it. Part two of this message, in effect.

> **pixel :-) said:**
> You can configure it, i don't now how.
the simplest, remove totem-mozilla.


I removed totem completely but I suppose I can put it back then disable the plugin if need be.

Thanks for this. :D

Back in a sec!

---

### Post by OriTheEep on 2009-05-27
An improvement, in that the i-Player now attempts to play the programme but the message is always "This content does not appear to be working", That's when FF doesn't abruptly disappear, which it is doing more often than not.

The IBM slam tracker from [Roland Garros]("http://www.rolandgarros.com/en_FR/index.html") (link on the right) is also crashing it, btw.

In the page that is all about plugins there is a section on RealPlayer 9 which I have attached. I'm not sure if this is relevant, though, sorry.

---

### Post by pixel :-) on 2009-05-27
"I removed totem completely" you just needed to remove the plugin

in a page with mplayer plugin, right click on it, and change the configuration

In BBC, change the audio output
For "Roland Garros" you'll have to change the video output

change to the outputs that are more stable.

also, configure caching, to something none zero

for example, how i set it up, in attachment, sometime mplayer plugin freezes at start up, just refresh the page. It never frezed while playback on me.

you can copy the url in a proper desktop music player, for example, from mplayer it gives
rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/6music/live/6music_dsat_g2.ra?BBC-UID=745a500b9791a7f5c3c8dd68b10fdec28b9a9cacb040326142d8a05464cd52a4&SSO2-UID=
cut "?BBC-UID=745a500b9791a7f5c3...."
and use rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/6music/live/6music_dsat_g2.ra
Of course since its the BBC, it could be that they periodical change.

---

### Post by nss0000 on 2009-05-27
Running Ux64_8.04.1

Unknown JAVA function. < java -version> gives a list of possible, but not actual(?) programs 

How do I remove the 20-odd GCJ (icetea) plugins from Firefox ?

---

### Post by pixel :-) on 2009-05-27
remove packages

icedtea-6plugin java-6-openjdk

and install

sun-java6-plugin

---

### Post by julianp on 2009-05-27
> **slayer^_^ said:**
> Try removing IcedTea:

```
sudo apt-get remove --purge icedtea-gcjwebplugin icedtea6-plugin icedtea-6-jre-cacao
```

If necessary, reinstall Java as explained in the first post of this thread and let me know your results...
Dear Slayer^^
thank you for your help about removing iced tea and I correctly followed the advice for java installation and I am extremely pleased to report that my system is now up and running on Firefox.
thanks for the patience in dealing with a newbie like myself
regards
Julianp

---

### Post by slayer^_^ on 2009-05-27
> **pixel :-) said:**
> remove packages

icedtea-6plugin java-6-openjdk

and install

sun-java6-plugin

Sorry, but if you remove java-6-openjdk openoffice goes away with it... :(

---

### Post by slayer^_^ on 2009-05-27
> **julianp said:**
> Dear Slayer^^
thank you for your help about removing iced tea and I correctly followed the advice for java installation and I am extremely pleased to report that my system is now up and running on Firefox.
thanks for the patience in dealing with a newbie like myself
regards
Julianp

Semper Paratus :D

---

### Post by OriTheEep on 2009-05-27
> **pixel :-) said:**
> "I removed totem completely" you just needed to remove the plugin



Totem Movie player is still there. When I pasted the rtsp url, that you gave, in its second form into a FF address bar, it offered to play the file with Totem not giving mplayer as an alternative. What name would I use in apt-get to remove the Totem Movie Player?

I've removed the Totem plugin now. Haven't put Totem itself back yet.

> **pixel :-) said:**
> 
in a page with mplayer plugin, right click on it, and change the configuration

In BBC, change the audio output
For "Roland Garros" you'll have to change the video output
change to the outputs that are more stable.

also, configure caching, to something none zero

for example, how i set it up, in attachment, sometime mplayer plugin freezes at start up, just refresh the page. It never frezed while playback on me.


Done that with a larger cache size and greater percentage of media.

Still crashing but now it's every time I try to launch it.

> **pixel :-) said:**
> you can copy the url in a proper desktop music player, for example, from mplayer it gives
rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/6music/live/6music_dsat_g2.ra?BBC-UID=745a500b9791a7f5c3c8dd68b10fdec28b9a9cacb040326142d8a05464cd52a4&SSO2-UID=
cut "?BBC-UID=745a500b9791a7f5c3...."
and use rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/6music/live/6music_dsat_g2.ra
Of course since its the BBC, it could be that they periodical change.


I've just tried to launch the MPlayer Movie Player from the Applications menu. It doesn't open.

How would I find the programme's url? The link from the programme page opens an i-Player window, run by Adobe Flash Player 10, presumably with a parameter that identifies the programme.

---

### Post by soymatias on 2009-06-02
Hi, i did every thing that you say and did'n wokr.

I've installed java 1.6.0_14 over ubutnu 8.04 64 bits with firefox 2.0.0.22pre,

root@localhost:/usr/lib/mozilla/plugins# java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

 And my about:pluginsshow this.

Shockwave Flash
 Nombre de archivo:  npwrapper.libflashplayer.so Shockwave Flash 9.0 r124   Tipo MIME Descripción Sufijos Habilitado    application/x-shockwave-flash Shockwave Flash swf Si   application/futuresplash FutureSplash Player spl Si  Java(TM) Plug-in 1.6.0_14
 Nombre de archivo:  libnpjp2.so The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   Tipo MIME Descripción Sufijos Habilitado    application/x-java-vm Java™ Plug-in 
Si   application/x-java-applet Java™ Plug-in Applet 
Si   application/x-java-applet;version=1.1 Java™ Plug-in 
Si   application/x-java-applet;version=1.1.1 Java™ Plug-in 
Si   application/x-java-applet;version=1.1.2 Java™ Plug-in 
Si....


An so on.

But when i go to any page with java doesn't show anything. It means where should be a java application  the page is in blank.

Java is enabled if firefox, but i don't know what happen.

Can you helpme please?

---

### Post by slayer^_^ on 2009-06-09
> **soymatias said:**
> Hi, i did every thing that you say and did'n wokr.

I've installed java 1.6.0_14 over ubutnu 8.04 64 bits with firefox 2.0.0.22pre,

root@localhost:/usr/lib/mozilla/plugins# java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

 And my about:pluginsshow this.

Shockwave Flash
 Nombre de archivo:  npwrapper.libflashplayer.so Shockwave Flash 9.0 r124   Tipo MIME Descripción Sufijos Habilitado    application/x-shockwave-flash Shockwave Flash swf Si   application/futuresplash FutureSplash Player spl Si  Java(TM) Plug-in 1.6.0_14
 Nombre de archivo:  libnpjp2.so The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   Tipo MIME Descripción Sufijos Habilitado    application/x-java-vm Java™ Plug-in 
Si   application/x-java-applet Java™ Plug-in Applet 
Si   application/x-java-applet;version=1.1 Java™ Plug-in 
Si   application/x-java-applet;version=1.1.1 Java™ Plug-in 
Si   application/x-java-applet;version=1.1.2 Java™ Plug-in 
Si....


An so on.

But when i go to any page with java doesn't show anything. It means where should be a java application  the page is in blank.

Java is enabled if firefox, but i don't know what happen.

Can you helpme please?

I am very busy at the time... I'll write a complete reply at the end of the week... sorry :(

---

### Post by Arup on 2009-06-09
The important point here is when you need to update Java, the one from repository locks you to a older version, this method allows you to sucessfully update new version whenever its released.

---

### Post by OldGaf on 2009-06-12
OK..... I am having trouble with some Java but not all in Fire Fox.

On my 32 bit install I am able to see the logo and water effect on this page:

[NialM Water Logo]("http://www.nialm.com/index/waterlogo.htm")

On my 64 bit install I "usually" only get a grey box.

Here is the odd bit....
If I make any changes to the Java installed, the page will display fine..... but ONLY until I refresh the page or restart FF.... then it never works again. 

Example:

I had this installed...

> There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java  

and the page was only showing a grey box.

I removed all the openjdk-6-jre "stuff" and switched back to the logo tab in fire fox (which was still running) and low and behold there was the logo and water effect. Refreshed the page and there it was..... gone.

This is what I have now: 

> sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


> java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

My question is..... what the heck is going on?
Obviously it CAN be displayed......

---

### Post by OldGaf on 2009-06-12
This is what I get from:
sudo update-java-alternatives -s java-6-sun

> 
No alternatives for appletviewer.                         
No alternatives for apt.                                  
No alternatives for extcheck.                             
No alternatives for HtmlConverter.                        
No alternatives for idlj.                                 
No alternatives for jar.                                  
No alternatives for jarsigner.                            
No alternatives for javac.                                
No alternatives for javadoc.                              
No alternatives for javah.                                
No alternatives for javap.                                
No alternatives for jconsole.                             
No alternatives for jdb.                                  
No alternatives for jhat.                                 
No alternatives for jinfo.                                
No alternatives for jmap.                                 
No alternatives for jps.                                  
No alternatives for jrunscript.                           
No alternatives for jsadebugd.                            
No alternatives for jstack.                               
No alternatives for jstat.                                
No alternatives for jstatd.                               
No alternatives for native2ascii.                         
No alternatives for rmic.                                 
No alternatives for schemagen.                            
No alternatives for serialver.                            
No alternatives for wsgen.                                
No alternatives for wsimport.                             
No alternatives for xjc.                                  
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt         
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck    
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj         
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner    
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar          
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac        
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc      
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah        
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap        
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole     
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb          
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat         
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo        
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap         
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps          
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript   
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd    
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack       
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd       
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat        
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'firefox-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'iceape-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'iceweasel-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'midbrowser-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'mozilla-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'xulrunner-1.9-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'xulrunner-javaplugin.so'.


---

### Post by OldGaf on 2009-06-13
Sigh.... just got a Firefox update...... on load the image is again drawn correctly.... on reload.... gone.....

---

### Post by slayer^_^ on 2009-06-20
Try following the tutorial from the beginning, it should do the trick :)

---

### Post by quixote on 2009-06-27
Java has always been a huge pain for me, so before I follow the nice simple instructions, ( sudo apt-get install sun-java6-plugin ) I want to be sure it won't blow anything else up, because if it does, I'll never get the damn thing working again.

I have a weird situation:  I thought I had java and jre installed.  Sun's java test page shows the frantic dancing thingy.  But I wanted to run [geotag]("http://geotag.sourceforge.net/"), which depends on java, and it said I didn't have it.  Huh?  So I run "java -version" and it says no java.  I look in synaptic, and it says neither openjdk, nor iced-tea, nor sun-java is installed.  More, "Huh?!"  How come some sites run, then?  I do have the plugin, libnpjp.so.

Now, when I tick sun-java6-plugin for installation in synaptic, it wants to install firefox 3.0.11.  I have FF 3.5RC2.  I don't want 3.0.  If I tell it to go ahead and install 3.0, how much danger is there that it'll step all over my 3.5? (which I do NOT want messed up) I know FF has gotten a lot better about parallel installations than in the good old days.

Presumably, since I apparently don't have openjdk to begin with, I don't need to uninstall it, and I'm not in danger of openoffice going with it?  There's another program I can't afford to mess up.

So, please, one of you experienced folks out there, tell me what I'm letting myself in for here. :D

( I do have a 64-bit system, and run Jaunty.)

---

### Post by udippel on 2009-06-28
> **OldGaf said:**
> 
[NialM Water Logo]("http://www.nialm.com/index/waterlogo.htm")

On my 64 bit install I "usually" only get a grey box.

My question is..... what the heck is going on?
Obviously it CAN be displayed......

Thanks for the link! Yes, I can confirm this for 64-bit Jaunty. Almost. What I have here, following the tutorial (so I think) is libnpjp2.so when calling 'about:plugins'.
When I go to that site, I get a white box just staying there. Nothing. And here I can't even close it, FF (3.0.11) simply freezes. 

$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

Any solution will be gratefully accepted!

Uwe

---

