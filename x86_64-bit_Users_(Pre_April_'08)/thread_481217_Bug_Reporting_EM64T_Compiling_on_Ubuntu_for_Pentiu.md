---
title: "Bug Reporting?: EM64T Compiling on Ubuntu for Pentium D (945)"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by KamakazieX on 2007-06-22
I created a custom kernel in ubuntu a couple months ago and thought it would be helpfull to report my findings.

I created the basic stripped down kernel, changed the architecture to EM64T and Core2 optimization. Kept everything else basically the same with the exception of the timer frequency and low-lat desktop.

I have a HUGE water cooling system. In 32bit mode in WinXP I run at around 30C w/o peltier on a Pentium D 945. After compiling under ubuntu my findings were an exponential increase in performance. With the exeption of OpenGL- Not sure if it was the Nvidia 9x.xx driver I was using for AMD64 or what not but if I were to run beryl as my desktop mgr. with XGL/NVidia as the renderer it would spike to 62-66C at idle with no activity on the desktop.

Possible bug in the Beryl 64 compilation? Nvidia compilation? Kernel misconfigured?

Eventually it ended up cooking my motherboard chipset after the processor overheated 4-5 times. I got a free replacement from good ol' intel.

I'd like to hear some follow-ups if anyone has any advice or similar experience

The chipset is also watercooled cooled

---

### Post by KamakazieX on 2007-06-22
Another follow up I forgot to report is I am also using a D945GTP intel board to match, with 4x1GB DDR2 and it fails to report (or even use?) the remainder 800mb of the ram.

I'm assuming its a bug in the motherboard firmware and will be contacting intel shortly after. In the meantime is there a kernel hack/workaround that would support the additional 800megs I do have?

.I already have enabled 4gb mem support and showed no improvement.

---

