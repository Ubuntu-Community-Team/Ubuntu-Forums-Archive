---
title: "Open WINE applications with Firefox"
date: 2008-07-02
forum: Wine
---

### Post by el-mar01 on 2008-07-02
Hi All,

I have a program called Alt.Binz which is a windows application that I use under WINE ... I download nzb files from the internet with Firefox and then go to Alt.Binz and open the downloaded nzb file ... is there any way I can make Firefox open the nzb file with Alt.Binz when I download it ?? ... I have tried pointing Firefox to the Alt.Binz executable but that didn't work.

Thanks,

PS: I am running Firefox 3 with the latest stable version of WINE.

---

### Post by SBFC on 2008-07-02
Just out of curiosity, why aren't you using one of the nzb utils in the ubuntu repos?

I use hellanzb and it works great.

---

### Post by el-mar01 on 2008-07-02
Because I prefer Alt.Binz's NZB video streaming capability .. I don't think you can do NZB streaming with hellanzb.

---

### Post by SBFC on 2008-07-02
Create a shell script that launches AltBinz with wine.

For instance, in /usr/local/bin create a file called 'nzb'.

Inside have 

```

#!/bin/bash

pushd /path/to/AtlBinz/install/dir
wine altbinz.exe $1

```

Then just select your 'nzb' script from Firefox's 'Open With' dialog.

---

### Post by sinnadyr on 2009-06-09
> **SBFC said:**
> Create a shell script that launches AltBinz with wine.

For instance, in /usr/local/bin create a file called 'nzb'.

Inside have 

```

#!/bin/bash

pushd /path/to/AtlBinz/install/dir
wine altbinz.exe $1

```

Then just select your 'nzb' script from Firefox's 'Open With' dialog.
That didnt work for me with µTorrent :\ Just wont open

EDIT: Forgot to make it executable, but it didnt do the job anyways

---

### Post by NightMKoder on 2009-06-09
> **sinnadyr said:**
> That didnt work for me with µTorrent :\ Just wont open

EDIT: Forgot to make it executable, but it didnt do the job anyways

Try it with "$@" instead of $1 (quotes included)

EDIT: /Smack self. Bad helper. Correction:

Try it with:
```

#!/bin/bash

pushd /path/to/AtlBinz/install/dir
wine altbinz.exe "`winepath -w \"$@\"`"

```
And don't forget to change the path.

---

