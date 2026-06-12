---
title: "The sudoers fixation"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by C.C.C.P. on 2009-04-22
Hello my problem is folowing
When I type sudo select-editor
sudo select-editor
>>> sudoers file: syntax error, line 14 <<<
sudo: parse error in /etc/sudoers near line 14

How can I fix it any possible answers?

---

### Post by michael37 on 2009-04-22
> **C.C.C.P. said:**
> Hello my problem is folowing
When I type sudo select-editor
sudo select-editor
>>> sudoers file: syntax error, line 14 <<<
sudo: parse error in /etc/sudoers near line 14

How can I fix it any possible answers?

Uggg. Ugly problem -- do you know root password on the computer to fix it?  Somehow, the syntax of the /etc/sudoers file got corrupted, thus you cannot use the "sudo" command.  At all.

Try this:
```

gksudo gedit /etc/sudoers 

```
If you get similar errors, you will need root password to fix it.

P.S.  The problem is not 64-bit specific.

---

### Post by sisco311 on 2009-04-22
> **C.C.C.P. said:**
> Hello my problem is folowing
When I type sudo select-editor
sudo select-editor
>>> sudoers file: syntax error, line 14 <<<
sudo: parse error in /etc/sudoers near line 14

How can I fix it any possible answers?

You have to boot in recovery mode to fix the file.
Here is a guide:[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

> **michael37 said:**
> Uggg. Ugly problem -- do you know root password on the computer to fix it?  Somehow, the syntax of the /etc/sudoers file got corrupted, thus you cannot use the "sudo" command.  At all.
...


Always edit the sudoers file with:
```
sudo visudo
```
If you wish to use a GUI editor:
```
VISUAL=gedit sudo -E visudo
```

Replace gedit with your editor of choice.

[noparse]
visudo edits the sudoers file in a safe fashion, analogous to vipw(8).
       visudo locks the sudoers file against multiple simultaneous edits,
       provides basic sanity checks, and checks for parse errors.  If the
       sudoers file is currently being edited you will receive a message to
       try again later.[/noparse]

---

### Post by lloyd_b on 2009-04-22
If you don't have a root password (which is how Ubuntu sets things by default), then boot into "Recovery Mode", then "cd /etc", and "nano sudoers" to make a fix.

Lloyd B.

---

