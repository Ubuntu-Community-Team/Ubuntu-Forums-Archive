---
title: "i8kfangui on 64 bit"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-05-21
I've downloaded i8kfangui for linux.  I can not get it running.  I've run "make" sucessfully.
"root@djr-laptop:/home/djr/Desktop/dellfand-0.7# make dellfand
make: `dellfand' is up to date."
Build:
	make

Run:
       dellfand mode sleep-seconds off low high

"root@djr-laptop:/home/djr/Desktop/dellfand-0.7# dellfand
bash: dellfand: command not found"

I can't figure out how to get this running, any help would be appreciated.
:popcorn:

---

### Post by shad0w_walker on 2007-05-22
From what i see you have only run the make command, this will compile the program but doesnt acctually install it into any of its destination folders. Should be fairly easy to fix, try running this command

```
sudo make install
```

That should install the program to the correct folders and it should run fine. Good luck.

---

### Post by Mr_bleu on 2007-05-22
root@djr-laptop:/home/djr/Desktop# cd /home/djr/Desktop/dellfand-0.7
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# sudo make install
make: *** No rule to make target `install'.  Stop.
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# make install dellfand
make: *** No rule to make target `install'.  Stop.
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# make install dellfand.cc
make: *** No rule to make target `install'.  Stop.
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# make dellfand install
g++ -Wall -O2 dellfand.cc -o dellfand
make: *** No rule to make target `install'.  Stop.
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# 

I'm a linux newbie......any help is greatly appreciated.  Thanks.  I've dumped windows completely.

---

### Post by shad0w_walker on 2007-05-23
Have you tried the steps you were following before (make, etc,etc) and then tried running the make install command again?

---

### Post by Mr_bleu on 2007-05-24
I haven't been able to get very far.  I've tried make, read the instructions and that's as far as i've gotten.  

Download/Build
dellfand is only available as a source tarball, since the static build would quickly overwhelm my bandwidth quota.

    dellfand-0.7.tar.bz2 

Extract with

    tar xvf dellfand-0.7.tar.bz2 

Build with

    cd dellfand-0.7; make 

CommandLine Usage
Without arguments, the daemon will print the fan status once and exit.

Normal usage is:

    dellfand mode sleep-seconds off low high 

You must run as root. All arguments are mandatory.

    * mode
      0 - run in the foreground, print stats periodically
      1 - run in the background as daemon, no output
    * sleep-seconds
      dellfand will check the CPU temperature with this interval and adjust the fan speed according to the last 3 arguments
    * off
      when the fan is on, turn it off when the temperature has dropped to this level
    * low
      turn the fan to low speed when it reaches this temperature
    * high
      turn the fan to high speed when it reaches this temperature 

Anyone know of a program to cool off my e1505?  I used this program in windows, doesn't work with my 64bit in linux.

---

### Post by Jouke74 on 2007-05-25
Took me also a while to figure this one out. The executable is there but it does not want to run. The simple answer is to put ./ in front of it... 

If you have to run it as root use the following:
1. Open terminal.
2. Go to the directory where you made the Dellfand
3. type "su" 
4. Give password for root.

5. Then instead of using "dellfand mode sleep-seconds off low high"

use "./dellfand mode sleep-seconds off low high"

the "./" is to make sure bash looks into the directory where you made it.

If this works you can copy the dellfand.bin executable to /usr/local/bin/ . Make sure you are root otherwise you wont have access to this directory. If it is here, you should be able to access Dellfand with the command without "./" as you initially tried.

---

### Post by Mr_bleu on 2007-05-25
I used cp to copy the files to /usr/local/bin.  Thanks.  Now could I get a copy of the right command line?  "root@djr-laptop:/home/djr/Desktop/dellfand-0.7# dellfand mode sleep-seconds off 20 low 40 high 50
 usage: dellfand [<mode> <sleep seconds> <off> <low> <high>]"  

call me slow.........Thanks again for the help.

---

### Post by Mr_bleu on 2007-05-26
I think i've got it.  
djr@djr-laptop:~$ dellfand 0 2 30 38 45
error: syscall ioperm failed: probably you're not running as root.
djr@djr-laptop:~$ sudo dellfand 0 2 30 38 45
Fan 0 Status 1->1 Speed 73380 CPU Temp 38C
Fan 0 Status 1->1 Speed 71970 CPU Temp 38C
Fan 0 Status 1->1 Speed 71610 CPU Temp 38C
Fan 0 Status 1->1 Speed 71610 CPU Temp 38C
Fan 0 Status 1->1 Speed 71970 CPU Temp 34C
Fan 0 Status 1->1 Speed 71970 CPU Temp 34C

It's working sweet.  Thanks.  Does anyone know how I can get this to start w/ os booting?

---

### Post by okos on 2007-05-27
Hi 
Thanks for the advice! You guys have been a great help!

I got frustrated with dellfand because it did not seem to work at first. I did not understand the syntax and there were no examples.

$./dellfand 0 10 40 45 50                works great!

I am not sure how to put it in the bin file because there is no dellfand.bin file.

Also how would you make dellfand start at boot?

any ideas?

okos

---

### Post by Jouke74 on 2007-05-27
The bin file is the linux executable. It's not always called .bin...

---

### Post by okos on 2007-05-27
These are the files in the dellfand dir:

bofn.licence.txt
DISCLAIMER
gpl.txt
CHANGES
etc.default.dellfand
Makefile
dellfand
etc.init.d.dellfand
MANIFEST
dellfand.cc
fan.cc
README

Would I move the dellfand file to the bin dir?

Also any ideas on starting dellfand at boot with all flags?

---

### Post by Mr_bleu on 2007-05-27
cp or mv dellfand.  It's the file you want.  I got frustrated too, I needed the syntax, and took awhile to figure it out.

---

### Post by okos on 2007-05-27
Thanks bleu,

Any ideas on how to start dellfand on boot?
;)

---

### Post by Mr_bleu on 2007-06-01
Not yet, I'm still typing it in a terminal after boot. Works though.

---

### Post by Mr_bleu on 2007-06-01
Another note for newbs, myself included.  You have to install g++ before it will make.  
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# smake
...g++ -Wall -O2 dellfand.cc -o dellfand
sh: g++: not found

I'm running ubuntu on my usb drive as well and it's a fresh install.  I'm installing g++ now.

---

### Post by Mr_bleu on 2007-06-01
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# make dellfand
make: `dellfand' is up to date.
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# cp dellfand /usr/local/bin
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# cp etc.default.dellfand /usr/local/bin
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# cp etc.init.d.dellfand /usr/local/bin
root@djr-laptop:/home/djr/Desktop/dellfand-0.7# dellfand
v0.7: Fan 0 Status 1 Speed 72300 CPU Temp 34

ANyone know how to get this running afterstartup automatically?

---

### Post by Mr_bleu on 2007-06-03
Recap:
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
Save to Desktop.
system>administration>synaptic manager
Install g++ (I clicked the Search button and typed it in)
Untar the file (I'm a former windows user so I double click, then extract)
Open a terminal
$cd ~/Desktop/dellfand-0.7
$chmod a+x dellfand
$sudo cp dellfand /usr/bin
$sudo cp etc.default.dellfand /usr/bin
$sudo cp etc.init.d.dellfand
$sudo dellfand                                            (This will display current fan status output and temp)
$sudo dellfand 1 10 25 35 43                    (My personal settings for dellfan)
OR
$sudo dellfand 0 10 25 35 43                      (This will output the status  until the terminal is closed)
output from the above command:
Fan 0 Status 2->1 Speed 123960 CPU Temp 37C

Still haven't figured out how to get it to run upon boot.
Good luck everyone!!

---

