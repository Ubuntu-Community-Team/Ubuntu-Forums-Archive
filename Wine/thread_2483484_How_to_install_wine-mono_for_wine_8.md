---
title: "How to install wine-mono for wine 8?"
date: 2023-01-31
forum: Wine
---

### Post by bjherbison on 2023-01-31
Running Ubuntu 22.04.1 LTS. Just updated software and wine-8.0 was installed.

The first run popped up a message saying wine-mono wasn't found. It could install it, but it recommended using a distribution package and pointed to [https://wiki.winehq.org/Mono](https://wiki.winehq.org/Mono) .

Unfortunately
1) The wiki page [https://wiki.winehq.org/Mono](https://wiki.winehq.org/Mono) doesn't list a Wine Mono Version for Wine version 8.0.
2) I don't know how to get that pop-up again so I can't have Wine install a version.
3) When I run a program under Wine I get a message below:

```
0084:fixme:hid:handle_IRP_MN_QUERY_ID Unhandled type 00000005
0084:fixme:hid:handle_IRP_MN_QUERY_ID Unhandled type 00000005
0084:fixme:hid:handle_IRP_MN_QUERY_ID Unhandled type 00000005
0084:fixme:hid:handle_IRP_MN_QUERY_ID Unhandled type 00000005
0024:err:module:import_dll Library OpenAL32.dll (which is needed by L"Z:\\.....exe") not found
0024:err:module:LdrInitializeThunk Importing dlls for L"Z:\\....exe" failed, status c0000135
```

(That program ran under the previous version of Wine.)

How do I move forward?

---

### Post by DuckHook on 2023-01-31
Do you need WINE 8?

I run a number of apps using WINE but here are some options that give me the biggest chance of success:

[LIST=1]
[*]Run WINE within a container (or VM), partially for the additional sandboxing (which is nice) but mainly for the ability to install both older and newer versions side by side—indeed, as many versions of WINE as I want,
[*]Run the stock version of WINE that is in the repos. I often find these to be less prone to problems than the latest and greatest. WINE has a tendency to break due to reversions. It also sometimes doesn't play nicely with custom distro kernel configurations. The WINE version in the repos is stressed by a community of testers and tends to work with the Ubuntu version that it is comes in.
[*]Use WINEtricks. This will sometimes help me by dragging in the native Windows dll which will work where the WINE dll will not. I don't quite recall but I believe that WINEtricks also allows you to install MONO.
[*]Post your problem on the WINE forums. After all, that's where all the WINE experts are.
[/LIST]

---

### Post by bjherbison on 2023-01-31
Thanks for the suggestions.

I don't need WIne 8. It just showed up as an update so I installed it.

Is there an easy way to determine which repository is responsible for putting wine 8 on my system?

---

### Post by DuckHook on 2023-01-31
I'm guessing that you installed WINE using the instructions on the WINE site. This adds their WINE repo to your install making it equivalent to Canonical's native repos. So, when you update/upgrade/install, it drags in the binary from the WINEHQ site instead of the Ubuntu site.

I just checked my own Jammy version and it is still on 6.0:```
duckhook@Zeus:~$  apt show wine
Package: wine
Version: 6.0.3~repack-1
Priority: optional
Section: universe/otherosfs
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Wine Party <debian-wine@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 200 kB
Provides: wine
Depends: wine64 (>= 6.0.3~repack-1) | wine32 (>= 6.0.3~repack-1), wine64 (<< 6.0.3~repack-1.1~) | wine32 (<< 6.0.3~repack-1.1~)
Suggests: q4wine, winbind, winetricks, playonlinux, wine-binfmt, dosbox (>= 0.74-4.2~), exe-thumbnailer | kio-extras
Breaks: libwine (<< 5.5-6), wine-stable (<< 3.0.1ubuntu1~)
Replaces: libwine (<< 5.5-6), wine-stable (<< 3.0.1ubuntu1~)
Homepage: https://www.winehq.org
Download-Size: 52.1 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: Windows API implementation - standard suite
 Wine is a free MS-Windows API implementation.
 .
 This package provides essential wrappers and convenience tools for the
 standard Wine components. It also employs the Debian alternatives system to
 provide the usual command names, e.g. "wine" instead of "wine-stable".
```

---

### Post by DuckHook on 2023-01-31
> **bjherbison said:**
> …Is there an easy way to determine which repository is responsible for putting wine 8 on my system?
Sorry, didn't even answer your question.

Yes, do the same: ```
apt show wine
```…command that I used. The line labelled APT-Sources tells you where yours is being pulled from.

---

### Post by DuckHook on 2023-01-31
I've been testing this further and I'm almost certain that you installed wine through the instructions from the WINEHQ site.

I have a container running WINE with the repo from that site and it too upgraded to WINE 8.0 just now. My bare metal install still points to WINE 6.0. Therefore, instructions in post #5 above is unlikely to show your real version of WINE. Instead, do:```
apt policy winehq* | grep -b2 -a7 Installed
```

Post the results back to this thread.

---

### Post by bjherbison on 2023-02-02
Thank you for your help. Your initial analysis was correct -- I had  added the the winehq repository in the past. I have no memory of why,  but likely an issue with some previous version of Wine.

I  uninstalled, removed the repository, reinstalled and everything I've  tried works. I'll get to Wine 8 eventually, when it is ready and  supported by Ubuntu.

Thank you for spending the time to help me.

---

### Post by mIk3_08 on 2023-02-03
> **bjherbison said:**
> I  uninstalled, removed the repository, reinstalled and everything I've  tried works. 

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

