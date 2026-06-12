---
title: "I can't open a .bin file"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by Gins on 2008-12-27
I downloaded the following file.

dynamips-0.2.7-amd64.bin


Afterwards, I did the following to change the executable rights.

root@ni-desktop:/home/ni/Desktop# chmod 755 dynamips-0.2.7-amd64.bin
root@ni-desktop:/home/ni/Desktop# 



The following didn't work.

root@ni-desktop:/home/ni/Desktop# sudo ./dynamips-0.2.7-amd64.bin
./dynamips-0.2.7-amd64.bin: 1: Syntax error: Unterminated quoted string
root@ni-desktop:/home/ni/Desktop# 

[B]What is the meaning of the error message?
How do I install the program? [/B]
The program is a router simulator.

---

### Post by cariboo on 2008-12-27
If you are running as root, you don't need sudo. At the prompt, just run the command without sudo.

Jim

---

### Post by Gins on 2008-12-27
Thanks cariboo for the reply.

First I logged on as a superuser and tried the following:

root@ni-desktop:/home/ni/Desktop# chmod 755 dynamips-0.2.7-amd64.bin
root@ni-desktop:/home/ni/Desktop# 
root@ni-desktop:/home/ni/Desktop# ./dynamips-0.2.7-amd64.bin
bash: ./dynamips-0.2.7-amd64.bin: cannot execute binary file
root@ni-desktop:/home/ni/Desktop# 

[B]What is the problem?
[/B]

---

### Post by jflaker on 2008-12-27
right click then Properties

Under Permissions, click on "Allow executing file as program"

I had to do that for Google Earth

---

### Post by Gins on 2008-12-27
Thanks jflaker for the reply.

I did what you suggested.

What is the next step?

---

### Post by Rog-Mahal on 2008-12-27
Don't you have to use sh to execute a .bin?

---

### Post by cariboo on 2008-12-28
I downloaded the file, I'm using jaunty alpha2, just made the bin executeable and it ran the way it was supposed to. I take you are taking a Cisco course of some sort, so usage should be in your documentation.

Jim

---

### Post by felker2 on 2008-12-28
You're trying to use the Cisco 7200 router emulator, right? 

first of all: check your OS with "uname -a", as trying to execute the amd64 binary on a 32-bit Ubuntu will result in an error

```
sander@flappie:~$ ./dynamips-0.2.7-amd64.bin 
bash: ./dynamips-0.2.7-amd64.bin: cannot execute binary file
sander@flappie:~$
```

If you use 32-bit Ubuntu (with 686 in the name, and not x86_64), then you should use the 32-bit version of the simulator.


Long story:



I downloaded the 32-bit version from [http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator](http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator) , and then did

```
chmod +x dynamips-0.2.7-x86.bin 
./dynamips-0.2.7-x86.bin
```

That works:


```
Cisco Router Simulation Platform (version 0.2.7-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: May 26 2007 11:51:28

Usage: ./dynamips-0.2.7-x86.bin [options] <ios_image>

Available options:
  -H <tcp_port>      : Run in hypervisor mode

  -P <platform>      : Platform to emulate (7200, 3600, 2691, 3725 or 3745) (default: 7200)

  -l <log_file>      : Set logging file (default is dynamips_log.txt)
<snip>

```

So, that's good.

Let's see what happens on my 64-bit system:

```
sander@ubuntu810-on-athlon64:~$ wget http://www.ipflow.utc.fr/dynamips/dynamips-0.2.7-amd64.bin
--2008-12-28 14:10:42--  http://www.ipflow.utc.fr/dynamips/dynamips-0.2.7-amd64.bin
Resolving www.ipflow.utc.fr... 195.83.155.17
Connecting to www.ipflow.utc.fr|195.83.155.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1003952 (980K) [application/octet-stream]
Saving to: `dynamips-0.2.7-amd64.bin'

100%[=================================================================================================>] 1,003,952   1013K/s   in 1.0s    

2008-12-28 14:10:43 (1013 KB/s) - `dynamips-0.2.7-amd64.bin' saved [1003952/1003952]

sander@ubuntu810-on-athlon64:~$ ll dynamips-0.2.7-amd64.bin 
-rw-r--r-- 1 sander sander 1003952 2007-05-26 12:10 dynamips-0.2.7-amd64.bin
sander@ubuntu810-on-athlon64:~$ chmod +x dynamips-0.2.7-amd64.bin 
sander@ubuntu810-on-athlon64:~$
sander@ubuntu810-on-athlon64:~$ ./dynamips-0.2.7-amd64.bin  | less

Cisco Router Simulation Platform (version 0.2.7-amd64)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: May 26 2007 11:55:39

Usage: ./dynamips-0.2.7-amd64.bin [options] <ios_image>

Available options:
  -H <tcp_port>      : Run in hypervisor mode

  -P <platform>      : Platform to emulate (7200, 3600, 2691, 3725 or 3745) (default: 7200)

  -l <log_file>      : Set logging file (default is dynamips_log.txt)
  -j                 : Disable the JIT compiler, very slow

<snip>
```

So: good too.

Steps for you:
1) delete old .bin file.
2) reload the bin file like above
3) chmod +x ...
4) execute it as normal user with ./dyn...

PS: first of all: check your OS with "uname -a", as trying to execute the amd64 on a 32-bit Ubuntu will result in an error

```
sander@flappie:~$ ./dynamips-0.2.7-amd64.bin 
bash: ./dynamips-0.2.7-amd64.bin: cannot execute binary file
sander@flappie:~$
```

---

### Post by felker2 on 2008-12-28
> **Gins said:**
> Thanks cariboo for the reply.

First I logged on as a superuser and tried the following:

root@ni-desktop:/home/ni/Desktop# chmod 755 dynamips-0.2.7-amd64.bin
root@ni-desktop:/home/ni/Desktop# 
root@ni-desktop:/home/ni/Desktop# ./dynamips-0.2.7-amd64.bin
bash: ./dynamips-0.2.7-amd64.bin: cannot execute binary file
root@ni-desktop:/home/ni/Desktop# 

[B]What is the problem?
[/B]

The cause might be that you're using a 32-bit Ubuntu. Check with "uname -a": i686 GNU/Linuxmean 32-bit, x86_64 GNU/Linux means 64-bit.
If you use 32-bit Ubuntu, use the 32-bit binary from the cisco7200-simulator site.

And: you don't have to be root to execute this file. It's safer not to be root.

See my other post for full explanation.

---

### Post by felker2 on 2008-12-29
@Gins: any results?

---

