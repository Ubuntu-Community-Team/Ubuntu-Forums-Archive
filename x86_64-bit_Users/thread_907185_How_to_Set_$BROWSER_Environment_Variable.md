---
title: "How to Set $BROWSER Environment Variable"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by raywood on 2008-09-01
When I start Google Earth 4.3 in Hardy 8.04 (gnome), I get this error message:

> Could not launch any web browser.  Please make sure you have set the $BROWSER environment variable to the filename of the web browser we should launch.

Anybody know how to do that?

---

### Post by Nepherte on 2008-09-01
This is how you export a variable (firefox is used in the example):
```
export BROWSER=/usr/bin/firefox
```

This variable only keeps its value until you close the terminal you typed it in. To make it permanent, add it to end of your .bashrc file.

---

### Post by raywood on 2008-09-01
Thanks.  I see two bash.bashrc and two dot.bashrc files in my File System.  I'm guessing that /etc/bash.bashrc is the one I should edit.

---

### Post by Nepherte on 2008-09-02
There are indeed 2 options:
[LIST]
[*]/home/username/.bashrc
[*]/etc/bash.bashrc (or /etc/profile)
[/LIST]
The difference is that first option only affects one user. The latter makes system wide changes. I would do it in the user's one for the simple reason that when you mess something up, it only affects one user instead of the whole system.

---

### Post by Weekendpartier on 2009-07-12
HEY, this doesn't work.  What's the proper syntax??

here's my bash.bashrc!  What gives?


# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi

export BROWSER=/home/steve/Firefox/firefox

---

