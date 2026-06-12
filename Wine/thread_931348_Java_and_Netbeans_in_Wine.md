---
title: "Java and Netbeans in Wine"
date: 2008-09-27
forum: Wine
---

### Post by PaulM1985 on 2008-09-27
Hi

I have to install windows version of Netbean 4.1 on my computer.  I managed to do this and install the java software to go with it.  Usually on a windows computer, you need to give class paths so that any software will be able to see java.exe, javac.exe etc from any folder on the computer.  Is there anyway to do this with Wine.

Any help would be much appreciated.

Paul

PS.  I know that Netbeans 6.0.1 is available, to I have been told for a Uni course that I am studying that I have to have version 4.1 as it is not backwards compatible.  I want to install the software that they have provided so that I am using the same software that the rest of the people on the course are using.

---

### Post by ooobuntooo on 2008-09-27
There is a Linux version of Netbeans!

---

### Post by PaulM1985 on 2008-09-27
I know.  I have 6.0.1.  I need 4.1

---

### Post by asdfoo on 2008-09-27
> **PaulM1985 said:**
> Hi

I have to install windows version of Netbean 4.1 on my computer.  I managed to do this and install the java software to go with it.  Usually on a windows computer, you need to give class paths so that any software will be able to see java.exe, javac.exe etc from any folder on the computer.  Is there anyway to do this with Wine.

Any help would be much appreciated.

Paul

PS.  I know that Netbeans 6.0.1 is available, to I have been told for a Uni course that I am studying that I have to have version 4.1 as it is not backwards compatible.  I want to install the software that they have provided so that I am using the same software that the rest of the people on the course are using.

I think you are confused... 

There are two different things, the PATH environment variable which is searched when the system searches for an executable by name "javac.exe" or otherwise.

If you want to modify/add these then you do that through the registry [http://www.winehq.org/site/docs/wineusr-guide/environment-variables](http://www.winehq.org/site/docs/wineusr-guide/environment-variables)

Then there is the classpath, which is specific to the compiler and runtime which is a list of locations to search for classes, either directories or inside jar files.

This is up to your build system, IDE etc, as a commandline switch to java/javac and iirc it may support an environment variable as well.

---

### Post by PaulM1985 on 2008-09-27
Hi asdfoo

Thanks for your response.  The error message I am getting when I try to run Netbeans is "Cannot find java.exe".  This lead me to think about setting paths... I have tried running "wine regedit" as mentioned in the link you provided, but I do not seem to have "HKEY_CURRENT_USER/Environment".  Have you any other advice or any other ideas that may help.

Thanks

Paul

---

### Post by asdfoo on 2008-09-27
> **PaulM1985 said:**
> Hi asdfoo

Thanks for your response.  The error message I am getting when I try to run Netbeans is "Cannot find java.exe".  This lead me to think about setting paths... I have tried running "wine regedit" as mentioned in the link you provided, but I do not seem to have "HKEY_CURRENT_USER/Environment".  Have you any other advice or any other ideas that may help.

Thanks

Paul

If it doesn't exist, create it.

---

### Post by PaulM1985 on 2008-09-27
Yup, I tried that, I guessed that was what you were going to say. I created "...\Environment" and "Path = C:\.... (java path)" and still I am getting a "can not find java.exe" error.  Would a screen shot of my regedit and the error message help?


Paul

---

### Post by asdfoo on 2008-09-27
> **PaulM1985 said:**
> Yup, I tried that, I guessed that was what you were going to say. I created "...\Environment" and "Path = C:\.... (java path)" and still I am getting a "can not find java.exe" error.  Would a screen shot of my regedit and the error message help?


Paul

If you want to test your theory, you can run 'wine cmd' after setting the environment variable which will give you a command prompt, at which you can type java to see if it can find java.exe in your PATH.

---

### Post by PaulM1985 on 2008-09-28
Hi

Thanks for the advice.  I tried that and ran java -version, and it can find java.exe in the path, so Path must be ok.  But still, I am getting the error with Netbeans saying that it can not find java.exe.  I have also tried copying java.exe into the netbeans folder and still got the same problem.  I am not sure why this is happening.  I guess there must be a specific folder that netbeans looks for rather than attempting to find java.exe in Path.  Do you think that this could be the case?

Paul

---

### Post by asdfoo on 2008-09-28
> **PaulM1985 said:**
> Hi

Thanks for the advice.  I tried that and ran java -version, and it can find java.exe in the path, so Path must be ok.  But still, I am getting the error with Netbeans saying that it can not find java.exe.  I have also tried copying java.exe into the netbeans folder and still got the same problem.  I am not sure why this is happening.  I guess there must be a specific folder that netbeans looks for rather than attempting to find java.exe in Path.  Do you think that this could be the case?

Paul

Hard to say without debugging the application.

If you want a log of all the file related operations that are performed when you run netbeans, run wine as such, from the netbeans install directory:

WINEDEBUG=+file wine netbeans.exe 2> filelog.txt

Of course, replace "netbeans.exe" with whatever the main program executable is or the command used to start netbeans which you can find from the launcher.

Once it starts and produces the same error message, you can exit then review the filelog.txt file to see where it's looking for java.exe

---

