---
title: "Is Ubuntu 64 ready?"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gotterdammerung on 2007-06-03
Is there already a sun java plugin to firefox 64bits? 
How about flash 64bits? 
Can I run it without nspluginwrapper?

Running a Ubuntu 32bits on a 64bits machine is OK until you need raw performance.

:-({|=

---

### Post by Kilz on 2007-06-03
> **Gotterdammerung said:**
> Is there already a sun java plugin to firefox 64bits? 
How about flash 64bits? 
Can I run it without nspluginwrapper?

Running a Ubuntu 32bits on a 64bits machine is OK until you need raw performance.

:-({|=

There is a 64bit java plugin. But per the [Java page on the wiki]("https://help.ubuntu.com/community/Java")

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. **Note however, that the plugin currently [COLOR="Red"]runs with no security manager.[/COLOR] This means that applets you load can do anything a java application that you download and run can do. [COLOR="Red"]Be **very** careful which applets you run[/COLOR].**

I wouldnt use it :D

There is no 64bit Flash plugin, you need nspluginwrapper. [I wrote a script that will install it in seconds.]("http://ubuntuforums.org/showthread.php?t=425672")

There is always the old standby of installing a 32bit browser and plugins so you have everything available. There is a script for that to, see my signature.

---

### Post by nss0000 on 2007-06-03
GD:

Yes. All things considered , usrland should get its' fatazz over to Ux64 asap. The socalled 'opportunity cost' is low, while rewards can be outstanding with software that exploits both the x64 bandwidth & multi-core environmont. My specific experience is with geo-analytic GRASS, but other examples are about.

SUNs' blunder in lax Java-pluginx64 dev ought not  discourage a software  transition long overdue w.r.t. hardware kit.
To paraphrase FOD, '... grab 'em by the nose and yank ... and they will come ...'

imho -- nss
***********

---

### Post by Gotterdammerung on 2007-06-03
> **Kilz said:**
> There is a 64bit java plugin. But per the [Java page on the wiki]("https://help.ubuntu.com/community/Java")

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. **Note however, that the plugin currently [COLOR="Red"]runs with no security manager.[/COLOR] This means that applets you load can do anything a java application that you download and run can do. [COLOR="Red"]Be **very** careful which applets you run[/COLOR].**

I wouldnt use it :D

There is no 64bit Flash plugin, you need nspluginwrapper. [I wrote a script that will install it in seconds.]("http://ubuntuforums.org/showthread.php?t=425672")

There is always the old standby of installing a 32bit browser and plugins so you have everything available. There is a script for that to, see my signature.

I know this java plugin, I meant a Sun java plugin. gcj-compat and blackdown are too old for what I need.

But thanks for the reply anyway. I guess I'll wait for flash 10 and java 7.

---

### Post by Kilz on 2007-06-03
> **Gotterdammerung said:**
> I know this java plugin, I meant a Sun java plugin. gcj-compat and blackdown are too old for what I need.

But thanks for the reply anyway. I guess I'll wait for flash 10 and java 7.

You can install java 6 , flash 9 and a 32bit browser. That way you would have the power for needed tasks, and nothing worse than you have now with the browser in the 32bit os.

---

