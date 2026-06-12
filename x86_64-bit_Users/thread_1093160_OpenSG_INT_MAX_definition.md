---
title: "OpenSG INT_MAX definition"
date: 2009-03-11
forum: x86 64-bit Users
---

### Post by odesu on 2009-03-11
Hello

I tried to compile OpenSG 1.8 from source and got an 'INT_MAX is not defined' error. I think the problem results of the incompatibility of limits.h on my 64bit system.
I know that ubuntu packages for OpenSG are availiable. But i have made some modifications in the contrib lib, and so i need to compile it from source.

Does somebody know this problem with limits.h on 64bit systems?

kg odesu

---

### Post by michael37 on 2009-03-12
> **odesu said:**
> Hello

I tried to compile OpenSG 1.8 from source and got an 'INT_MAX is not defined' error. I think the problem results of the incompatibility of limits.h on my 64bit system.
I know that ubuntu packages for OpenSG are availiable. But i have made some modifications in the contrib lib, and so i need to compile it from source.

Does somebody know this problem with limits.h on 64bit systems?

kg odesu

Try their support forums?

---

### Post by Yellow Pasque on 2009-03-12
Suggestions:
- Make sure you have libc6-dev installed
- If you're still having issues, try editing the troublesome block of code to define INT_MAX manually, i.e.:
```
#define INT_MAX 2147483647
```

---

### Post by odesu on 2009-03-12
Hello

Thanks for the replies.
Adding limits.h in some headers fixed the problem.


greetings, odesu

---

### Post by davemorris on 2009-10-06
> **odesu said:**
> 
I know that ubuntu packages for OpenSG are availiable. But i have made some modifications in the contrib lib, and so i need to compile it from source.
kg odesu


You don't actually need to rebuild the whole of OpenSG to build your own nodes, libs etc.  I also recommend you don't since it's quicker not to.

I kinda explained how to do it here - [http://davemorris.wordpress.com/2008/07/04/enabling-ply-support-for-opensg-on-ubuntu-hardy/](http://davemorris.wordpress.com/2008/07/04/enabling-ply-support-for-opensg-on-ubuntu-hardy/)

Also if you look at alot of the makefiles for the code I have at [http://novellab.brighton.ac.uk/?q=projects/opensg](http://novellab.brighton.ac.uk/?q=projects/opensg) you'll see that you can easily build your own stuff outside of the OpenSG build system.

Any problems just drop me a line via IM or email.

---

