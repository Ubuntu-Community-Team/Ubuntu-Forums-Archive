---
title: "Adobe Flash 10 Astro on Ubuntu 64 bit - VERY SIMPLE"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by slayer^_^ on 2009-02-27
**_Updated 12/12/2010 with a new version of Flash Player 10.3 "SQUARE" 64 bit_**

_**If you use a 64 bit version of Ubuntu**_ probably you would like to install a native 64 bit version of the flash player (that is far more stable than the version you install with the package flasplugin-nonfree ,  which is a 32 bit version of it emulated with nspluginwrapper)

It is very simple:


1) Remove previous existing versions of flash player: type in terminal, string by string:

_This code has been updated. Please try it if you had problems with this tutorial before._

```

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/mozilla/plugins/*flash*

```

2) Download the 64 bit Flash Plugin SQUARE 10.3 from its website:

```
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz
```

this is the link of the adobe labs download page for 64 bit flash player (just if you wanna check if new versions of it have been released...)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) or [http://labs.adobe.com/downloads/flashplayer10_square.html]("http://labs.adobe.com/downloads/flashplayer10_square.html")

(If you are downloading a newer release and this guide shouldn't have been updated at the time, just put the file in you "home" folder and change the next terminal commands to fit the new name of the file...)

3) Extract the archive:

```
sudo tar xzf flashplayer10_2_p3_64bit_linux_111710.tar.gz
```

4) Move it in its folder:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
```

5) Restart Firefox, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!


_If you're using the Opera browser:_

Do this **_only_** if, after having done point 4 and 5, you can't experience flash in Opera

4) Maybe Opera isn't searching into the Mozilla Plugins folder, then let's put the Flash plugin in its folder. The steps are the same as above, the only difference is step 4:

```
sudo mv libflashplayer.so /usr/lib/opera/plugins
```

5) Reboot Opera, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!


Bye ;)

---

### Post by orthopod on 2009-02-27
Didn't work for me.  Now I just get a black white space, instead of the blank black box I used to get with the old non-working flash plugin.

---

### Post by slayer^_^ on 2009-02-27
i updated the guide right now... try again and let me know!

p.s. it works for everyone i know!

---

### Post by orthopod on 2009-02-27
I had tried that as well. - no go

what did work was uninstalling Firefox, re- installing it,(Still not working).  
Then I tried installing the Adobe non-free plugin which then gave me working youtube..

---

### Post by slayer^_^ on 2009-02-27
what i think is that:

1) you did not COMPLETELY REMOVE the nspluginwrapper and flashplugin-nonfree packages by synaptic

2) you pasted the .tar.gz file in the home/.mozilla/plugins folder

3) you pasted in a wrong folder

4) you did not reboot firefox before trying it


i really suggest yo uto do so, because the native 64 bit flash plugin eliminatesmost of the firefox crashes and the annoying grey windows in youtube that forced you to update the page a million of times..

..please try again and let me know!

---

### Post by orthopod on 2009-02-27
Sorry - did all those things, extracted the file, etc.  even logged out.
thanks for the help anyway.

---

### Post by slayer^_^ on 2009-02-27
uhm... I am pretty sure it works :\

---

### Post by simtaalo on 2009-02-27
> **slayer^_^ said:**
> 
```
 sudo nautilus 
```


that should be ```
gksu nautilus
```

---

### Post by slayer^_^ on 2009-02-27
correct... providing changes!

---

### Post by slayer^_^ on 2009-02-27
however i think that the medibuntu guys (and the ubuntu-restricted-extras guys) should add this antive plugin... it is an alpha, ok, but it works like a charm! Absolutely better than the nspluginwrappered version...

:popcorn:

---

### Post by MickSulley on 2009-03-01
it just does not work for me, I have followed all the steps (several times!) and I just get a blank window on youtube.

Any ideas what I can do to fix it?

Thanks

Mick

---

### Post by istblacken on 2009-03-01
alternatively, after removing other versions of flash player, you can put the plugin into home/<username>/.mozilla/plugins

---

### Post by MickSulley on 2009-03-01
i've put it in there as well and it still does not work.  I had to create the directory for plugins, is that normal?

---

### Post by WildeBeest on 2009-03-01
Didn't work for me either.

Is this just for 8.10?

---

### Post by HuaiDan on 2009-03-02
This is for 64 bit. It works on 8.10.

Tried it on 3 different machines of varying specs, all 64 bit, all work.

 This comes just in time so I can load a set of firefox kids games and educational tools for firefox called Kidzui. Didn't work before, got a flash 8 needed error. Now it totally works. Thanks!

---

### Post by MickSulley on 2009-03-02
I am running 64 bit 8.10 and it is not working. Does anyone have any idea what could be wrong?  Is it likely to work with 9.04?

---

### Post by Yashiro on 2009-03-02
> alternatively, after removing other versions of flash player, you can put the plugin into **/home/<username>/.mozilla/plugins**
Some CPU spike cases have been resolved in this update but it still crashes on alot of websites unfortunately. [www.streetfighter.com](www.streetfighter.com) being a prime example.

(Firefox 3.0.6/Ubuntu 8.04 LTS/2.6.24-23-generic x86_64)

---

### Post by istblacken on 2009-03-02
> **Yashiro said:**
> Some CPU spike cases have been resolved in this update but it still crashes on alot of websites unfortunately. [www.streetfighter.com](www.streetfighter.com) being a prime example.

(Firefox 3.0.6/Ubuntu 8.04 LTS/2.6.24-23-generic x86_64)

i haven't experienced any crash with this version of flash (including the site you mentioned above ) although CPU spike cases have always been a problem at least for me while using flash player on any linux.

---

### Post by Mocker on 2009-03-02
This worked fine for me. I haven't tested extensively, but after the update I did last night, the Flash plugin seemed to be totally borked... Firefox could apparently still see that it was installed, but on every site I went to with Flash, I got the "Plugins missing, click here to install them" banner. After doing this install, I get YouTube running just fine.


Thanks!

---

### Post by SuperSonic4 on 2009-03-02
No for I already had flash installed via the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") most notably > 32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of this page to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart your web browser and use the plugin.


However, your guide looks like it works although I'd have to take the minor step of either using either ```
sudo cp <source> <dest>
``` or ```
kdesudo dolphin
``` XD

---

### Post by slayer^_^ on 2009-03-02
micksulley, are you sure you removed the old versions of flash you've installed?

if you did and you pasted the extracted content of the .tar.gz archive (and not the .tar.gz file itself) i don't see any reason it shouldn't work...

---

### Post by Yashiro on 2009-03-02
> i haven't experienced any crash with this version of flash (including the site you mentioned above ) although CPU spike cases have always been a problem at least for me while using flash player on any linux.
Then the blame for flash crashing on some flash content must be linked to either my video (fglrx 9.1) or alsa (pulse audio is not running). Given it's on a small number of cases but 100% reproducible suggests there is a dependency, or something specific about the stream data.
Movies on veoh.com are also affected if I recall correctly. Plugin fails in Opera too on the same sites. Although it doesn't crash the browser. 

Pointless mentioning anything about this in detail on this forum though. :)

---

### Post by slayer^_^ on 2009-03-03
yay, but don't forget that the adobe 64 bit flash plugin is still an alpha release... the point is that it works much better than the 32 bit version with nspluginwrapper!!!

---

### Post by MickSulley on 2009-03-03
I followed all the instructions from SuperSonic4 but it is still not working properly.  Videos on YouTube sometimes work and sometimes don't, but the real reason for wanting to get it working is that I play Chess on Facebook, and the board and everything else displays fine, but there are no pieces displayed, which is a bit of an issue.  I have contacted ChessPro support and they say that it is a problem with Flash.

Any help would be most welcome

Thanks

Mick

---

### Post by slayer^_^ on 2009-03-03
did you restart firefox after copying the plugin?

if so, try to restart your session and let me know...

again, you got to consider it's still an alhpa... even if i experienced flash lockup with the 64 bit version just once, the point is if it works better than the 32 bit version with nspluginwrapper.

...and it does, for me, absolutely!

---

### Post by philinux on 2009-03-03
> **MickSulley said:**
> I followed all the instructions from SuperSonic4 but it is still not working properly.  Videos on YouTube sometimes work and sometimes don't, but the real reason for wanting to get it working is that I play Chess on Facebook, and the board and everything else displays fine, but there are no pieces displayed, which is a bit of an issue.  I have contacted ChessPro support and they say that it is a problem with Flash.

Any help would be most welcome

Thanks

Mick

Just make sure you got rid of previously installed flash do this.

```
sudo updatedb
then
locate libflashplayer.so
```

---

### Post by MickSulley on 2009-03-03
updatedb seemed to run OK, then I get

mick@mick-desktop:~$ locate libflashplayer.so
/home/mick/.mozilla/plugins/libflashplayer.so
/home/mick/Desktop/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
mick@mick-desktop:~$ 

Rebooted and it is still does not work

---

### Post by slayer^_^ on 2009-03-03
**/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so**
**/usr/lib/firefox/plugins/npwrapper.libflashplayer.so**

_those are the 32 bit version ported by nspluginwrapper.._ try removing those files and let us know...

beware, you'll need to access a nautilus with root privileges, you can easily do it by typing in the terminal:

```
gksu nautilus
```

more likely, however, those are links.. so see if you got also this file in this location:

**/var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so**

and remove it.


moreover this:

**/usr/lib/flashplugin-nonfree/libflashplayer.so**

makes me think you didn't correctly remove the nspluginwrapper package from synaptic (or you didn't mark _for complete removal_), or you did and didn't apply the changes... why is it still there, then???

p.s. if it doesn't work still, try removing all these files:

/home/mick/.mozilla/plugins/libflashplayer.so
/home/mick/Desktop/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so

in order to leave just the one in the /usr/lib/mozilla/plugins folder, as specified in teh first post of this thread.

Then restart your firefox and let us know if you succeeded

---

### Post by WildeBeest on 2009-03-03
Update.

I got it working with firefox, but not Opera.

Any ideas?

---

### Post by slayer^_^ on 2009-03-03
please take a look at the first post of the thread, that I updated a few minutes ago...

just a few questions

1) are you using intrepid or another 64 bit distro?

2) try removing **_all_ the libflashplayer.so or nsplugin.flashplayer.so **files that you can find by tiping in terminal

```
sudo update d
locate libflashplayer.so
```

with a nautilus with administrator privileges that you can use by typing in terminal:

```
gksu nautilus
```

and, again, [B]please be sure that you marked for complete removal the package nspluginwrapper , and then applied the changes  in the synaptic package manager
[/B]

until, doing again

```
sudo update d
locate libflashplayer.so
```

you got a result like this one:

```
yourname@yourname-desktop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```

_when you're sure_ that there's just one libflashplayer.so file only in the folder /usr/lib/mozilla/plugins , then restart firefox and give a try to flash applications (f.e. youtube). 

then let us know...:popcorn:

---

### Post by WildeBeest on 2009-03-03
64 bit Hardy

Search for files results with this.

```

/home/willy/.mozilla/plugins/libflashplayer.so
/home/willy/Downloads/libflashplayer.so
/home/willy/lib/opera/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so
/usr/lib/opera/9.63/libflashplayer.so
/usr/lib/opera/plugins/libflashplayer.so
w
```

all the libflashplayer.so have the same date and size( 9.1 MB, 2/2/2009)


Like I said fire-fox works.

Opera does not.

---

### Post by slayer^_^ on 2009-03-03
sorry, Wildebeste, as I've written I am tired, thus i didn't understand your answer, actually.

I can suggest you:

1) Keep only the plugin file in this folder:

/usr/lib/mozilla/plugins/libflashplayer.so

delete all the other libflashplayer.so files in the other folders

2) Be sure Opera searchs for plugins in the /usr/lib/mozilla/plugins (it does, by default).

Open an Opera window and go to page [HTML]opera:plugins[/HTML]

You should see  something like this: 

> Shockwave Flash

application/futuresplash    spl
application/x-shockwave-flash    swf
/usr/lib/mozilla/plugins/libflashplayer.so

If not --> Tools / Preferences / Contents / Plugin Options

then --> Plug-in path / Add new

add the /usr/lib/mozilla/plugins/ path and enable it

then restart Opera and give it a try


Please let me know your progresses...

---

### Post by MickSulley on 2009-03-03
I did as you said and now have just the one 

mick@mick-desktop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
mick@mick-desktop:~$ 

I have re-booted but it still does not work.  Is there anything else I can do?

Thanks

Mick

---

### Post by slayer^_^ on 2009-03-03
sorry about the question. but are you trying with firefox or with another browser?

because

1) if you are using, for example, Opera, probably it isn't searching for plugins in the mozilla folder (usually it does...). Then you can try to paste the libflashplayer.so file into the directory /usr/lib/opera/plugins .

2) if it's firefox you're using. please try in a  firefox window --> Tools / Plug-ins and see if the "Shockwave Flash" plugin version 10.0 r22 is present and enabled

---

### Post by MickSulley on 2009-03-04
I am using Firefox.  In Tools>Add-ins I see 3 Shockwaves
Shockwave Flash 9.0.r999. Gnash 0.8.4, the GNU SWF Player
Shockwave Flash 9.0.r999
Shockwave Flash 10.0.r22

There are all enabled. I have tried all combinations of enable/disable and if I do not have the first one enabled my chess screen does not even show hte board, with that one enabled the board displays but no pieces.  The other two don't seem to make any difference

---

### Post by slayer^_^ on 2009-03-04
> **MickSulley said:**
> I am using Firefox.  In Tools>Add-ins I see 3 Shockwaves
Shockwave Flash 9.0.r999. Gnash 0.8.4, the GNU SWF Player
Shockwave Flash 9.0.r999
Shockwave Flash 10.0.r22

There are all enabled. I have tried all combinations of enable/disable and if I do not have the first one enabled my chess screen does not even show hte board, with that one enabled the board displays but no pieces.  The other two don't seem to make any difference



maybe that's the reason why, you have gnash installed (an alternative flash player) and it generates conflict...

So I suggest:

1) Try leaving only Shockwave Flash 10.0.r22 enabled and restarting Firefox, if it doesn't work:

2) From synaptic package manager mark for complete removal the package "gnash" and apply the changes; then be sure that Shockwave Flash 10.0.r22 plugin is enabled in Firefox, restart it and give it a try...


p.s. it was a point of the guide... 2) Remove previous existing versions of flash player

---

### Post by MickSulley on 2009-03-04
I have done a complete uninstall of Gnash and I just have the one flashplayer
/usr/lib/mozilla/plugins/libflashplayer.so

I now don't even see the board in Facebook Chess and in YouTube I don't even get the window to open up to play a video

I just went to the Adobe Flash site [http://www.adobe.com/products/flashplayer/features/](http://www.adobe.com/products/flashplayer/features/) and clicked on the demos there, all 3 just open up a new Firefox window and after a couple of second display done at the bottom, but the window is still blank.

---

### Post by slayer^_^ on 2009-03-04
is the plugin activated in firefox?

if yes, maybe (since you had gnash installed) you've got other flash versions installed... try this more intensive clean-up:

```
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

---

### Post by MickSulley on 2009-03-04
It works!!!!!
It works!!!!!
It works!!!!!
It works!!!!!

That cleanup removed swfdec-mozilla and now I can see my chess pieces again!  I have also tried YouTube and that seems OK.

Thank you so much, you have been very patient and seen it through to the end. I am very grateful for all your help.  It is assistance like this that makes Ubuntu great.

Thanks

Mick

---

### Post by floyd0 on 2009-03-04
Amazing... Worked first time for me!. No black screens!!! Thanks

---

### Post by slayer^_^ on 2009-03-04
I am very happy of having been helpful... please, do something for all the others now: tell me if the first post of the thread (the guide) is complete and simple in your opinion, so I can make it better and easier to understand to newbies :)

Again, I am glad it worked ;)

---

### Post by soxs on 2009-03-04
Did work for opera 9.64 and firefox 3.x.x on ubuntu 8.10
Latest flash

THANK YOU!

---

### Post by slayer^_^ on 2009-03-04
You're welcome ;)

...it's Ubuntu :D

---

### Post by zika on 2009-03-04
- clean all the remnants of flash plugin as described above
- download (wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz))
- extract libflashplayer.so in /opt/flash/ (create directory first)
- sudo ln -s /opt/flash/libflashplayer.so ~/.mozilla/plugins
- sudo ln -s /opt/flash/libflashplayer.so /usr/lib/mozilla/plugins

works with FF2.*, FF3.0.*, FF3.1*, FF3.2*, Epiphany, Swiftweasel, Opera9.*, Opera 10.* ...

this way, when new version of libflashplayer.so comes You have to repeat only first two steps and You have only one copy of it on Your machine. symbolic links are taking care of the rest.

also, You did not mess with the Ubuntu arrangement of files.

disclaimer: I just write from mine and experience of several others. I do not claim to have a howto or whatever it's called ... ;)

---

### Post by slayer^_^ on 2009-03-04
what's the difference between your method and overwriting the unique file libflashplayer.so in /usr/lib/mozilla/plugins , when a new version comes up??

of course all this "walkthrough" will become useless when a standard version will be released and added in the repositories (thus updating the 64 bit version of the flashplugin-nonfree package)


all ideas are welcome :popcorn:

---

### Post by WildeBeest on 2009-03-04
> **slayer^_^ said:**
> sorry, Wildebeste, as I've written I am tired, thus i didn't understand your answer, actually.

I can suggest you:

1) Keep only the plugin file in this folder:

/usr/lib/mozilla/plugins/libflashplayer.so

delete all the other libflashplayer.so files in the other folders

2) Be sure Opera searchs for plugins in the /usr/lib/mozilla/plugins (it does, by default).

Open an Opera window and go to page [HTML]opera:plugins[/HTML]

You should see  something like this: 

If not --> Tools / Preferences / Contents / Plugin Options

then --> Plug-in path / Add new

add the /usr/lib/mozilla/plugins/ path and enable it

then restart Opera and give it a try


Please let me know your progresses...



about:plugins

```
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so
```

When I go to youtube, it just displays a white box.

---

### Post by soxs on 2009-03-04
> **slayer^_^ said:**
> what's the difference between your method and overwriting the unique file libflashplayer.so in /usr/lib/mozilla/plugins , when a new version comes up??

of course all this "walkthrough" will become useless when a standard version will be released and added in the repositories (thus updating the 64 bit version of the flashplugin-nonfree package)


all ideas are welcome :popcorn:
Yours is straight forward and does the job and places the file where everybody would expect them. Placing them somewhere else only keeps you thinking about the next update, why the hel it doesn't work (or where did I save that lib blah flash .so again? )

So it's rather personal suggestion than any usefull critic on yur great howto

---

### Post by slayer^_^ on 2009-03-04
> **WildeBeest said:**
> about:plugins

```
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so
```

When I go to youtube, it just displays a white box.



I have re-written the howto... please 

1) follow the updated clean-up method in the first post for deleting _all_ the previous free and non-free vesions of flash you have installed, then 

2) keep _only_ the libflashplayer.so file in the /usr/lib/mozilla/plugins folder (opera is set to automatically search in that folder for plugins), so delete the one in /usr/lib/opera/plugins 

3) restart opera and try... we are about to solve your trouble! Most of the problems were caused by my omissis in the removal of opensource versions of flash like gnash

---

### Post by soxs on 2009-03-04
for anyone else out there having wild libflashplayer.so files running around like invisble aliens, do ```
sudo updatedb; locate libflasplayer.so
``` remove all of them ( rm -vf /path/to/lib...so ) afterwards it will work (shutting down all browsers first of course)

---

### Post by slayer^_^ on 2009-03-04
> **soxs said:**
> Yours is straight forward and does the job and places the file where everybody would expect them. Placing them somewhere else only keeps you thinking about the next update, why the hel it doesn't work (or where did I save that lib blah flash .so again? )

So it's rather personal suggestion than any usefull critic on yur great howto

great howto? ahhahaha, I just hope it's useful !!! ;)

Thank you man!

---

### Post by soxs on 2009-03-04
> **slayer^_^ said:**
> great howto? ahhahaha, I just hope it's useful !!! ;)

Thank you man!

It's straight forward, like a howto should be, though you could do and get some non-intrusive colours into some important parts, a lot of useres (including me) tend to overread (correct word?, I doubt)...

---

### Post by slayer^_^ on 2009-03-04
colours? maybe I should... :D

thanks for the adivice!

---

### Post by WildeBeest on 2009-03-04
I followed soxs procedure and Opera still does not work.
The Opera plugin path is:

```
/usr/lib/mozilla/plugins:/usr/lib/opera/9.64
```

about:plugins output is:

```
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/libflashplayer.so
```

The results of sudo updatedb; locate libflashplayer.so

```
/home/wildebeest/.mozilla/plugins/libflashplayer.so
/opt/flash/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

```

any ideas?

---

### Post by Yashiro on 2009-03-04
Delete two of them.

---

### Post by slayer^_^ on 2009-03-04
> **WildeBeest said:**
> I followed soxs procedure and Opera still does not work.
The Opera plugin path is:

```
/usr/lib/mozilla/plugins:/usr/lib/opera/9.64
```

about:plugins output is:

```
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/libflashplayer.so
```

The results of sudo updatedb; locate libflashplayer.so

```
/home/wildebeest/.mozilla/plugins/libflashplayer.so
/opt/flash/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

```

any ideas?


Paste this code in terminal, string by string:

```

sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /home/wildebeest/.mozilla/plugins/libflashplayer.so
sudo rm -f /opt/flash/libflashplayer.so
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

Then copy the original libflashplayer.so file you downloaded in the folder /usr/lib/mozilla/plugins . Opera searchs there for plugins, it's better it finds a plugin than a link, isn't it?

Then restart Opera and give it a try... and let me know in the shortest time possible (because i gtg to sleep :) )

---

### Post by WildeBeest on 2009-03-04
> **Yashiro said:**
> Delete two of them.

The '/usr/lib/mozilla/plugins/libflashplayer.so' is a link to '/opt/flash/libflashplayer.so'
as Zika suggested.

The one in the Downloads folder is just an extraction of the original tar ball.

I don't see how deleting 2 of those would make a difference.

I have restarted Opera numerous times.

---

### Post by slayer^_^ on 2009-03-04
1) because opera sees two plugins and tries to use them both ( I tested yesterday and it decreased the performances)

2) most of the code i pasted you in the previous post is needed to remove _open-source_ or _alternative_ flash players, that prevent the plugin you are trying to use now from correctly working.

Please try the terminal codes I pasted you in the previous post, restart opera and give it a try..

---

### Post by WildeBeest on 2009-03-04
Ok, I executed all the commands in your previous post except for 'sudo rm -f /opt/flash/libflashplayer.so' because '/usr/lib/mozilla/plugins/libflashplayer.so' is a link to it.

Opera still does not work. White box.

go to bed, I'll catch up with you tomorrow.
I usually get home from work at 1600 my time.

firefox doesn't work now either.

I get the error message:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player.

---

### Post by MickSulley on 2009-03-04
> I am very happy of having been helpful... please, do something for all the others now: tell me if the first post of the thread (the guide) is complete and simple in your opinion, so I can make it better and easier to understand to newbies 

Yes I think that the original post is complete now since you latest edits.  I think it was removal of swfdec-mozilla that fixed it for me, but that is now included within your script.

Again - thanks for all your help.

Mick

---

### Post by slayer^_^ on 2009-03-04
> **WildeBeest said:**
> Ok, I executed all the commands in your previous post except for 'sudo rm -f /opt/flash/libflashplayer.so' because '/usr/lib/mozilla/plugins/libflashplayer.so' is a link to it.

Opera still does not work. White box.

go to bed, I'll catch up with you tomorrow.
I usually get home from work at 1600 my time.


I asked you to remove the file /opt/flash/libflashplayer.so and paste the libflashplayer.so file you downloaded from the adobe website in the folder /usr/lib/mozilla/plugins .

Please do it and let me know, when you've got time.

The rationale is that Opera searches for plugins in that mozilla folders, I don't think it works if it finds a link...

Good night !

---

### Post by WildeBeest on 2009-03-04
Now the only instance of 'libflashplayer.so' is in the '/usr/lib/mozilla/plugins'.

Opera still doesn't work, nor does firefox.


There are other links in the folder ('/usr/lib/mozilla/plugins') such as java that do work.

---

### Post by Yashiro on 2009-03-04
And it still shows up as active in 'about:plugins' right?

You should uninstall ALL Flash players that have an entry in Synaptic. ie ones that you have installed as a package or by using apt-get.

Then simply put the latest adobe one in the plugins folder in your home directory.

---

### Post by WildeBeest on 2009-03-04
Flash does not appear in about:plugins.

Also there are no flash packages installed by Synaptic.

---

### Post by Yashiro on 2009-03-04
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

# Save the .tar.gz file to your desktop and wait for the file to download completely.
# Quit your browser.
# Remove all existing Adobe Flash Player installations from the system.
# Unpackage the file. A directory with contains libflashplayer.so will be created.
# Copy libflashplayer.so to /home/yourname/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet. So you now should have /home/yourname/.mozilla/plugins/libflashplayer.so
# Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu.

This is the easiest way to test any plugin.

---

### Post by WildeBeest on 2009-03-04
Thanks Yashiro, that gets firefox flash working again.

Still doesn't work with Opera. Get the white box.

---

### Post by Yashiro on 2009-03-04
Adding your home plugins dir to the opera path should work.

That doesn't mean that the actual plugin will work in practice.
You can set it all up correctly and it still fails. I've gotten used to Flash being garbage by now, it's a pretty sad state of affairs.

---

### Post by slayer^_^ on 2009-03-05
> **WildeBeest said:**
> Thanks Yashiro, that gets firefox flash working again.

Still doesn't work with Opera. Get the white box.


It sounds very strange... what's the result of [HTML]opera:plugins[/HTML] in an opera windows, regarding the flash player, when you put the libflashplayer.so file in the /usr/lib/mozilla/plugins folder ?

---

### Post by WildeBeest on 2009-03-05
You do mean about:plugins in an Opera tab?

Here it is, looks good to me.

```
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by slayer^_^ on 2009-03-05
> **WildeBeest said:**
> You do mean about:plugins in an Opera tab?

Here it is, looks good to me.

```
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/libflashplayer.so
```


Did put the libflashplayer.so file (and not the link) in the /usr/lib/mozilla/plugins folder?

---

### Post by WildeBeest on 2009-03-05
yes

Tried it both ways. Same results.

---

### Post by slayer^_^ on 2009-03-06
If I were you, I would try with a complete removal and reinstall of the Opera browser... it will allow a fresh search for codecs and plugins and, since it works on firefox, I don't see any reason why it shouldn't with Opera.

---

### Post by WildeBeest on 2009-03-06
Off to work now, I'll give it a shot when I get home.

---

### Post by WildeBeest on 2009-03-06
Un and re-install didn't work either.

I'll just have to use firefox for youtube or sites with flash content.

Thank you for taking the time to assist me with this.

---

### Post by slayer^_^ on 2009-03-07
> **WildeBeest said:**
> Un and re-install didn't work either.

I'll just have to use firefox for youtube or sites with flash content.

Thank you for taking the time to assist me with this.


I don't know what else you could try... this flash version works on my Opera, I can't understand why it doesn't for you... :\

---

### Post by zika on 2009-03-07
> **WildeBeest said:**
> Un and re-install didn't work either.
I'll just have to use firefox for youtube or sites with flash content.
Thank you for taking the time to assist me with this.
I do not have Opera installed at this moment. but several days ago when I did both 9.6* and 10 worked with newest flash plugin and locations of my *libflashplayer.so* are:
*/opt/flash/libflashplayer.so* (this is where I keep it and where I do update it)
*/home/zika/.mozilla/plugins/libflashplayer.so* (link)
*/usr/lib/mozilla/plugins/libflashplayer.so* (link).
this might help ...

update: just now I realized that I have posted already about this several days ago in this thread. sorry.

---

### Post by WildeBeest on 2009-03-07
@zika

After exhausting everything suggested here, I have my system setup as you suggested. Opera still does not work.
Like I said, I give up.

---

### Post by inxygnuu on 2009-03-08
Thanks! finally get it working! I read another article, but there was no download link, leaving me helpless.

Thanks,
3v4n;):popcorn::KS:):P:o:D

---

### Post by ubiDD on 2009-03-10
@WildeBeest:

If you haven't yet - run gksudo nautilus (alt+F2, type gksudo nautilus)
go to /home/usr/.mozilla/plugins (you can copy that into the address bar)
- you should have the 64bit libflashplayer.so in there, right-click and select "make link"
- you now want to MOVE this link to /usr/lib/mozilla/plugins, NOT copy.
- move/paste link there, close out and reopen Opera

*I did read somewhere that not all sites work with Opera, this may be the case if it doesn't work; I went to a few sites with my newly downloaded Opera before replying to this thread and all worked fine.

---

### Post by zika on 2009-03-10
in Terminal```
sudo ln -s  /home/usr/.mozilla/plugins/libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by nroussi on 2009-03-10
I am using 8.04 64 with an LTSP server and the edubuntu add on. This is what I have:
> nicolas@edubuntuS2new:~$ locate libflashplayer.so
/home/nicolas/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so

I manually added to all these directories one by one executing
> sudo killall -9 firefox
at every step and trying it. It does not work. Any ideas?

---

### Post by slayer^_^ on 2009-03-10
> **nroussi said:**
> I am using 8.04 64 with an LTSP server and the edubuntu add on. This is what I have:

I manually added to all these directories one by one executing

at every step and trying it. It does not work. Any ideas?



sorry man, but why did you add all those folders? didn't the walkthrough in the first post of the thread work for you?

---

### Post by wsscott on 2009-03-10
Worked for me.

Thanks!

---

### Post by athaki on 2009-03-10
works, but no sound.

---

### Post by pbaic on 2009-03-11
The original post didn't work on Hardy. Once I moved the file from /usr to /home and made the link in /usr, it worked.

---

### Post by soxs on 2009-03-11
> **pbaic said:**
> The original post didn't work on Hardy. Once I moved the file from /usr to /home and made the link in /usr, it worked.
If that's true, then we need to handle permissions of libflashplayer.so. Anyone having trouble with flashnot working should try chmod a+x ./libflashplayer.so just to exclude any trouble....

---

### Post by ubiDD on 2009-03-11
Thanks Zika! Still learning ins and outs :P

---

### Post by zika on 2009-03-11
> **ubiDD said:**
> Thanks Zika! Still learning ins and outs :P
I liked that animated image very much .. ;)

---

### Post by slayer^_^ on 2009-03-11
> **pbaic said:**
> The original post didn't work on Hardy. Once I moved the file from /usr to /home and made the link in /usr, it worked.

interesting... anyone has the same issue?

---

### Post by nroussi on 2009-03-11
> **slayer^_^ said:**
> sorry man, but why did you add all those folders? didn't the walkthrough in the first post of the thread work for you?

No it didnt. Also I have chmod'ed 777 in all above directories and still nothing. When I type about:plugins all plugins are located in the xulrunner-addons directory. Thats why I added it there as well. I followed the first thread to the letter and when it did not work then I started adding it to the other directories. I will place it in /usr/lib/mozilla/plugins only, do a chmod a+x on it and report back. BTW, I am using it on edubuntu on the thin client. Should I build the client image again?

I have done that and still no go. I am on the console now and nothing.

---

### Post by ralph961 on 2009-03-15
This worked but only after search for all other occurences of the file and deleting them.

Thanks

---

### Post by rplantz on 2009-03-22
Many sites work, including youtube. But lots of them crash Firefox with an "illegal instruction" error. For example, vimeo.com.

The "illegal instruction" error suggests that the stack is being trashed.

---

### Post by martini1179 on 2009-05-07
Hello, 

I'm just wondering if anyone has had any problems with Firefox 3.0.10 crashing seemingly at random on 9.04 with this flash player alpha installed? 

I'm trying to determine why my Firefox sessions are crashing every few hours. I don't think my browser extensions are at fault, so its either something internal with the browser, or the flash player, since it IS an alpha.  

I'm new to Ubuntu, and I've only been using Intrepid for half a week before Jaunty came out, and so I'm not sure if this was also a problem with the previous version or not. 

Thanks, and I'd love to get some input.

---

### Post by bobince on 2009-05-07
Certainly I've had crashes from the 64-bit Flash alpha under both Jaunty and Intrepid. (Hell, even the ‘release quality’ 32-bit Windows Flash plugin would happily crash now and again!)

It seems to be video-related; one site that will reliably take 64-bit Flash down in a couple of minutes is the [Uniqlock](http://www.uniqlo.jp/uniqlock/).

I'd strongly recommend looking at the Flashblock add-on for Firefox to reduce the random crashes caused by misbehaving Flash in adverts; you can then choose only to run known-good Flash like YouTube and MySpace. (Also cuts down nicely on the obnoxiously noisy or CPU-hogging ads unexpectedly ruining your day.)

---

### Post by slayer^_^ on 2009-05-08
I dunno, everything works perfectly with me... Just be sure that isn't Java the trouble!

---

### Post by adrianx on 2009-05-09
Thank you slayer, it worked for me!

---

### Post by DerFahnder on 2009-05-10
Thank you very much, the 32Bit Flash version drove me nuts.

---

### Post by Fstop on 2009-05-10
WOW! 

I went through your steps and flash works PERFECTLY now! I used to have about an 85% success rate with YouTube, and recently [www.playlist.com](www.playlist.com) stopped working for me. Everything works GREAT now. 

You sir, kick ***!

---

### Post by popat007 on 2009-05-11
Thanks, works great.!!!!o:o:o:o:o:guitar::guitar::guitar:

---

### Post by marcelkoopman on 2009-05-11
Hello,

I've created an debian package for this, because its better to maintain that way instead of having to manually remove and set this up.

The debian package will also remove other conflicting packages like flashplugin-nonfree etc.

Download here:

[http://members.lycos.nl/marcelk1607/flash-amd64.deb](http://members.lycos.nl/marcelk1607/flash-amd64.deb)

Please test it, let me know if this works for you!

---

### Post by aimonas on 2009-05-11
hello everyone,

for me the variation of copying the *.so file to ~/.mozilla/plugins/
worked perfectly. Tested already youtube, kcrw.

it also works with firefox-3.5 beta4 (aka shiretoko)

thank you slayer, thanks to the community as well

greets

---

### Post by Method9455 on 2009-05-11
The .deb worked perfectly for me, thanks.

---

### Post by adamthompson on 2009-05-15
I have not been able to get this to work. I'm using Hardy 8.04 and Firefox 3.0.10. I tried the instructions in the first post in this thread. I also tried putting libflashplayer.so in /home/myhome/.mozilla/plugins, which also didn't work. It doesn't work in Opera either. I tried putting libflashplayer.so in /usr/lib/opera/plugins, which didn't help. I tried the deb. That didn't work either. Does anyone have any suggestions? My preference would be to have native Flash Player (no plugin wrapper) in Firefox. But I'd be willing to use a different browser if I can get Flash working in it. Thanks.

---

### Post by slayer^_^ on 2009-05-16
Have you tried to remove the previously installed flash plugins?

```
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
```

also, you can try visiting the webpage [about:plugins]("about:plugins") to find out which flash plugin is installed and remove it, so you can install the one explained in this guide...

then let us know the results :P

---

### Post by marcelkoopman on 2009-05-16
> **adamthompson said:**
> I have not been able to get this to work. I'm using Hardy 8.04 and Firefox 3.0.10. I tried the instructions in the first post in this thread. I also tried putting libflashplayer.so in /home/myhome/.mozilla/plugins, which also didn't work. It doesn't work in Opera either. I tried putting libflashplayer.so in /usr/lib/opera/plugins, which didn't help. I tried the deb. That didn't work either. Does anyone have any suggestions? My preference would be to have native Flash Player (no plugin wrapper) in Firefox. But I'd be willing to use a different browser if I can get Flash working in it. Thanks.
What do you mean "doesnt work". I cant help you if you just say "it doesnt work".

---

### Post by adamthompson on 2009-05-16
> **marcelkoopman said:**
> What do you mean "doesnt work". I cant help you if you just say "it doesnt work".

Sorry for the vagueness. What I mean is that if I view a Web site that requires Flash, I see a message that I need to install the Adobe Flash Player and I don't see any Flash content. Depending on the Web site, I may see a non-Flash replacement (in Google Finance, for example).

---

### Post by adamthompson on 2009-05-16
> **slayer^_^ said:**
> Have you tried to remove the previously installed flash plugins?

```
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
```

also, you can try visiting the webpage [about:plugins]("about:plugins") to find out which flash plugin is installed and remove it, so you can install the one explained in this guide...

then let us know the results :P

I definitely tried to remove the previously installed Flash plugins. That was the first thing I did.

In Firefox, about:plugins shows no Flash plugins except gecko-mediaplayer 0.6.0: MIME Type=video/x-flv; Description=Flash Video; Suffixes=flv; Enabled=yes. Should I remove gecko-mediaplayer?

---

### Post by slayer^_^ on 2009-05-16
It seems that gecko-mediaplayer is set up to play flash videos for you... try removing it.

Try installing the package mozilla-mplayer instead of that one.

Let us know your results :D

p.s. A good idea is to, also, browse your Firefox Add-Ons and disable eventual flash players...

---

### Post by www.pjstemplates.com on 2009-05-16
yay, but don't forget that the adobe 64 bit flash plugin is still an alpha release... the point is that it works much better than the 32 bit version with nspluginwrapper!!!

---

### Post by marcelkoopman on 2009-05-17
> **adamthompson said:**
> Sorry for the vagueness. What I mean is that if I view a Web site that requires Flash, I see a message that I need to install the Adobe Flash Player and I don't see any Flash content. Depending on the Web site, I may see a non-Flash replacement (in Google Finance, for example).

Did you do the following:
sudo dpkg -i flash-amd64.deb

Restart Firefox, type this in the location bar:
about:plugins

Do you see this at the bottom: 

Shockwave Flashs, o
File name: libflashplayer.so
Shockwave Flash 10.0 r22

If yes, go to google finance and it should work.

---

### Post by northwestuntu on 2009-05-17
thanks slayer^_^ :p

your guide worked perfectly.  very simple to follow.  they should really sticky your guide.

---

### Post by adamthompson on 2009-05-17
slayer, I removed gecko-mediaplayer. Flash videos & charts still don't play. about:plugins now shows no plugin for flash.

marcelkoopman, I tried sudo dpkg -i flash-amd64.deb. The result was "cannot access archive: No such file or directory".

---

### Post by marcelkoopman on 2009-05-17
You need to download my deb at:
[http://members.lycos.nl/marcelk1607/flash-amd64.deb](http://members.lycos.nl/marcelk1607/flash-amd64.deb)

Then install it with:
sudo dpkg -i flash-amd64.deb

Please try it and let me know.

---

### Post by adamthompson on 2009-05-17
> **marcelkoopman said:**
> You need to download my deb at:
[http://members.lycos.nl/marcelk1607/flash-amd64.deb](http://members.lycos.nl/marcelk1607/flash-amd64.deb)

Then install it with:
sudo dpkg -i flash-amd64.deb

Please try it and let me know.

Marcel,

Sorry about my earlier idiotic response. I installed your deb as described above. It didn't help at all, I'm afraid. I still can't view any Flash content, and about:plugins shows no Flash plugin.

---

### Post by marcelkoopman on 2009-05-18
Are you using Firefox?

what is the contents of /usr/lib/mozilla/plugins?

---

### Post by adamthompson on 2009-05-18
> **marcelkoopman said:**
> Are you using Firefox?

what is the contents of /usr/lib/mozilla/plugins?

Yes, I am using Firefox. Version 3.0.10.

/usr/lib/mozilla/plugins$ ls
libflashplayer.so  libnpjp2.so  nphelix.so  nphelix.xpt

---

### Post by marcelkoopman on 2009-05-18
> **adamthompson said:**
> Yes, I am using Firefox. Version 3.0.10.

/usr/lib/mozilla/plugins$ ls
libflashplayer.so  libnpjp2.so  nphelix.so  nphelix.xpt
Can you remove realplayer? (You can reinstall it later)
Also try running firefox from the terminal, maybe you can see some debugging messages there.

---

### Post by adamthompson on 2009-05-18
> **marcelkoopman said:**
> Can you remove realplayer? (You can reinstall it later)
Also try running firefox from the terminal, maybe you can see some debugging messages there.

Thanks for the suggestions. I removed realplayer. I also ran Firefox from the terminal, and I did get some dubugging messages although they don't really seem relevant: 

LoadPlugin: failed to initialize shared library /usr/local/java/jre1.6.0_06/plugin/i386/ns7-gcc29/libjavaplugin_oji.so [/usr/local/java/jre1.6.0_06/plugin/i386/ns7-gcc29/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /opt/real/RealPlayer/mozilla/nphelix.so [/opt/real/RealPlayer/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]

---

### Post by marcelkoopman on 2009-05-19
It looks like you have 32 bit packages installed on 64-bit Ubuntu.
You installed the 64 bit Ubuntu right? Did you do an upgrade lately?

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by slayer^_^ on 2009-05-19
Indeed, are you using Ubuntu 32 or 64 bit?

If you're using Ubuntu 32 bit no way you can use this walkthrough...

Elseway I'd uninstall real player and Java... then do again what explained in this walkthrough and reinstall Java (and realplayer if yuo really need it...).

if you're using Jaunty 64 bit you can easily install java again through the packages, if you're using previous 64 bit ubuntu versions (i.e. Ibex, Heron...) I'd suggest this other walkthrough (again, done by me): [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

Let us know your progresses... ):P

---

### Post by adamthompson on 2009-05-19
> **slayer^_^ said:**
> Indeed, are you using Ubuntu 32 or 64 bit?

If you're using Ubuntu 32 bit no way you can use this walkthrough...

Elseway I'd uninstall real player and Java... then do again what explained in this walkthrough and reinstall Java (and realplayer if yuo really need it...).

if you're using Jaunty 64 bit you can easily install java again through the packages, if you're using previous 64 bit ubuntu versions (i.e. Ibex, Heron...) I'd suggest this other walkthrough (again, done by me): [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

Let us know your progresses... ):P

I am using Ubuntu 64 bit (and 64-bit Firefox). I removed realplayer and java. Then I reinstalled java using your walkthrough (thank you for the walkthrough). Then I followed the steps in this Flash walkthrough.  I'm no longer getting any errors when I run Firefox from the terminal. But I still can't view Flash content on Web sites and about:plugins in Firefox still shows no Flash plugin.

---

### Post by Vinno on 2009-05-19
Thanks for the tutorial, working great :)

---

### Post by zika on 2009-05-19
> **adamthompson said:**
> I am using Ubuntu 64 bit (and 64-bit Firefox). I removed realplayer and java. Then I reinstalled java using your walkthrough (thank you for the walkthrough). Then I followed the steps in this Flash walkthrough.  I'm no longer getting any errors when I run Firefox from the terminal. But I still can't view Flash content on Web sites and about:plugins in Firefox still shows no Flash plugin.
just check if You have it in right places:```
/home/zika/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```...
You migh have to create ~/.mozilla/plugins directory ...

---

### Post by adamthompson on 2009-05-19
> **zika said:**
> just check if You have it in right places:```
/home/zika/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```...
You migh have to create ~/.mozilla/plugins directory ...

Yes, I had it in /usr/lib/mozilla/plugins. I added it to ~/.mozilla/plugins, but I still can't view flash content and no flash player shows up in about:plugins.

locate libflashplayer.so
/home/myname/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by kawika molon labe patriot on 2009-05-19
aloha slayer MAHALO, THANK YOU, gracias, merci,Danke and respect. I have been searching for that very solution for months. I love linux and ubuntu but have been tired of it not working. so mahalo! now if I could just use the clipboard I'd be set.

---

### Post by slayer^_^ on 2009-05-20
> **adamthompson said:**
> Yes, I had it in /usr/lib/mozilla/plugins. I added it to ~/.mozilla/plugins, but I still can't view flash content and no flash player shows up in about:plugins.

locate libflashplayer.so
/home/myname/.mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Maybe I got it...

Try this:

1) There has to be only one - highlander 

```
sudo rm -f /home/myname/.mozilla/plugins/libflashplayer.so
```

2) Everybody must be able to use it - (citation needed)

```
SUDO CHMOD 777 /usr/lib/mozilla/plugins/libflashplayer.so
```


_Please let us know if it works for you, so I can update the tutorial for other users with your same problem !!!_

---

### Post by zika on 2009-05-20
> **slayer^_^ said:**
> Maybe I got it...

Try this:

1) There has to be only one - highlander 

```
sudo rm -f /home/myname/.mozilla/plugins/libflashplayer.so
```2) Everybody must be able to use it - (citation needed)

```
SUDO CHMOD 777 /usr/lib/mozilla/plugins/libflashplayer.so
```_Please let us know if it works for you, so I can update the tutorial for other users with your same problem !!!_
-1 on 1)
+1 on 2)

```
zika@zika-desktop:~$ locate libflashplayer.so
/home/zika/.mozilla/plugins/libflashplayer.so
/opt/flash/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```1. and 3. are symbolic links to 2. where the file is stored.
```
zika@zika-desktop:~/.mozilla/plugins$ ls -la
total 8
drwxr-xr-x 2 zika zika 4096 2009-03-29 19:23 .
drwx------ 6 zika zika 4096 2009-04-02 12:16 ..
lrwxrwxrwx 1 root root   28 2009-03-27 09:09 libflashplayer.so -> /opt/flash/libflashplayer.so
zika@zika-desktop:~/.mozilla/plugins$ cd /usr/lib/mozilla/plugins/
zika@zika-desktop:/usr/lib/mozilla/plugins$ ls -la
total 8
drwxr-xr-x 2 root root 4096 2009-04-14 16:54 .
drwxr-xr-x 4 root root 4096 2009-03-12 02:03 ..
lrwxrwxrwx 1 root root   28 2009-03-27 09:10 libflashplayer.so -> /opt/flash/libflashplayer.so
zika@zika-desktop:/opt/flash$ ls -la
total 9344
drwxr-xr-x 2 root root    4096 2009-03-27 09:02 .
drwxr-xr-x 6 root root    4096 2009-05-19 12:56 ..
-rwxr-xr-x 1 zika zika 9543400 2009-02-03 05:03 libflashplayer.so
```(I was writing this post just because I think flash doesn't work without libflashplayer.so in ~/.mozilla/plugins ... since I am now in a process of tweaking radeon and radeonhd and drm modules in 2.6.28 and 2.6.30 ... I am not in the mood to test it right now but will if necessity arises ... :), my notebook reflects the fact that it was like that at the time I was setting flash ... )

---

### Post by slayer^_^ on 2009-05-20
Isn't one of the symbolic links you posted a link to the /opt/flash folder only, and not to the plugin?

---

### Post by zika on 2009-05-20
> **slayer^_^ said:**
> Isn't one of the symbolic links you posted a link to the /opt/flash folder only, and not to the plugin?
corrected ... :) (in a process of cut and paste a line was truncated ...)

---

### Post by Siggma on 2009-05-20
> **zika said:**
> -1 on 1)
+1 on 2)

```
zika@zika-desktop:~$ locate libflashplayer.so
/home/zika/.mozilla/plugins/libflashplayer.so
/opt/flash/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```1. and 3. are symbolic links to 2. where the file is stored.
```
zika@zika-desktop:~/.mozilla/plugins$ ls -la
total 8
```
Come on guys. This HOW-TO is anything but simple.

Use the $HOME or ~ variable. None of us have a /home/zika folder and I ain't makin one. Not to mention that locate is unreliable unless you "updatedb" as root just before running it. Plus, there is no reason whatsoever to use /opt, it will only confuse you.

The following **will** work *if you have an amd64 installation*. But beware the playback is not any better. Full screen is still choppy and tears badly during playback.

DON'T JUST GRAB EVERY CODE BOX AND RUN IT.
First, let's fix the apple trailer bug that prevents HD videos from playing.

Follow this guide and return when finished:
[http://ubuntuforums.org/showthread.php?t=1162691](http://ubuntuforums.org/showthread.php?t=1162691)
[COLOR="Red"]Be sure to remove the line from your /etc/apt/sources.list or your updates will be all messed up.[/COLOR]

[Download the amd64 plugin from Adobe]("http://labs.adobe.com/downloads/flashplayer10.html").
*Unpack it to your Home Folder*. You'll see one file named libflashplugin.so Before you can use the amd64 version you need to remove nswrapper and all references to it. Then you can replace the 32-bit version of the plugin.

You CAN have two copies as long as they are actually copies, not different versions but it's stupid and it slows down firefox. First, run firefox from a console so you can see what it's doing.

```
firefox
```
THIS IS WHAT I SEE:
siggma@ubu:~$ firefox
siggma@ubu:~$ 

It's clean because I've removed plugins that don't load. If you see a reference to any .so, go to where it says it can't load it and delete the damn thing, then purge and reinstall the missing plugin. If it won't load it's worthless and it slows down firefox loading. If you completely mess up firefox you can delete and reinstall it without trashing your settings. The code below will reinstall firefox and the sun-java6-plugin. If you don't want the java plugin, remove the reference before pressing enter.

```

sudo apt-get purge firefox-3.0
sudo apt-get install firefox-3.0 sun-java6-plugin

```

Now let's clean up some of the plugins mess:
```

cd /usr/lib/mozilla/plugins/
sudo rm nsplugin*
ls 

```

You should see something like this:
siggma@ubu:/usr/lib/mozilla/plugins$ ls
libflashplayer.so  libtotem-cone-plugin.so  libtotem-mully-plugin.so        nphelix.so
libjavaplugin.so   libtotem-gmp-plugin.so   libtotem-narrowspace-plugin.so  nphelix.xpt

If you see any nsplugin crap, DELETE IT. 

Now back up one directory and see if there is a /usr/lib/nspluginwrapper DIRECTORY.
```

cd ..
ls

```
If you see the nsplugin* directory, delete it.
```
sudo rm -rf nsplugin*
```

Now we can replace the old flash plugin with the amd64 bit version you downloaded earlier.

```

cd /usr/lib/mozilla/plugins
sudo rm ~/./mozilla/plugins/libflashplugin.so
sudo rm /usr/lib/mozilla/plugins/libflashplugin.so
sudo cp ~/libflashplugin.so /usr/lib/mozilla/plugins

```

Now run firefox from a terminal:
```
firefox
```
It should load clean. If you see plugins that don't load you can safely remove them, they are easy to reinstall and if they don't load they are useless.

Firefox should now play flash and HD apple trailers correctly if you have the horsepower and the internet speed.
-Tom

---

### Post by slayer^_^ on 2009-05-20
Sorry Siggma, but I guess you didn't get some things...

1) This guide is not that hard if you just follow the first post and not the following replies... when something works i am adding it directly into the first post.

2) You can't have a zika folder because that's the name of the user that posted above (zika indeed)

3) We're trying to figure out why it works for the 80% of the users and for others it doesn't... I think it's a permission - related problem (as i posted in my last post... if it is confirmed, i am updating the first post)

4) Nobody copies and pastes automatically, this is a forum and everybody tries to figure out a solution for other users... and I see no reasons of complaining at all, everybody does his best for free.

---

### Post by Siggma on 2009-05-20
> **slayer^_^ said:**
> Sorry Siggma, but I guess you didn't get some things...

I got it. If it worked their would be a lot of working amd64 plugins. What's with the /opt/mozilla directory? It's unnecessary for a plugin. /opt is for extra stuff, not standard system fare like plugins.

It's not permissions. Root, su or sudo writes files as read world unless specified otherwise. Firefox does not need to write to the plugin, just read it. If you can see it in a directory you can read it.

It's more likely nspluginwrapper, duplicate plugins of differing architecture, video driver or other video related issue than a plugin issue if it won't load. Running firefox from a terminal will help debug plugins not loading. Asking if totem or mplayer plays OK is also an indicator. If gstreamer, xine or mplayer can't play a vid, flash won't either. And for the vast majority of people there is no reason at all to put a *necessity* plugin like flash in their home directory. It wastes disk space and increases the load time of firefox.

Plus, there are some useful updates in the totem-gstreamer branch of the karmic repo that can help stabilize firefox as a whole and correct the js script that loads HD videos.

Thats my take. Look at the poll results. 

Those who fail to learn from their own history are doomed to repeat it. Those who ignore their own history, they are simply doomed&#8230;

---

### Post by slayer^_^ on 2009-05-20
> I got it. If it worked their would be a lot of working amd64 plugins. What's with the /opt/mozilla directory? It's unnecessary for a plugin. /opt is for extra stuff, not standard system fare like plugins. 

That's why it's **not** mentioned in this guide...

> It's not permissions. Root, su or sudo writes files as read world unless specified otherwise. Firefox does not need to write to the plugin, just read it. If you can see it in a directory you can read it.


And if the permission is set for access only by the root user ? Have you thought about it ?

> 
It's more likely nspluginwrapper, duplicate plugins of differing architecture, video driver or other video related issue than a plugin issue if it won't load. 

That's exactly what this guide is **not** about... we're talking about native 64 bit flash. 

> Running firefox from a terminal will help debug plugins not loading. Asking if totem or mplayer plays OK is also an indicator. If gstreamer, xine or mplayer can't play a vid, flash won't either. 

This guide is specifically about the flash plugin... talking about mplayer or java too is nonsense.

> And for the vast majority of people there is no reason at all to put a *necessity* plugin like flash in their home directory. It wastes disk space and increases the load time of firefox.

In the guide I suggested to put the plugin in the /usr folder, not into the /home one... also because different users can use the same plugin. I suggested to put it into the /home folder just in case of necessity of limiting the plugin to a certain user. _But... have you read the guide or not before posting?_

> Plus, there are some useful updates in the totem-gstreamer branch of the karmic repo that can help stabilize firefox as a whole and correct the js script that loads HD videos.

But... are we talking about flash or what?

> Thats my take. Look at the poll results. 

I've seen that the guide is helpful  for 8 users on 10. That's a 4/5, I assume it's pretty good. And that's why everybody here is contributing to help the remaining 1/5

> Those who fail to learn from their own history are doomed to repeat it. Those who ignore their own history, they are simply doomed&#8230;

Is this supposed to be about me ?

---

### Post by zika on 2009-05-21
> **Siggma said:**
> Use the $HOME or ~ variable. None of us have a /home/zika folder and I ain't makin one. Not to mention that locate is unreliable unless you "updatedb" as root just before running it. Plus, there is no reason whatsoever to use /opt, it will only confuse you.
You are right when You say that none of us have a **/home/zika** folder. even I do not ...  that was written as example and I thought it was clear since my user-name here is, guess, _**zika**_. I did not say I recommend installing it in **/opt**, I just do and that way I can easily replace new version of plugin without changing anything in system folders ... if it confuses You, I am really sorry. if You read my post You will see that I was not proposing any kind of How-to but just giving the current state of affairs on my machine, ... be sure that I run updatedb on a regular basis and **locate** was used just to explain how these lists were generated. nowhere in my post I did not say that I'm giving a recipe for anything just giving ... never mind, ...  I was just trying to help, by giving the feedback to an effort to make a good How-to ... my mistake, I should have kept myself quiet ...
I simply suspect that You have not carefully read my post ...

---

### Post by marcelkoopman on 2009-05-21
I dont think its wise to remove things from /usr/lib/mozilla/plugins or .mozilla/plugins.
If you would later install a package you need to redo these things again.
This is why i made this deb package.
We should follow the ubuntu way, thats debian packages.
Removing files all over the place makes it hard to maintain.

---

### Post by zika on 2009-05-21
> **marcelkoopman said:**
> I dont think its wise to remove things from /usr/lib/mozilla/plugins or .mozilla/plugins.
If you would later install a package you need to redo these things again.
This is why i made this deb package.
We should follow the ubuntu way, thats debian packages.
Removing files all over the place makes it hard to maintain.
+1
(that is one of the reasons I use /opt ...)
all the stuff I removed from my system in pursuit of making 64-bit-flash work was uninstalled through synaptic ... that is also the reason I, sort of insist, on using both of these two folders because I want flash to work in any browser I choose to use ... and it does up to now and counting ... :)
to rephrase:Removing and putting files all over the place makes it hard to maintain.

---

### Post by marcelkoopman on 2009-05-21
I cannot test the debian package when people are removing and adding files everywhere. Please test the debian package and let us fix bugs for that.

---

### Post by zika on 2009-05-21
> **marcelkoopman said:**
> I cannot test the debian package when people are removing and adding files everywhere. Please test the debian package and let us fix bugs for that.
You must be aware of the fact that if simple unpack, copy, symbolic link making, can provide You completely working plugin not too many people are willing to try a .deb package they do not have control of ...
not to say that a proper .deb package should be able to determine a state of the system itself and act accordingly ... not all (if any) systems are in "mint" condition ...

---

### Post by marcelkoopman on 2009-05-21
> **zika said:**
> You must be aware of the fact that if simple unpack, copy, symbolic link making, can provide You completely working plugin not too many people are willing to try a .deb package they do not have control of ...
not to say that a proper .deb package should be able to determine a state of the system itself and act accordingly ... not all (if any) systems are in "mint" condition ...
I think you have total control over a debian package because you can easily remove it. And you have less control if you symbolic link files and add single files. Problem is that the debian package can not remove invalid plugings from .mozilla/plugins, so please dont add things there, it makes things impossible to maintain.

---

### Post by zika on 2009-05-21
> **marcelkoopman said:**
> I think you have total control over a debian package because you can easily remove it. And you have less control if you symbolic link files and add single files. Problem is that the debian package can not remove invalid plugings from .mozilla/plugins, so please dont add things there, it makes things impossible to maintain.
I beg to differ and I respect Your efforts to help the community ...
Ubuntu is about all of us being different but do not take our differences against each other ... :)

---

### Post by marcelkoopman on 2009-05-21
I want to help people. I just disagree with this approach of hacking files everywhere. I still believe creating a debian package is the best option.

---

### Post by unclejac on 2009-05-21
> **slayer^_^ said:**
> _**If you use a 64 bit version of Ubuntu**_ probably you would like to install a native 64 bit version of the flash player (that is far more stable than the version you install with the package flasplugin-nonfree ,  which is a 32 bit version of it emulated with nspluginwrapper)

It is very simple:



It works you know. Thanks very much! \\:D/

---

### Post by zika on 2009-05-21
> **marcelkoopman said:**
> I want to help people. I just disagree with this approach of hacking files everywhere. I still believe creating a debian package is the best option.
  if "You want endless discussion" goto [COLOR=Red]1[/COLOR] or re-read my last post
     else
  fi
[COLOR=Red]1[/COLOR] in order to define "best" we must define metric ... I do not plan to ... 

as far as I am concerned: over and out ...

---

### Post by slayer^_^ on 2009-05-21
May I enter the package \ non package discussion? :)

Well I don't think that creating a package is _not_ the **best** option, I think that is, of course, the **most simple**...

Let me state some points we could discuss, please...

1) This flash version is an alpha yet, asap an official release comes, hopefully the repository guys will add it into them, as for the 32 bit one, so tutorials or packages are, of course, a _transitory method_.

2) A .deb package is the most simple thing for newby users, but I believe that even them would read this tutorial after several efforts of making flash work on 64 bit more properly (i.e. after noticing that firefox crashes, that youtube goes gray etc. etc.). So we got to assume there are alternative flash players installed, wrong symbolic links created, packages that create conflict and whatever else would not let this tutorial or an eventual .deb package work properly. So, the .deb package should take care of removing several kinds of free or alternative flash plugins and several and different plugin configurations... I am not a package creator, but this purpose seems quite hard to obtain.

3) We got to assume **we are creating a transitory method**. Then we got to assume we are creating it **for people who read this forum**. What does it mean? Take a look at the poll... There's a 20% of users who couldn't make this tutorial (or .deb package) work. Te question is: why?

- Tutorial too difficult for newby users with a little experience on the terminal way;
- The tutorial doesn't consider other alternative flash plugins or alternative configurations, so it doesn't work even average users;

4) Having considered all this I suggest:

_Solution step 1) _ Creating a .deb package and putting it on top of the tutorial, specifying that newby users with little experience with configuration by terminal should try it as step one. Please note that I have written "creating a .deb package" because, in my humble opinion, it seems the very good one created and posted doesn't work for everyone. 

_Solution step 2)_ Taking care of average users who, following this tutorial, couldn't make the 64 bit flash plugin work, so we can understand eventual wrong or incomplete steps in the tutorial and updating it for the joy of the average users.

I know it seems I've discovered hot water, but this is just a statement on which way to follow... what do you think about it?

---

### Post by zika on 2009-05-21
> **slayer^_^ said:**
> what do you think abut it?
I read Your post at least 3 times and I could not find even a punctuation mark I could disagree with You on (and I do not think I did in my previous posts ... :) ). my only mistake was meddling in the discussion with my setup. my only intent was to help. 
as I said: all Ubuntu is about is all of us being different and we do not take our  differences against each other ... :smile:
as a mathematician myself I think I know how hard is to find a "solution" that work in (almost) all the cases ...

---

### Post by slayer^_^ on 2009-05-21
I am sorry, zika, maybe I wasn't very much clear on this point... Your experience and help, of course, is precious, welcome and appreciated.
Maybe I started this tutorial, but it of course belongs to the community right now, not just to me! What I wanted to do in my last post was tracing a kind of road-map to make this tutorial better and working for everyone.

Everyone's help is **of course** welcome, there shouldn't be any doubt about it. :)

---

### Post by zika on 2009-05-21
> **slayer^_^ said:**
> I am sorry, zika, maybe I wasn't very much clear on this point... Your experience and help, of course, is precious, welcome and appreciated.
Maybe I started this tutorial, but it of course belongs to the community right now, not just to me! What I wanted to do in my last post was tracing a kind of road-map to make this tutorial better and working for everyone.
Everyone's help is **of course** welcome, there shouldn't be any doubt about it. :)
no, I did not even contemplate that You were "against" me in any way. I was not clear enough myself leaving a doubt in my writing that You could understood as my bitterness. I, simply and clearly, do not like competition (which I not find in Your efforts to help) in process of helping others and that is the reason I might sounded wrong. I, also, dislike word "best" when no metric is given (I said already, that is mathematician in me speaking) ... glad I could participate in this thread ... hope I could be of any help ...
(tweaking is my vice, be it tweaking a computer, HiFi, or a car ... :) )

---

### Post by slayer^_^ on 2009-05-21
Thank you for your reply zika...

Excuse me if I go a bit Off Topic...

Well, being a Popper follower in the scientific field, I dislike too the word _"best"_, that's why I used the word _"better"_. 
Moreover, I was talkin', in my previous post, about _"the most simple"_ method.
Being the aim of my guides the spreading of Ubuntu and free- and open-source software, and being a way to reach this aim the perfect working of Linux for users who are undecided if using Linux or commercial OSes, I can assume that "the most simple" and "better", regarding methods, are sympathetic if not coincident in this case.

Too much Off-Topic in this thread, though... :D

Well, going back to the instructions\package thing, I would like to know which kind of instructions are executed by the package already posted in this guide. 
I was thinking about compiling a package that:
1) Pasted the plugin file into the /usr/lib/mozilla/plugin folder ;
2) Removed conflictual packages, alternative flash plugins and nspluginwrappered 32 bit flash versions.
If, however, these above are the same instructions executed by the package posted in this guide, all my efforts would be useless :D

C'mon, we can do it ;)

---

### Post by gretarsson on 2009-05-21
> **slayer^_^ said:**
> _**If you use a 64 bit version of Ubuntu**_ probably you would like to install a native 64 bit version of the flash player (that is far more stable than the version you install with the package flasplugin-nonfree ,  which is a 32 bit version of it emulated with nspluginwrapper)

It is very simple:


1) Download the 64 bit flash 10 plugin from here, and save it on the desktop: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

this is the link of the adobe labs download page for 64 bit flash player (just if you wanna check if new versions of it have been released...)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

if the link above should not work try downloading by this link (a bit elder version, though...)

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml)

2) Remove previous existing versions of flash player: type in terminal, string by string:

```

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so 

```

3) Open the terminal and execute your file manager with root privileges, for example in gnome (ubuntu):

```
gksu nautilus
```

4) Enter the /usr/lib/mozilla/plugins folder

5) Extract the package you downloaded on the desktop and drag and drop the "libflashplayer.so" file from the desktop to the folder.

6) Restart Firefox, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!

_If you're using the Opera browser:_

Do this **_only_** if, after having done point 4 and 5, you can't experience flash in Opera

7) Restart Opera and give a try to the youtube website. if flash doesn't work go forward:

8 ) Enter the /usr/lib/opera/plugins folder

9) Extract the package you downloaded on the desktop and drag and drop the "libflashplayer.so" file from the desktop to the folder.

6) Reboot Opera, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!

Bye ;)
Hi I hope you are not irritated about answer post like mine but I take a risk you are not but I have ubuntu 9.04 64bit and firefox 3 my adobe flashplayer was working and now it is not if i go to youtube it say I need to install adobe fl.player so I see your post and did what it say but still the same, first I clean all out and then downloaded newest fl.player and moved libflashplayer.so to usr/lib/mozilla/plugin as gksu nautilus but I see all flash player in plugin map have arrow on top but not
libflashplayer.so it is like mozilla can not see it. take a look on my picture
Thanks for the help

---

### Post by eris23 on 2009-05-22
1st post fixed most problems, but still can't get [http://www.imdb.com/video/wab/vi652476697/](http://www.imdb.com/video/wab/vi652476697/) to work.

---

### Post by zika on 2009-05-22
> **gretarsson said:**
> Hi I hope you are not irritated about answer post like mine but I take a risk you are not but I have ubuntu 9.04 64bit and firefox 3 my adobe flashplayer was working and now it is not if i go to youtube it say I need to install adobe fl.player so I see your post and did what it say but still the same, first I clean all out and then downloaded newest fl.player and moved libflashplayer.so to usr/lib/mozilla/plugin as gksu nautilus but I see all flash player in plugin map have arrow on top but not
libflashplayer.so it is like mozilla can not see it. take a look on my picture
Thanks for the help
try this:
```
sudo mkdir ~/.mozilla/plugins
sudo ln -s usr/lib/mozilla/plugin/libflasplayer.so ~/.mozilla/plugins/libflashplayer.so
```(it works for me, it doesn't mean that it is the right way to do it ... it can be undone easily)
(sudo might not be necessary here but ... this is what worked for me ...)
if it doesn't work we'll fix it, ... or at least we'll try ...
You could do this also as gksu in nautilus with going Home, then Ctrl-H to see hidden files, go to .mozilla, create folder plugins, and create link in that folder to usr/lib/mozilla/plugin/libflashplayer.so ... I'm a Terminal guy ... :)

---

### Post by martini1179 on 2009-05-22
So if I wanted to remove this flash player plugin, all I'd have to do is remove libflashplayer.so from /usr/lib/mozilla/plugins and restart the browser?

---

### Post by adamthompson on 2009-05-22
> **slayer^_^ said:**
> Maybe I got it...

Try this:

1) There has to be only one - highlander 

```
sudo rm -f /home/myname/.mozilla/plugins/libflashplayer.so
```

2) Everybody must be able to use it - (citation needed)

```
SUDO CHMOD 777 /usr/lib/mozilla/plugins/libflashplayer.so
```


_Please let us know if it works for you, so I can update the tutorial for other users with your same problem !!!_

I'm sorry to say that this didn't work either. I still can't view Flash content, and about:plugins lists no Flash plugin.

---

### Post by slayer^_^ on 2009-05-22
> **gretarsson said:**
> Hi I hope you are not irritated about answer post like mine but I take a risk you are not but I have ubuntu 9.04 64bit and firefox 3 my adobe flashplayer was working and now it is not if i go to youtube it say I need to install adobe fl.player so I see your post and did what it say but still the same, first I clean all out and then downloaded newest fl.player and moved libflashplayer.so to usr/lib/mozilla/plugin as gksu nautilus but I see all flash player in plugin map have arrow on top but not
libflashplayer.so it is like mozilla can not see it. take a look on my picture
Thanks for the help

libflashplayer.so hasn't got an arrow on it because it is a file, the other ones are symbolic links. Moreover it seems your firefox has recognized the plugin, because it is present in the plugin list. Have you rebooted firefox before trying?

Visit [about:plugins]("about:plugins") for more informations about your plugins...

---

### Post by slayer^_^ on 2009-05-22
> **martini1179 said:**
> So if I wanted to remove this flash player plugin, all I'd have to do is remove libflashplayer.so from /usr/lib/mozilla/plugins and restart the browser?

Yes... or just disable it through firefox ;)

---

### Post by slayer^_^ on 2009-05-22
> **adamthompson said:**
> I'm sorry to say that this didn't work either. I still can't view Flash content, and about:plugins lists no Flash plugin.

Sorry man, but have you tried :

1) In Firefox do : Tools --> Add-ons (or Plugins) --> Plugins 
and see if Shockwave flash is enabled or not?

2) In [about:plugins]("about:plugins") to check if another plugin is associated to the .swf and .spl file extension and selectively disable that plugin?

---

### Post by martini1179 on 2009-05-22
> **slayer^_^ said:**
> Yes... or just disable it through firefox ;)

Oh, word. I forgot about disabling via the addons menu. 

And if Adobe ever gets around to updating their 64-bit Linux flash player, I take it that I can just overwrite the old libflashplayer.so with the new one and restart. Correct?

---

### Post by slayer^_^ on 2009-05-22
> **martini1179 said:**
> Oh, word. I forgot about disabling via the addons menu. 

And if Adobe ever gets around to updating their 64-bit Linux flash player, I take it that I can just overwrite the old libflashplayer.so with the new one and restart. Correct?

I believe that as soon as adobe releases a stable (this is an alpha, even if it works pretty well) version of 64 bit flash player for linux, simply installing the package flashplugin-nonfree or flashplugin-installer should do the trick (i.e. overwriting previous versions of flash).

---

### Post by slayer^_^ on 2009-05-22
**_To everybody who has problems making this tutorial work_**

1) In Firefox do : Tools --> Add-ons (or Plugins) --> Plugins
and see if Shockwave flash is enabled or not.

2) In [about:plugins]("about:plugins") check if another plugin is associated to the .swf and .spl file extension and selectively disable or remove that plugin.

---

### Post by martini1179 on 2009-05-22
BTW, the tutorial is easy to follow and the plugin supposedly works perfectly (well, as well as an alpha can). I'm only asking about how to remove it because I'm having some problems with Firefox closing several times a day whenever I open a new tab, and an alpha is first on the list for removal to determine the cause.

---

### Post by gretarsson on 2009-05-22
> **slayer^_^ said:**
> libflashplayer.so hasn't got an arrow on it because it is a file, the other ones are symbolic links. Moreover it seems your firefox has recognized the plugin, because it is present in the plugin list. Have you rebooted firefox before trying?

Visit [about:plugins]("about:plugins") for more informations about your plugins...
Thanks for your reply if I do this about:plugins it say: "no plugin are istalled" but it is not right I have few plugins installed like java. see photo.
I had install adobe flash player from synaptic p manager before and it work fine but now it dont work so I follow your post and remove it from synaptic p m. and then I did same thing as you say in your post + I tried this too 
"sudo mkdir ~/.mozilla/plugins"
"sudo ln -s usr/lib/mozilla/plugin/libflasplayer.so ~/.mozilla/plugins/libflashplayer.so"
but still not working

---

### Post by slayer^_^ on 2009-05-22
> **gretarsson said:**
> Thanks for your reply if I do this about:plugins it say: "no plugin are istalled" but it is not right I have few plugins installed like java. see photo.
I had install adobe flash player from synaptic p manager before and it work fine but now it dont work so I follow your post and remove it from synaptic p m. and then I did same thing as you say in your post + I tried this too 
"sudo mkdir ~/.mozilla/plugins"
"sudo ln -s usr/lib/mozilla/plugin/libflasplayer.so ~/.mozilla/plugins/libflashplayer.so"
but still not working

I don't understand... Shockwave Flash, that's it, I can see it in your snapshot and it is installed... :o

---

### Post by gretarsson on 2009-05-22
> **slayer^_^ said:**
> I don't understand... Shockwave Flash, that's it, I can see it in your snapshot and it is installed... :oHi again 
I know but if I go to youtube or some wear player are needed it always say I need to install or upgrade my player see photo
but if you look in my priv photo you see all my plugins got arrow in corner but not libplayer.so way? and if I do about.plugins it say I dont have any???

---

### Post by adamthompson on 2009-05-22
> **slayer^_^ said:**
> Sorry man, but have you tried :

1) In Firefox do : Tools --> Add-ons (or Plugins) --> Plugins 
and see if Shockwave flash is enabled or not?

2) In [about:plugins]("about:plugins") to check if another plugin is associated to the .swf and .spl file extension and selectively disable that plugin?

1) In Tools -> Add-ons -> Plugins, there's no Shockwave Flash plugin to be enabled or disabled.

2) In about:plugins, no plugin is associated w/ .swf or .spl.

---

### Post by alliance1975 on 2009-05-22
Thank you Slayer, it worked perfectly.

---

### Post by Lutin on 2009-05-22
Thanks for that, worked a treat! :biggrin:

---

### Post by slayer^_^ on 2009-05-22
Jo jo... well, please post your experience !! I mean, please tell us if just following the tutorial worked or you needed some extra configuration steps. We all would be very glad to know :)

---

### Post by gretarsson on 2009-05-23
> **slayer^_^ said:**
> I don't understand... Shockwave Flash, that's it, I can see it in your snapshot and it is installed... :o Hi I found a way to fix my problem it only need to reinstall firefox in sy.pa.man. but thanks for all help

---

### Post by slayer^_^ on 2009-05-24
_**To everyone who couldn't get this tuorial to work:**_

I've just updated the previous-installed-flash removal informations. Please try this new version of the tutorial and let me know if it works for you.

---

### Post by zika on 2009-05-24
> **slayer^_^ said:**
> _**To everyone who couldn't get this tuorial to work:**_
I've just updated the previous-installed-flash removal informations. Please try this new version of the tutorial and let me know if it works for you.
I finally found some time to play with Flash. You were right. ~/.mozilla/plugins is not necessary (any longer) ... :)
(somewhere in the "history" of my Ubuntu meanderings I found that I needed Flash and Java plugins in that directory. At that time I was using FF from sub-folder in "home" folder so that might have been the reason. Now I am completely "straight" as all my applications reside in /usr/bin and are properly installed. so ... I admit You were right ... ;) )

---

### Post by fooman on 2009-05-24
this does work well,  but fullscreen flash still sucks.

i have found that using greasemonkey with the "youtube without flash" script runs fullscreen flash silky-smooth.

first grab greasemonkey (tools - add-ons) search for/install the greasemonkey extension.

then install this script:  

[http://userscripts.org/scripts/show/41722](http://userscripts.org/scripts/show/41722)

restart firefox,  browse to youtube,  click a video and when it pops up you will see options below the video window for "view without flash".  click on one of those and enjoy fullscreen youtube flash videos.  ;)

only trouble is it seems to only work on youtube.

---

### Post by Siggma on 2009-05-24
> **slayer^_^ said:**
> That's why it's **not** mentioned in this guide...
Referring to /opt/mozilla usage; Yes it is. In the post previous to what I replied to.

> And if the permission is set for access only by the root user ? Have you thought about it ?
Yes, as I said. sudo cp or root writes files with read world by default. So unless someone deliberately changed the permissions, in which case they don't really need this guide. In any case deleting and copying a fresh version will correct any permission issues. The plugin will not load if there are conflicting arch versions in any of the paths searched by firefox during init. Since most of us had a copy of the distribution flashplayer installed, it's possible there are remnants of it remaining; like the nspluginwrapper package. Both mozilla-flashplugin and nspluginwrapper need to be completely deleted or the amd64 plugin will not load. It's also possible that gnash or swfdec packages, which can be installed in parallel with 32bit flash will prevent the 64bit flash plugin from loading.

> That's exactly what this guide is **not** about... we're talking about native 64 bit flash. 
But if the flash plugin won't work you need to ask a few more questions. Does video even play? Did you install the mozilla-flashplugin package first? Do you see nspluginwrapper directories? Flash is an integrated, dependent package like most of ubuntu. If the dependencies are conflicting or not installed, it won't run.


> This guide is specifically about the flash plugin... talking about mplayer or java too is nonsense.
The title makes that clear. However, asking related questions *is clearly on the very topic of installing a working flash 64 plugin.*

> In the guide I suggested to put the plugin in the /usr folder, not into the /home one... also because different users can use the same plugin. I suggested to put it into the /home folder just in case of necessity of limiting the plugin to a certain user. _But... have you read the guide or not before posting?_
I did read your guide. It didn't work for me which is why I did some research and responded. I hope I didn't confuse anyone, that was not my intent. I've installed this thing on several different systems including debian lenny and ubuntu and it works fine as long as there are no conflicts like swfdec or gnash.


> Is this supposed to be about me ?
Why would you think it's about you? What I was pointing out is that the guide uses commands that are specific to you. It's easier to take 5 minutes and read other guides to glean things like "$HOME" or "~/libflash..." so users can copy what you've written and it will work.

---

### Post by zika on 2009-05-24
@Siggma: You've incorrectly attributed my posts (and inherent weaknesses in them) to slayer^_^...
[SIZE=4]**shame, guilt and blame are on me not on him ... :)**[/SIZE]
Just two notes:
1. I never put $HOME$ or ~/ in my posts since that way anybody that want to use it [SIZE=4]**can not**[/SIZE] do that by simply copy&paste ... 
2. I put stuff that is not "regularly" installed on [SIZE=6]**my**[/SIZE] machine(s) in /opt so I can keep the track of it ...

---

### Post by adrianx on 2009-05-24
> **zika said:**
> 1. I never put $HOME$ or ~/ in my posts since that way anybody that want to use it [SIZE=4]**can not**[/SIZE] do that by simply copy&paste ... 
Sorry to butt in - it's none of my business.... but if you did that then everybody would be able to copy & paste. Everybody can do "cd ~" and it will take them to their home directory. Or, am I missing something?

---

### Post by zika on 2009-05-24
> **adrianx said:**
> Sorry to butt in - it's none of my business.... but if you did that then everybody would be able to copy & paste. Everybody can do "cd ~" and it will take them to their home directory. Or, am I missing something?
sorry, I do not see Your point.
You want to just copy and paste?
OK.
You can do that but You will have to replace zika with adrianx or what ever ...
Is that too much to ask?
That way I introduce just a moment fro You to reconsider my advice, it might be wrong, it might be malicious ...
I do not say I am right but that is the way I see it and I hope that is not (and it surely have not been) the obstacle for most of the people to use the advice I might have ...
More than 25 years of teaching left a mark on me ... sorry ...
Please read the posts that led us to this discussion ... 
[http://ubuntuforums.org/showpost.php?p=7317216&postcount=129](http://ubuntuforums.org/showpost.php?p=7317216&postcount=129)
[http://ubuntuforums.org/showpost.php?p=7338715&postcount=171](http://ubuntuforums.org/showpost.php?p=7338715&postcount=171)
This discussion is leading us from the theme of this thread and I am done.
Over and out.

---

### Post by slayer^_^ on 2009-05-24
> Referring to /opt/mozilla usage; Yes it is. In the post previous to what I replied to.

It's not in my guide, I did not suggest it, I don't support it.

> Yes, as I said. sudo cp or root writes files with read world by default. So unless someone deliberately changed the permissions, in which case they don't really need this guide. In any case deleting and copying a fresh version will correct any permission issues.

Changing the permission was a trial for the few non-working users, it's not mentioned in the tutorial.

> The plugin will not load if there are conflicting arch versions in any of the paths searched by firefox during init. Since most of us had a copy of the distribution flashplayer installed, it's possible there are remnants of it remaining; like the nspluginwrapper package. Both mozilla-flashplugin and nspluginwrapper need to be completely deleted or the amd64 plugin will not load. It's also possible that gnash or swfdec packages, which can be installed in parallel with 32bit flash will prevent the 64bit flash plugin from loading.

Thank you for the lesson, I already knew it... that's why the tutorial has a lot of strings that aim to remove every single remnants of previous flash installations. Most of them are redundant, just to be sure. Thank you but I already knew the things you posted, that's why they were already mentioned in the tutorial. The problem is that, maybe, there were some destinations not considered. 
_The problem is to find all the present flash alternatives_ and, as you can see by the increasing number of parameters in the tutorial, that's what I am trying to do.

> But if the flash plugin won't work you need to ask a few more questions. Does video even play? Did you install the mozilla-flashplugin package first? Do you see nspluginwrapper directories? Flash is an integrated, dependent package like most of ubuntu. If the dependencies are conflicting or not installed, it won't run.

That's the first thing I've done...

> The title makes that clear. However, asking related questions *is clearly on the very topic of installing a working flash 64 plugin.*

Related to Flash YES. Related to Java or mplayer-plugin NOT. It creates confusion.

> I did read your guide. It didn't work for me which is why I did some research and responded. I hope I didn't confuse anyone, that was not my intent. I've installed this thing on several different systems including debian lenny and ubuntu and it works fine as long as there are no conflicts like swfdec or gnash.

It's not me or you the problem, then, it's the non-working users... If it was my pc I could get it working in one minute. But I am trying to help other users by a forum, knowing absolutely not enough about their configuration or the installed packages. It's not easy. The problems are single and different, that's why posts should be short and focused. Posting another tutorial every post, posting different methods that are absolutely equal to the tutorial, explaining how ubuntu works to the one who has written the guide and, most important, going off-topic _doesn't make things easier_.


> Why would you think it's about you? What I was pointing out is that the guide uses commands that are specific to you. It's easier to take 5 minutes and read other guides to glean things like "$HOME" or "~/libflash..." so users can copy what you've written and it will work.

Once again, _the guide is the first post of this thread ok_?? The other posts are proposals of solutions for those who can't make this tutorial work and proposals to make this tutorial simpler. And, once again, I ask you if you have really read the tutorial before posting in thread, because there are no commands specific to my computer, my configuration or my folders. Please read twice before posting, what shall i say?

**Again**: eEveryone's help is needed and welcome, of course. However, please, focus on the problems of the non-working users. As soon as single problems are solved, I am updating the first post of this thread, ok ???

**Again 2**: As I've written shortly above, the guide has been updated with more recent and more complete previous-flash-removal strings. Please try it and then post your experience (if negative with as more info as you can provide).

---

### Post by slayer^_^ on 2009-05-24
> **zika said:**
> sorry, I do not see Your point.
You want to just copy and paste?
OK.
You can do that but You will have to replace zika with adrianx or what ever ...
Is that too much to ask?
That way I introduce just a moment fro You to reconsider my advice, it might be wrong, it might be malicious ...
I do not say I am right but that is the way I see it and I hope that is not (and it surely have not been) the obstacle for most of the people to use the advice I might have ...
More than 25 years of teaching left a mark on me ... sorry ...
Please read the posts that led us to this discussion ... 
[http://ubuntuforums.org/showpost.php?p=7317216&postcount=129](http://ubuntuforums.org/showpost.php?p=7317216&postcount=129)
[http://ubuntuforums.org/showpost.php?p=7338715&postcount=171](http://ubuntuforums.org/showpost.php?p=7338715&postcount=171)
This discussion is leading us from the theme of this thread and I am done.
Over and out.

I totally agree.
Please everybody stay calm and go back to the thread basics.

---

### Post by Elfy on 2009-05-24
> Please everybody stay calm and go back to the thread basics.I totally agree.

---

### Post by OriTheEep on 2009-05-24
Thanks, Slayer. I wish I'd spotted this tutorial before starting to pull all my hair out over Firefox plugins. Still have to get Realplayer or a substitute working and work out what went wrong with installing Java. Then I've got to...

Linux is more problematic than I'd expected but I'll stick with it.

Does Linux not have an equivalent to a DOS batch file or is that what a .deb is? I ask because repeating <highlight>, CTRL-INS, ALT-TAB, SHIFT-INS, ENTER, ALT-TAB over and over again could have led to missed lines. I'd have rather copied the whole block of text into a file and executed that.

:confused:

---

### Post by zika on 2009-05-25
> **OriTheEep said:**
> work out what went wrong with installing Java
You might want to take a look at a thread we had about Java ... [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) ...

---

### Post by slayer^_^ on 2009-05-25
> **OriTheEep said:**
> Thanks, Slayer. I wish I'd spotted this tutorial before starting to pull all my hair out over Firefox plugins. Still have to get Realplayer or a substitute working and work out what went wrong with installing Java. Then I've got to...

Linux is more problematic than I'd expected but I'll stick with it.

Does Linux not have an equivalent to a DOS batch file or is that what a .deb is? I ask because repeating <highlight>, CTRL-INS, ALT-TAB, SHIFT-INS, ENTER, ALT-TAB over and over again could have led to missed lines. I'd have rather copied the whole block of text into a file and executed that.

:confused:

...and this is my thread about Java : [http://ubuntuforums.org/showthread.php?t=1155925](http://ubuntuforums.org/showthread.php?t=1155925)

choose the one you like the most and have fun :°D

p.s. I always preferred the "copy and paste" method, it makes you aware of what you are doing (simply executing whatever you can sounds like weendous :D). You can, however, copy and paste the lines into a text file, make it executable rom the properties and run it :P

---

### Post by OriTheEep on 2009-05-25
> **zika said:**
> You might want to take a look at a thread we had about Java ... [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) ...

> **slayer^_^ said:**
> ...and this is my thread about Java : [http://ubuntuforums.org/showthread.php?t=1155925](http://ubuntuforums.org/showthread.php?t=1155925)

choose the one you like the most and have fun :°D

Thanks for the replies, zika and slayer^_^. I looked at the threads and, in my simple way, decided that the simpler seeming and more recent post would suit me better until I found some sort of foothold. I even managed to mess the simple one up! :(

> **slayer^_^ said:**
> p.s. I always preferred the "copy and paste" method, it makes you aware of what you are doing (simply executing whatever you can sounds like weendous :D). You can, however, copy and paste the lines into a text file, make it executable rom the properties and run it :P

Thanks for that! I'm learning more all the time.

"weendous"? :-s

---

### Post by alliance1975 on 2009-06-05
Slayer,

Used your guide without problem on previous 9.04 -64 install. For other reasons had to reinstall 9.04-64. Followed guide again and had problems. Despite purge instructions, about:plugins listed flash10 and flash9.22 or something like that. Disabled flash 9 but am still concerned about old stuff hanging around. I do not want to run janitor as that caused the above problems that made me reinstall 9.04-64. Any suggestions?

---

### Post by Koltor on 2009-06-08
Thank you so much, it worked perfectly. The current stick doesn't work and causes firefox to crash repeatedly. Your solution worked the first time! :D

---

### Post by slayer^_^ on 2009-06-09
> **alliance1975 said:**
> Slayer,

Used your guide without problem on previous 9.04 -64 install. For other reasons had to reinstall 9.04-64. Followed guide again and had problems. Despite purge instructions, about:plugins listed flash10 and flash9.22 or something like that. Disabled flash 9 but am still concerned about old stuff hanging around. I do not want to run janitor as that caused the above problems that made me reinstall 9.04-64. Any suggestions?

I am very busy at the time... I'll write a complete reply at the end of the week... sorry :(

---

### Post by brotherlen on 2009-06-09
Thank you very much.

---

### Post by shane2peru on 2009-06-10
hmm, help I tried this on my wife's Hardy 64bit installation and it doesn't work.  She can't use her facebook thing.  That isn't a good thing.  Any ideas?  I'm pretty apt with command line, and didn't have any problems installing it, I'm wondering if there was/is a problem with Hardy and Flash10?  is that possible?

Shane

---

### Post by shane2peru on 2009-06-10
Hmm, for some reason this worked for me:  
[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

I think for some reason some links or something were hanging around.  I noticed this script also makes an extra link or so.  Other than that the ways are about the same.  This worked for me. 

Shane

---

### Post by pragmaticist logos on 2009-06-12
thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you, slayer^_^ !

---

### Post by kTizRuLeZd00d! on 2009-06-12
Wow, thanks a bunch man!
I followed all of the directions exactly, and it worked fine.

I've been looking for something like this to work for a long time, thanks! :D

---

### Post by kneewax on 2009-07-02
great solution. Thank you, been trying to get Flash10 working since it was released.  Thanks

---

### Post by alphapupster on 2009-07-04
> **slayer^_^ said:**
> _**If you use a 64 bit version of Ubuntu**_ probably you would like to install a native 64 bit version of the flash player (that is far more stable than the version you install with the package flasplugin-nonfree ,  which is a 32 bit version of it emulated with nspluginwrapper)

It is very simple:


1) Remove previous existing versions of flash player: type in terminal, string by string:

_This code has been updated. Please try it if you had problems with this tutorial before._

```

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/mozilla/plugins/*flash*

```

2) Download the 64 bit Flash Plugin (Alpha) from its website:

```
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
```

this is the link of the adobe labs download page for 64 bit flash player (just if you wanna check if new versions of it have been released...)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

(If you are downloading a newer release and this guide shouldn't have been updated at the time, just put the file in you "home" folder and change the next terminal commands to fit the new name of the file...)

3) Extract the archive:

```
sudo tar xzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
```

4) Move it in its folder:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
```

5) Restart Firefox, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!


_If you're using the Opera browser:_

Do this **_only_** if, after having done point 4 and 5, you can't experience flash in Opera

4) Maybe Opera isn't searching into the Mozilla Plugins folder, then let's put the Flash plugin in its folder. The steps are the same as above, the only difference is step 4:

```
sudo mv libflashplayer.so /usr/lib/opera/plugins
```

5) Reboot Opera, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!


Bye ;)

As a new user this was an amazing exercise and it worked! My only suggestion is to reboot with Firefox as well, if necessary. It was for me. 
Yep, the Linux learning curve is steep but the freedom and control is worth it. And there's a lot of great info., guides, and good coding to copy and paste as the above. Great stuff! 

Thanks again! :-D
alphapupster

---

### Post by akniss on 2009-07-04
I just tried this, and flash indeed works... However now Gmail causes firefox to seg fault each time I visit the page.  Which is a very bad regression.  How do I undo this? or fix the crashing problem?

---

### Post by Wlo on 2009-07-05
I'm going a bit nuts here, nothing seems to work for me.  Could someone give me a sanity check please?

I'm running Jaunty 64bit with Firefox 3.5.

I've tried libflashplayer.so in both /usr/lib/mozilla/plugins and ~/.mozilla/plugins.

An "about: plugins" in Firefox only shows two plugins (both veetle ones) but not flash.  These two other veetle plugins are located ~/.mozilla/plugins , which makes me think that's the correct place for it.

[email]rolo@motherbrain:~/.mozill[/email]a/plugins$ ls -l
total 23492
-rwxr-xr-x 1 rolo rolo  9543400 2009-07-04 08:56 libflashplayer.so
-rwxr-xr-x 1 rolo rolo  1068704 2009-02-05 01:24 libveetle-core-plugin.so
-rwxr-xr-x 1 rolo rolo 13401584 2009-02-05 01:24 libveetle-player-plugin.so

I've rebooted several times, tried downloading the plugin again, and I've nuked everything with both the script in this thread, and a script in another thread.  Any other ideas?  Is there somewhere I can see the log of whether Firefox is attempting to load the plugin?

Thanks loads for any assistance.  FF is mighty unstable with the current release version of Flash so am hoping this 64bit version does the trick.

Cheers.

Wlo.

---

### Post by Wlo on 2009-07-06
Right, sussed this.

The problem is, UbuntuZilla installed the 32bit version of Firefox 3.5.

You can check which one you're running by typing about:buildconfig into the FF address bar.

I installed the 64 bit build of FF and now it's recognizing the flash plugin :>.

To install 64bit FF build follow instructions here, [http://www.google.co.uk/search?q=firefox+3.5+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=firefox+3.5+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) .

Wlo.

---

### Post by Ejene on 2009-07-15
Thanks for the fix! I'm one step further to moving from Firefox to Opera!

---

### Post by martini1179 on 2009-07-17
Apparently, some people have gotten Flash to work in the latest Chromium alphas: [http://ubuntuforums.org/showthread.php?t=1207863](http://ubuntuforums.org/showthread.php?t=1207863)

How can we get this excellent workaround to work with Chromium?

---

### Post by slayer^_^ on 2009-07-17
> **martini1179 said:**
> Apparently, some people have gotten Flash to work in the latest Chromium alphas: [http://ubuntuforums.org/showthread.php?t=1207863](http://ubuntuforums.org/showthread.php?t=1207863)

How can we get this excellent workaround to work with Chromium?

try putting the libflashplayer.so file in the directory /usr/lib/chromium-browser/plugins instead of /usr/lib/mozilla/

You can follow the instructions given in the first post of this guide changing the name of the folder as specified below...


However Chrome for linux is quite experimental and they say flash doesn't work... so why losing time?

---

### Post by martini1179 on 2009-07-23
> **slayer^_^ said:**
> try putting the libflashplayer.so file in the directory /usr/lib/chromium-browser/plugins instead of /usr/lib/mozilla/

You can follow the instructions given in the first post of this guide changing the name of the folder as specified below...


However Chrome for linux is quite experimental and they say flash doesn't work... so why losing time?

I was able to get Flash to work on Chromium by downloading the 32-bit Flash .tar.gz file and then moving the 32-bit libflashplayer.so from the desktop (where I originally saved it) by typing 

```
sudo mv Desktop/libflashplayer.so /usr/lib/chromium-browser/plugins/
```Just start/restart Chromium and viola!

Oh, and make sure that you start Chromium with --enable-plugins.

---

### Post by maruchan on 2009-07-28
I have the same problem with GMail crashing. Not fun, but Flash seems to work OK...:P

---

### Post by merlin666 on 2009-08-04
> **Wlo said:**
> I'm going a bit nuts here, nothing seems to work for me.  Could someone give me a sanity check please?

I'm running Jaunty 64bit with Firefox 3.5.



Is flash possible with Jaunty and Shiretoko?

---

### Post by maruchan on 2009-08-04
I'm using Jaunty and Shiretoko, and Flash works, but the Flash plugin likes to crash (fortunately not when I'm in the middle of anything).

---

### Post by merlin666 on 2009-08-05
Sweet, this actually installed flash for both Shiretoko and Firefox 3.0:

sudo mv libflashplayer.so /usr/lib/mozilla/plugins

Also noticed the occasional crash of FireFox - this was annoying as I have the session restore enabled and it would just crash again. NoScript, Flashblock or other add-ons can help control crashes sometimes.

---

### Post by zelhar on 2009-08-22
Why do some people use these commands after flash install while others omit them ?  
> echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/xulrunner-addons/plugins/

---

### Post by maruchan on 2009-08-22
> **zelhar said:**
> Why do some people use these commands after flash install while others omit them ?

If you use vuze, liferea, rsswol, or other applications that are based on Mozilla code, they'll need to know where the Flash plugin is.

It's optional. Some people care, others don't.

---

### Post by Cresho on 2009-08-22
I don't know what astro is but my 32bit on a 64bit flash 10 works fine.  There is a script that works but you need to throw the commands at it line by line and correct some of the old links and new package errors that it spits out.

---

### Post by javanet22 on 2009-09-20
Worked great for me......thanks

---

### Post by alotofloudcheese on 2009-09-24
this worked great for me as well. Thank You

---

### Post by Cornbreadly on 2009-10-08
I am wondering if anyone has had issues with port 9339?

I am trying to use the website planning app [www.hotgloo.com](www.hotgloo.com), and I was getting errors saying my 9339 port is firewalled.  

It is not.  I googled "flash 10 port 9339" and I got some hits indicating that there may be a bug in flash 10 (poker app in facebook doesnt work).

I tried the latest 64 version (great walkthrough btw) and now I get timed out messages instead of the port is firewalled.  I guess I could downgrade, but I could not find a flash 9 linux 64 version out there.

Any suggestions?

---

### Post by merlin666 on 2009-10-08
> **Cornbreadly said:**
> I am trying to use the website planning app [www.hotgloo.com](www.hotgloo.com), and I was getting errors saying my 9339 port is firewalled.  


I tried this site and when I enable the flash it crashes the browser.

---

### Post by Cornbreadly on 2009-10-08
> **merlin666 said:**
> I tried this site and when I enable the flash it crashes the browser.

The app is nice enough to want to figure out this bug.  I have used it on xp machines.  I would hate to have to go back to dual booting at home FOR A WEB APP.

Is there a way to force flash to use another port while still connecting with hotgloo the way it needs?

---

### Post by x C0MMAND0 x on 2009-10-08
This process works.  My biggest problem was that I did not remove all of the old flash crap I had in the first place.  I had extracted the file properly but it did not work 100% until I had removed all of the old files.

---

### Post by hanx9999 on 2009-10-09
Worked perfectly for me thanks a lot for thread. :guitar:firefox is rock'n now.

---

### Post by Donnchad on 2009-10-10
Using the 64bit plugin I get browser crashes on many websites, yet I have no issues using the 32bit plugin through the wrapper.  I also have found that compiz can cause issues with flash and using metacity eliminates them.

---

### Post by jt_04 on 2009-11-01
> **Wlo said:**
> The problem is, UbuntuZilla installed the 32bit version of Firefox 3.5.

You can check which one you're running by typing about:buildconfig into the FF address bar.

I installed the 64 bit build of FF and now it's recognizing the flash plugin :>.

To install 64bit FF build follow instructions here, [http://www.google.co.uk/search?q=firefox+3.5+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=firefox+3.5+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) .

Wlo.

i believe that this is also my problem.  i used ubuntuzilla to install firefox 3.5.3 and when i type "about:buildconfig" it says "i686-pc-linux-gnu", leading me to believe that it is NOT 64 bit firefox.

how can i install 64-bit firefox 3.5?  google searches seem to be fruitless.  I explored the released versions on ftp.mozilla.org but the only 3.5 that exists there for linux appears to be the i686 one, which is not a 64 bit version?

edit: [this post]("http://blog.cosmix.org/2009/06/23/we-don%E2%80%99t-have-64-bit-support-for-linux-in-3-5/") makes it seem like 64-bit firefox 3.5 for linux does not exist

after re-installing 32bit flashplayer, i now have flash in 32-bit firefox 3.5 on my 64 bit machine.

---

### Post by slayer^_^ on 2009-11-02
> **jt_04 said:**
> i believe that this is also my problem.  i used ubuntuzilla to install firefox 3.5.3 and when i type "about:buildconfig" it says "i686-pc-linux-gnu", leading me to believe that it is NOT 64 bit firefox.

how can i install 64-bit firefox 3.5?  google searches seem to be fruitless.  I explored the released versions on ftp.mozilla.org but the only 3.5 that exists there for linux appears to be the i686 one, which is not a 64 bit version?

edit: [this post]("http://blog.cosmix.org/2009/06/23/we-don%E2%80%99t-have-64-bit-support-for-linux-in-3-5/") makes it seem like 64-bit firefox 3.5 for linux does not exist

after re-installing 32bit flashplayer, i now have flash in 32-bit firefox 3.5 on my 64 bit machine.

1) Upgrade to 9.10 karmic koala and you'll get Firefox 3.5.3

2) Install the package firefox-3.5 and you'll have a new browser (called shiretoko) that is just the new firefox... Have fun !!

---

### Post by zika on 2009-11-02
You might need **ppa:ubuntu-mozilla-daily/ppa** to install firefox-3.5  and, while You are there, check out firefox-3.6 and firefox-3-7 ...

---

### Post by merlin666 on 2009-11-02
> **slayer^_^ said:**
> 1) Upgrade to 9.10 karmic koala and you'll get Firefox 3.5.3


My friend upgraded to Karmic (32-bit) and it caused a mess with the flash-plugin. The fix was not straightforward. How well is flash working in 64-bit Karmic?

---

### Post by Flywaver on 2009-11-02
Thank you slayer^_^
It worked perfectly in 9.10 and FF 3.5.5! :)

---

### Post by Flywaver on 2009-11-02
Ok, for some odd reason the trick worked...until I closed FF and restarted it again! :o

---

### Post by jt_04 on 2009-11-02
> **slayer^_^ said:**
> 1) Upgrade to 9.10 karmic koala and you'll get Firefox 3.5.3

2) Install the package firefox-3.5 and you'll have a new browser (called shiretoko) that is just the new firefox... Have fun !!

i have the 64-bit karmic koala but firefox 3.5.3 is still 32bit. :sad: hopefully firefox 3.7 will be available in 64 bit.

---

### Post by slayer^_^ on 2009-11-05
> **jt_04 said:**
> i have the 64-bit karmic koala but firefox 3.5.3 is still 32bit. :sad: hopefully firefox 3.7 will be available in 64 bit.

i've got karmic koala and i've got firefox 3.5.4 64 bit by default...

---

### Post by zika on 2009-11-05
> **slayer^_^ said:**
> i've got karmic koala and i've got firefox 3.5.4 64 bit by default...I have 3.5, 3.6 and 3.7 (mozilla-daily ppa) all in 64-bit ...

---

### Post by boublik on 2009-11-05
Very Simple indeed. Got firefox 3.5.3 by default with the Karmic 64 and worked beautifully. 
Thanks

---

### Post by jt_04 on 2009-11-05
> **slayer^_^ said:**
> i've got karmic koala and i've got firefox 3.5.4 64 bit by default...

how to you tell?  I used "about:buildconfig" and it returned this.  is that the right way to check?

> Source

Built from [http://hg.mozilla.org/releases/mozilla-1.9.1/rev/0da982f65d37](http://hg.mozilla.org/releases/mozilla-1.9.1/rev/0da982f65d37)
Build platform
target
i686-pc-linux-gnu

Build tools
Compiler 	Version 	Compiler flags
/tools/gcc/bin/gcc 	gcc version 4.1.2 20061011 (Red Hat 4.1.1-29) 	-Wall -W -Wno-unused -Wpointer-arith -Wcast-align -W -Wno-long-long -pedantic -gstabs+ -fno-strict-aliasing -pthread -pipe -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions -finline-limit=50
/tools/gcc/bin/g++ 	gcc version 4.1.2 20061011 (Red Hat 4.1.1-29) 	-fno-rtti -fno-exceptions -Wall -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof -Wno-long-long -pedantic -gstabs+ -fno-strict-aliasing -fshort-wchar -pthread -pipe -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions -finline-limit=50

Configure arguments
--enable-application=browser --enable-optimize --enable-update-channel=release --enable-update-packaging --disable-debug --disable-tests --enable-official-branding 

the 64bit flashplayer won't work for me but the 32 bit will, so that was another clue that led me to believe that i don't have 64 bit firefox.

---

### Post by eris23 on 2009-11-05
My target is:

x86_64 (64bit)

Yours is i686 (32bit)

---

### Post by Jenkins1 on 2009-11-06
Hi,

edit:It now works however i still can't click any falsh buttons without right clicking first. I have attached my about:plugins page for flash.

I have followed all of the instructions in the first post any ideas? Is this just because its an alpha?

---

