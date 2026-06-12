---
title: "Mp3 on iMac G3 350 Mhz"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Henke on 2006-04-15
Hi all Ubuntu-lovers!

I've just installed Ubuntu 5.10 on my iMac. Why doesn't Rythmbox recognize my mp3:s? Anyone having the same problems? Any tips?

Henke :rolleyes:

---

### Post by 3rdalbum on 2006-04-16
Ubuntu doesn't come with "Restricted Format" codecs like MPEG and MP3. Open up the Synaptic Package Manager program from System > Administration > Synaptic Package Manager, do a search for "gstreamer" and install everything that comes up (except for packages with "-dev" in their name). Now Rhythmbox and Totem will be able to play the MP3s and lots of other formats.

Or install XMMS - it's the most popular audio player for Linux, and I think it has MP3 decoding inbuilt.

---

### Post by Henke on 2006-04-16
[QUOTE=3rdalbum]
Or install XMMS - it's the most popular audio player for Linux, and I think it has MP3 decoding inbuilt.[/QUOTE]

Now I've installed XMMS. Works just great... Thanx for the tip! A bit embarrassing I didn't think of that...:oops: 

On my Dell computer, I run MEPIS-Linux, which comes fully prepared for mp3 with three different players. It's just to click, drag and fully enjuy! But MEPIS has KDE. Maybe thats the reason..?

In my opinion, support for playing mp3:s should be implementated in all distros without having the problems with missing libraries etc... But that is my very personal opinion...

Regards
Henke

---

### Post by Jason_25 on 2006-04-16
[QUOTE=Henke]
In my opinion, support for playing mp3:s should be implementated in all distros without having the problems with missing libraries etc... But that is my very personal opinion...
[/QUOTE]
Most people here feel the same.  Too bad it's illegal.

---

### Post by Henke on 2006-04-16
[QUOTE=Jason_25]Most people here feel the same.  Too bad it's illegal.[/QUOTE]

What's illegal, most people, the same feelin's or the mp3:s? ;) 
Henke

---

### Post by aimislame15 on 2006-04-16
I don't really see the issue with it being illegal. Either way, it's not difficult to get almost everything working.

 I havent been able to get wmv's to work on my ppc box, can anyone help me out?

---

### Post by Ptero-4 on 2006-04-16
Mepis ability to play MP3 isn't b/c of KDE. It's b/c mepis includes the "non-free" codecs by default. Ubuntu doesn't do that to avoid "copyright" issues.

---

### Post by 3rdalbum on 2006-04-17
[QUOTE=aimislame15]
 I havent been able to get wmv's to work on my ppc box, can anyone help me out?[/QUOTE]

As you've found out, downloading the w32codecs doesn't work, and there's no equivilant for PPC.

This isn't an ideal solution, because it doesn't support more recent versions of WMV, but you can install VLC (sudo apt-get install vlc), and that will allow programs to access some WMV files.

---

### Post by Henke on 2006-04-17
[QUOTE=Ptero-4]It's b/c mepis includes the "non-free" codecs by default. Ubuntu doesn't do that to avoid "copyright" issues.[/QUOTE]

Aahh, so MEPIS is going to fly away over the non-free border then, or did I get this wrong..? :-k 

By the way, do You know which the "non-free" codecs are?

Henke

---

### Post by kadymae on 2006-04-17
If it's not supported out of the box on Ubuntu, it's not free as in 100% OSS/Public Domain/GPL/BSD.

> so MEPIS is going to fly away over the non-free border then, or did I get this wrong.

It's an ideological stance.  Ubuntu is not going to include anything on the default install that's proprietary/not public domain.

Though widely used, .mp3 files are a proprietary codec. The same with DVDs.  I *believe* that though the programs to play mp3s and DVDs are open source, there are certain license agreements involved in having permission to create the program in the first place. 

In theory these permissions can be revoked; the rights to the mp3/dvd codec could be transferred to a party who wants to place further restrictions on them -- such as revoking all past licenses and charging everybody $$$ for the player.

[Read up on the issues involving the decss case and DVD Jon ]("http://en.wikipedia.org/wiki/Dvd_jon")and that will more fully explain it.


Or, from wikipedia, about DVDs:

> The CSS has caused major problems for the inclusion of DVD players in any open source operating systems, since open source player implementations are not officially given access to the decryption keys or license the patents involved in the CSS. Proprietary software players were also difficult to find on some platforms. However, a successful effort has been made to write a decoder by reverse engineering, resulting in DeCSS. This has led to long-running legal battles and the arrest of some of those involved in creating or distributing the DeCSS code, through the use of the controversial U.S. Digital Millennium Copyright Act, on the grounds that such software could also be used to facilitate unauthorized copying of the data on the discs. These laws currently affect only the United States; most other countries can use de-scrambling software to bypass the DVD restrictions. A number of software programs have since appeared on the Web to view DVDs on a number of different platforms..

---

