---
title: "Steam stuck at &quot;UPDATING STEAM&quot; screen."
date: 2006-07-25
forum: Wine
---

### Post by Refrozen on 2006-07-25
Response on Cedega Forums is rather slow, so I figured I'd post this here to see if some of you could help.

> Finally, I got Steam to install. I had to open a console and run "cedega SteamInstall.exe," rather than using the UI, but that doesn't matter: Steam installed... I think (there's no files for it yet? That I can find anyway? :( ) 

After the install, Steam immediately launches itself and goes to a "Updating Steam..." screen. This screen seemingly uses 100% CPU indefinitely, and nothing, not even the cancel button have any effect. The cancel button RESPONDS (i.e., gets "pressed" in looking), but never does anything. Steam seems to never pass this point.

Hmm? Any advice?

---

### Post by rittub on 2006-08-19
I have the same problem :(

---

### Post by GameGod on 2006-10-25
I'm having the same problem too... Steam used to work on my PC too, so it might have been a WINE update that broke it.

This person had the same problem with Cedega:
[http://transgaming.org/forum/viewtopic.php?t=6506](http://transgaming.org/forum/viewtopic.php?t=6506)
... however, it looks like the solution is Cedega-only...

Anyone else?

---

### Post by T3h_Dohtem on 2006-10-26
Im having a similar issue.
Steam runs, updates to 26%, then closes. When I try to run it again, same thing.

---

### Post by GameGod on 2006-10-26
T3h_Dohtem: The 26% problem is a different issue.

However, last night I had an epiphany and I fixed my "Updating Steam..." / "0%" problem: I disabled moblock.
If you're running PeerGuardian or Moblock, they'll block Steam from connecting.

Before I run Steam, I just do a "sudo killall moblock", and it's fixed.

Hope this helps someone!
(Make sure you have your firewall turned off as well...)

---

### Post by soxs on 2007-10-30
Quote from winehq.org

_**26% Bug Workaround**_

Run this from the directory you installed Steam to:

```
nice -n 19 wine Steam.exe
```

If that doesn't work try this:

```
wine steamTmp.exe SelfUpdate "Steam.exe" 14
```

If all fails try this before the previous command:
```

rm ClientRegistry.blob

```

---

### Post by Uchihakid23 on 2007-11-20
Sorry to seem like a newb, but how//where do I add this code?

---

### Post by GameGod on 2007-11-20
Uchihakid23:

You'll want to open up a terminal, and then change directories to the directory where you installed Steam to. If you installed Steam in the default directory, you'll want to open a terminal and type the following into it:

```
cd ~/.wine/drive_c/Program\ Files/Steam
```

... then continue to run the commands in the post above.

---

### Post by kerryhall on 2008-01-18
Ahhh thank you so much GameGod, I didn't realize Steam couldn't update if you are running MoBlock! :)

---

### Post by jre on 2008-01-21
> **GameGod said:**
> Before I run Steam, I just do a "sudo killall moblock", and it's fixed.
With the debian packages from moblock-deb.sf.net this will cause troubles. Better do a "moblock-control stop" instead. (Otherwise the iptables rules still exist and send traffic to moblock which is no more running. Therefore all traffic would be stuck forever).
Instead of stopping noblock you can also remove the "steam" lines from the blocklist or whitelist the blocked IPs (see what is blocked in /var/log/moblock.log). Have a look at /etc/moblock/moblock.conf.

---

### Post by Syo on 2008-02-10
Just edit /etc/moblock/moblock.conf and add

IP_REMOVE="valve;limeli"


Then reload moblock.


Once its finished reloading steam should work again.

---

### Post by vahnx on 2008-02-23
I tried the stop and kill moblock, and there is no /etc/moblock/moblock.conf for me. I guess I don't have this 'moblock' installed and I still can't get passed the Updating Steam... part. Please, anyone help?
EDIT: Google for steaminstall.exe and use that instead of the msi.

---

### Post by mikeym on 2009-09-09
Hmmmmm..... Steam does not like MoBlok.

I've found that I needed to remove the following IPs (I did it from within settings in Mobloquer)

```
qwest communications corporation
limelight networks
valve corporation
```

Not sure if this is strictly speaking "safe". Probably best stopping MoBlock by hand when you run steam then restarting it.

---

### Post by jre on 2009-09-09
By now blockcontrol (which you have installed, if you use mobloquer) supports allow lists. So you may add [the contents of the steam allow list from iblocklist.com]("http://list.iblocklist.com/?list=steam") to /etc/blockcontrol/allow.p2p

---

### Post by executorvs on 2009-09-09
thank you for that. I know someone who will be quite happy to hear it.

---

### Post by Ankhwatcher on 2011-01-31
> **jre said:**
> By now blockcontrol (which you have installed, if you use mobloquer) supports allow lists. So you may add [the contents of the steam allow list from iblocklist.com]("http://list.iblocklist.com/?list=steam") to /etc/blockcontrol/allow.p2p

Would you mind showing an example of how that is done?
I can't figure out how to allow ranges in BlockControl.
Also do the IP Addresses just need to added for incoming, or for outgoing too?

Thanks,
ANkh

---

### Post by s.fox on 2011-01-31
[IMG]http://s3.postimage.org/wwatx561a/Thread_Necromancer.jpg[/IMG]

Thread Closed.

---

