---
title: "Openoffice Freeze"
date: 2008-08-06
forum: x86 64-bit Users
---

### Post by emist on 2008-08-06
Hey I'm running Gutsy in a twinview setup. Whenever I open any openoffice application it starts up fine and it displays fine, however, it just freezes. I can't use it at all. It also takes a while to terminate once I send it a kill signal. 

Any ideas whats going on?

My xconf is:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
    Option         "TwinView"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "MetaModes" "1440x900, 1440x900"
EndSection

```

---

