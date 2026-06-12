---
title: "Programms are not closed &quot;soft&quot; on shutdown"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by blauer-affe on 2009-02-15
Hi, my problem is that programs are just closed on shutdown.
firefox for example claims it has been closed unexpected after a systemrestart and asks for session restore, gedit doesnt ask if i'd like to save my files before shutdown.

i also tryed to use sudo shutdown -h now and ran killall5 -15 
allways the same reaction programs are killed and not terminated properly

i dont know if this is a normal behaviour, but i dont think so...

any ideas?

(using ubuntu x64 8.10)

---

### Post by blauer-affe on 2009-02-15
anyone? plz

---

### Post by blauer-affe on 2009-02-15
sry for double Post problem already mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=1054598](http://ubuntuforums.org/showthread.php?t=1054598)

still no answers... :confused:

---

### Post by novafluxx on 2009-02-15
I have noticed the same thing. So far it appears only firefox complains about it. It happens in the 32bit version as well (I frequently use both).

If its a bug I'm sure its been noticed, check the launchpad...don't ask me how im a noob too!

---

### Post by Ng Oon-Ee on 2009-02-15
It's normal behaviour, AFAIK. The shutdown scripts do not include any 'soft' kill behaviours for programs. The programs themselves need to implement something of the sort, I believe.

---

### Post by blauer-affe on 2009-02-16
hmm thx for that

so i will try to add some commands to the shutdown script myself...

```
dcop amarok MainApplication-Interface quit
```

this works for amarok since its a kde app, but im still looking for a similar command to close firefox...

if someone knows a way to tell firefox to exit from command line plz let me know!

---

### Post by blauer-affe on 2009-02-17
i found an app witch does what i need:

wmctrl
```
sudo apt-get install wmctrl
```

and i wrote a little shell script which uses wmctrl to close all instances of an app...
```

#!/bin/sh
kclose ( )
{
if test $1
then
run=1
if test $2
then
window=$2
echo "  procname is: $1    windowtitle is: $window" 
else
window=$1
echo "  procname is: $1    (used as windowtitle)"
fi
while [ $run -eq 1 ];
do
P_ID=`pidof -s $1`
if test $P_ID
then
echo $P_ID "$1 still running closing it kindly..."
if test $1 = "amarokapp"
then
dcop amarok MainApplication-Interface quit
else
wmctrl -c $window
fi
sleep 1
else
echo "$1 seems closed"
run=0
fi
done
else
echo "plz specify process to close!"
echo "kclose [process] (windowtitle)"
fi
}

#klose [process] (windowtitle)
#kclose will check if the process is running and close every instance "gracefully" using wmctrl (dcop for amarok)
#wmctrl uses the window title and not the process name so if the title is diffrent from the processname, 
#you may specify the correct name as the second argument (windowtitle).

kclose firefox
kclose amarokapp
kclose gnometris
kclose gnomine Mines
kclose thunderbird
kclose gedit

sleep 2
sudo shutdown -h now 
```

---

