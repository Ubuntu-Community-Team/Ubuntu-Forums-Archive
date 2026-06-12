---
title: "Error when installing icedtea-gcjwebplugin from Firefox"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by aaronb on 2008-11-01
When I use Firefox to view a site that uses java. Firefox gives me an
option to install 'icedtea-gcjwebplugin'. The installation stops with an
error to do with unresolved dependencies.

The same thing happens in Synaptic.

Please see the attached screen prints. I have the following questions:
1. Is anyone else getting this error?
2. Is the correct work around to install 'icedtea6-plugin'?

Bug 283950 was open with this error, but it has now been marked as 'Invalid'. If I raise a new bug will that too be marked as invalid too?

Thanks in advance for any feedback.

---

### Post by Nintendo01 on 2008-11-01
I am also having this problem, but I'm trying to install icedtea-gcjwebplugin from the repositories. 

I just upgraded to Intrepid, and used gjcwebplugin for my Java plugin in Hardy because it worked better than icedtea6-plugin. Now when I try to switch back to gjc (apparently Intrepid defaults to icedtea6-plugin or because of this: ) it says it needs icedtea6-plugin as a dependency, but then fails because it has the unresolved dependency of icedtea6-plugin. Perhaps it's trying to reference the Hardy repository of icedtea6-plugin and the repositories are for Intrepid? Thats the only thing I can think of, but then I'm a linux noob, too.

I can use icedtea6-plugin, but RuneScape and FunOrb games get the sound screwed up. With gjc RuneScape sound worked in Mono, but it's doing it for mono and stereo now. FunOrb games never had a mono selection, so their sound was always glitchy.

---

### Post by Nintendo01 on 2008-11-01
I just tried to install it from the terminal and got this:

```
wayne@wayne-desktop:~$ sudo apt-get install icedtea-gcjwebplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  icedtea-gcjwebplugin: Depends: icedtea6-plugin but it is not going to be installed
E: Broken packages
```

I'm guessing that the "E: Broken packages" at the end is the reason it won't install. I still don't know what it really means though...

---

### Post by aaronb on 2008-11-01
Raised bug report [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/292432](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/292432)

We'll see what happens. :popcorn:

---

### Post by Yellow Pasque on 2008-11-02
The Java plugin package has been forked in Intrepid. "icedtea6-plugin" replaces "icedtea-gcjwebplugin". There is also the "gcjwebplugin" package which uses cacao as the Java VM (you may want to try this).

---

### Post by aaronb on 2008-11-02
Temüjin: Thanks for posting, so which one is Ubuntu's recommended version use?

I thought it was icedtea-gcjwebplugin / icedtea6-plugin.

---

### Post by jamesstansell on 2008-11-02
aaronb: for a 64-bit plugin with liveconnect support use icedtea6-plugin

(if you don't know if that's what you need or not, then it probably is)

As for you bug, I personally think it sounds like an issue in the firefox packaging, but I'm not sure.

---

### Post by LO Matt on 2008-11-02
> **jamesstansell said:**
> aaronb: for a 64-bit plugin with liveconnect support use icedtea6-plugin

(if you don't know if that's what you need or not, then it probably is)

As for you bug, I personally think it sounds like an issue in the firefox packaging, but I'm not sure.

Where is icedtea6-plugin in Hardy?  It doesn't show in the repositories for me.

---

### Post by aaronb on 2008-11-03
LO Matt: icedtea6-plugin is in Intrepid.

---

