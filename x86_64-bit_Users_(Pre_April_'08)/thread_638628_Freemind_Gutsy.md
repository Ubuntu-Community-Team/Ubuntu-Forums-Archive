---
title: "Freemind? Gutsy?"
date: 2007-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by edieguez on 2007-12-12
Hi, anyone got freemind working on Gutsy? Its not in the repository so what is the easiest way to get it installed?

---

### Post by rada on 2007-12-12
<no useful data>

---

### Post by mac.ryan on 2007-12-20
See if this part of the official manual helps:
[http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux)

> ote, on ubuntu 7.10 I found this not to work properly; I must let freemind know where the java environment is as for example:  #!/bin/bash
#launch by ./'Launch freemind'
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/;export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.03/bin/;freemind


---

