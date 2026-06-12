---
title: "apt-get update segmentation fault"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by edieguez on 2007-04-21
I upgraded to Fiesty and now apt-get always crashes whenever I run "apt-get update" or any other apt-get command. Anyone else have this problem? I tried clearing the cache with "rm /var/cache/apt/*.bin" but the problem persists.

---

### Post by Kilz on 2007-04-21
> **edieguez said:**
> I upgraded to Fiesty and now apt-get always crashes whenever I run "apt-get update" or any other apt-get command. Anyone else have this problem? I tried clearing the cache with "rm /var/cache/apt/*.bin" but the problem persists.

Have you tried 

```
sudo apt-get clean
```

or 

```
sudo apt-get -f install
```

---

### Post by edieguez on 2007-04-21
Yes I tried both. With "sudo apt-get clean" nothing happens but "sudo apt-get -f install" again gives me "Segmentation fault (core dumped)"

---

### Post by introspectif on 2007-04-25
```
sudo apt-get clean
```

worked for me. THanks!

---

### Post by zzarr on 2007-04-25
Hello!

I have the same problem on a debian installation on arm (architecture).

The thing is that, when ever apt-* or aptitude (or any other package command) is checking the dependency tree it chrashes and segmentation faults....

If I strace apt-get update for a sample it shows that the /var/lib/dpkg/status was the last file it used.

Greetings zzarr

---

### Post by zzarr on 2007-04-26
Hello again!

Test this!

rm /var/cache/apt/*.bin

Maby that helps?

Greetings zzarr

---

### Post by edieguez on 2007-04-26
Nope, I tried all these suggestions and it still crashes.

---

### Post by Dansken on 2007-04-27
Hi

I seem to have the same problem.
Can't run ANY package-installer programs, synaptic gives same failure message as apt-get and aptitude even send a SIGSEGV on top of the standard segmentation-fault message.

Worked until recently. Last thing I installed was W32 codecs through synaptic, if that has any relevance, then the problem appeared.

Have also followed all the suggestions, but with the same results as edieguez.

---

### Post by Dansken on 2007-04-27
Ok so i played around a little tampering with everything I could, couldn't get any worse right, and finally fixed the problem by editing the sources list and removing anything except the standard entrys. 

I have absolutly no idea how this could be the problem since it worked fine earlier, but hey, IT WORKED :D.

so try doing a "sudo gedit /etc/apt/sources.list"
and remove anything but standard entrys, I tried commenting out first but it didn't work.

Should probably do a "sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup" first just to be safe.

---

### Post by edieguez on 2007-04-27
Dansken that solved my problem. Thanks!

---

