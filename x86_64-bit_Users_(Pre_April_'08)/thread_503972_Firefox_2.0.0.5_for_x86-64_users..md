---
title: "Firefox 2.0.0.5 for x86-64 users."
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by mhenriday on 2007-07-18
Today, **Mozilla** released **Firefox 2.0.0.5** with several patches, most importantly one which fixed a recently discovered bug which allowed **IE** to permit launching of malware in **Firefox**. Of no great relevance to **Ubuntu** users, of course, as we fortunately don't have **IE** built into our systems, but there are also other **Firefox** bugs, which may be more pertinent to our concerns, that are addressed in this patch. In addition to versions for other set-ups, **Mozilla** offers [**Linux i686**]("http://www.mozilla.com/en-US/firefox/all.html") downloads in various languages. My question is : can we install them on our **x86-64** machines and if so, how, or do we have to wait until a compatible version becomes available in **Synaptic** ?...

Henri

---

### Post by Sockerdrickan on 2007-07-18
**We** have to **wait** for 20 more **hours**, if it goes on as **usual**. :)

---

### Post by Kilz on 2007-07-18
> **Tux0r said:**
> **We** have to **wait** for 20 more **hours**, if it goes on as **usual**. :)

I wonder if [Swiftweasel]("http://swiftweasel.wiki.sourceforge.net/") will beat the Ubuntu deb's release.

---

### Post by mhenriday on 2007-07-18
> **Tux0r said:**
> **We** have to **wait** for 20 more **hours**, if it goes on as **usual**. :)**Twenty hours !** However will we make it ?!! I presume, **TuxOr**, that you're timing the process ?...

Henri

---

### Post by Sockerdrickan on 2007-07-18
Well it isn't too many hours left now if the releases comes as usual! :popcorn:

---

### Post by Sockerdrickan on 2007-07-18
It would be cool if Swiftweasel had some kind of integrated nspluginwrapper

---

### Post by Kilz on 2007-07-18
> **Tux0r said:**
> It would be cool if Swiftweasel had some kind of integrated nspluginwrapper

I think its kinnd of hard to get flash installed, without distributing flash. Most foss projects have problems with that and make the user download it. But my easy as can be nspluginwrapper script does work with swiftweasel.

---

### Post by praxis22 on 2007-07-18
Well, I tried:

Configured thus:

```

./configure --with-x --enable-application=browser --enable-canvas --disable-mailnews --disable-ldap --disable-xft --disable-javaxpcom --enable-extensions --enable-safe-browsing --disable-debug --enable-optimize="-Os -mtune=nocona -march=nocona -m64 -msse3 -mmmx -falign-functions=64 -fforce-addr -fomit-frame-pointer" --enable-strip

```

For a core 2 duo, you can take the -mtune -march out for a non-specific build, or replace them with pentium4 etc, to tune for your CPU, (I would also point out that my system is configured to build stuff, like the kernel if yours isn't all of this is likely to fail.)

Then I typed:

**make**

But it bombed out thus:
```

c++ -o nsGfxFactoryGTK.o -c -fvisibility=hidden -DNATIVE_THEME_SUPPORT -DMOZILLA_INTERNAL_API -DOSTYPE=\"Linux2.6.22\" -DOSARCH=\"Linux\" -DBUILD_ID=0000000000 -DUSE_POSTSCRIPT -I../.. -I./. -I./.. -I./../shared -I./../x11shared   -I../../../dist/include/xpcom -I../../../dist/include/string -I../../../dist/include/widget -I../../../dist/include/view -I../../../dist/include/util -I../../../dist/include/pref -I../../../dist/include/uconv -I../../../dist/include/unicharutil -I../../../dist/include/locale -I../../../dist/include/necko -I../../../dist/include/content -I../../../dist/include/layout -I../../../dist/include/gfx -I../../../dist/include -I../../../dist/include/nspr    -I../../../dist/sdk/include    -fPIC   -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -Os -mtune=nocona -march=nocona -m64 -msse3 -mmmx -falign-functions=64 -fforce-addr -fomit-frame-pointer  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -DMOZILLA_CLIENT -include ../../../mozilla-config.h -Wp,-MD,.deps/nsGfxFactoryGTK.pp nsGfxFactoryGTK.cpp
../../../dist/include/gfx/nsCoord.h: In function ‘float NS_IEEEPositiveInfinity()’:
../../../dist/include/gfx/nsCoord.h:65: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../dist/include/gfx/nsCoord.h: In function ‘PRBool NS_IEEEIsNan(float)’:
../../../dist/include/gfx/nsCoord.h:69: warning: dereferencing type-punned pointer will break strict-aliasing rules
./../nsRenderingContextImpl.h: At global scope:
./../nsRenderingContextImpl.h:194: warning: ‘virtual nsresult nsRenderingContextImpl::DrawString(const char*, PRUint32, nscoord, nscoord, const nscoord*)’ was hidden
nsRenderingContextGTK.h:160: warning:   by ‘virtual nsresult nsRenderingContextGTK::DrawString(const nsString&, nscoord, nscoord, PRInt32, const nscoord*)’
./../nsRenderingContextImpl.h:198: warning: ‘virtual nsresult nsRenderingContextImpl::DrawString(const PRUnichar*, PRUint32, nscoord, nscoord, PRInt32, const nscoord*)’ was hidden
nsRenderingContextGTK.h:160: warning:   by ‘virtual nsresult nsRenderingContextGTK::DrawString(const nsString&, nscoord, nscoord, PRInt32, const nscoord*)’
nsGfxFactoryGTK.cpp: In function ‘nsresult nsFontEnumeratorConstructor(nsISupports*, const nsIID&, void**)’:
nsGfxFactoryGTK.cpp:155: error: ‘nsIFontEnumerator’ was not declared in this scope
nsGfxFactoryGTK.cpp:155: error: ‘result’ was not declared in this scope
make[4]: *** [nsGfxFactoryGTK.o] Error 1

```

Seems to be a font problem, which from a quick browse seems to be the most common cause of build failures. However, now I'm going to bed, so I'll have to pass the torch.

---

### Post by Kilz on 2007-07-18
I just took a look [at the swiftweasel site]("http://swiftweasel.sourceforge.net/"), there is a entry that builds will be available within 24 hours. :D

---

### Post by mhenriday on 2007-07-19
_Twenty-two hours_ and counting, **TuxOr**, since I posted my first message to the thread and _22 hours_ and counting since you responded. *Det är svårt att sia om framtiden*....

Henri

---

### Post by Rui Pais on 2007-07-19
> **Kilz said:**
> I just took a look [at the swiftweasel site]("http://swiftweasel.sourceforge.net/"), there is a entry that builds will be available within 24 hours. :D

yep, swiftweasel wined!! 
2.0.0.5 is available:
[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

:)

---

### Post by Sockerdrickan on 2007-07-19
> **mhenriday said:**
> _Twenty-two hours_ and counting, **TuxOr**, since I posted my first message to the thread and _22 hours_ and counting since you responded. *Det är svårt att sia om framtiden*....

Henri
Should be here anytime now! :P

---

### Post by amgeex on 2007-07-19
It's here now! Just upgraded and all went fine! :D

---

### Post by Kilz on 2007-07-19
Im loving the new Swiftweasel 2.0.0.5, it seems even faster than the 2.0.0.4 version was.

---

### Post by stmiller on 2007-07-20
Kilz: Is this latest swiftweasel in your script? Thanks,

---

### Post by Kilz on 2007-07-20
> **stmiller said:**
> Kilz: Is this latest swiftweasel in your script? Thanks,

The new version is not not in the script yet. But if you have already installed the script once for another browser. You can just download the deb file for Swiftweasel on the howto to install it, or upgrade it.

---

### Post by Rui Pais on 2007-07-20
> **Kilz said:**
> Im loving the new Swiftweasel 2.0.0.5, it seems even faster than the 2.0.0.4 version was.

I was think the same here... seems to start faster at least. 
This should be a secure update only, but it seems to work better!! Well why complain ;)

---

### Post by Sockerdrickan on 2007-07-20
FF 2.0.0.5 released

---

### Post by mhenriday on 2007-07-21
> **Tux0r said:**
> FF 2.0.0.5 releasedThree very load cheers for the **Ubuntu** developers who put an **x86_64** version at our disposal on **Synaptic** so quickly ! No hassle, just download with a few mouseclicks. **Way to go !**...

Henri

PS : Any **Mozilla** expert who's thinking of updating **Synaptic**'s **Thunderbird** download ?...

---

### Post by Kilz on 2007-07-21
> **mhenriday said:**
> Three very load cheers for the **Ubuntu** developers who put an **x86_64** version at our disposal on **Synaptic** so quickly ! No hassle, just download with a few mouseclicks. **Way to go !**...

Henri

PS : Any **Mozilla** expert who's thinking of updating **Synaptic**'s **Thunderbird** download ?...

You should try Swiftweasel, it is a build of the Mozilla Firefox code. It has .deb files available and is real quick.

---

### Post by Sockerdrickan on 2007-07-22
> **Kilz said:**
> You should try Swiftweasel, it is a build of the Mozilla Firefox code. It has .deb files available and is real quick.
I think he wants a Thunderbird look-a-like

---

### Post by Rui Pais on 2007-07-22
> **mhenriday said:**
> ...

PS : Any **Mozilla** expert who's thinking of updating **Synaptic**'s **Thunderbird** download ?...

If you want updated Thunderbird though your package manager you can use this repos:
[http://ubuntu.iuculano.it/dists/feisty/thunderbird](http://ubuntu.iuculano.it/dists/feisty/thunderbird)

they are very good :)
(and both for 32 and 64bits)

---

### Post by nss0000 on 2007-07-22
Running DAPPERx64:
What FireFox 2.x ?? I see NO such creature in my SYNAPTIC repository, nor have I been prompted by the autoinstall wizard. 

Is this another case of Dapper-o-phobia by UBUNTU ???

---

### Post by Kilz on 2007-07-22
> **nss0000 said:**
> Running DAPPERx64:
What FireFox 2.x ?? I see NO such creature in my SYNAPTIC repository, nor have I been prompted by the autoinstall wizard. 

Is this another case of Dapper-o-phobia by UBUNTU ???

Dapper came with Firefox 1.5, the Ubuntu developers are not planing on porting Firefox 2.0 to Dapper. They are applying the security fixes to the Firefox 1.5 code base. But if you would like to use Firefox 2.0.0.5, [Swiftweasel]("http://swiftweasel.sourceforge.net/"), an optimized build of Firefox works fine on Dapper. its basically a fast Firefox.

---

### Post by Krydahl on 2007-07-22
Complete newbie here.

Just used your script to install 32 bit swiftweasel. Worked like a charm. Have now upgraded to 2.0.0.5, also effortless. Thanks.

---

### Post by Rui Pais on 2007-07-22
> **Krydahl said:**
> Complete newbie here.

Just used your script to install 32 bit swiftweasel. Worked like a charm. Have now upgraded to 2.0.0.5, also effortless. Thanks.

The safest way would be, download the new version for your cpu from [here]("http://sourceforge.net/project/showfiles.php?group_id=195473").
Uninstall old one:
```
sudo apt-get remove swiftweasel
```
and install new one:
```
sudo dpkg -i siftweasel32-2.0.0.5_*.deb
```

---

### Post by Krydahl on 2007-07-22
As far as I can see, ia32-lib-firefox installed it for me. I think this had already been installed by the script. All I did was double click on the deb once I'd downloaded it and it installed itself.

Is this in some way less reliable than what you suggest?

---

### Post by Rui Pais on 2007-07-22
Double click on it make the package install over the old... 
I prefer not to do that to avoid old mixing stuff, but since this is just a minor security update, files should preserve more or less the same structure and they must be saved on disc the new over the old with no complications...

If you want to be sure that nothing is wrong just do an aptitude purge swiftweasel, then a sudo rm -rf /usr/local/swiftweasel32 and then double click on file again (or use dpkg -i). But that should be necessary, in fact.

---

