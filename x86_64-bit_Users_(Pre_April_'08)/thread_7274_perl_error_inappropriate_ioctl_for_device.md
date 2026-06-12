---
title: "perl error: inappropriate ioctl for device"
date: 2004-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rink on 2004-12-05
I'm getting the above error in my Perl program.

Searches on google and the like suggest that this is an incompatability associated with 'bleeding edge distros' (sounds right!)

my simple code is as follows:

```

sub DXFHeaders{
[INDENT]
open(OUTFH,">/tmp/dxf");
print OUTFH  "  0\nSECTION\n  2\nHEADER\n  0\nENDSEC";
[/INDENT] 
}

``` 

It was working, but has ceased. Anyone got any ideas?

---

### Post by Rink on 2004-12-05
Sorry, forgot to mention that I used 

'or die"File write failed";'

which didn't die and print the error, but just proceeded as if the file had been written to.

It was only when I interrogated $! that I got the error string.

---

