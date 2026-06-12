---
title: "office 2007 dies after splash screen Possible Crossover Games issue ?"
date: 2008-05-25
forum: Wine
---

### Post by donavan on 2008-05-25
I managed to get Excel 2007 installed but it dies after the splash screen the program comes up but then I get one of those windows to send info to microsoft.  I have followed several tutorials and finally found something that got me this far.  The one question I have is there appears to be something with crossover games which might be causing my problems but I cant besure because I cant get it to compile.  Does anyone know what is needed from this or if I even need it all?

---

### Post by Kinst on 2008-05-25
Yeah, it'll work best with the rpcrt4.dll from crossover.

You can also try compiling wine 9.58 from source overtop of your existing .wine.

---

### Post by donavan on 2008-05-26
Can I use the demo version or am I stuck having to buy the full version?  I know there is a 7 day trial limit, but I wasn't sure it they had written anything into that file.

---

### Post by Kinst on 2008-05-26
Here's a guide for getting their rpcrt4 because crossover is open source.

[http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html](http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html)

---

### Post by donavan on 2008-05-27
Knist:

Thanks for the link I tried following the instructions befoer but everytime I try to run the ./configure it gives me the following 

configure: error: C compiler cannot create executables.
See 'config.log' for more details.

I think the error happens here:

configure:2663:$? = 1
configure:2701: result:
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.55"
| #define PACKAGE_STRING " Wine 0.9.55"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
|/* end confdefs.h. */
|
|int
|main()
|{
|
|   ;
|   return 0;
|}
configure:2708: error: C compiler cannot create executables
See 'config.log' for more details.


This seems to be looking for wine 0.9.55 unfortunately I am using 1.0rc2.  Any ideas?

I think the rpcrt4.dll is the problem I have redone everything else a bunch of times using different guides in different ways and this seems like the only holdup.  I have been able to get word to load up but as soon as I try top open something it crashed, Excel on the other hand just dies after the splash screen.  

Thanks to everyone for the help so far and any further help I get here.

---

### Post by jrusso2 on 2008-05-27
> **donavan said:**
> Can I use the demo version or am I stuck having to buy the full version?  I know there is a 7 day trial limit, but I wasn't sure it they had written anything into that file.

I would say is worth a try to just copy the dll out of the demo version and see if that works.

---

