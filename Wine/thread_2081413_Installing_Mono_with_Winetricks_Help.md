---
title: "Installing Mono with Winetricks *Help*"
date: 2012-11-06
forum: Wine
---

### Post by flamingblueyoshi on 2012-11-06
Hello! Currently I am trying to make steam work on ubuntu 11.10, and I'm having a problem installing mono. When I type

"winetricks mono210"

It tries and download the files, but fails. It provides the download link, so I checked it out in firefox. I get the response "Object not found". Why isnt the file there? Please help

Link: [http://ftp.novell.com/pub/mono/archive/2.10.2/windows-installer/5/mono-2.10.2-gtksharp-2.12.10-win32-5.exe](http://ftp.novell.com/pub/mono/archive/2.10.2/windows-installer/5/mono-2.10.2-gtksharp-2.12.10-win32-5.exe)

                                                                                   flamingblueyoshi

---

### Post by directhex on 2012-11-09
> **flamingblueyoshi said:**
> Hello! Currently I am trying to make steam work on ubuntu 11.10, and I'm having a problem installing mono. When I type

"winetricks mono210"

It tries and download the files, but fails. It provides the download link, so I checked it out in firefox. I get the response "Object not found". Why isnt the file there? Please help

Link: [http://ftp.novell.com/pub/mono/archive/2.10.2/windows-installer/5/mono-2.10.2-gtksharp-2.12.10-win32-5.exe](http://ftp.novell.com/pub/mono/archive/2.10.2/windows-installer/5/mono-2.10.2-gtksharp-2.12.10-win32-5.exe)

                                                                                   flamingblueyoshi

Mono is no longer hosted by Novell, that's why it's not there.

Install recent Wine from a PPA, it includes Mono.

---

