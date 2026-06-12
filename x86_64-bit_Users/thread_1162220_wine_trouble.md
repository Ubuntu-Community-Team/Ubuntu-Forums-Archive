---
title: "wine trouble"
date: 2009-05-17
forum: x86 64-bit Users
---

### Post by c4tly5t on 2009-05-17
i am currently trying to build wine-1.1.21
and when i sudo apt-get build-dep wine i get this


Errors were encountered while processing:
 tex-common
 texlive-common
 texlive-doc-base
 texlive-base-bin
 texlive-base
 texlive-latex-base
 texlive-fonts-recommended
 texlive-latex-recommended
 tipa
 jadetex
 docbook-utils
 dvipdfmx
 latex-xcolor
 pgf
 latex-beamer
 lmodern
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-base-bin-doc
 texlive-extra-utils
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

what do i do to fix it?
i also get the same error when i dpkg --configure -a

---

### Post by pixel :-) on 2009-05-17
are you aware that you can simply installed a binary package? Or you are trying to do something fancy?

---

### Post by Yellow Pasque on 2009-05-17
> **pixel :-) said:**
> are you aware that you can simply installed a binary package? Or you are trying to do something fancy?
Even so, the build-dep command should work and his/her dpkg is probably borked now.

To OP: If dpkg is not working, we need more detail as to what actually caused that error if you want us to troubleshoot. You can find this detail towards the end of /var/log/apt/term.log

---

