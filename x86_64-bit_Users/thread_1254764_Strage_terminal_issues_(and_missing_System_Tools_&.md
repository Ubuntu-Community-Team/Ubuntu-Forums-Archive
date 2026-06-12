---
title: "Strage terminal issues (and missing System Tools &gt; Root Menu)"
date: 2009-08-31
forum: x86 64-bit Users
---

### Post by pearjam on 2009-08-31
Hi!

So, been a while since I've posted here!

I'm having a hard time finding the answers to these - so I thought I'd see if anyone here knew...

1) In the terminal, when vi'ing a file, "i" for insert doesn't show "INSERT" at the bottom, and the arrow keys are disabled.

I can however insert text. Other messages do dispaly - eg: I can / and search, :, etc. I'm not sure why it's not showing "INSERT", is this some preference setting I changed without knowing?


2) I also found that if I go to System Tools > Root Terminal, the log in prompt displays but never brings up the root terminal after logging in. I have to su from my user, or I add *gnome-terminal -e "sudo -i"* to the properties for the root terminal launcher. What's up with the missing root terminal?


3) While in the terminal and using the up arrow to go to previous commands, some other command I've typed stays stuck at the prompt and more up arrows produce 1/2 commands on the front of the command that's stuck.

This actually happens on my home Ubuntu box, my work box, and when ssh'ed into my centos server. It doesn't happen all the time. I'll try to type out what it looks like - let's say I did "less xxxxxxx" then "vi zzzzzzz" - back at the command line, if I hit the up arrow I get:

vi zzzzzzz

..hit the up arrow again, and I get:

vi zzzss xxxxxxx


Any ideas on any of this stuff?

---

### Post by pearjam on 2009-08-31
. . . . . ):P . . . .
:KS:popcorn::KS

---

