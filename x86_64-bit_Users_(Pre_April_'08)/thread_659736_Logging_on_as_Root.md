---
title: "Logging on as Root"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by stefcep on 2008-01-06
When I installed &.10 64 Bit I created 2 users by using the migration assistant.  One of those has administrator privelages but is not called "root".  Some directories i need to write to belong to root and I need access to them.  How do log in as root?

---

### Post by MariusSilverwolf on 2008-01-06
Ubuntu, by default, does not allow the ability to log in as the root user for security measures.

However, anytime you need to run a command or access a folder as the root user, you can do so by either the sudo command in the terminal, or the gksudo command in the Alt+F2 graphical run line, and follow gk/sudo with the command of the program you need to run.

For example, to access nautilus for easy copy/paste purposes between multiple folders, from the desktop hit Alt+F2, type gksudo nautilus, and hit enter.  When prompted for your password, enter it, and the program will launch.  From there, do as you wish.

---

### Post by lisati on 2008-01-06
As I understand it, the installation process usually hides the "root" user, in order to help system security.

There are ways of doing things that would normally be done by user "root" from an account with administrator privileges.

What sort of things did you have in mind?

---

### Post by stefcep on 2008-01-06
I installed an emulator ( uae )via synaptic that got put in /bin.  This directory belongs to root.  I have to copy a ROM in that directory, from my winxp partition.

---

### Post by MariusSilverwolf on 2008-01-06
> **stefcep said:**
> I installed an emulator ( uae )via synaptic that got put in /bin.  This directory belongs to root.  I have to copy a ROM in that directory, from my winxp partition.

From the desktop, hit Alt+F2.  Type " gksudo nautilus "  Enter your password when prompted.

Within Nautilus, navigate to to wherever your XP partition is, copy the ROM file, and paste it into your /bin folder.

By launching Nautilus with the gksudo command prefacing it, you are using Nautilus AS root.  Simple, neh?

---

### Post by stefcep on 2008-01-07
> **MariusSilverwolf said:**
> From the desktop, hit Alt+F2.  Type " gksudo nautilus "  Enter your password when prompted.

Within Nautilus, navigate to to wherever your XP partition is, copy the ROM file, and paste it into your /bin folder.

By launching Nautilus with the gksudo command prefacing it, you are using Nautilus AS root.  Simple, neh?

Yes it is simple when you know how.  I have PCLInuxOS as well and this lists all the users at boot time including root, so if I want to do some admin stuff, then thats what i log in as, and thats what I thought all distros did.  Evidently not!

---

