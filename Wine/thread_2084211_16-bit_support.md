---
title: "16-bit support?"
date: 2012-11-14
forum: Wine
---

### Post by conradin on 2012-11-14
Hi all, 
I have an application I am trying to run in Wine. The last time I recall running it was in 2008. Reading the wineHQ page I saw something about recolationg 16-bit modules. 

I can run parts of the program, but the 16-bit calls to the serial port fail. Can anyone assist?

here are the errors I get when the program trys to access the com port:
```

fixme:comm:CloseComm16 no cid=1 found!
fixme:comm:CloseComm16 no cid=2 found!
fixme:comm:CloseComm16 no cid=3 found!
fixme:comm:CloseComm16 no cid=4 found!

```

how can i get this application to call the com port?
I added a com1 device, 
```

lrwxrwxrwx 1 s s   10 2012-11-14 18:11 com1 -> /dev/ttyS0


```

what else do i need to do?

---

### Post by conradin on 2012-11-30
Bumpity. 
maybe I can run this in Java. 
To be clear, I need 16bit serial port support under wine. 
Anyone have ideas?

---

