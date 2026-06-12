---
title: "Firefox and Yelp hosed ... Suggestions?"
date: 2006-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by stirmac on 2006-05-22
Hey folks, I'm new to the Ubunto (and linux in general) and have managed to make firefox and yelp unuseable in 5.10.  All was working well until I installed all the packages to get mp3/DVD/Real Player/etc. working.  I did this with synaptic, but allowed firefox and yelp to remain open so I could follow the instructions.  I've tried rebooting and reinstalling firefox to no effect.

When I attempt to start firefox, it acts like it tries for ~10 seconds then nothing.  With yelp, it just brings up an error message asking if I want to report the problem.

Any suggestions?

Regards,
Stirling

---

### Post by Ribs on 2006-05-25
Do you get any error messages when you try to run firefox from the console? Try re-installing firefox from Synaptic.

---

### Post by rplantz on 2006-05-27
[QUOTE=stirmac]
When I attempt to start firefox, it acts like it tries for ~10 seconds then nothing.  With yelp, it just brings up an error message asking if I want to report the problem.

Any suggestions?

Regards,
Stirling[/QUOTE]

I experienced the same problem on Breezy. Start up a terminal, make sure that you are in your home directory, then cd into .mozilla/firefox. In this directory you should see a directory that ends with ".default". (The first part will probably be different from mine.)
```

bob@ubuntu:~$ cd
bob@ubuntu:~$ cd .mozilla/firefox/
bob@ubuntu:~/.mozilla/firefox$ ls
pluginreg.dat  profiles.ini  xfi6xbsb.default
bob@ubuntu:~/.mozilla/firefox$

```

cd into this directory. In there you will see a file named "compreg.dat". Remove that file. (To be very cautious, move it to your home directory. If firefox/yelp work okay after this, then deleted the "compreg.dat" file in your home directory.) For example,
```

bob@ubuntu:~/.mozilla/firefox/xfi6xbsb.default$ mv compreg.dat ../../

```
will move it to your home directory. If you are a little more adventerous, simply do
```

bob@ubuntu:~/.mozilla/firefox/xfi6xbsb.default$ rm compreg.dat

```

---

