---
title: "Firefox: Authentication Rejected"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by MaindotC on 2009-01-03
Firefox isn't starting when I click the icon on the top panel, so I tried launching it from the command prompt:
```

amd64@amd64-desktop:~$ firefox

(firefox:27368): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
amd64@amd64-desktop:~$

```

This started happening after I tried installing adblockplus.  FF crashed and when I restarted it, it did not restore my previous tabs, my bookmarks were gone, and if I tried logging into UF nothing happened when I clicked the "login" button.  I "marked for complete removal" all files containing "firefox" or "mozilla" in Synaptic (except some library that like everything depended on), re-installed, same problem.  Then I did:
```

sudo mv ~/.mozilla .mozilla.backup

```
and that's when I started getting this problem.

I CAN run firefox as root, which is what I'm doing right now, which is probably very unsecure so I hope someone can help me asap.

---

### Post by Rog-Mahal on 2009-01-04
Running firefox as root was your problem in the first place, I think. Try running the following in terminal.

```
sudo chown -R username:username ~/.mozilla
``` 

Then open firefox normally. Running it as root changes all the permissions for its folders, that should make it go back to normal.

---

### Post by MaindotC on 2009-01-05
I didn't run it as root prior to this happening.  When I did run it as root, it created a configuration director in /root/.mozilla, and I used cmp on the ~/.mozilla directory before and after I ran FF as root and nothing changed.  How could running FF as root cause any problems other than it being a security issue?

---

### Post by Paul S on 2009-01-05
If you really ran

```
sudo mv ~/.mozilla .mozilla.backup
```

then "sudo" changed the ownership to root.

When he said to run

```
sudo chown -R username:username ~/.mozilla
```

he wants you to substitute you're name instead of the word username in that line.  Use the command "ls -l .mozilla" to see who owns it and what the permissions are.  If it's still showing "root:root" then you didn't do it right.  You should be able to use you're .mozilla.backup to retrieve you're bookmarks and other stuff.

---

### Post by MaindotC on 2009-01-06
That command changed the permissions of the .mozilla folder, not the FF binary.  I know about changing permissions and I've already stated in my original post that I didn't execute the mv command until after I had problems with FF.

---

