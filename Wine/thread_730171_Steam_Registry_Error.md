---
title: "Steam Registry Error"
date: 2008-03-20
forum: Wine
---

### Post by DavidFromCanada on 2008-03-20
Ok I'm running xubuntu and when I start Steam.exe I get an error.

Steam.exe (main exception): Unable to start Steam Engine: *SteamStartEngine(0x33e7b0) failed with error 1: The registry is in use by another process, timeout expired

This problem is in the Wine AppDB, but only mentions the error with the launching of games not Steam itself, therefore their solutions are no use. 

Anyone having the same issue and have a solution?

---

### Post by clvn on 2008-03-20
I got the same error message as you, just a couple of minutes ago.. I'll do some more googling to see if i find an answer. Please notify the rest of us if you find something helpful, "DavidFromCanada" :)

---

### Post by clvn on 2008-03-20
I've found a solution that worked for me.

I updated from wine 0.9.46 to 0.9.57, and it worked like a charm.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by DavidFromCanada on 2008-03-21
Ya somehow I can start steam now but I get the error when starting a game. I am using the newest version of wine 0.9.57. I'll keep trying but this is annoying.

---

### Post by aoanla on 2008-03-21
I hate to be grumpy at you, but you know how at the top of this forum there's a reminder to "check the WineHQ database to see if they already have information on your application before posting a question."?

Well, if you check the WineHQ database for Steam, you'll find that it says this:

> Games don't start with message "The registry was in use by another process"

This is Steam bug due to Linux caching some file operations at the wrong time. You can fix this problem by shutting down Steam cleanly (keep running and exiting steam itself until you get a clean shutdown without any errors after "Shutting down" - watch the console you ran steam from) and then restarting it. Once steam has been shut down cleanly and restarted the error should not occur.

If all fails, start Steam, right-click on the game and select Properties. Go to Local files tab and click on Verify integrity of game cache...

Some file systems support extra sync flag. This should solve the problem. However it will reduce performance, so use with care!

chattr -R +S ~/.wine/drive_c/Program\ Files/Steam


So, please remember to check the AppDB in future, eh? It'll save you time as well...

---

### Post by DavidFromCanada on 2008-03-21
This is a completely different issue because in AppDB the solutions assume you got Steam running and that you can't get games started. While we can't get Steam running at all. I was able to log on to Steam *once* and I ran into the issue that AppDB covers (although no solution works for me).

---

### Post by aoanla on 2008-03-21
It's actually not a *completely* different issue - all registry errors from Steam arise from some issue with syncing on Steam's cached files and registry.

Have you tried deleting ClientRegistry.blob?

---

### Post by DavidFromCanada on 2008-03-21
Ya it didn't work.

---

### Post by DavidFromCanada on 2008-03-21
Ok after being persistant I was able to get Steam running but this is random and I'm trying to find a pattern that I can then write a script to remove the .blob file and launch steam. But even in Steam it took +5 trys to get games launched. I'm confused about how people I know have Steam running fine in wine and I can't. Because the problem is how linux caches files so it should be a universal problem?

---

### Post by aoanla on 2008-03-22
Well, I found that some versions of Wine were more iffy with Steam than others; several versions back, now, there was a release of Wine that persistently gave the registry error, even after removing the ClientRegistry.blob etc - but setting the file attributes to sync for the Steam directory as mentioned above fixed all problems for me - I've not had a registry in use error since I did that.

---

### Post by DavidFromCanada on 2008-03-22
Solution
Edit these two files and set the value to 1.

```
sudo mousepad /proc/sys/vm/dirty_expire_centisecs
Default value is 3000
```

```
sudo mousepad /proc/sys/vm/dirty_writeback_centisecs
Default value is 500
```

This should put all your files into sync mode. This solved my problem but I have no idea if there are negative effects to this. 

Also I wrote a script to do this command to start Steam, which will now start always.
```
cd /yoursteamdirectory/Steam
wine steam.exe
```

---

