---
title: "Technology behind Wine"
date: 2015-07-28
forum: Wine
---

### Post by denaxin on 2015-07-28
Hello! I've used linux for almost five years now, and wine has been always with me since the begining.
Still, I can't fully understand how this works. I know, It doesn't emulate anything, but Translates the code to Linux compitable code. But here are the questions:


[LIST]
[*] Is there a **Wine SDK**? 
[*] How does Wine **translate** the code to Win32 code? 
[*] Why haven't **.NET** (as it is **open source** now) been implemented in **Mono** yet? 
[*] Where does the *"Wine is not an emulator" *name come from? Is it simply a **joke**? 
[*] Is it **legal**? I mean, it uses _some_ dependencies **made by Microsoft**, like *mscorefonts*... 
[*] What **language** is Wine written in? 
[/LIST]
 
Hope somebody answers this without commenting on this like "*lel, u should gogle it!!!1*". I tried, but many of those thing were hard to find. And I came up with some of the questions while writing this post, so it I tough somebody would give me a direct answer instead! I will thank with reputation (If you use it here on Ubutnuforums.org, like Tenforums.com do!)!

Cheers!

---

### Post by howefield on 2015-07-28
While I wouldn't say just google it, the answers are probably on the Wine website, Wiki and forums... [https://www.winehq.org/about/](https://www.winehq.org/about/)

---

### Post by denaxin on 2015-07-28
> **howefield said:**
> While I wouldn't say just google it, the answers are probably on the Wine website, Wiki and forums... [https://www.winehq.org/about/](https://www.winehq.org/about/)

Well... It only partially answered the second question :/
Thanks anyway, sir! ;)

---

### Post by Simon_Tomoko on 2015-07-28
Q: Is there a **Wine SDK**?

A: I am a doctor, not a programmer but this is "open source" so that would be akin to development tools for something open to public use?

Q: How does Wine **translate** the code to Win32 code?

A: There are Linux-AMD-64 versions have Win64 available with ability to fallback to 32. 

Q: Why haven't **.NET** (as it is **open source** now) been implemented in **Mono** yet?
A: I don't know, but you can install dotnet using winetricks.


Q: Where does the *"Wine is not an emulator" *name come from? Is it simply a **joke**?

A: Because it is not an emulation of Windows but rather an [overlay]("https://en.wikipedia.org/wiki/Overlay_(programming)"). It could have been called WIAO (WIAO Is An Overlay) but that doesn't spell anything. WINE started as an WINdows Emulator. Its meaning changed to, "Wine Is Not an Emulator" in order to differentiate the software from CPU emulators.

Q: Is it **legal**? I mean, it uses _some_ dependencies **made by Micro$oft**, like *mscorefonts*...

A: WINE in of itself is legal.  Opinions vary as to what you use it in concert with; obviously if you download pirated games, you are not using it as intended. Some people think WINE is holding back Linux development in some areas. Others don't want to use anything MS related or free to use dependencies such as Direct X. Since I purchased Windows XP a long while back, I still hold legal license to the OS. I should be able to use the core fonts but I am not a lawyer. I believe I would be breaking the law, if I used something from Vista since I never purchased that OS.

Q: What **language** is Wine written in?

 A: C

All this information and more is available on the [wikipedia here]("https://en.wikipedia.org/wiki/Wine_(software)").

---

### Post by coldraven on 2015-07-28
> Is it **legal**? I mean, it uses _some_ dependencies **made by Micro$oft**, like *mscorefonts*...
To install those fonts you have to agree to Microsofts terms and conditions. Did you read them?

---

### Post by denaxin on 2015-07-29
> **Simon_Tomoko said:**
> Q: Is there a **Wine SDK**?

A: I am a doctor, not a programmer but this is "open source" so that would be akin to development tools for something open to public use?

Q: How does Wine **translate** the code to Win32 code?

A: There are Linux-AMD-64 versions have Win64 available with ability to fallback to 32. 

Q: Why haven't **.NET** (as it is **open source** now) been implemented in **Mono** yet?
A: I don't know, but you can install dotnet using winetricks.


Q: Where does the *"Wine is not an emulator" *name come from? Is it simply a **joke**?

A: Because it is not an emulation of Windows but rather an [overlay]("https://en.wikipedia.org/wiki/Overlay_(programming)"). It could have been called WIAO (WIAO Is An Overlay) but that doesn't spell anything. WINE started as an WINdows Emulator. Its meaning changed to, "Wine Is Not an Emulator" in order to differentiate the software from CPU emulators.

Q: Is it **legal**? I mean, it uses _some_ dependencies **made by Micro$oft**, like *mscorefonts*...

A: WINE in of itself is legal.  Opinions vary as to what you use it in concert with; obviously if you download pirated games, you are not using it as intended. Some people think WINE is holding back Linux development in some areas. Others don't want to use anything MS related or free to use dependencies such as Direct X. Since I purchased Windows XP a long while back, I still hold legal license to the OS. I should be able to use the core fonts but I am not a lawyer. I believe I would be breaking the law, if I used something from Vista since I never purchased that OS.

Q: What **language** is Wine written in?

 A: C

All this information and more is available on the [wikipedia here]("https://en.wikipedia.org/wiki/Wine_(software)").


WOW! Thanks for the information! You helped me a lot! Thank you so much! :D

> **coldraven said:**
> To install those fonts you have to agree to Microsofts terms and conditions. Did you read them?

Of course I did. I read every terms and conditions Companies throw at me. Like every normal human begin! :lolflag:

---

