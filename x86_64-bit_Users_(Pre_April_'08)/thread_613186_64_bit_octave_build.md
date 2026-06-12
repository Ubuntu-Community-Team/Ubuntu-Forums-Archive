---
title: "64 bit octave build"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ljbusse on 2007-11-14
Is anyone running a 64 bit version of octave?  If so, I'm interested in knowing the result of this command:
[c,s]=computer
What is returned for s?
This is the MAXSIZE of a matrix and I need it to be really big.
Thanks for your help.

---

### Post by jpkotta on 2007-11-14
I get an error with that command.  My octave apparently thinks it only returns a scalar.

```
octave:1> [c,s] = computer 
c = x86_64-pc-linux-gnu
error: element number 2 undefined in return list
error: evaluating assignment expression near line 1, column 8
octave:1> s
error: `s' undefined near line 1 column 1

```

---

### Post by jpkotta on 2007-11-15
Ah, I needed a more up to date octave.  The limit is the same as the 32-bit version.
```
octave:2> [c m e] = computer
c = x86_64-pc-linux-gnu
m =  2.1475e+09
e = L
```

---

### Post by ljbusse on 2007-11-15
Did you build your new version of octave?  If so, were there any flags to enable 64-bit addressing or code generation?
Thanks.

---

### Post by jpkotta on 2007-11-15
I just installed the octave2.9 package.

Edit: I was curious, and I got the source.  Apparently there is such an option.
```

[jpkotta@gauss octave-2.9.17](0)$ ./configure --help
...
  --enable-64             (EXPERIMENTAL) use 64-bit integers for array
                          dimensions and indexing
...

```

---

### Post by Pinoy915 on 2007-11-15
This is what I got:

```

[c,s]=computer
octave:1> [c,s]=computer
c = x86_64-pc-linux-gnu
s =  2.1475e+09
octave:2> 

```

---

### Post by ljbusse on 2007-11-16
Thanks for the help.  I'm a little surprised, 2.1xe+09 is approximately 2^31.  I would have expected more from a 64-bit build of octave.  :confused:

---

