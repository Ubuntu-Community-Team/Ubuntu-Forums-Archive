---
title: "Cannot create 32bit wine prefix without being hidden"
date: 2015-10-29
forum: Wine
---

### Post by Spency on 2015-10-29
Ubuntu 15.10
Wine 1.7.52

Prefix architecture check script: [http://askubuntu.com/questions/500069/how-to-check-if-my-wine-prefix-is-32-bit-or-64-bit](http://askubuntu.com/questions/500069/how-to-check-if-my-wine-prefix-is-32-bit-or-64-bit)

For some reason whenever I try to create a 32bit prefix like so
```
WINEARCH=win32 WINEPREFIX=~/wine32 winecfg 
```
The winearch.sh test returns 
[B]Prefix is 64 bit

[/B]However, if I create a hidden prefix
```
WINEARCH=win32 WINEPREFIX=~/.wine32 winecfg 
```
The winearch.sh test returns 
[B]Prefix is 32 bit
[/B]
Not really an issue for me any more but it too a while for me to figure this out. Why is this happening?

---

