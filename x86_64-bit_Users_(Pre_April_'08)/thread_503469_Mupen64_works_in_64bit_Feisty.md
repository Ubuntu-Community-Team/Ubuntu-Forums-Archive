---
title: "Mupen64 works in 64bit Feisty"
date: 2007-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by stmiller on 2007-07-17
Some good news for the old school gamers out there:

Using the excellent script provided by thegreenblob [**here**]("http://ubuntuforums.org/showthread.php?t=464165") I have [Mupen64]("http://mupen64.emulation64.com/") working fine in 64bit Feisty. I do have all of the ia32 debs installed for all of the Ubuntu 32bit libraries.

The only problem is that the input plugin for my USB gamepad would not work. Only the keyboard works for controls. So I used a program [QJoyPad]("http://qjoypad.sourceforge.net/") to map the keyboard keys to my gamepad. 

And Ubuntu puts USB gamepads at /dev/input/js0, where most apps look for your joystick at /dev/js0. So just make a sym link

```

$ sudo ln -s /dev/input/js0 /dev/js0

```

---

### Post by LJarvis on 2007-07-19
exactly what packages should i install? I installed Mupen64 but it wont open.

---

### Post by stmiller on 2007-07-19
$ sudo synaptic

and search for ia32

install all of those.

---

