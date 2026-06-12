---
title: "[SOLVED] Any luck with ProWritingAid under Ubuntu/WINE?"
date: 2019-10-09
forum: Wine
---

### Post by WB0HYQ on 2019-10-09
I am running Ubuntu version 16.04 (xenial) and WINE version 1.6.2. I've done quite a bit of searching, but found nothing about running this great writer's aid under Ubuntu/WINE. Has anyone managed to get this application running?

Bill

---

### Post by WB0HYQ on 2019-10-10
Anyone?

---

### Post by DuckHook on 2019-10-11
[WineHQ database]("https://appdb.winehq.org/") has no record of this app (it's always the first place to check). This means that it is untested and unknown to them. Since they are the foremost experts on their own app compatibility, it is not likely that anyone on this forum can better their knowledge or experience. If web searching and a WINE database search both return nothing, you are likely forging a new path exploring virgin territory.

The usual suggestion for apps that don't run in WINE is to run them in a Windows VM.

If you do decide to experiment with this app on WINE, please consider signing up with the WINE community and recording your experiences on their database. It will greatly help the FOSS community.

---

### Post by WB0HYQ on 2019-10-11
The DB was the first place I tried. I've been experimenting with various methods to kick the application into gear, but nothing works so far. I will get the "waiting" circle for perhaps a half-sceond, then nothing. No error, no notification, nothing.

I may have to go the VM route, although I'd rather not.

Bill

---

### Post by DuckHook on 2019-10-11
> **WB0HYQ said:**
> The DB was the first place I tried.
On the forums, we have no idea of our members' IT savvy, so we perforce assume the the lowest common denominator. If you are familiar with WINE appDB, then you are well ahead of the game.
>  I've been experimenting with various methods to kick the application into gear, but nothing works so far.
The only advice I can think of is cycling through the common *winetricks* kludges. I'm sure you are already well aware of *winetricks*.
> I may have to go the VM route, although I'd rather not.
FWIW, I gave up trying to shoehorn stubborn Windows apps into WINE quite a few years ago. These days, if I can't get a Windows app to play nice in WINE with just a few modifications, I go straight to a VM. It helps that I have both XP and Vista VMs still kicking around although I would never dare enable the NIC for those two VMs. Setting up a shared directory makes interactions relatively painless. Only you can judge whether the exposure is worth the functionality.

---

### Post by Skaperen on 2019-10-11
if i needed to run something that expects Windows, i'd do it in a VM.

---

### Post by WB0HYQ on 2019-10-12
> **DuckHook said:**
>  . . . . I would never dare enable the NIC for those two VMs. Setting up a shared directory makes interactions relatively painless. Only you can judge whether the exposure is worth the functionality.

I hadn't thought of that. Good advice, as I'd end up spending a boatload of time doing updates. I have a spare Win 7 install disk with a never-used key. I can go with that. I have a bunch of shared directories for use between all my machines (I have 7 of them running various flavors of OS).

Bill

---

### Post by WB0HYQ on 2019-10-17
I am not sure HOW this happened, but today I updated UBUNTU from 14.04 to 18.04. The process hit a couple of snags, yet installed fine. After a few tweaks, I decided to try once more getting my writing software to run under WINE. I right-clicked the EXE file in Program files (x86), chose "Run under 'a wine application' ". I was so astonished it started--and ran well--after flatly refusing to run under 14.04.

The program was all its functionality it had under Windows. How do I make this known to the Wine program compatibility list? Or, is there something that has to be tested to allow this to happen?

Bill

---

### Post by WB0HYQ on 2019-10-17
> **DuckHook said:**
>  . . . .

If you do decide to experiment with this app on WINE, please consider signing up with the WINE community and recording your experiences on their database. It will greatly help the FOSS community.

I created a new account at wineDB. They said they sent me an email so I could log in. Been waiting for three hours. No email has arrived. Even checked my online spam folder (I use Thunderbird normally).
Does it take this long to become a member?

Bill

---

### Post by DuckHook on 2019-10-17
> **WB0HYQ said:**
> I am not sure HOW this happened, but today I updated UBUNTU from 14.04 to 18.04. The process hit a couple of snags, yet installed fine. After a few tweaks, I decided to try once more getting my writing software to run under WINE. I right-clicked the EXE file in Program files (x86), chose "Run under 'a wine application' ". I was so astonished it started--and ran well--after flatly refusing to run under 14.04.

The program was all its functionality it had under Windows. How do I make this known to the Wine program compatibility list? Or, is there something that has to be tested to allow this to happen?

Bill
Congrats. I should apologize for not reading your initial post well enough…

You mentioned the version number which is very old. Your new experience was likely the result of updating to a later version of WINE which came with Bionic. My practice is to install the latest wine-stable from their PPA, but I would not recommend that in your case. Sometimes, later versions actually suffer from regressions. If it ain't broke, don't fix it.
> **WB0HYQ said:**
> I created a new account at wineDB. They said they sent me an email so I could log in. Been waiting for three hours. No email has arrived. Even checked my online spam folder (I use Thunderbird normally).
Does it take this long to become a member?

Bill
I don't recall it taking long at all, but my info is years out of date. I suggest contacting them again to see what's up.

It's kind of you to go to the trouble. Kudos to you.

Regards,
DH

---

### Post by WB0HYQ on 2019-10-17
What's really old, apparently, is the WINE version number. According to this command:

bill@bill-UBU:~$ wine --version
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
wine-3.0 (Ubuntu 3.0-1ubuntu1)
bill@bill-UBU:~$

I'm running 2.0. Isn't WINE up there around 4.something now? If so, I should update it, no?

Bill

---

### Post by DuckHook on 2019-10-20
Apologies for the late response. When a thread is marked "solved" by its author, I unsubscribe from it. I only happened to run across yours again by accident.

The default WINE version installed by each version repo is invariably old. This is done because WINE is under heavy development and therefore changes constantly, whereas the Ubuntu devs understandably prefer stability over new bells and whistles. But when it comes to WINE, those new bells and whistles often make all the difference between functionality and non-functionality.

You can always elect to install the latest version of wine rather than the default one in the repos by adding the WINE PPA to your software sources. I do not usually recommend the addition of PPAs, but one exception is WINE.

Please be careful. There are many PPAs for WINE, most of which are obsolete or of questionable security and therefore are not advisable. The official WINE repos are hosted at winehq.org. Instructions for installing it are: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

### Post by WB0HYQ on 2019-10-20
I added that very WINE PPA and the software updater failed with a "check your internet connection" error (which is ludicrous considering I am here typing). When I uncheck it, the updater runs fine. I do, now, apparently have the latest version. I've managed to get three programs (all three not listed in the database) and would love to submit them for review. However, nobody seems inclined to help me over there. I've submitted three emails now concerning the return email I'm supposed to get when I register. I can't raise anyone. So, I'm happily running Windows stuff I thought I'd lose when I changed to LINUX.

Bill

---

### Post by DuckHook on 2019-10-21
> **WB0HYQ said:**
> &#8230;nobody seems inclined to help me over there. I've submitted three emails now concerning the return email I'm supposed to get when I register. I can't raise anyone. So, I'm happily running Windows stuff I thought I'd lose when I changed to LINUX.
They are good people producing a good (and needed) product purely as a public service, to which your own experience will attest. It's a shame they aren't responding to you. Nothing more you can do about that, I suppose.

It's good that you got more than just the one app working. Congrats. However, just a minor alert: it's not best practice to port over Windows apps to run on Linux. While WINE is a good app and appears to work marvellously in your case, in the final analysis, it's best to run Linux apps in Linux and Windows apps in Windows. Among other reasons, WINE is not guaranteed to continue working for you (regressions are a known and constant problem), Windows apps do not adhere to Linux security practices, WINE is a know security risk (so the less apps running on it, the better) and the point of moving to Linux was&#8212;presumably&#8212;to move to Linux.

The Bionic repos have 64,229 packages available for installation. Though many are not strictly apps, a large proportion are. I encourage you to look for native Linux replacements for some of those Windows programs. I think that their functionality and completeness might surprise you.

Good Luck and Happy Ubuntu-ing!
DH

---

### Post by WB0HYQ on 2019-10-21
Oh, I've been searching for replacements to be sure. A couple of them, like my railroad simulator Trainz, will not run on anything but Windows. For this, i bought a super-duper gaming machine (running Windows 10 unfortunately). As I find replacements for Windows applications in Linux, I remove them from Windows. Just a couple left. Some of what I run under WINE are simple hacks and I know they will be blown out of the water at some point.

Being an author, I was also reluctant to stop using Microsoft's Office as I've found LibreOffice Writer not quite up to the demands I make of Word. That, I still do on Win10. In fact, I use Remmina to connect my Linux machine to the Win10 and do odd jobs. I have one bank which refuses to support any browser other than IE.

Bill

---

