---
title: "How to run the Windows .net version of Keepass2 on Ubuntu?"
date: 2012-11-24
forum: Wine
---

### Post by abexman on 2012-11-24
Hello, Ubuntu/WINE beginner here. So I would like to run Keepass2 on Ubuntu. There is a Ubuntu port but it has some  bugs (I was told by Keepass dev they are mono related) that make it unworkable for me. Is it possible to run the Windows portable or Windows installation of keepass under Ubuntu? It requires .net I think, so I am not sure this can work? 

I tried to run the .exe from the portable version but it seemed the same as Keepass2 for Ubuntu, that is still using mono?

Otherwise maybe I could run the mac version or other.

[http://keepass.info/download.html](http://keepass.info/download.html)

---

### Post by directhex on 2012-11-24
> **abexman said:**
> Hello, Ubuntu/WINE beginner here. So I would like to run Keepass2 on Ubuntu. There is a Ubuntu port but it has some  bugs (I was told by Keepass dev they are mono related) that make it unworkable for me. Is it possible to run the Windows portable or Windows installation of keepass under Ubuntu? It requires .net I think, so I am not sure this can work? 

I tried to run the .exe from the portable version but it seemed the same as Keepass2 for Ubuntu, that is still using mono?

Otherwise maybe I could run the mac version or other.

[http://keepass.info/download.html](http://keepass.info/download.html)

Keepass2 is .NET software, so it needs a .NET runtime to run on. On Linux this is ordinarily Mono. It's possibly possible to get Microsoft.NET installed in Wine to use that, but it's not really very well supported.

---

### Post by rai4shu2 on 2012-11-24
The bugs listed on the bug tracker show nothing severe with the Ubuntu "port." You're probably better off using KeePassX, in any case.

---

### Post by abexman on 2012-11-24
> **rai4shu2 said:**
> The bugs listed on the bug tracker show nothing severe with the Ubuntu "port." You're probably better off using KeePassX, in any case.

Keepassx is a no-go for me since it cannot synchronize db files and has no password history. 

Here's what I have posted but have yet to get any help with on Keepass2/mono:
[http://stackoverflow.com/questions/13501047/mono-keepass2-bugs-errors-in-entering-master-password-via-paste-or-using-backs](http://stackoverflow.com/questions/13501047/mono-keepass2-bugs-errors-in-entering-master-password-via-paste-or-using-backs)

---

### Post by abexman on 2012-11-24
> **directhex said:**
> Keepass2 is .NET software, so it needs a .NET runtime to run on. On Linux this is ordinarily Mono. It's possibly possible to get Microsoft.NET installed in Wine to use that, but it's not really very well supported.

Is there a particular .NET runtime version I should use? Any idea the steps to take? How do I get KP2 to use .NET and not mono then? It would seem mono & Keepass2 are not well supported anyway since I have not gotten any help on the issues I was having with that combination. KP2 worked well for me in Windows though so I figure I could try and use it as it works in Windows.

---

### Post by rai4shu2 on 2012-11-25
> **abexman said:**
> Keepassx is a no-go for me since it cannot synchronize db files and has no password history.

There are many other tools that can sync up any kind file for whatever purpose. I don't see how that's a blocker feature.

Password history? Really? What on Earth do you need that for?

---

### Post by abexman on 2012-11-27
> **rai4shu2 said:**
> There are many other tools that can sync up any kind file for whatever purpose. I don't see how that's a blocker feature.

Password history? Really? What on Earth do you need that for?

So if I have multiple machines that are not on the same network and start changing passwords of accounts, how do I propagate those changes to all my Keepass db files? Keepass2 was great, you just sync two versions of the file.  This is only further complicated by some accounts that do not have easy ways to recover lost passwords, so if I make a change to a password, thinking it has changed online but it doesn't "take" because of a failed online connection or something, it creates major hassles. Some times you don't get a second chance on encryptions. Am I missing some features or programs I should know about?

---

