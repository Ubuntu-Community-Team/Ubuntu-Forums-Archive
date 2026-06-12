---
title: "Path to javac command"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by cloudRunner on 2006-03-25
Hi, I recently installed the Java SDK 1.5.0 on my computer.  I have to type in the whole path to the javac & java commands in order to compile/run my programs.  Is there any way I can just type 'javac' while in my home directory?  I tried adding this line to my .bash_profile file:

> 
export PATH="$PATH:/jdk50/bin/javac"

I receive the following error:
> bash:  javac:  command not found

Any help would be appreciated.

---

### Post by soce_32 on 2006-03-25
Your PATH variable should only contain directories, not the actual command.

I think what you are looking for is export PATH="$PATH:/jdk50/bin", and javac should be found then.

After you add anything to your .bash_profile, you can run 'source ~/.bash_profile' to get it to take effect in your current terminal without logging out or restarting anything.

---

### Post by cloudRunner on 2006-03-25
Can I add 'source ~/.bash_profile' to my .bashrc file, so I don't have to type it in each terminal session?

---

### Post by soce_32 on 2006-03-26
No, when you log in or open a new terminal, ~/.bash_profile is automatically sourced.  The only time you would need to do this is after you make changes to your .bash_profile.  Like so:

> vi .bash_profile
<add path to java>
> which javac
javac not found
> source .bash_profile
> which javac
> /usr/local/j2sdk/bin/javac

Sourcing after the edit has the same effect if you would just do an 'export PATH="$PATH:/path/to/javac".

---

