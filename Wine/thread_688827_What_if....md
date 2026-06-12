---
title: "What if..."
date: 2008-02-05
forum: Wine
---

### Post by -gabe-noob- on 2008-02-05
what if you downloaded directX onto wine, for graphics chips that cannot support opengl good, would this enable the use of dirext x in games?

---

### Post by yabbadabbadont on 2008-02-05
Nope.  :D

And even if it did, your performance would probably be worse anyway, as WINE converts all graphics access into OpenGL.  Better to just stick with OpenGL in the first place.

---

### Post by -gabe-noob- on 2008-02-05
Kay, how bout on CrossOver? :P

---

### Post by yabbadabbadont on 2008-02-05
No clue.  You probably need to ask that on the transgaming forums.  :)

---

### Post by Ferrat on 2008-02-05
> **yabbadabbadont said:**
> No clue.  You probably need to ask that on the transgaming forums.  :)

CrossOver is not Transgaming  
**OT a bit:**
[I]in short 

WINE is open source, free and very sexy making leaps and bounds with almost every release and it is OpenGL based and only transforms the DX3D calls from DX to OpenGL calls, DirectX itself wont work on wine due to the many differences between wine and windows API and files ect. 

Transgaming is handeling Cedega which is a hacked and patched early version of WINE that has been modified over and over again and they take cash for you to use it, a monthly subscription fee and from what I hear (only hearsay) their support isn't really what it should be, altho the have had some games running better on Cedega than on WINE but how that is now I don't know, but since Cedega is build on wine I think it does the same with converting DX calls to OpenGL 

CrossOver is also a rewrite of WINE and it costs money, but there is a big difference against Cedega, WINE devs hope that more people use CrossOver because CrossOver puts down money on the development of the source code and share back and forth with the developers of WINE and also they give a supported alternative to WINE since WINE is open source and some updates breaks functionallity of some apps and games from release to release CrossOver provides a safety net with support for the apps that does work on their product. CrossOver however is mainly devoted to apps more than games while wine being driven along alto by the Linux gaming commun is working harder than CrossOver to get games working. 
But in a nutshell they work the same way of converting DX 2 OpenGL [/I]

**Back to the topic at hand**
DirectX doesn't work on linux in anyway, the DirectX you see in WINE as stated is just a conversion of DirectX calls to OpenGL, the WINE guys are developing a API that can mimic DX functions without actually using any DX code and since WINE is more or less a rewrite of the winAPI but without using any windows code it's like a book being translated by someone that only knows the basic story and how it ends without reading the original book itself. 

Just translating a book is hard, for ex. the bible, it has alot of translations and they all have their difference because words can mean different things but still be the same word in the original language even if two of the translations doesn't match and that is when you can acctually read the book, imagine someone translating the bible from scratch without actually reading it first, just knowing that there was this dude named jesus and someone named Noah ect. 
Then think of installing DirectX being like pulling out page 234 of the original bible and putting it in to the "new" bible that has been translated without seeing the original text and putting that page between page 233 and 235 of that book, that page most likely wouldn't make much sense or fit at all. 

Hope that clear things up :)

---

