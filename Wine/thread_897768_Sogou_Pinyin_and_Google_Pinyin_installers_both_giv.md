---
title: "Sogou Pinyin and Google Pinyin installers both give NSIS error no matter what i do."
date: 2008-08-22
forum: Wine
---

### Post by koffeinöverdos on 2008-08-22
I spoiled myself with sogou pinyin on windows and I just don't know if i can put up with SCIM much longer, it's just not an intelligent IME no matter which way you try to cut it, it's barely better than Microsoft's IME.

When I launch the installer for either IME in the terminal, I get no errors printed, just a windows pop up that says "NSIS error: Error launching installer."

I have tried using every windows version (using wine 1.1.2)

I searched as hard as i could on the internet and I found nothing, which gives me the bad feeling that people have already tried this and it just can't be done.

I believe gecko ie engine is running just fine since i can browse the internet with wine iexplore.

(i don't think the audio and graphics stuff below is relevant but I will add it anyway since i'm an idiot with wine and linux in general)

I have no library overrides. Only ALSA driver is checked in Audio. In Graphics, "Allow window manager to decorate windows" is checked, under Direct3D, "Allow Pixel Shader" is checked, vertex shader support: Hardware


My home folders are in chinese. for example my desktop is ~/&#26700;&#38754; but it's showing up in Desktop Integration as ~/&#21475;&#21475;. I really don't see why this would be killing it as not only does it not have to install anything to this directory, but it's also not even reaching the installation process, but does it sound possible that this could be causing problems with wine globally?

i don't need both of these to work, just either one. preferrably sogou, but either one.

---

### Post by koffeinöverdos on 2008-08-24
All this is really a matter of probably is does anyone know how to fix this particular error if it can be fixed at all?

**NSIS error: Error launching installer.**

again no terminal errors or anything. Thank you in advance.:KS

---

### Post by baisong on 2010-03-04
ever end up solving this issue? 

I'm on Karmic, with folders named Chinese, but I can still install some .exe's fine. I had trouble trying to install a Wubi Chinese Typing Tutor-- verbatim error message. Don't know where I can find more error messages or tweak things... 

do I need to get a new version of NSIS? I admit I installed the pre-packaged Wine found in the Ubuntu Software Center menu.

---

