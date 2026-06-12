---
title: "Frequent Firefox Freezing"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by elmoosecapitan on 2008-10-31
Hi All,

I upgraded from Heron to Ibex yesterday and since the upgrade firefox [3.0.3] has been freezing very regularly. Whenever I open a loaded (graphically speaking) page, or have multiple tabs open, FF goes gray and locks me out. This can happen as infrequent as once every other hour to 15 in a 20 minute period.

cheers

---

### Post by PinkFloyd102489 on 2008-10-31
This happens to me also. Firefox also likes to just simply close itself out sometimes.

---

### Post by dillon533 on 2008-10-31
The same was happening to me but I had bitcomet running through wine. As soon as I took this out including wine it's been working fine.

---

### Post by davidw89 on 2008-10-31
Happened once.

I switched to:

[http://getswiftfox.com/](http://getswiftfox.com/)

[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

Both are very simple to install (.deb) and have AMD x64 support.

---

### Post by Tosa on 2008-11-01
This also happens to me, only it is not frequent, it's constant. It works for 5 min, or even less and then freezes. When I start it again it freezes immediately. I have to log out, restart window manager and log in. It just went off 3 times while I was typing this.

I am not sure, but it began a few days ago when I updated kernel...

---

### Post by empty_tank on 2008-11-01
i reinstalled flash 10.  It seems to have fixed the firefox freezing problem.

---

### Post by elmoosecapitan on 2008-11-01
Hooray! Firefox works now!

I found a script that successfully uninstalls and reinstalls flash.

[http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

cheers

---

### Post by camurgo on 2008-11-05
> **elmoosecapitan said:**
> Hooray! Firefox works now!

I found a script that successfully uninstalls and reinstalls flash.

[http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

cheers


Worked like charm, thx :)

---

### Post by Kilz on 2008-11-11
> **elmoosecapitan said:**
> Hooray! Firefox works now!

I found a script that successfully uninstalls and reinstalls flash.

[http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

cheers

The command in that howto downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time. Im not saying this script has been. But it is unsafe and should not be blindly trusted. Users should read and understand all scripts they install, especially from 3rd party sites. This is impossible to do if it downloads and automatically installs.

---

### Post by alexcuervo on 2008-11-17
> **Kilz said:**
> The command in that howto downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time. Im not saying this script has been. But it is unsafe and should not be blindly trusted. Users should read and understand all scripts they install, especially from 3rd party sites. This is impossible to do if it downloads and automatically installs.

@ Klitz, I wonder what makes your scripts more trustworthy? This is also a 3rd party website. YOUR scripts can also change at any time. And some of YOUR scripts are even hosted on a home computer, for instance this one: [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz) at your post at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)) 

The source code for the script at ([http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)) has always been available for everyones review and CONSTRUCTIVE criticism.

Besides, it is not true that the command "wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh" will "Automatically Install" as you put it. The user still needs to give his authorization before is executed. I see no difference in this and you telling your users in your posts to:

> 
**5. Select "Run in Terminal"**

1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash10" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.
8. If you select anything but Hardy Heron the script will not install anything.


By the way, your flash 10 script is surprisingly similar to the one at [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

---

### Post by xebian on 2008-11-17
Well, the 64-bit Flash is here.  It doesn't need the ia32-libs nor the nspluginwrapper.

---

### Post by RT236 on 2008-11-18
> **davidw89 said:**
> Happened once.

I switched to:

[http://getswiftfox.com/](http://getswiftfox.com/)

[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

Both are very simple to install (.deb) and have AMD x64 support.
I had the same problem, but also sometimes quite slow and sometimes almost hanging since I upgraded to Ubuntu 8.10.  I found using Swiftfox highly beneficial to solving this difficulty.  Also, I run a dual core processor, so liked the idea that Swiftfox was also specifically available for Intel Dual Core Processors.  I've also monitored my CPU utilization since doing this and the CPUs are doing a split load.  I have also  loaded about 20 sites via tabs and done constant refreshes to reload all sites at once and Swiftfox performed quickly and perfectly!!!  I'm glad I came across your posting so I did not list a duplicate solution on the Forums.  Duane

---

### Post by lyjg1113 on 2008-11-18
[**?k?C**](http://www.shunfengbj.cn/) &#26381;&#21153;&#20844;&#21496;&#20026;&#24744;&#25552;&#20379;&#19987;&#19994;&#30340;&#21051;&#31456;[**?k?C**](http://www.shunfengbj.cn/) &#26381;&#21153;&#65292;&#26159;[**?k?C**](http://www.shunfengbj.cn/) &#34892;&#19994;&#30340;&#20348;&#20348;&#32773;&#65292;&#25216;&#26415;&#21183;&#21147;&#38596;&#21402;&#65292;&#20449;&#35465;&#27714;&#29983;&#23384;&#65292;&#36136;&#37327;&#27714;&#21457;&#23637;&#8212;&#26377;&#28120;&#23453;&#25293;&#25293;&#35780;&#20215;&#20026;&#35777;&#65281;[**?k?C**](http://www.shunfengbj.cn/) &#19987;&#19994;&#20195;&#21150;&#21508;&#31867;&#21457;&#31080;&#12289;&#36710;&#29260;&#12289;&#25991;&#20973;&#12289;&#35777;&#20214;&#12289;&#21051;&#31456;&#12290;&#21457;&#31080;&#31867;&#65306;&#24314;&#31569;&#19994;&#12289;&#26381;&#21153;&#19994;&#12289;&#25151;&#22320;&#20135;&#12289;&#36816;&#36755;&#12289;&#39184;&#39278;&#21457;&#31080;&#12289;&#38144;&#21806;&#21457;&#31080;&#12289;&#31246;&#21153;&#21457;&#31080;&#12289;&#21307;&#38498;&#38376;&#35786;&#12289;&#20303;&#38498;&#31561;&#36710;&#29261;&#31867;&#65306;&#27494;&#35686;&#29260;&#29031;&#12289;&#37096;&#38431;&#29260;&#29031;&#12289;&#22320;&#26041;&#29260;&#12289;&#25705;&#25176;&#36710;&#29260;&#31561;&#12290;&#25991;&#20973;&#31867;&#65306;&#26412;&#31185;&#12289;&#22823;&#20013;&#19987;&#12289;&#39640;&#21021;&#20013;&#31561;&#12290;&#35777;&#20214;&#31867;&#65306;&#26410;&#23130;&#35777;&#12289;&#32467;&#23130;&#35777;&#12289;&#20934;&#29983;&#35777;&#12289;&#33410;&#32946;&#35777;&#12289;&#20986;&#29983;&#35777;&#12289;&#32467;&#25166;&#35777;&#12289;&#30005;&#28938;&#24037;&#25216;&#26415;&#31561;&#32423;&#35777;&#12289;(&#20891;&#29992;)&#39550;&#39542;&#35777;&#12289;&#65288;&#20891;&#29992;&#65289;&#34892;&#39542;&#35777;&#12289;&#21449;&#36710;&#35777;&#12289;&#38130;&#36710;&#35777;&#12289;&#36864;&#20237;&#35777;&#12289;&#24037;&#31243;&#24072;&#12289;&#21416;&#24072;&#36164;&#26684;&#35777;&#12289;&#36710;&#33337;&#35777;&#12289;&#23548;&#28216;&#35777;&#12289;&#22823;&#23398;&#33521;&#35821;&#22235;&#20845;&#32423;&#12289;&#25104;&#20154;&#33258;&#32771;&#27605;&#19994;&#35777;&#12289;&#23398;&#20301;&#35777;&#12289;&#20250;&#35745;&#24072;&#35777;&#12289;&#35745;&#31639;&#26426;&#25216;&#26415;&#19982;&#36719;&#20214;&#32771;&#35797;&#35777;&#20070;&#12289;&#20250;&#35745;&#20174;&#19994;&#36164;&#26684;&#35777;&#12289;&#24515;&#29702;&#21672;&#35810;&#24072;&#35777;&#12289;&#33829;&#36816;&#35777;&#12289;&#23381;&#26816;&#35777;&#12289;&#26032;&#26087;&#29256;&#36523;&#20221;&#35777;&#12289;&#20581;&#24247;&#35777;&#12289;&#33829;&#19994;&#25191;&#29031;&#12289;&#20859;&#36335;&#35777;&#12289;&#25151;&#22320;&#20135;&#26435;&#35777;&#12289;&#21051;&#21046;&#22810;&#31181;&#20844;&#31169;&#31456;&#12289;&#36130;&#21153;&#31456;&#65292;&#21487;&#21327;&#21161;&#12289;&#38506;&#21516;&#23458;&#25143;&#21046;&#20316;&#35777;&#20214;&#12290;&#21051;&#31456;&#31867;&#65306;&#20840;&#22269;&#21508;&#34892;&#19994;&#30340;&#22823;&#23567;&#20844;&#31169;&#31456;&#21360;&#12290;[**?k?C**](http://www.shunfengbj.cn/) &#30340;&#23447;&#26088;&#26159;&#8220;&#35802;&#20026;&#20808;&#12289;&#21644;&#20026;&#36149;&#12289;&#24773;&#20026;&#37325;&#8221;&#25105;&#20204;&#24895;&#22312;&#35802;&#23454;&#20026;&#20225;&#19994;&#26381;&#21153;&#20013;&#19982;&#24191;&#22823;&#20225;&#19994;&#21450;&#20010;&#20154;&#24314;&#31435;&#30495;&#27491;&#30340;&#24863;&#24773;&#21644;&#21451;&#35850;&#12290;

---

