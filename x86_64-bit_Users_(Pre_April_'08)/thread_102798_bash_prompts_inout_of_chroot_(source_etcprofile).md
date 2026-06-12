---
title: "bash prompts in/out of chroot (source /etc/profile?)"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by hollywoodb on 2005-12-12
I've set up different bash prompts to make it immediately noticeable whether I'm in or out of my chroot environment, using /etc/bash.bashrc

the reason I don't use ~/.bashrc is because /home/ is the same in/out of chroot while /etc/ is not.

so, 
```
source /etc/profile
```
will initiate my custom prompts, however i need to do it manually.
I'd like for the prompts to be in effect whether I'm at console, xterm, etc etc, lets just say 'globally at all times'; changing of course when I enter/exit chroot.

---

### Post by macgyver2 on 2005-12-12
[QUOTE=hollywoodb]I've set up different bash prompts to make it immediately noticeable whether I'm in or out of my chroot environment, using /etc/bash.bashrc

the reason I don't use ~/.bashrc is because /home/ is the same in/out of chroot while /etc/ is not.

so, 
```
source /etc/profile
```
will initiate my custom prompts, however i need to do it manually.
I'd like for the prompts to be in effect whether I'm at console, xterm, etc etc, lets just say 'globally at all times'; changing of course when I enter/exit chroot.[/QUOTE]
Here's a trick I picked up from somewhere else...I thought it was from a howto on the wiki, but I couldn't find it just now.  Maybe it was in a debian tutorial.  When I have more time I'll look for it...I want to credit the proper place.

Anyway...

Here's an excerpt from my ~/.bashrc:
```
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

export PS1='\[\033[01;31m\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\h \[\033[01;34m\]\w \$ \[\033[00m\]'
```
In each of my chroots I put the name I want in that chroot's /etc/debian_chroot...when I enter the chroot my common ~/.bashrc is automatically sourced and the name of the chroot shows up in parentheses in red at the beginning of my prompt.  (Of course you can choose any color or any place in the prompt you want.)  When I exit the chroot I get my "normal" prompt back (I don't have a debian_chroot file in my true /etc directory).

---

