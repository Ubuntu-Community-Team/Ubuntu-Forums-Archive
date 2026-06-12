---
title: "[SOLVED] Java and JRE in Gutsy"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Inxsible on 2007-10-24
I downloaded the jdk from Sun's website because i didnt see that the same version is available in synaptic.

Now that I know its there, I am going to install it from synaptic itself. jdk has only one package. however for the jre there is[LIST]
[*]sun-java6-jre - Sun Java Runtime Environment (JRE) 6 (architecture independent files) and
[*]sun-java6-bin - Sun Java Runtime Environment (JRE) 6 (architecture dependent files).[/LIST]Which one should I be installing given that I use 64 bit Gutsy ?

---

### Post by ndihmo on 2007-10-24
have a look here:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

If you are going to code in java and use javac you need to install 

sun-java6-jdk

If you want to know the differences use:

```
aptitude show sun-java6-jre
```

---

### Post by Inxsible on 2007-10-24
I did ```
 sudo aptitude install sun-java6-jdk
``` and it is installing sun-java6-bin and sun-java6-jre both. So I guess my question is moot.

I did what you suggested in aptitude show. But the info it gives is not what i was after. I already know what a jre does. I just wanted to find out if I should install architecture dependent or architecture independent files. But like I said, it doesnt matter any more. :)

---

### Post by pieisgood4589 on 2007-10-24
Hey everybody. HERE'S THE EASIEST WAY TO INSTALL JAVA AND JRE. Go to add and remove programs. Select add/remove programs to search "all available applications. Then, search: "jre" and wait for it to load up...
...
Next, choose the one that says "Sun Java 5.0 Plugin" and check it off and click "apply changes." Then, bootup firefox, and Java and jre are both installed! Hope this helped.

---

### Post by dewey on 2007-10-24
> **pieisgood4589 said:**
> Hey everybody. HERE'S THE EASIEST WAY TO INSTALL JAVA AND JRE. Go to add and remove programs. Select add/remove programs to search "all available applications. Then, search: "jre" and wait for it to load up...
...
Next, choose the one that says "Sun Java 5.0 Plugin" and check it off and click "apply changes." Then, bootup firefox, and Java and jre are both installed! Hope this helped.
That doesn't help the JDK situation, not to mention java is up to 6.0 now.

I too need to install the JDK, but am unsure exactly what to install.

Edit:
I just saw the link that was posted above, and am trying what was written there.

---

### Post by Inxsible on 2007-10-25
> **dewey said:**
> That doesn't help the JDK situation, not to mention java is up to 6.0 now.

I too need to install the JDK, but am unsure exactly what to install.

Edit:
I just saw the link that was posted above, and am trying what was written there.
Simply do a ```
sudo aptitude install sun-java6-jdk
``` this will also install the dependency which is the jre

---

### Post by dewey on 2007-10-25
Yes, I found out how simple it was after reading the link posted above.  Thank you for providing your help though.

Now I just need to find a good JCreator-like IDE for java.  I know about eclipse and such, but they're way more than I need.

---

