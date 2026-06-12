---
title: "Firefox 3.5 no Java plugin?"
date: 2009-07-06
forum: x86 64-bit Users
---

### Post by tom.swartz07 on 2009-07-06
Hi all,

I downloaded and installed firefox 3.5 the day it came out on the official release, and Im really happy with it. I had a little bit of trouble getting the flash plugin to work correctly, but discovered in the process that the plugins for 3.5 are stored in a different directory than 3.0.11. When I copied the flash plugin file to this new directory, FF 3.5 instantly regained flash player compatibility. Just the other day, I was attempting to load photos on to facebook- which requires a java plugin- and was informed that I 'did not have it installed'

My question is, is there a similar situation to the flash player debacle? Is there a specific file that was used in FF 3.0.* to inform the browser that java is installed that 3.5 cannot locate due to the change in plugin directory? 

I have tried to (re)install java several times, all to no avail. The (re)install completes successfully, but whenever i launch FF; still no java.

Any help would be greatly appreciated!!!!

Tom

---

### Post by hkkea on 2009-07-07
Are you using 64bits plugins for 3.0.11? I have a problem with 64bit flash player for this new 3.5. Ended up I have to replace it with a 32bits flash player (in ~/mozilla/plugins/) then the problem solved. am not sure is this FF 3.5 really a x86_64 version even it showed on <About Mozilla Firefox> under <Help> menu. 

I am not sure is this the same issue that you have, you can try to think it in this way. But I don't want to install a 32bit Java just for this program, so I prefer to call up the original 3.0.11 for some purpose like uploading pictures in Facebook...

---

### Post by VastOne on 2009-07-07
> **tom.swartz07 said:**
> Hi all,

I downloaded and installed firefox 3.5 the day it came out on the official release, and Im really happy with it. I had a little bit of trouble getting the flash plugin to work correctly, but discovered in the process that the plugins for 3.5 are stored in a different directory than 3.0.11. When I copied the flash plugin file to this new directory, FF 3.5 instantly regained flash player compatibility. Just the other day, I was attempting to load photos on to facebook- which requires a java plugin- and was informed that I 'did not have it installed'

My question is, is there a similar situation to the flash player debacle? Is there a specific file that was used in FF 3.0.* to inform the browser that java is installed that 3.5 cannot locate due to the change in plugin directory? 

I have tried to (re)install java several times, all to no avail. The (re)install completes successfully, but whenever i launch FF; still no java.

Any help would be greatly appreciated!!!!

Tom

What directory are 3.5 plugins now installed in?

---

### Post by philinux on 2009-07-07
I installed 3.5 from the repos. 

As you will see in the screen shot. FF 3.0.11 and FF 3.5 beta4 use the same plugin.

---

### Post by VastOne on 2009-07-07
> **philinux said:**
> I installed 3.5 from the repos. 

As you will see in the screen shot. FF 3.0.11 and FF 3.5 beta4 use the same plugin.

I installed it using the Ubuntuzilla script. 

I have no plugins installed and if I try to open a download directory or an application (.deb or anything I have dloaded) I get a "Choose An application" to run.

So, even though I have my extensions running well, I have no plugins and other parts of my profile are borked.


Appreciate any insight

---

### Post by philinux on 2009-07-07
> **VastOne said:**
> I installed it using the Ubuntuzilla script. 

I have no plugins installed and if I try to open a download directory or an application (.deb or anything I have dloaded) I get a "Choose An application" to run.

So, even though I have my extensions running well, I have no plugins and other parts of my profile are borked.


Appreciate any insight

Ubuntuzilla sort of parks the original, in this case 3.0.11. The ubuntu repos FF3.5 beta4 will very soon be upgraded to 3.5 release. I would use ubuntuzilla's script to uninstall 3.5.

Your other problem is odd. Try right clicking on a downloaded package and choose open with option. Choose open with Gdebi.

---

### Post by VastOne on 2009-07-07
> **philinux said:**
> Ubuntuzilla sort of parks the original, in this case 3.0.11. The ubuntu repos FF3.5 beta4 will very soon be upgraded to 3.5 release. I would use ubuntuzilla's script to uninstall 3.5.

Your other problem is odd. Try right clicking on a downloaded package and choose open with option. Choose open with Gdebi.

Thanks Phil. I did unload Ubuntuzilla and got FF3.5 Beta 4 working again after a reboot (separate issue).

I am quited impressed with Beta 4 and honestly I even like the blue....

---

