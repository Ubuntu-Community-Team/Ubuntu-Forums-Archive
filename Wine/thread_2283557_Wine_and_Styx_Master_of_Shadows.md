---
title: "Wine and Styx: Master of Shadows"
date: 2015-06-22
forum: Wine
---

### Post by brad39 on 2015-06-22
I have been trying to get Wine to work with Styx: Master of Shadows on Steam, but have been running into a lot of problems. I've managed to fix most of them via tutorials on these forums and other websites, but there's just one more I can't seem to crack. 

I finally got Styx (sorta) working today. I launched it from Steam, and the little splash screen popped up. And then it loaded with sound, but no video. An application didn't even load. All I could see is my desktop (couldn't navigate it, mind you), yet hear the audio for Styx. Is anyone able to help guide me through this last little bug? Here are the steps I've taken so far:

I've purged Wine from the system twice, and reinstalled. I then went in the terminal and installed the following programs:

```
winetricks -q xact_jun2010 vcrun2010  dotnet40
```

After that, I installed Steam.

```
winetricks steam
```

Finally, I let Steam do all of its updates, then I downloaded Styx with relatively no issues. That was the process I used to get to this point, and I'm not sure how to proceed. Any advice?

---

### Post by david-gamiz on 2015-11-29
Hi Brad,

 you could report your experience to winehq. It is one of the few current games that are not discharged from its database. So the community, or a colleague who wants to play the game under GNU/Linux will have first hand information.

[https://appdb.winehq.org/objectManager.php?sClass=application_queue&sTitle=Submit+Application&sAction=add](https://appdb.winehq.org/objectManager.php?sClass=application_queue&sTitle=Submit+Application&sAction=add)

 If you are not registered, you can register directly on the link: [https://appdb.winehq.org/account.php?sCmd=new](https://appdb.winehq.org/account.php?sCmd=new)

 As an example I stick a post I did:

[ https://appdb.winehq.org/objectManager.php?sClass=version&iId=30315]("http://https://appdb.winehq.org/objectManager.php?sClass=version&iId=30315")

 Greetings and thanks for share your experience,

David Gámiz Jiménez

---

