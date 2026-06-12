---
title: "[SOLVED] Citrix ICA client on 64-bit Ubuntu (Edgy)"
date: 2006-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkroto on 2006-12-08
**[COLOR=Red]_***The guide below worked for me but there is an easier way,  look at this write-up _[/COLOR]**[http://www.ubuntuforums.org/showthread.php?p=1997835#post1997835](http://www.ubuntuforums.org/showthread.php?p=1997835#post1997835)**[COLOR=Red]_ and enjoy your citrix****_[/COLOR]**


This is intended to help anyone who is trying to use the Citrix ICA client on a 64-bit system.  Don&#8217;t know if this is a how-to or a workaround, don&#8217;t know the difference, call it what you want, it worked for me.  If it should be in another place on the forum, please move it.  Also, I did not want to setup chroot as suggested [here]("http://www.ubuntuforums.org/showthread.php?t=124426&highlight=citrix").  Looked way to complicated for me.

If you are like me you can log into a Citrix server somewhere for work purposes, or other, allowing for remote access.  Yeah, now I can work more!  I don&#8217;t know if this is the best way to make Citrix work, but for me it was very easy and installed very cleanly without much effort.  I&#8217;m new to Ubuntu so if anyone has a cleaner, easier way please let me know.  I&#8217;m running Edgy 64-bit on a Core 2 Duo.  First ran Automatix to get setup after a clean install, then:

Here&#8217;s how I got it to work:

1. First, used this [ deb]("http://www.ubuntuforums.org/showthread.php?t=297280&highlight=wine") from napsilan and then [this]("http://www.ubuntuforums.org/showthread.php?t=185557") script by Kilz to install wine (I&#8217;m not sure if I needed the deb and the script, but with the deb I couldn&#8217;t do a &#8216;winecfg&#8217; and when I tried to run Kilz script before the deb and it told me I didn&#8217;t have Wine installed and killed the process.  Maybe I didn&#8217;t follow Kilz guide correctly, but after running the deb then the script Wine was installed.)  _Bottom line _is that you need to install Wine to work on your 64-bit system.

2. Run
```
 sudo aptitude update && sudo aptitude install cabextract wine
```3. After 1 and 2 are done and Wine is configured you need to install Internet Explorer (Ie4Linux).  As much as I didn&#8217;t want to install IE, it was the only way I could think to make this work.  I used part of the guide at psychocats, [http://psychocats.net/ubuntu/ies4linux](http://psychocats.net/ubuntu/ies4linux) to get it running, including the code in step 2.  Thanks goes to psychocats and Aysiu for pointing out all the helpful stuff on that site.

4. Next, I went to the [IE4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") site and followed the directions on how to install, which are, at the time of this post:
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```I ran them one line at a time and followed the prompts.  I only installed IE6, not 5.5 or 5.
Now you should have an IE icon on your desktop.

5.  Finally, I opened up IE and navigated to my remote login site.  At that site it gives me a link to download an ICA32 client.  I clicked on the link, ran it from the site and it installed, I'm sure you could do the same from [www.citrix.com]("http://www.citrix.com").  Logged myself in and I&#8217;m golden.

Final Note:  prior to getting Citrix to work through IE as described above, I did install Firefox32 using Kilz guide [here]("http://www.ubuntuforums.org/showthread.php?p=1174435").  Then I tried to install the Citrix client but couldn't get it to work.  Running through FF32 would be cleaner, I think, so if someone can get it working let me know.

Hope this helps anyone looking to do this on 64-bit, and hope even more that Citrix comes out with a 64-bit Linux client soon.
Thanks to all those mentioned in this guide for their guides-- helping to make my (first) 64-bit experience a good one.
Any questions, just let me know.

EDIT (12/14/06):  I was informed that you can use Swiftfox and make Citrix work through that.  Since I don't use Swiftfox I cannot confirm, nor deny, the truth or veracity of these statements.....
EDIT (1/11/07): link to new guide

---

