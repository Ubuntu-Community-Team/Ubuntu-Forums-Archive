---
title: "I can't get flash to work with firefox."
date: 2009-10-25
forum: x86 64-bit Users
---

### Post by jamily on 2009-10-25
"A man has to know his limits" -- Dirty Harry

I am new to Ubuntu and despite a few problems, I love it. One of the biggest problems is I can't get flash to work in firefox. This is a big problem. I have tried quite a few things. I even upgraded firefox to version 3.5.3 when I couldn't get flash to work with the original firefix, hoping this will help (strangely the "check for upgrades" is not active in the Help menu in Firefox 3.5.3).

I am running 64bit Ubuntu 9.04.

I have checked Synaptic Package Manager, searching under "flash" and made sure that all flash stuff is uninstalled. Then I do the following in the bash shell (making sure firefox is closed first):

sudo aptitude purge flashplugin-nonfree
sudo apt-get clean && sudo apt-get autoremove
sudo aptitude install flashplugin-nonfree

Everything looks like it goes fine.  However, when I open firefox and go to [www.youtube.com]("http://www.youtube.com/") and try to play a video, I can't even see the video.  Instead I get the message:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

A contributor by the name of Zita, wrote on April 6th 2009 that

"flashplugin-nonfree is still 32-bit (as far as I know) so that might be the valid reason for 64-bit users ...
I agree with You in the sense that flashplugin-nonfree is more reliable for less demanding users but You must agree that there is a difference in quality of use for more demanding users on 64-bit installations ...
we have to have a way of circumventing the fact that 64-bit plugins exists and is easily installable but is not yet offered through regular ways ..."

I don't know what to make of this.  I heard that firefox is still 32 bit (but as I mentioned, my system is 64 bit).

Next I uninstalled flashplugin-nonfree again from Synaptic Package and did a 

sudo aptitude purge flashplugin-nonfree
sudo apt-get clean && sudo apt-get autoremove

then I downloaded "libflashplay-10.0.32.18.linux-x86_64.so.tar.gz" from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).  Uncompressed
and did a 

sudo mv libflashplayer.so /usr/lib/mozilla/plugins

I then rebooted and it still did not work.  

Thinking maybe java was required and not working I installed ubuntu-restricted-extras from Synaptic Package Manager and tried again. Still does not work.

I have installed gnash and that did not work.  (it is now uninstalled).

Any ideas? Looking on the web this seems to be a major problem (maybe the biggest?) users are having with Ubuntu. If anyone could help, I would be mucho grateful.

---

### Post by macaholic on 2009-10-25
[This]("http://dl.getdropbox.com/u/307214/native-64bit-flash-installer.sh") is a slightly modified version of a script I found here: [http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html) (I changed the downloaded flash version to the lastest release). 
Things to note: It will quit firefox, so if you are doing anything critical in firefox, finish before running this script. Also, make sure you run a chmod +x on the .sh file so it can be executed.
Hope that helps!

---

### Post by jamily on 2009-10-25
macaholic,

Thanks for your advice.  I read the script (it looked fine).  Reading the website you gave, it seems this script has served other folks very well.  I ran the script you gave me and it seemed to run just fine.  However, I still can not get youtube video (youtube error message, "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/")."

I have spent a lot of time at this and I am completely stuck.  Now that I have tasted ubuntu I would hate to have return to microsoft's world several times a day just to use flash.

I appreciate your help.

---

### Post by oldos2er on 2009-10-25
[http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

---

### Post by jamily on 2009-10-25
By the way, I have no idea if this is relevant, or even what it means, but here is a command are reply I get in terminal,

mhm@TURK:~/comp/unix$ aptitude search swf | grep mozilla
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F

---

### Post by jamily on 2009-10-25
oldos2er,

Thanks for the script.  I ran it and again, it ran fine but I still have no flash and I still get

mhm@TURK:~/comp/unix$ aptitude search swf | grep mozilla
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F

I appreciate the help.

---

### Post by oldos2er on 2009-10-25
> **jamily said:**
> oldos2er,

Thanks for the script.  I ran it and again, it ran fine but I still have no flash and I still get

mhm@TURK:~/comp/unix$ aptitude search swf | grep mozilla
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F

I appreciate the help.

 Uninstall the package swfdec-mozilla.

---

### Post by macaholic on 2009-10-25
> **jamily said:**
> oldos2er,

Thanks for the script.  I ran it and again, it ran fine but I still have no flash and I still get

mhm@TURK:~/comp/unix$ aptitude search swf | grep mozilla
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F

I appreciate the help.

That's a command that's searching for any package installed with "swf" in the name, and returning anything from that which contains "mozilla". If that's returning swfdec-mozilla, then neither script is working correctly, and you should uninstall it manually.

---

### Post by jamily on 2009-10-25
> **oldos2er said:**
> Uninstall the package swfdec-mozilla.
oldos2er (Ann),

I checked with Synaptic Package Manager and swfdec-mozilla was not installed.  Just to make sure I installed it and then did a complete removal.  I then ran the script you gave me again.  Results below:

mhm@TURK:~/comp/unix/flash$ Get64bitFlash 
mkdir: cannot create directory `/tmp/pluginstall': File exists

 This script is used to setup the Flash 10 Alpha. 
 By entering yes below you acknowlage that you 
 are installing development software and you 
 will file bug reports with Adobe for every 
 problem you incounter.

 Do you agree? yes or no : 
(please type the whole word in lower case letters)yes
Flash installing.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswfdec-0.8-0 libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswfdec-0.8-0 libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswfdec-0.8-0 libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2009-10-25 14:09:37--  [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
Resolving download.macromedia.com... 96.6.163.191
Connecting to download.macromedia.com|96.6.163.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3727613 (3.6M) [application/x-gzip]
Saving to: `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.4'

100%[===================================================================================================================================>] 3,727,613    348K/s   in 10s     

2009-10-25 14:09:48 (347 KB/s) - `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.4' saved [3727613/3727613]

libflashplayer.so
Please restart Firefox to enable Flash

Unfortunately, flash still does not work.

---

### Post by macaholic on 2009-10-25
Is "Shockwave Flash" listed under "Tools>Add-Ons>PLugins" in firefox?

---

### Post by jamily on 2009-10-25
> **macaholic said:**
> Is "Shockwave Flash" listed under "Tools>Add-Ons>PLugins" in firefox?

Macaholic,

"Shockwave Flash" is not listed.

---

### Post by oldos2er on 2009-10-25
Run **sudo apt-get autoremove** if you haven't already.

 Not sure why the script is not working for you. You can manually copy libflashplayer.so to /usr/lib/mozilla/plugins then restart Firefox.

---

### Post by jamily on 2009-10-25
> **oldos2er said:**
> Run **sudo apt-get autoremove** if you haven't already.

 Not sure why the script is not working for you. You can manually copy libflashplayer.so to /usr/lib/mozilla/plugins then restart Firefox.

oldos2er,

I ran 

sudo apt-get autoremove\

and it ran fine.  In /usr I found three directories.  In lib and lib64 there is a mozilla/plugin subdirectory and I manually copied libflashplayer.so into both of them from libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.  In lib32 there was no subdirectory mozilla.  I have manually copied libflashplayer.so  before (though not not to \usr/lib64/mozilla/plugins).  No matter, I still can't get youtube to work.

Sorry for being such a pain.

---

### Post by macaholic on 2009-10-26
YOu can try adding this repository: [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash) .
Note: I have no experience with this PPA but it has seemed to help other users.

---

### Post by pwebster25 on 2009-10-26
Macaholic-
I am having the same problem.  I have ubuntuzilla 64 bit firefox 3.5.3 installed and I can't get flash or java to work right.  I did the script [HERE]("http://dl.getdropbox.com/u/307214/native-64bit-flash-installer.sh"), that you provided.  It seemed to run but still no apparent flash install.

In fact, after uninstalling all versions of firefox and reinstalling the ubuntuzilla version I still seem to have problems with many file types I encounter.  Firefox doesn't seem to know what to do with them and the drop-down when it asks what to do, is rather useless.  What about deleting my preferences folder entirely?

---

### Post by pwebster25 on 2009-10-26
The sevenmachines repository looks promising but it is only listed for Karmic.  Anyone using it on jaunty?

---

### Post by oldos2er on 2009-10-26
> **jamily said:**
>  
Sorry for being such a pain.
   It's not your fault. The only other thing I can think to try is to go to [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) and scroll down to 'Flash Optimizations,' and trying the suggestions there.

---

### Post by drdos2006 on 2009-10-27
Here is how I did it.
Close browser before executing the sudo commands.

Downloaded  libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
Extracted into /usr/lib/mozilla/plugins/

Executed from /usr/lib/mozilla/plugins/ via Terminal.
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

Run Firefox
Worked for me.

---

### Post by mjpatey on 2009-10-27
The path I always copy the libflashplayer.so file into is not /usr/lib... but rather

~/.mozilla/plugins

also known as  /home/yourusername/.mozilla/plugins

The .mozilla folder is hidden when you're navigating in Nautilus, so if you're using the GUI method to copy files, hit CTRL-H to display hidden files/folders first.  Also, there may not be a /plugins folder in ~/.mozilla yet; if not, just create it and Firefox will see it... then copy libflashplayer.so into it.

I hope this helps!

---

### Post by alotofloudcheese on 2009-10-27
Hi i had similar trouble with my jaunty 9.04. tried several different flash players nothing worked but the new flash 10 from for 64 bit. followed instructions here and my flash works on most everything.
   
  [http://ubuntuforums.org/]("http://ubuntuforums.org/showthread.php?t=1081964")[showthread.php?t=1081964]("http://ubuntuforums.org/showthread.php?t=1081964")

---

### Post by nanotube on 2009-10-27
> **pwebster25 said:**
> Macaholic-
I am having the same problem.  I have ubuntuzilla 64 bit firefox 3.5.3 installed and I can't get flash or java to work right.  I did the script [HERE]("http://dl.getdropbox.com/u/307214/native-64bit-flash-installer.sh"), that you provided.  It seemed to run but still no apparent flash install.

In fact, after uninstalling all versions of firefox and reinstalling the ubuntuzilla version I still seem to have problems with many file types I encounter.  Firefox doesn't seem to know what to do with them and the drop-down when it asks what to do, is rather useless.  What about deleting my preferences folder entirely?

if you're using ubuntuzilla, read and follow the ubuntuzilla faq for 64bit users for getting plugins to work:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)

---

### Post by jamily on 2009-10-27
I have tried about everything (it takes a lot of time) and I don't seem to be able to get flash working.  This despite generous help from others on this thread.  I read some of

[http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

that alotofloudcheese recommended.  It mentioned compiz, which I had installed.  I uninstalled it, but flash still did not work.

Ubuntu can't be my operating system if flash does not work.  I am thinking of installing 64bit Karmic Koala on my office machine when it comes out in two days and see if I can get flash to work there.  (I am also thinking of installing it on a usb drive and playing around on my home machine so as not to disturb my current Jaunty installation.)  I figure this may end up to be less work (if it works) and will allow me to upgrade some of the software I use without risking introducing conflicts.  Does this make sense?

Thanks again for all that assisted me ([oldos2er]("http://ubuntuforums.org/member.php?u=338320"), [macaholic]("http://ubuntuforums.org/member.php?u=352858"), ...).  The scripts are great - I only wished they always worked.  I am glad they worked for some.

---

### Post by jamily on 2009-10-27
> **nanotube said:**
> if you're using ubuntuzilla, read and follow the ubuntuzilla faq for 64bit users for getting plugins to work:

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)


Thanks nanotube.  the advice you pointed to at sourceforge did the trick!  It seems that "secret" was to

1.) use the 32bit flash plugin from Adobe and
2.) put libflashplayer.so in ~/.mozilla/plugins (instead of the sytem's /usr/lib/mozilla/plugins.

I love Ubuntu!

---

### Post by jamily on 2009-10-27
One last thing.  Compiz works too along with flash.

---

### Post by mrmhead on 2009-10-27
Hello,
I'm chasing down this flash thing too - ..
I'm running on 32-bit - Xubuntu 9.04.

Will that work /  is it safe to run those commands on 32-bit?

I also saw a suggestion to remove gnash and swfdec and than install flashplugin-installer.  um.. how is that done - or where are help pages (I haven't spent time to search yet)



I'm new to Xubuntu / Linux (2 days), but I do have plenty of Windows experience (professional)... 



m

---

### Post by nanotube on 2009-10-27
> **jamily said:**
> Thanks nanotube.  the advice you pointed to at sourceforge did the trick!  It seems that "secret" was to

1.) use the 32bit flash plugin from Adobe and
2.) put libflashplayer.so in ~/.mozilla/plugins (instead of the sytem's /usr/lib/mozilla/plugins.

I love Ubuntu!

you're welcome! :)

---

### Post by nanotube on 2009-10-27
> **mrmhead said:**
> Hello,
I'm chasing down this flash thing too - ..
I'm running on 32-bit - Xubuntu 9.04.

Will that work /  is it safe to run those commands on 32-bit?

I also saw a suggestion to remove gnash and swfdec and than install flashplugin-installer.  um.. how is that done - or where are help pages (I haven't spent time to search yet)



I'm new to Xubuntu / Linux (2 days), but I do have plenty of Windows experience (professional)... 



m

in synaptic, search for swfdec and gnash and uninstall if they are installed, then search for flashplugin-nonfree and install it. then restart firefox.

---

### Post by mrmhead on 2009-10-27
> **nanotube said:**
> in synaptic, search for swfdec and gnash and uninstall if they are installed, then search for flashplugin-nonfree and install it. then restart firefox.

Uninstalled swfdec, gnash wasn't there.  And it worked!

Thanks!!

... now to figure out sound...  ;)

---

### Post by scott1256ca on 2009-10-28
I am having much the same problem, but I don't think any plugins are working in firefox
I upgraded from ubuntu 8.10 a couple of days ago.

uname -a shows 64bit
Linux scott-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux

firefox (tried 2 or 3 different installs) is now installed from synaptic as

firefox-3.5 and shows
Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

(despite the i686 part in there, I THINK this is the 64 bit version)
flash is libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

I have tried this is plugin in
~/.mozilla/plugins
/usr/lib/xulrunner-addons/plugins/ (which is linked from /opt/firefox/plugins)
and no luck.

oh, I also ran the script  [http://www.myscienceisbetter.info/in...-on-linux.html]("http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html") from the first page, and it didn't help. I changed the version number to the one above, though.

Shouldn't I be seeing SOMETHING in the plugins section? Synaptic shows sun-java6-bin installed, but nothing seems to show up in firefox.

Any suggestions on what I can try next? This is becoming very frustrating.

---

### Post by scott1256ca on 2009-10-28
Well, this is a little embarrassing.
Just to make sure I covered my bases, I uninstalled everything firefox via synaptic. Then I went and removed all files to it that I could find in /opt and /usr (after tarring them up first). Then reinstalled everything. Then went to launch firefox, nothing there. Gave me "failed to launch child process" error, couldn't find firefox. So I went to use the other browser which I remembered from a previous distribution (Konquerer or something like that). It isn't there, of course, but that is when I saw Shiretoko, which, from my reading I assumed was some previous release no longer required (because a "real" 3.5.3 was available).

Anyway, that is what I am using now, and flash seems to work, and I see other plugins as well. Perhaps it has been there for a while. I never looked. So, my problem is solved, anyway.

Scott

---

### Post by daranthony on 2009-10-30
1) A. purge the nspluginwrapper and the other flash installer and flash plugin non-free


   B.  download and extract

  libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

  from this website:

  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

2) make sure you have root privledges and place the 
  extracted libflashplayer.so into the following directories, if you have them:

usr/lib/adobe-flashpugin
usr/lib/firefox/plugins
usr/lib/firefox-addons/plugins
usr/lib/firefox-3.5.3/plugins
usr/lib/mozilla/plugins
usr/lib/mozilla-firefox/plugins


3) restart firefox 

4) It should work.  If not, try to purge the nspluginwrapper and the other flash installer and flash plugin non-free, and try again

Hope this helps.

AL

---

### Post by omarly on 2009-10-30
I just tried 2 install gnash and ...Then i just uninstalled them from synaptic. Now i can see the vids on [www.ted.com](www.ted.com) just by reloading the page. 

Hope this works for more than just me :)

---

