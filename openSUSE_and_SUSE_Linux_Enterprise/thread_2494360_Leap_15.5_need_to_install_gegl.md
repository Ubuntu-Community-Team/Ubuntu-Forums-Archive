---
title: "Leap 15.5: need to install gegl ?"
date: 2024-01-14
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-01-14
```
maketopsite:/home/maketopsite #  LANG=C zypper lp && LANG=C zypper if gegl
Loading repository data...
Reading installed packages...

Repository                                                   | Name                      | Category    | Severity | Interactive | Status   | Since | Summary
-------------------------------------------------------------+---------------------------+-------------+----------+-------------+----------+-------+--------------------------------------------------
Update repository with updates from SUSE Linux Enterprise 15 | openSUSE-SLE-15.5-2024-91 | feature     | moderate | ---         | optional | -     | Feature update for jetbrains-annotations, saxon10
Update repository with updates from SUSE Linux Enterprise 15 | openSUSE-SLE-15.5-2024-98 | recommended | moderate | ---         | needed   | -     | Recommended update for gegl

Found 2 applicable patches:
1 patch optional                                                         (use '--with-optional' to include optional patches)
1 patch needed (0 security patches)

Loading repository data...
Reading installed packages...


Information for package gegl:
-----------------------------
Repository     : Update repository with updates from SUSE Linux Enterprise 15
Name           : gegl
Version        : 0.4.34-150400.3.5.2
Arch           : x86_64
Vendor         : SUSE LLC <https://www.suse.com/>
Installed Size : 41.3 KiB
[COLOR=#ff0000]Installed      : No
Status         : not installed[/COLOR]
Source package : gegl-0.4.34-150400.3.5.2.src
Upstream URL   : http://gegl.org/
Summary        : Generic Graphics Library
Description    : 
    GEGL provides infrastructure to do demand based cached non destructive
    image editing on larger than RAM buffers. Through babl, it provides
    support for a wide range of color models and pixel storage formats for
    input and output.

```

I don't know this package, is it please really necessary to install it ?

---

### Post by maketopsite on 2024-01-21
needed by gimp

---

