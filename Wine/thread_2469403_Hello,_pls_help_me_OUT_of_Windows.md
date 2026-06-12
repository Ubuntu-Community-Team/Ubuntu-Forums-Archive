---
title: "Hello, pls help me OUT of Windows"
date: 2021-11-28
forum: Wine
---

### Post by aexistenax on 2021-11-28
Hello, good morning/afternoon/evening/night/day, whatever applies to your timezone!
I've been trying to make POL and WINE work for a few weeks now, and I can't get the hold of any of them.
For POL it gives me an error message saying I don't have installed the latest ".NET Framework" from Microsoft, and when I attempt tp install it it claims that yet ANOTHER small Microsoft package is lacking and therefore it can't continue the installation.
My WINE simply crashes , over and over. Yes, I tried disinstalling it and re.installing it from scratch, but that didn't give any results.
I am currently playing a free-to-play game called "RAID Shadow Legends", and I am ashamed to acknowledge that each time I play it I've to switch to my Windows OS to be able to do so. So PLEASE, if ANYONE has any idea on how to solve at least ONE of these problems so I can run RAID in my Ubuntu 20.04, I'd be much thankful.
Thanks in advance for your time and efforts.
Long live open source!

---

### Post by octawizard43 on 2022-05-06
You need to install Wine Gecko and Mono in order for Wine to correctly work. I have also hade super much problems with installing Wine packages. But when I first installed Wine Gecko and Mono it worked I have Wine Mono and Gecko to install Wine Mono just write in the Terminal sudo apt install mono-complete and to install Wine Gecko. To install Wine Gecko its more complicated but if you have 32-bit computer write in Terminal (wget [http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86.msi](http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86.msi)) type that in the Terminal without parentheses to install it. If you have 64-bit type in the Terminal without parentheses (wget [http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86_64.msi](http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86_64.msi)) If you want both and want Multiarch so you can have 32-bit and 64-bit Gecko so applications will work better in both 32-bit applicationd & 64-bit application type in the Terminal. Both (wget [http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86.msi](http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86.msi)) And (wget [http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86_64.msi](http://dl.winehq.org/wine/wine-gecko/2.47.1/wine-gecko-2.47.1-x86_64.msi)) again dont include parentheses in Terminal. But i don't think its possible in Ubuntu with multiarch yet. So install only 64-bit gecko in 64-bit machine.

---

