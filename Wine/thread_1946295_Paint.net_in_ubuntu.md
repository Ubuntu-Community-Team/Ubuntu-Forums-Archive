---
title: "Paint.net in ubuntu?"
date: 2012-03-24
forum: Wine
---

### Post by gandalf3 on 2012-03-24
I'm new to Linux and installed Ubuntu 11.10
Gimp is fine, but I'm wondering is it possible to install paint.net in Ubuntu?
I read this thread, [http://ubuntuforums.org/showthread.php?t=1520917&highlight=Paint.net+ubuntu%3F](http://ubuntuforums.org/showthread.php?t=1520917&highlight=Paint.net+ubuntu%3F)
but I couldn't make much sense out of it.. also it didn't say what type of Linux..
[]("http://ubuntuforums.org/showthread.php?t=1520917&highlight=Paint.net+ubuntu%3F")

---

### Post by Karlchen on 2012-03-24
Hello, gandalf3.

Hopefully you are aware that [Ubuntu is not another Microsoft Windows](http://linux.oneandoneis2.org/LNW.htm). It is a different operating system. Paint.net is a Windows application. Out of the box, Windows will not run any Ubuntu software, and vice versa Ubuntu will not run any Windows software.

In order to be able to install and run Windows software on Ubuntu, you will have to get and install Wine first. Once you have done so, you may or may not be able to use Paint.net on Ubuntu.

Please, visit the following webpage for more information on Wine: [**WineHQ**]("http://www.winehq.org/").
Check whether Paint.Net can be run on Linux (Ubuntu) with the help of Wine here: [**WineHQ - AppDB**]("http://appdb.winehq.org/").

**[The entries found there for Paint.NET]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6551")** are not too encouraging. Paint.NET is a .NET Framework application. .NET is pretty Windows specific. So the challenge is a double one: install .NET framework on Wine, install Paint.NET on Wine. Hope that both run correctly and co-operate.

In case you cannot get used to Wine, it may be wiser to look for genuine Linux based alternatives instead of trying to run Paint.NET on Ubuntu through Wine.

Kind regards,
Karl

---

### Post by gandalf3 on 2012-04-01
hmm.. well, i can use gimp, but i think i'm going to attempt to get paint.net going, but i'm not really expecting it to work..
i've downloaded paint.net 3.5.10 (couldn't find any earlier versions..) but I'm not sure how to install it with out it trying to install .net framework 3.5 and instead use the .net framework that I can install using wine (though i'm not sure how to install that either.. what's a "clean wine prefix"? 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10166](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10166))

if anyone can help me here, i think i desperately need it..:confused:

---

### Post by Mait on 2012-04-01
You could try Pinta - [http://pinta-project.com/](http://pinta-project.com/).

Available at ubuntu software center.

---

### Post by jerrrys on 2012-04-01
I too switched over to gimp.  But last I heard paintdotnet forum had support for linux/wine.

---

### Post by gandalf3 on 2012-04-01
> I too switched over to gimp.  But last I heard paintdotnet forum had support for linux/wine.really? i couldn't find anything.. but maybe it was a dated thread?

i looked a bit at the home page for the porting project [http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)
does anyone know if anybody is still working on this?
anyway i decided to try pinta..

---

### Post by oldos2er on 2012-04-01
Thread moved to Wine.

---

### Post by directhex on 2012-04-01
Pinta is a Linux-targeted app based on Paint.NET's source (replacing the ugly WinForms toolkit with GTK+). It should do what you need.

---

### Post by gandalf3 on 2012-04-01
i just tried pinta, so far does everything i ever hoped to get out of paint.net through wine and more, but it lagged horribly when using the gradient tool.. any idea why this happened? my system isn't particularly high end, but it handled paint.net gradient in windows fine.. and the only program i had running at the time was pinta..:icon_frown:

---

### Post by directhex on 2012-04-02
> **gandalf3 said:**
> i just tried pinta, so far does everything i ever hoped to get out of paint.net through wine and more, but it lagged horribly when using the gradient tool.. any idea why this happened? my system isn't particularly high end, but it handled paint.net gradient in windows fine.. and the only program i had running at the time was pinta..:icon_frown:

Possibly a limitation with the library being used by Pinta instead of Windows libraries.

---

### Post by gandalf3 on 2012-04-02
hm.. oh well.. i guess thats that
thanks, directhex for telling me about pinta :-)

---

