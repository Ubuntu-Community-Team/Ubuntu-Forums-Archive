---
title: "Conky for 64-bit?"
date: 2006-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sonic Reducer on 2006-11-26
i got a 64-bit XP-3200+ and i tried following the excellent instructions found [here]("http://ubuntuforums.org/showthread.php?t=205865") but they seem to be for a 32-bit CPU

i got it kinda working now, except i have the default background and conky comes up in black text, so it's all but unusable. it also comes up on the taskbar, like a running app, sometimes it does run like it should (nothing o the taskbar) but it only does that for a few seconds before disappearing, and it reappears for a few seconds right as i'm shutting down. this is a very cool and informative app with horrible set up.

please help me, if there is enough help i would personally set up a thread with links to every trick submitted (how to add HDD temp, song currently playing, etc.) and oversee it.

thanks, i'm completely new to this

---

### Post by taurus on 2006-11-26
Here's the info regarding conky and Gnome...

[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)

Or some nice ~/.conkyrc...

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by Sonic Reducer on 2006-11-26
```
check my latest post for my current conkyrc contents
```
this is the conkyrc file i am using, but whenever it is on the desktop no icons are there, but if i click+drag over a place with an icon it becomes visible once it is slectedd by the field. and if i click+hold over conky it disappears until it refreshes, heres a screenshot:

[[IMG]http://img90.imageshack.us/img90/5926/conkyerrorscreenshot1jb2.th.png[/IMG]](http://img90.imageshack.us/my.php?image=conkyerrorscreenshot1jb2.png)
(the firefox shortcut wasn't there before i click+dragged)


what should i do to fix it?

---

### Post by taurus on 2006-11-26
Try changing the gap_x & gap_y in your ~/.conkyrc to

```

gap_x 5
gap_y 5

```
Then, kill it and start it up again...

---

### Post by Sonic Reducer on 2006-11-26
well **taurus** it moved, but to here:
[[IMG]http://img154.imageshack.us/img154/8879/conkyerrorscreenshot2ih4.th.png[/IMG]](http://img154.imageshack.us/my.php?image=conkyerrorscreenshot2ih4.png)

and to open it i open terminal and type "conky" but whenever i close that terminal window it closes conky as well

---

### Post by taurus on 2006-11-26
Well, change the "gap_x" to something like 1000 or until you get it to where you want it.  And yes, when you close the terminal that you run conky, it will terminate also.  Therefore, if you want conky to start when you log in, then add it to System -> Preferences -> Sessions -> Startup programs.

Log out and back in again.

---

### Post by Sonic Reducer on 2006-11-26
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- ryan
#

# set to yes if you want Conky to be forked in the background
background no

# Create own window instead of using desktop (required in nautilus)
own_window no
# own_window_type override
own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Boolean value to set on bottom of desktop
on_bottom yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 15

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${}C
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   ${memperc}%   ${membar 6}$color
Root:  ${fs_used_perc /} %   ${fs_bar 6 /}$color 

${color orange}NETWORK (${addr ra0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```

this is the latest conkyrc i tweaked. i have an athlon 64 XP3200+ and i don't know how to get temps reported, so i edited it out, it still takes up a space on the taskbar, even though i forked it to the desktop (which worked with the other .conkyrc i used)

---

### Post by Sonic Reducer on 2006-11-29
so right now i fixed a few simnple things, like spacing and the networking address reported to the router, but i still have no temperature feedback from the processor and i would like that (possibly even a CPU fan RPM, but i'm using the external pot that came with my Zalman CNPS7700 so i don't know if it'll work)

the conky window works perfectly, if i put a window semi on top of it the other window is always on top, it refreshes @ 1Hz so it looks alive, it has all the info i'd need (has it all in theory :) ) and it looks nice. it also unfortunately has a slot on the taskbar. how can i fix this?

---

