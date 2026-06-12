---
title: "OpenJDK won't install?"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by DarkGob on 2008-09-02
I tried following the instructions in the sticky thread for the 64-bit Java plugin, but using Add/Remove to install OpenJDK and Icedtea gives me an error message about unspecified conflicts, and says I should use Synaptic.

I cleared out sun-java6 (as well as sun-java5, dunno why that was still there) and have tried installing OpenJDK through Synaptic, but no dice; the dependencies seem to loop back onto themselves (openjdk-6-jre-lib depends on openjdk-6-jre-headless and vice versa), making it impossible to install the JRE or JDK. I can't even get the source files. What's going on here?

Example:
```
openjdk-6-source:
 Depends: openjdk-6-jdk but it is not going to be installed
 Depends: openjdk-6-jre but it is not going to be installed
```

---

### Post by IntuitiveNipple on 2008-09-02
Copy the output of apt-get so we can see the reasons:
```

sudo apt-get install openjdk-6-jre

```

---

### Post by DarkGob on 2008-09-03
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (= 6b09-0ubuntu2) but it is not going to be installed
```

Okay, let's try -headless...
```
The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: tzdata-java but it is not going to be installed
```

tzdata-java:
```
tzdata-java: Depends: tzdata (= 2008b-1ubuntu1) but 2008e-1ubuntu0.8.04 is to be installed
```
Okay, so from the looks of things, I have tzdata (2008e-1ubuntu0.8.04) installed, but the version of tzdata-java that I'm requesting is 2008b-1ubuntu1. What do I do about this?

---

### Post by jespdj on 2008-09-03
Strange. You could try "sudo apt-get update" to refresh the package information on your computer and then try to install OpenJDK again.

---

### Post by tuxxy on 2008-09-03
Install this package first **tzdata-java** , now install JDK

---

### Post by IntuitiveNipple on 2008-09-03
> **DarkGob said:**
> tzdata-java:
```
tzdata-java: Depends: tzdata (= 2008b-1ubuntu1) but 2008e-1ubuntu0.8.04 is to be installed
```
Okay, so from the looks of things, I have tzdata (2008e-1ubuntu0.8.04) installed, but the version of tzdata-java that I'm requesting is 2008b-1ubuntu1. What do I do about this?

You have the hardy-updates repository enabled (no bad thing). It has the updated tzdata and tzdata-java (version 2008e-1ubuntu0.8.04) which will be installed in preference to the older version in the primary hardy repository (2008b-1ubuntu1).

Check the installed versions:
```

dpkg-query -l 'tzdata*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  tzdata                 2008e-1ubuntu0.8.04    time zone and daylight-saving time data
ii  tzdata-java            2008e-1ubuntu0.8.04    time zone and daylight-saving time data for use by java runt
un  tzdata-lenny           <none>                 (no description available)


```
I suspect you simply need to update tzdata-java which for some reason isn't triggering:
```

sudo apt-get update
sudo apt-get install tzdata-java

```

---

### Post by The Keeper on 2008-09-15
When installing OpenJDK dependancies cannot be met because they want tzdata-java_2008e-1ubuntu0.8.04_all, which is in the proposed repository. Current universe repository contains tzdata-java_2008b-1ubuntu1_all which won't satisfy dependancies.

My solution to the problem was to go to [https://launchpad.net/ubuntu/hardy/+package/tzdata-java](https://launchpad.net/ubuntu/hardy/+package/tzdata-java) and download tzdata-java_2008e-1ubuntu0.8.04_all from there.

After that I could install OpenJDK.

---

### Post by CyberBob on 2009-02-08
Thank You!  

```

My solution to the problem was to go to 
https://launchpad.net/ubuntu/hardy/+package/tzdata-java 
and download tzdata-java_2008e-1ubuntu0.8.04_all from there.

```

After doing this myself, I could then install openjdk-6-jre successfully.

---

