---
title: "Adding parameters."
date: 2013-07-09
forum: Wine
---

### Post by Ashboy on 2013-07-09
Hi there. Having a bit of a problem with a small Windows program that requires some extra parameters to be fed to it. It works fine in Windows, but in Linux the additional symbols confuse command shell, I think. It splits it up in smaller bits and assumes they are seperate commands.

This is the exact line:
```
wine MOD144.exe [ --mins | --form CGRID.wav | CGRID.wav ]
```

There can be no variations after the .exe, it needs to be exactly like this or it won't work. Is there any way to achieve this properly?

---

### Post by Beren Camlost on 2013-07-09
Try wrapping it in "", like this:

```

wine "MOD144.exe [ --mins | --form CGRID.wav | CGRID.wav ]"
```

---

### Post by Ashboy on 2013-07-09
Doesn't work. If I do that, I all it returns is:
```
wine: cannot find 'MOD144.exe [ --mins | --form CGRID.wav | CGRID.wav ]'
```

I'm guessing it thinks that is the entire filename. Which it of course isn't.

---

### Post by steeldriver on 2013-07-09
Wait... are you literally typing 

```
[ --mins | --form CGRID.wav | CGRID.wav ]
```

That doesn't sound right - that type of square bracket syntax usually indicates *optional *arguments i.e. EITHER

```
MOD144.exe --mins
```

OR

```
MOD144.exe --form CGRID.wav
```

OR

```
MOD144.exe CGRID.wav
```

---

### Post by Ashboy on 2013-07-09
I'm sorry, but I am right. Vary even slightly from the way I typed it and the program doesn't accept it. God knows why, I didn't make it.

---

### Post by steeldriver on 2013-07-09
well in that case you could try single quotes around the argument string (this should prevent the linux shell from attempting to expand it) i.e.

 ```
wine MOD144.exe [COLOR=#0000ff]**'**[/COLOR][ --mins | --form CGRID.wav | CGRID.wav ][COLOR=#0000ff]**'**[/COLOR]
```

---

### Post by Ashboy on 2013-07-09
I found a different solution by running it through '$ wine cmd' first. That completely negated the Linux syntax for me.

---

