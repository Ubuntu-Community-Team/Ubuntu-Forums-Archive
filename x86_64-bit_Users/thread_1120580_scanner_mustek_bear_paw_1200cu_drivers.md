---
title: "scanner mustek bear paw 1200cu drivers"
date: 2009-04-09
forum: x86 64-bit Users
---

### Post by rcmonitor on 2009-04-09
i`ve got ubuntu 8.10 x64
and mustek bear paw 1200cu
smoking forums on the issue bring me to
[http://www.sane-project.org/sane-mfgs.html#SCANNERS]("http://www.sane-project.org/sane-mfgs.html#SCANNERS")
where my scanner is good supported
so i downloaded gt68xx (1.0-84), set it up
and sudo apt-get install xsane
starting xsane ends with error:
"failed to open device `gt68xx:libusb:002:003': invalid argument"

how do i supposed to fix it?

---

### Post by desertdog on 2009-04-11
See the man page for the gt68xx sane backend at [http://www.sane-project.org/man/sane-gt68xx.5.html](http://www.sane-project.org/man/sane-gt68xx.5.html). Also see [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/).

You have to extract a firmware file from the windows driver and put in a file on your linux machine. See the above links for descriptions on how to do this.

---

