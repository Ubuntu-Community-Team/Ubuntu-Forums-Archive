---
title: "Conky how to Tutorial"
date: 2010-12-13
forum: Zimbabwe Team
---

### Post by TheGizmo on 2010-12-13
Hie all

Here is a little how to i wrote.

[http://dl.dropbox.com/u/6854866/Conky_How_To.pdf](http://dl.dropbox.com/u/6854866/Conky_How_To.pdf)

It shows you how to install, customize and run conky background system monitor. Couldn't upload it on these here forums, it exceeds the size limit so you can get it from my public dropbox folder.

i had an issue though with the jpegs, everytime i exported a PDF they would get a little blurry[ i thought it had something to do with compression]. I couldnt solve this through tweaking and changing settings// any thoughts?

This is my first try at writing a how to tutorial so please try to review and give feedback.

---

### Post by raymondswart on 2010-12-15
Hi TheGizmo,

Thank for your tutorial, followed it through and got it working first time thanks for the effort you put into it.

---

### Post by NIT006.5 on 2010-12-15
For a first attempt at writing a tutorial, I think you did brilliantly! :) Easy to follow and well explained. Many thanks!

---

### Post by pheebs on 2010-12-15
Great tutorial and resource, thank you a bunch.

I played around with one of the samples you listed and came up with a simple .conkyrc

```
# UBUNTU-CONKY
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 800

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 2

# border width
border_width 2

# Default colors and also border colors, grey90 == #e5e5e5
default_color eeeeee

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

text_buffer_size 1024

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color${font ubuntu:size=9}
${alignc}$nodename@$sysname $kernel on $machine${font ubuntu:size=8}

${color orange}CPU 
${hr}$color

${freq}MHz
${alignr}${loadgraph 10,250 e5e5e5 F1AA0E}
CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${acpitemp}
${alignr}${cpubar 0 20,250}
# 1: ${color}${cpu cpu1}% ${alignr} 2: ${color}${cpu cpu2}%
# ${cpugraph 1 6,120 e5e5e5 F1AA0E}${alignr}${cpugraph 2 6,120 e5e5e5 F1AA0E}
# 3: ${color}${cpu cpu3}% ${alignr} 4: ${color}${cpu cpu4}%
# ${cpugraph 3 6,120 e5e5e5 F1AA0E}${alignr}${cpugraph 4 6,120 e5e5e5 F1AA0E}
NAME${alignr}PID         CPU%        MEM%
${top name 1}${alignr}${top pid 1}       ${top cpu 1}          ${top mem 1}   
${top name 2}${alignr}${top pid 2}       ${top cpu 2}          ${top mem 2}   
${top name 3}${alignr}${top pid 3}       ${top cpu 3}          ${top mem 3}   
${top name 4}${alignr}${top pid 4}       ${top cpu 4}          ${top mem 4}   

${color orange}MEMORY / DISK 
${hr}$color

Total: ${color}${memmax} ${alignr} Free: ${color}${memfree}
RAM: $memperc% ${alignr}Swap: $swapperc% 
${membar 6,120} ${alignr} ${swapbar 6,120 }
root: ${fs_used_perc /}% ${fs_bar 6 /}$color

${color orange}NETWORK (${addr eth0})
${hr}$color

Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,120 e5e5e5 F1AA0E} ${alignr}${upspeedgraph eth0
20,120 e5e5e5 F1AA0E}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

```

It uses eth0 inststead of wireless, and I ripped out the battery stuff, and fooled around with the style a bit.

Again, thank you very much!

---

### Post by TheGizmo on 2010-12-15
I'm glad the tutorial has been useful to you guys...
Here is my conky configuration file

```
# — Pengo (conky@pengo.us)
#
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints below

minimum_size 185 768
maximum_width 185

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont DejaVu Sans:size=7
xftalpha 0.8

# Update interval in seconds
update_interval 2.0
total_run_times 0
double_buffer yes
text_buffer_size 1024

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no 

# Stippled borders?
stippled_borders 3
border_margin 5
border_width 6

default_color white
own_window_colour brown
own_window_transparent yes

alignment top_right
gap_x 12
gap_y 30

# stuff after ‘TEXT’ will be formatted on screen

TEXT

${color white}${alignc}${font Ubuntu:size=8}THY NAME HERE${font}
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}B${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}
${voffset 4}${font styleBats:size=14}R${font} ${voffset -5}ROOT:${alignr}${fs_used /}/${fs_size /}
${voffset 4}${font styleBats:size=14}S${font} ${voffset -5} HOME:${alignr}${fs_used /home}/${fs_size /home}
${voffset 4}${font styleBats:size=14}B${font} ${voffset -5}SWAP:${alignr}${fs_used swap}/${fs_size swap}

NETWORK ${hr 2}
${if_up wlan0}
${voffset -6}${font PizzaDudeBullets:size=14}O${font} Up: ${upspeed wlan0} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDudeBullets:size=14}U${font} Down: ${downspeed wlan0} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDudeBullets:size=14}N${font} Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDudeBullets:size=14}T${font} Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDudeBullets:size=14}Z${font} Signal: ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDudeBullets:size=14}a${font} Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDudeBullets:size=14}b${font} Public Ip: ${alignr}${execi 3600 curl http://riivo.eu/php/ip.php}
${else}
${if_up eth0}
${voffset -6}${font PizzaDudeBullets:size=14}O${font} Up: ${upspeed eth0} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDudeBullets:size=14}U${font} Down: ${downspeed eth0} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDudeBullets:size=14}N${font} Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDudeBullets:size=14}T${font} Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDudeBullets:size=14}a${font} Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDudeBullets:size=14}b${font} Public Ip: ${alignr}${execi 3600 curl http://riivo.eu/php/ip.php}
${endif}${else}
${font PizzaDudeBullets:size=14}4${font} Network Unavailable
${endif}

CPU MANAGER ${hr 2}
${voffset 6}${color #e5e5e5}${top name 1}${alignr}${top cpu 1}%
${color #c4c4c4}${top name 2}${alignr}${top cpu 2}%
${color #a3a3a3}${top name 3}${alignr}${top cpu 3}%
${color #828282}${top name 4}${alignr}${top cpu 4}%
${color #505050}${top name 5}${alignr}${top cpu 5}%
${color white}${alignc}${font styleBats:size=14}K${font}

${color white}MEM MANAGER ${hr 2}
${color #e5e5e5}${top_mem name 1}${alignr}${top_mem mem 1}%
${color #c4c4c4}${top_mem name 2}${alignr}${top_mem mem 2}%
${color #a3a3a3}${top_mem name 3}${alignr}${top_mem mem 3}%
${color #828282}${top_mem name 4}${alignr}${top_mem mem 4}%
${color #505050}${top_mem name 5}${alignr}${top_mem mem 5}%
${color white}${alignc}${font styleBats:size=14}U${font}

${color white}DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %B}
${alignc}${font OpenLogos:size=30}T
```

This one uses some special fonts that can be found [here]("http://www.dafont.com").

---

### Post by PuddingKnife on 2011-01-04
Thanks! Very helpful  :)

---

### Post by Gr1tz582 on 2011-01-08
I am really new to Ubuntu and I found this really easy to follow and very well written Thanks so much!
Does anyone know where I can get a good Conkyrc file from?
I can't really write that stuff yet because I have only just been converted from Windows and have very little programming experience.

---

### Post by TheGizmo on 2011-01-09
> **Gr1tz582 said:**
> I am really new to Ubuntu and I found this really easy to follow and very well written Thanks so much!
Does anyone know where I can get a good Conkyrc file from?
I can't really write that stuff yet because I have only just been converted from Windows and have very little programming experience.

you can always search through [http://gnome-look.org/](http://gnome-look.org/) or just enter conkyrc file in your favourite search engine

---

### Post by Megaptera on 2011-01-09
Quote"Does anyone know where I can get a good Conkyrc file from?"

This thread [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by Prescilla on 2012-05-08
how can i stop (kill) running conky, so i can test my own conky scripts?

---

