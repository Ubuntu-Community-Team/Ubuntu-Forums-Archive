---
title: "gtk version problem"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2005-11-27
So I have a problem installing LiVES 
```

checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
so I'm guessing that it would go something like
```

#PKG_CONFIG_PATH=gtk+-2.0.pc
#export PK_CONFIG_PATH

```
... is this correct ?
... and where do I find the .pc file ?

---

### Post by RAOF on 2005-11-27
Do you have the gtk-dev libs installed?  They should set up the environment themselves.

(I think the package you want is called libgtk2.0-dev, but synaptic search is your friend ;))

---

