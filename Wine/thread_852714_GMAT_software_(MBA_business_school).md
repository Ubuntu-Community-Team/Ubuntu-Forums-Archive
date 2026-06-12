---
title: "GMAT software (MBA business school)"
date: 2008-07-07
forum: Wine
---

### Post by julien2233 on 2008-07-07
Hi to everybody,

I'm under Hardy (ubuntu version) and I tried to intall the GMAT free software to practice before trying to pass the GMAT exam.
[http://www.mba.com/mba/TaketheGMAT/ToolsToHelpYouPrepare/GMATPrepProducts/FreeGMATPrepTestPreparationSoftware.htm](http://www.mba.com/mba/TaketheGMAT/ToolsToHelpYouPrepare/GMATPrepProducts/FreeGMATPrepTestPreparationSoftware.htm)
The installation is ok under wine, without any error, however, when I try to launch the program, I got only a blue rectangle in the center of my screen.
I don't know what to do.

I checked on the files installed by the program and it looks like the files are .jar so there is probably a way to launch the program with the java from ubuntu.

The launcher in the wine menu is:
> env WINEPREFIX="/home/julien/.wine" wine "C:\Program Files\GMATPrep\jre\bin\javaw.exe" -ms64m -mx256m -jar "C:\Program Files\GMATPrep\lib\GMATPrep.jar" "C:\Program Files\GMATPrep"

I already tryed to lauch the Gmatprep.jar with the java command under ubuntu but without any success (there is no mistake with the caps):
```
java -jar /home/julien/.wine/drive_c/Program\ Files/GMATPrep/lib/gmatprep.jar
2008-07-07 21:54:39,648 ERROR java.lang.IllegalArgumentException: The content directory was not specified as a command line argument.
                              Method ------ main
                              Stack trace--
                              vue.exam.client.gmac.gmatprep.Application.main(Application.java:98)
2008-07-07 21:54:41,344 INFO Display Message: An application error has occurred. The application will now exit. <new line>  <new line> Error Description: <new line> The content directory was not specified as a command line argument. <new line> (java.lang.IllegalArgumentException)
2008-07-07 21:55:02,480 INFO Response To Message: OK
```

And my last try with adding the directory at the end:
```
java -jar /home/julien/.wine/drive_c/Program\ Files/GMATPrep/lib/gmatprep.jar /home/julien/.wine/drive_c/Program\ Files/GMATPrep
2008-07-07 21:59:40,137 ERROR java.lang.IllegalStateException: Required resource not found: html/01AboutGMATPrep/1.1HowtoUseGMATPrep/index.html
                              Method ------ a
                              Stack trace--
                              vue.exam.client.gmac.gmatprep.Application.a(Application.java:190)
                              vue.exam.client.gmac.gmatprep.ui.MainFrame.<init>(MainFrame.java:209)
                              vue.exam.client.gmac.gmatprep.Application.a(Application.java:316)
                              vue.exam.client.gmac.gmatprep.Application.main(Application.java:106)
2008-07-07 21:59:41,070 INFO Display Message: An application error has occurred. The application will now exit. <new line>  <new line> Error Description: <new line> Required resource not found: html/01AboutGMATPrep/1.1HowtoUseGMATPrep/index.html <new line> (java.lang.IllegalStateException) <new line>  <new line> For more information, please refer to the following log file: <new line> /home/julien/.wine/drive_c/Program Files/GMATPrep/Application.log
2008-07-07 22:00:05,062 INFO Response To Message: OK
```

I got the following message from a java dialog box:
> Error Description:
Required ressource not found: html/01AboutGMATPrep/1.1HowToUseGMATPrep/index.html

Is there anybody who encountered the same problem?
Has anybody a suggestion I can try?

Thanks in advance for your help.
Julien

---

### Post by julien2233 on 2008-07-13
I think I found the problem but I'm unable to fix it!

The problem comes from the difference between windows and linux. Linux is case sensitive and the developers programed probably under windows that is not case sensitive... and of course they have done mistake by naming the directories/files.

Does anybody have an idea how I can run this software with these mistakes inside?
I tried java under linux and java under wine... but nothing conclusive.

[I already sent en email to the company, but I'm not convinced they will correct the software :( ]

Julien

---

