---
title: "Latitude C610 running Starcraft wavy video"
date: 2007-12-04
forum: Wine
---

### Post by KD2012 on 2007-12-04
Hello All,

I am running Ubuntu 7.10 on a Dell C610, I have the latest version of Wine and successfully installed Starcraft. The problem I'm having is I cannot play the game because of wavy lines, which turns out to be a driver issue according to Blizzard. The same installation worked fine with my older Latitude. I have tried other distributions and it also worked fine, so I am quite certain that the problem is 7.10 driver related. If anybody has any suggestions or resolutions to my problem it would be greatly appreciated.

Thank you.

---

### Post by cogadh on 2007-12-07
What video hardware does the C610 have?

---

### Post by KD2012 on 2007-12-07
Here is the information you requested. 

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"

---

### Post by cogadh on 2007-12-07
I'm not that versed in the intricacies of ATI hardware on Linux (die-hard Nvidia fanboy), but you probably need to update to the proprietary ATI driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by KD2012 on 2007-12-07
I am definitely on the Nvidia bus with you but when the laptop comes as is you take what you can get and deal with it.  I will give your suggestion a try on my testing installation and kiss it good bye if it blows it away.

I appreciate your help.
Thank you

---

