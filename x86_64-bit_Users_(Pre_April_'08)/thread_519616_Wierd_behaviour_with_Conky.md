---
title: "Wierd behaviour with Conky"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by nowhere.elysium on 2007-08-07
Hi Folks. I'm havinga  bit of a strange time with conky. Basically, I've got it t install, and it starts up just fine on bootup. However, as soon as I click on the desktop, it blanks out. The process is still running, though.
I've tried all three options on the own_window_type, with the same results each time.
Here's my .conkyrc file:

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

```

I cut out the text parameters, because that's just formatting and orientation stuff. I don't think that it's going to seriosuy affect the issue that I'm having.

So... any thoughts?

---

### Post by kerry_s on 2007-08-07
# Create own window instead of using desktop (required in nautilus)             
own_window yes                                                                  
own_window_type override                                                        
own_window_hints undecorated,below,skip_taskbar

---

### Post by nowhere.elysium on 2007-08-07
Top banana! I shall try that when I get back from t'pub. Cheers :D

---

### Post by nowhere.elysium on 2007-08-08
Nope, still spacks out randomly. Bugger. It seems to be refreshing the desktop when it does it...

---

### Post by nowhere.elysium on 2007-08-08
Haha! Sorted! I now havea  very sweet configuration working like a charm...
```

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 38
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$nodename $alignr $kernel
AMD64X2 4600+ $alignr${freq_g cpu0}Ghz
$alignc CPU Average
${cpugraph cpu0 eeeeee cccccc}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

$alignc Disk I/O
${diskiograph} 
$alignc Filesystem Usage
/ ${fs_used_perc /}% ${fs_bar /}
$alignc Swap Usage 
$color $swap/$swapmax $color $swapperc% ${swapbar}

$alignc Processes
$alignr $running_processes Running 
$alignr $processes Sleeping

$alignc Top Processes
CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
${downspeedgraph eth0}
Up $alignr ${upspeed eth1} kb/s
${upspeedgraph eth0}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

${execi 1800 /home/nowhere/.weather/weather.sh UKXX0085}

```

edit: Added screenshot. Sorted :D

---

