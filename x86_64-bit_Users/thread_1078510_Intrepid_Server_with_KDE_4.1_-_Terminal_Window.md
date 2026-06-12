---
title: "Intrepid Server with KDE 4.1 - Terminal Window"
date: 2009-02-23
forum: x86 64-bit Users
---

### Post by snorkytheweasel on 2009-02-23
I installed Intrepid Server - x86-64. My first action was to install KDE (4.1). 

I have used desktop since 6.x, server since 7.x, so I think I have a good idea of what should be available. I am surprised at all of the functionality that isn't immediately available. I can't tell if KDE is the problem, or if Intrepid is the source of this bizarre behavior. I'm asking these dumb questions because
[LIST]
[*]the help system sucks (look up 'terminal' or 'shell' and then find instructions on how to launch a terminal window ... or shell )
[*]the set of applications available is bizarre - very little of what is available is useful (widgets for network admin??), and very little of what is available is useful for server/network admin ... there isn't a file system browser or web browser)
[/LIST]

Anti-flame war disclosure:
[LIST]
[*]I'm not interested in a quarrel over whether or not I should be using a GUI with server. However, I am open to Gnome vs KDE for this environment.
[*]If the answers were obvious (to me) I wouldn't be asking.
[/LIST]

Dumb Question #1: How do I open a Terminal Window?

I should be able to open a terminal from the desktop. From there I can install the many other missing programs (or install a front-end for apt) and manage the system.

---

### Post by cariboo on 2009-02-23
There are very few gui server apps for Ubuntu, most of the configuration is done editing text files. You may be better of installing [webmin]("http://webmin.com/") and using that to administer your server.

Jim

---

### Post by snorkytheweasel on 2009-02-23
> **cariboo907 said:**
> There are very few gui server apps for Ubuntu, most of the configuration is done editing text files. You may be better of installing [webmin]("http://webmin.com/") and using that to administer your server.

Jim

That's  part of the plan... but how do I get a terminal window so that I can install webmin (and some other vital tools)?

The problem is that the machine boots to a KDE logon screen. My installation of KDE has no way (that I can find) to be able to execute commands like apt-*.

At my office I'm running Gutsy server 7.10 (x86-32) with KDE 3.5.8. It came with a mountain of apps useful for a sysadmin - including a terminal, synaptic, "system settings 0.2" (yes, that is the filename), konqueror. With a terminal and konqueror. I could set up the server to do everything I need (including editing config files). 

KDE 4.1 gives me widgets and some other goofy apps better suited for a workstation - but no terminal!

On my Linux-based netbook I get a terminal with CRTL-ALT-T. How do I launch a terminal window when using a real workhorse desktop? Surely there is a one-sentence answer that will get meunstuck.

---

### Post by ssri on 2009-02-23
In KDE 4.2.0 (maybe 4.1.x), I can activate the konsole shortcut key (CTRL+ALT+T) by enabling it in input actions (alt+f2->"input actions").  It is in examples, so drag it to preset actions and make sure it is enabled.

---

### Post by SuperSonic4 on 2009-02-23
what about installing konsole (and maybe konqueror) in the normal way?

```
sudo apt-get install konsole konqueror
```

---

### Post by snorkytheweasel on 2009-02-23
> **SuperSonic4 said:**
> what about installing konsole (and maybe konqueror) in the normal way?

```
sudo apt-get install konsole konqueror
```

I must be getting into this conversation late.

Doesn't your method require a terminal window? 
[INDENT]
1st time I asked: How do I open a Terminal Window?[/INDENT]
[INDENT]
2nd Time I asked: I should be able to open a terminal from the desktop. From there I can install the many other missing programs (or install a front-end for apt) and manage the system ... but how do I get a terminal window so that I can install webmin (and some other vital tools)?[/INDENT]

[INDENT] 3rd time I asked: How do I launch a terminal window when using a real workhorse desktop? Surely there is a one-sentence answer that will get me unstuck.[/INDENT]

---

### Post by dtsmith1984 on 2009-02-24
CTRL-ALT-F1 or F2 or F3 etc will take you to the console.

Then to get back to X try ALT-F7 or F8

---

### Post by snorkytheweasel on 2009-02-24
> **dtsmith1984 said:**
> CTRL-ALT-F1 or F2 or F3 etc will take you to the console.

Then to get back to X try ALT-F7 or F8

Thank you. That's what I needed to know. Now I can use apt-get & eventually, synaptic, to flesh out the installation.

):P ):P

---

