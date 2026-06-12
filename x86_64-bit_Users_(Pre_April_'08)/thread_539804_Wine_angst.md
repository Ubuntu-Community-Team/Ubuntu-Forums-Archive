---
title: "Wine angst"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by groeswenphil on 2007-08-31
I think I'm almost there.
I've downloaded the deb...........I think I got it to run using force architecture.
Now, when I try wincfg I got this.

~/Desktop$ sudo dpkg -i --force-architecture wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 137294 files and directories currently installed.)
Preparing to replace wine 0.9.43~winehq0~ubuntu~6.06-1 (using wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.43~winehq0~ubuntu~6.06-1) ...

philip@concertina:~/Desktop$ winecfg
wine: creating configuration directory '/home/philip/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/philip/.wine'.
philip@concertina:~/Desktop$ wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/system.reg : No such file or directory
wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/user.reg : No such file or directory


Is this because I set Terminal to read the deb package from the desktop and now I should be somewhere else?

All the best,
Phil

---

### Post by crjackson on 2007-08-31
> **groeswenphil said:**
> I think I'm almost there.
I've downloaded the deb...........I think I got it to run using force architecture.
Now, when I try wincfg I got this.

~/Desktop$ sudo dpkg -i --force-architecture wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 137294 files and directories currently installed.)
Preparing to replace wine 0.9.43~winehq0~ubuntu~6.06-1 (using wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.43~winehq0~ubuntu~6.06-1) ...

philip@concertina:~/Desktop$ winecfg
wine: creating configuration directory '/home/philip/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/philip/.wine'.
philip@concertina:~/Desktop$ wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/system.reg : No such file or directory
wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/user.reg : No such file or directory


Is this because I set Terminal to read the deb package from the desktop and now I should be somewhere else?

All the best,
Phil

Are you trying to install wine?  It looks like you are trying to install 32 bit Wine on a 64 bit OS.  Why don't you just install the 64 bit version.  If you enable all your repositories, I think it's in the synaptic package manager.  I installed it once before and I used NO command line interface, and didn't have to force anything.

---

### Post by Kilz on 2007-08-31
> **crjackson said:**
> Are you trying to install wine?  It looks like you are trying to install 32 bit Wine on a 64 bit OS.  Why don't you just install the 64 bit version.  If you enable all your repositories, I think it's in the synaptic package manager.  I installed it once before and I used NO command line interface, and didn't have to force anything.

Perhaps he is using an older version of Ubuntu. There is only a 64bit deb for Feisty. He is getting it from the same place the 64bit deb is at. It wont make any difference anyway. Wine is a 32bit application, the 64bit deb just makes it easier to install. Wine is a 32bit application layer, it has to be because all windows applications are 32bit.

In any event
> **groeswenphil said:**
> ..

philip@concertina:~/Desktop$ winecfg
wine: creating configuration directory '/home/philip/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/philip/.wine'.
philip@concertina:~/Desktop$ wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/system.reg : No such file or directory
wineserver: could not save registry branch to /home/philip/.wine-xpKGHH/user.reg : No such file or directory

Is this because I set Terminal to read the deb package from the desktop and now I should be somewhere else?

All the best,
Phil

No, the errors are quite common. You are going to want to [take a look at this howto]("http://ubuntuforums.org/showthread.php?t=185557") and install the sidenet script to help setup wine. You may also have to install accelerated video drivers if that doesn't solve the problem.

---

### Post by groeswenphil on 2007-09-01
OK Did the sidenet thing and it appeared to load in.
Now when I try winecfg I get this.

philip@concertina:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
philip@concertina:~$


????????Phil

---

### Post by Kilz on 2007-09-01
> **groeswenphil said:**
> OK Did the sidenet thing and it appeared to load in.
Now when I try winecfg I get this.

philip@concertina:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
philip@concertina:~$


????????Phil

Please read that howto page , it gives the information on your error.

---

### Post by groeswenphil on 2007-09-01
[SIZE="7"]IT'S WORKING NOW !!![IMG]http://www.esnips.com/imageable/medium/4b76ec00-dc25-4fac-a674-e6a534de6e8e/?du=2f5daf47-90d8-49a9-9138-1855fa1248b4&uu=6b519b74-c652-4d38-8ae5-5c31a92cd95c&dt=1188243319000&fu=25fc0b73-73a2-4a33-a5b6-2f120984e4b2[/IMG][/SIZE]:guitar:

---

