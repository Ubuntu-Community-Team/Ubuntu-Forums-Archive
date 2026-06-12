---
title: "Problems installing Ultrastar deluxe"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by arashiko28 on 2009-05-26
I used to have it running and working like a charm when I used 32-bit version. Now it turns out that there's no 64-bit version, even though I forced architecture and installed, had to compile several libraries and I'm missing the libportaudio.so.2, It's not available on synaptic, I have looked for it but only appears as an rpm package for fedora, I downloaded it and converted it to .deb with alien but still get an error message about not being able to convert because even after choosing the x86 64-bit version, it only downloads the i386... Please help!

---

### Post by pixel :-) on 2009-05-26
You can compile it, they promise that its trivial, just copy paste the stuff in the terminal
[http://ultrastardeluxe.xtremeweb-hosting.net/wiki/doku.php?id=development:how_to_compile_usdx_using_the_makefile_quick](http://ultrastardeluxe.xtremeweb-hosting.net/wiki/doku.php?id=development:how_to_compile_usdx_using_the_makefile_quick)



If compiling doesn't work:

"had to compile several libraries" that wasn't nescessairy, and i bet you compilled them as 64 bit or put them in the wrong place.
 
"converted it to .deb with alien" this doesn't work, paths have to be changed

for the libraries, on synaptic, you have the 64 bit libraries, but you, you need the 32 bit libraries, as long as they are installed in the corect places the os can figure out what libs to use for 32 and 64 bit programs. Normally you can run everything 32 bit in 64 bit

first try 

sudo apt-get install ia32-libs

this will install a bunch of 32libs that generally fix the dependencies

if some 32lib is missing, or the version in ia32-libs is incompatible

find the libraries on the internet, extract them by hand, put them in a folder and

/lib/ld-linux.so.2 --library-path PATH EXECUTABLE

this way it will use them
 
with 

ldd executable

you get a list of all the libraries that this executable need, and if the are met.

if it doesn't work, give me a link to all packages you used, i'll try to do it for you.

---

### Post by arashiko28 on 2009-05-29
I already tried that link, no good, but thanks anyway. All the files that I have needed to compile I've downloaded them from getdeb or ubuntu official pages. except for the portaudio.so.2 that one I got it from fedora's page.

---

### Post by pixel :-) on 2009-05-30
It seems that it works in wine. I have no microphone.

OR
You installed the 32bit version?

In synaptic you only have the 64bit stuff, you just compilled and unstiled 64 bit stuff, so its not going to work

if you still have 32bit system, copy the libraries that he needs and put them in /usr/lib32 getlibs will tell you what libs he whants, be carefull the libs them selves depend on other libs.

if not
use getlibs to fix the dependencies

[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

its old, so you will have to hunt down the correct packages, and install them with getlibs. Getlibs looks only in the 32bit repository of the version of your current system.

hunting is here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

sudo apt-get install ia32-libs

installs a bunch of libs that usually are needed, but if the package is old, it may not work

---

### Post by arashiko28 on 2009-05-31
Right now I'm formatting my computer and reinstalling the system. I have 64-bit and that's the one I'm installing now. I had all that 32-bit libs, let's see after installation finishes.;)

---

