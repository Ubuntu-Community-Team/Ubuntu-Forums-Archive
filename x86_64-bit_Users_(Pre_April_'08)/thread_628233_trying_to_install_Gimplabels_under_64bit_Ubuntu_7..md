---
title: "trying to install Gimplabels under 64bit Ubuntu 7.10"
date: 2007-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joe_Linux on 2007-12-01
I am trying to install Gimplabels from 
[http://www.shallowsky.com/software/gimplabels/](http://www.shallowsky.com/software/gimplabels/)
I have tried 
joe51@joe51-desktop:~$ cp labels.scm ~/.gimp-2.4/scripts/
cp: cannot stat `labels.scm': No such file or directory
joe51@joe51-desktop:~$ 

and 
joe51@joe51-desktop:~$ cp gimplabels-0.5 ~/.gimp-2.4/scripts/cp: omitting directory `gimplabels-0.5'
joe51@joe51-desktop:~$ 

The above is in 64bit Ubuntu 7.10
Thank you for any help 
P S I am running Gimp 2.4.0-rc-3, I un tared gimplabels-0.5 it is in my home directory

---

### Post by Kilz on 2007-12-01
> **Joe_Linux said:**
> I am trying to install Gimplabels from 
[http://www.shallowsky.com/software/gimplabels/](http://www.shallowsky.com/software/gimplabels/)
I have tried 
joe51@joe51-desktop:~$ cp labels.scm ~/.gimp-2.4/scripts/
cp: cannot stat `labels.scm': No such file or directory
joe51@joe51-desktop:~$ 

and 
joe51@joe51-desktop:~$ cp gimplabels-0.5 ~/.gimp-2.4/scripts/cp: omitting directory `gimplabels-0.5'
joe51@joe51-desktop:~$ 

The above is in 64bit Ubuntu 7.10
Thank you for any help 
P S I am running Gimp 2.4.0-rc-3, I un tared gimplabels-0.5 it is in my home directory

if gimplabels-0.5 is in your home directory

```
cp ~/gimplabels-0.5/labels.scm ~/.gimp-2.4/scripts/
```

will copy the file into place.
The command is 
cp (copy)   Exact/location/of/the/file     Exact/location/you/want/it/placed
~ = path to your home directory.

---

