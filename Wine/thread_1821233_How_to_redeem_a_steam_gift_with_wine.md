---
title: "How to redeem a steam gift with wine"
date: 2011-08-08
forum: Wine
---

### Post by Elliot Cooper on 2011-08-08
I was recently gifted a game on steam and found that the only way to redeem it was via a link in an email of the form:

steam://ackMessage/ackGuestPass/A4DB5087A9F35F54

Which didn't work. I started trying to find out how to get this working with my copy of steam running under wine but only found some really old instructions which I couldn't get working.

In the end I discovered that the following will work and is much easier. All you need to do is to execute the steam binary with the steam:// link from the email following it. E.g.:

wine /home/user/path/to/Steam.exe steam://url

In my case it looked like the following (it should be all on one line):

wine /home/elliot/.PlayOnLinux/wineprefix/Steam/drive_c/Program\ Files/Steam/Steam.exe steam://ackMessage/ackGuestPass/A4DB5087A9F35F54

You can get the URL by right-clicking on the "Click Here" link and selecting "Copy Link Address"

You can find the steam binary with this find command executed from your home directory:

find . -type f -name Steam.exe

This (should) work with all distros. I am posting it here because the ubuntu forms always rank highly on google and it may save someone some time.

Thanks
e

---

