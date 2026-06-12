---
title: "Cant execute files.."
date: 2006-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by deanhopkins on 2006-12-07
Ok. I just installed Edgy x64 from Edgy x86, and backed up some files that I wanted to keep data from. Specifically:

SuperPi
Folding@Home

None of these are arch specific, so I dont see how it can make any difference.

But basically, ive put them into my home folder, and whenever I try to execute them I get this:

```
dean@linux:~/Folding$ ./FAH504-Linux.exe
bash: ./FAH504-Linux.exe: No such file or directory
dean@linux:~/Folding$
```

Even though it clearly is there, im looking right at it in nautilus.

Ive tried it as sudo, same problem. Cant think of anything else so im posting here.

Thanks for any help.

---

### Post by endersshadow on 2006-12-07
Try this:

```
chmod +x ~/Folding/FAH504-Linux.exe
~/Folding/FAH504-Linux.exe
```

That should run it.  Though usually exe's only run under Windows...

---

### Post by deanhopkins on 2006-12-07
Its just a normal linux script, check the f@h FAQ :)

Will try that now.

---

### Post by deanhopkins on 2006-12-07
```
dean@linux:~/Folding$ ./FAH504-Linux.exe
bash: ./FAH504-Linux.exe: No such file or directory
dean@linux:~/Folding$ 
```

---

### Post by bAnj0 on 2006-12-08
I think it's an error given by the script , not by the shell,
so it doesn't that **FAH504-Linux.exe** doesn't exist, but
something which is called by the script doesn't exist.

check the first line #!bin/bash ot whatever shell you use if it's still
in that location.
if the shell it's ok you can add on the second line a : set -x to see debug info. 

I hope it helps 


```
dean@linux:~/Folding$ ./FAH504-Linux.exe
bash: ./FAH504-Linux.exe: No such file or directory
dean@linux:~/Folding$
```

---

### Post by dbott67 on 2006-12-08
Can you please post the output of:
```
ls -all ~/Folding/
```

Thanks,
Dave

---

### Post by Tintazul on 2006-12-11
Hi everyone. ls -all folding/ yields

```
total 264
drwxr-xr-x  2 master master   4096 2006-12-11 17:45 .
drwxr-xr-x 17 master master   4096 2006-12-11 17:39 ..
-rwxr-xr-x  1 master master 250964 2006-12-11 16:58 FAH504-Linux.exe
-rwxr-xr-x  1 master master     34 2006-12-11 17:45 myfoo
master@atl:~$ 

```
I have the same problem: can't execute what seems to be there (FAH504-Linux.exe). And that's a binary, not a shell script. myfoo is a script which just outputs "ll" - I made it for testing whether the problem was general.

My rig is an AMD64 3500+, running edubuntu 6.10. I have a very old Intel MMX running xubuntu, and it's finding its own FAH504-Linux.exe without any problem.

Help... ](*,)

---

### Post by dbott67 on 2006-12-11
What command are you typing in?

Generally, you need to precede the command with **[COLOR="Red"]./[/COLOR]**

CD to your folding directory and type in:
```
./FAH504-Linux.exe
```

If that's what your already doing, then perhaps it may be related to the bash vs. dash issue that others have faced when running scripts that expect to see bash (I believe the developers have switched to dash instead of bash).  I know it caused me grief when trying to install the ATI drivers.

This is the bash/dash hack:
> Depending how recently updated your Edgy installation is, you may run into problems with the installer complaining about syntax errors. A recent Edgy update changed the shell sh from bash to dash. You will have to do some extra work on the command line by temporarily making the sh command redirect to bash instead.
1. Backup current shell & switch to bash:
```
sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh
```
2. Run script:
```
./FAH504-Linux.exe
```
3. Restore dash as shell:
```
sudo mv /bin/sh.bak /bin/sh
```

or you can just try pre-pending the script with 'bash':
```
bash ./FAH504-Linux.exe
```

-Dave

---

### Post by Tintazul on 2006-12-11
Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs. It's now working fine! The solution was found on this thread of the Folding Community forum: [64 Bit Linux Needs 32 bit compatibility libraries? [YES]]("http://forum.folding-community.org/viewtopic.php?t=17223")

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

---

### Post by Xenolard on 2007-02-11
> **Tintazul said:**
> Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs. It's now working fine! The solution was found on this thread of the Folding Community forum: [64 Bit Linux Needs 32 bit compatibility libraries? [YES]]("http://forum.folding-community.org/viewtopic.php?t=17223")

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

Magic, that sorted me too. Thanks!

---

