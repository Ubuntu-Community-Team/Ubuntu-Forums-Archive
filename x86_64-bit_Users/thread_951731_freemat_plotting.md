---
title: "freemat plotting"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by soxs on 2008-10-18
I try to plot data. But as soon as it comes to the plot functions I only get this thrown at me gai and again: ```
Error: Undefined function or variable plot 
```

The script itself:
```
t=1:128;
x=cos(2*pi*t/32);
y=sin(2*pi*t/32);
plot(x,y)
```

Plx help me! I need it to study!

---

### Post by soxs on 2008-10-19
Anyone??? Pease!

BUMP

---

### Post by jpkotta on 2008-10-19
I've never heard of FreeMat, and I'm trying it out.  

I use Octave, and it has seldom let me down.  Is there some specific functionality that FreeMat provides and Octave doesn't?

```
sudo aptitude install octave2.9 gnuplot-x11
```

---

### Post by jpkotta on 2008-10-19
It's a path issue.  Unfortunately, it seems even the path() function isn't in the path.  I just built FreeMat, and I got the same error.  If I cd to FreeMat-3.6/toolbox/graph, plot() is defined, because the pwd is always in the path in Matlab.  Of course, then it complains about missing length(), which is somewhere else.  You need to figure out how to set the path and add all the stuff in the toolbox directory.  I'm going to stick with Octave, even though FreeMat looks very nice.

---

### Post by soxs on 2008-10-20
> **jpkotta said:**
> I've never heard of FreeMat, and I'm trying it out.  

I use Octave, and it has seldom let me down.  Is there some specific functionality that FreeMat provides and Octave doesn't?

```
sudo aptitude install octave2.9 gnuplot-x11
```

Does octave have compatibility with Matlab? That's what I basically require, well at least it seems to be like that.

Btw, does octave have the option to simplyfy terms and differenciate and integrate?

---

### Post by jpkotta on 2008-10-20
Octave generally considers incompatibilities with Matlab as bugs.  See the FAQ.  If you write your programs correctly, they will run on both Matlab and Octave.

I've always found Matlab to be horrible for symbolic math.  Try Maxima (wxMaxima is the GUI) for that.  Personally, I prefer Mathematica or a TI-89 for that stuff, but those cost money.

---

### Post by soxs on 2008-10-20
Thanks for the bunch of tips, I will try as many as I have time to do so... +1

---

### Post by akabla on 2008-12-15
I had the same problem on Intrepid Ibex after downloading the software from synaptic.

As mentioned by jpkotta, one way to solve it is to set the path in the environment. This can be done from the menu: Tools --> Path tool
then select with the left folder tree /usr/share/freemat/toolbox
click "Add With Subfolder"
then save, and it should solve the problem. At least it did for me.

Good luck with that.

---

