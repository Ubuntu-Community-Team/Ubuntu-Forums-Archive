---
title: "TW 32bit: gstreamer file conflicts"
date: 2023-11-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-11-24
```
# zypper dup
Downloading: mpv-bash-completion-0.37. 0+git20231121.2a57a6ee[done (1.1 MiB/s)]

Search for file conflicts: ....................................[error]
2 detected file conflicts:

File/usr/lib/gstreamer-1.0/libgstresindvd.so
  from the installation of
     gstreamer-plugins-bad-1.22.7-432. 1.i586 (multimedia:libs)
  conflict with the package file
     gstreamer-plugins-bad-codecs-1.22.7-1699. 1.pm.1.i586 (@System)

File/usr/lib/gstreamer-1.0/libgstsiren.so
  from the installation of
     gstreamer-plugins-bad-1.22.7-432. 1.i586 (multimedia:libs)
  conflict with the package file
     gstreamer-plugins-bad-codecs-1.22.7-1699. 1.pm.1.i586 (@System)

File conflicts occur when two packages try to install files with the same name but different content. If you continue, the conflicting files will be overwritten and you will lose the previous content.
Continue? [yes/no] (no):
```

What is please optimal solution ?

---

### Post by maketopsite on 2023-11-30
Solved by another distribution upgrade.

---

### Post by maketopsite on 2023-12-14
Recomended solution: [https://www.linuxquestions.org/questions/suse-opensuse-60/tw-32bit-gstreamer-file-conflicts-4175731168/#post6470117](https://www.linuxquestions.org/questions/suse-opensuse-60/tw-32bit-gstreamer-file-conflicts-4175731168/#post6470117)

---

