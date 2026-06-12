---
title: "Ubuntu 11.04, unable to connect to Steam"
date: 2011-07-07
forum: Wine
---

### Post by psyko_chewbacca on 2011-07-07
Hi, I tried installing Steam trought WineTricks and PlayOnLinux and both give me the same error.

I enter my login information and try to connect but I get an error message saying that I could not connect to Steam server. I'm sure I'm having the good username/password combinaison as they work on the website.

I tried relauching the client, no go.

I tried deleting the file ClientRegistry.blob but everytime I delete it and relauch Steam the client updates itself and reinstall  the said file. So then I tried deleting the ClientRegitry.blob file one Steam is fully updated and running but still a no go.

I don't know what to do...

Thanks in advance!

---

### Post by bobwyajnr on 2011-07-08
> **psyko_chewbacca said:**
> 
I enter my login information and try to connect but I get an error message saying that I could not connect to Steam server. I'm sure I'm having the good username/password combinaison as they work on the website.


Hi

I am one of the maintainers (read: glorified moderator :) ) for this application on [Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444"). I can confirm it works very well with Wine 1.3.23 (the most recent Wine release) - it's running the actual games that causes the problems! :popcorn:

What version of Wine do currently have installed? Some command line output would be useful (since Wine outputs all it's debug data straight to the console). If it's a lot (shouldn't be!) you could attach it as a plan text file (or edit-out the lines with **fixme:** tags that are generally just placement notes to the developers on unimplemented Windows API features).

Perhaps you could indicate your confidence at using the command line? I'm quite happy to take/talk you through the process! :popcorn:

Bob

---

