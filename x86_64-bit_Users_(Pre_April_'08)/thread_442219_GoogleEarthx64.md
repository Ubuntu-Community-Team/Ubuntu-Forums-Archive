---
title: "GoogleEarthx64??"
date: 2007-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-05-13
Gents:

From Google, GoogleEarth installed some-time-ago without issue on my Dapperx64 kit. Does this mean that proggie is a native, UBUNTUx64 app?

Thinking not, I searched for 'WINE' using [places] and found only a <wine.desktop> in /usr/share/app-install/desktop ... nothing else. MidCommander tells me the same. I have no idea what that listing means --- In fact I have no idea how/where/what(?)  WINE works. 

So what's the truth of the matter? Is my GoogleEarth a native x64 app, or is it hiding inside a hidden  WINE installation?  Vis' security that would really bother me.

nss
******

---

### Post by x64Jimbo on 2007-05-13
My best understanding is that Google has adapted its apps (Google Earth and Picasa) to run in almost any environment by using a diverse set of libraries that come with the package. I know that WINE is not required to run it, but it is not a 64 bit app either.

---

### Post by JAPrufrock on 2007-05-13
yes, it's a 32 bit app that installs its own 32 bit lib files.

---

### Post by Case_f on 2007-05-13
And it doesn't require Wine install because it basically installs its own customized version of Wine within the Google Earth install directory.

---

### Post by nss0000 on 2007-05-13
Gents:

Oh ... so it's like the old "static" OPERA_browser. And with 2-G fast ram and sata in my kit those extra libs don't slow stuff down. Heck, maybe it's even faster .....guess when you're Google ya can bust_code as-you-please.

Thanks for the clues, gents.

nss
*****

---

