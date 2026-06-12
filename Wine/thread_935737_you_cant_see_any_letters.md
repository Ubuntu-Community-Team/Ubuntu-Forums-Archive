---
title: "you cant see any letters"
date: 2008-10-02
forum: Wine
---

### Post by bklynboi014 on 2008-10-02
i installed everything i need to run cs but yet when i go to login i cant see any letters i need help

---

### Post by ad_267 on 2008-10-02
By CS do you mean Counter Strike? Counter Strike Source maybe? And by "everything i need," do you mean you installed the Tahoma font?

---

### Post by aoanla on 2008-10-02
In addition, if you *do* mean Counter Strike Source, have you tried running it with the -dxlevel 81 switch enabled in Launch Options in Steam?

---

### Post by kylet450 on 2008-10-02
It depends what directx your card can handle:

for Directx 7 card: -dxlevel 71
Directx 8 card: -dxlevel 81
Directx 9 card: -dxlevel 91
( any lower than direct x 7 and youll have problems, if you dont know your directx card capabilities or your not sure, use -dxlevel 71 ) 

Also add : -width {Your monitors width} -height {your monitors height} ( minus the brackets )

Mine is: -dxlevel 91 -Width 1280 -height 1024

---

### Post by aoanla on 2008-10-02
No - the instruction to use -dxlevel 81 is in fact to avoid Wine's DX9 implementation, which *can* cause this issue of letters being invisible.

I'm fairly sure that pretty much everyone has a DX8 compatible card nowadays...

---

### Post by kylet450 on 2008-10-02
im using -dxlevel 91 with no problems.

---

### Post by Gcentrex on 2008-10-02
> **kylet450 said:**
> im using -dxlevel 91 with no problems.

That is fine if your running CSS but not a good idea when running HL2:EP2/Portal/TF2/DODS (Source2007) since these use more features of DX9X unlike CSS (Source engine 2) and other HL2 (Source engine) based games.

---

### Post by kylet450 on 2008-10-02
im running TF2 with -dxlevel 91 too.

But i do have a directx 10 compatible card.

---

### Post by aoanla on 2008-10-02
> **kylet450 said:**
> im running TF2 with -dxlevel 91 too.

But i do have a directx 10 compatible card.

That, of course, makes no difference, since the issue is in Wine's implementation of DX9 and not in your card's hardware or drivers. ;)

---

