---
title: "Conky"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by Hagen. on 2009-08-08
Hi, I'm new here. I was looking for the whole internet about my problem but I couldn't find anything useful. Problem is the next: I have conky 1.6.0 installed on my Ubuntu 9.04 64 bits, it starts fine on statup but after a time and for aprox 8 min, conky stops refreshing itself and the time and all the other values stay freeze (always inside conky). My .conkyrc is fine, I checked its configuration a lot of time but can't find anything wrong. I tried to rise the priority level of conky but it didn't work. Please, somebody could help me or give an answer?

Here I leave you a copy of my conkyrc.

[html]&#65279;# .conkyrc - Edited from various examples compiled from the web
# by Naf

# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
total_run_times 0
update_interval 0.5
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 45

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1.0
maximum_width 250
stippled_borders 3
border_margin 9
border_width 10
default_color #92A2C7

# --- Text --- #
draw_outline no
draw_borders no
font Sans:size=8:weight=bold
uppercase no
draw_shades yes
override_utf8_locale yes

TEXT
${font Sans:size=9:weight=bold}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}
${alignc 30}${color #E67B13}${font OpenLogos:size=50}u${font}
${font Sans:size=14:weight=bold}${color #99CBFF}            ${time %H:%M}
${font Sans:size=11:weight=bold}${color #99CBFF}    ${time %A} ${time %e} ${time %B} ${time %G}

${font Sans:size=9:weight=bold}${color  #99CBFF}System Information ${hr 2}$color${font Sans:size=8:weight=bold}
${color  #99CBFF}Computer$color Ubuntu 9.04 ${alignr}${color  #99CBFF} Uptime$color $uptime
${color  #99CBFF}Kernel$color  $kernel ${alignr}${color  #99CBFF}Arch.$color $machine

${color  #99CBFF}Date ${hr 2}

${color 888888}${font LCDMono:bold:size=12}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color 888888}'" "/}

${font Sans:size=9:weight=bold}${color  #99CBFF}Computer ${hr 2}$color
${font Arial:bold:size=8}${color #ff0000}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2- | sed 's#Processor ##'}$font$color
${color  #99CBFF}Frequency:$color ${execi 20 sensors |grep "Core0 Temp" | cut -d" " -f4} $font$color$alignr${freq_g 2} GHZ ${color green}${execi 20 sensors |grep "Core1 Temp" | cut -d" " -f4}  $color${alignr}${color  #99CBFF}Processes:$color $running_processes/ $processes

${font Sans:size=9:weight=bold}${color  #99CBFF}CPU ${hr 2}$color
${color green}CPU1          ${color white}${cpu cpu0}%        ${color green}CPU2         ${color white}${cpu cpu1}%        
${cpugraph cpu0 25,120 000000 ff6600 }  ${cpugraph cpu1 25,120 000000 ff6600 }   
${color green}CPU3         ${color white}${cpu cpu2}%
${cpugraph cpu2 25,120 000000 ff6600 }

${font Sans:size=9:weight=bold}${color  #99CBFF}5 Process Top ${hr 2}{color} ${alignr}${color green}
Name                                    ${alignr}CPU  ${alignr}RAM  $color
${top name 1}${alignr}${top cpu 1}${alignr }${top mem 1}
${top name 2}${alignr}${top cpu 2}${alignr }${top mem 2}
${top name 3}${alignr}${top cpu 3}${alignr }${top mem 3}
${top name 4}${alignr}${top cpu 4}${alignr }${top mem 4}
${top name 5}${alignr}${top cpu 5}${alignr }${top mem 5}

${font Sans:size=9:weight=bold}${color  #99CBFF}Ram & Swap ${hr 2}$color${font Sans:size=8:weight=bold}
${color #99CBFF}RAM$color  ${memperc}%  ${color  #99CBFF}${membar 3.180}
${color #99CBFF}SWAP$color  ${swapperc}%  ${color  #99CBFF}${swapbar 3.180}

${font Sans:size=9:weight=bold}${color  #99CBFF}Partition ${hr 2}$color${font Sans:size=8:weight=bold}
${color #99CBFF}Root$color  ${fs_free_perc /}%$alignr${fs_free /}/ ${fs_size /}
${color  #99CBFF}${fs_bar 3 /} 
${color #99CBFF}Home$color  ${fs_free_perc /home}%$alignr${fs_free /home}/ ${fs_size /home}
${color  #99CBFF}${fs_bar 3 /home}

${font Sans:size=9:weight=bold}${color  #99CBFF}Public IP: ${execi 1~/.scripts/ip.sh} ${hr 2}$color${font Sans:size=8:weight=bold}
${font Sans:size=9:weight=bold}${color  #99CBFF}Network IP: ${addr eth0} ${hr 2}$color${font Sans:size=8:weight=bold}

${color #99CBFF}Transfer Speed
${color green}Download.$color ${downspeed eth0}&#1050;b/s${alignr}${color red}Upload.$color${alignr} ${upspeed eth0}&#1050;b/s
${downspeedgraph eth0 25,120 000000 00ff00} ${alignr}${upspeedgraph eth0 25,120 000000 ff0000}$color

${font Sans:size=9:weight=bold}${color  #99CBFF}&#1058;raffic ${hr 2}$color${font Sans:size=7:weight=bold}
${color green}Downstream ${totaldown eth0} ${alignr}${color red}Upstream ${alignr} ${totalup eth0}

${font Sans:size=8:weight=bold}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}[/html]

---

### Post by darco on 2009-08-09
You want to check out this HUGE thread for help:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

darco

---

### Post by Hagen. on 2009-08-09
> **darco said:**
> You want to check out this HUGE thread for help:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

darco

Thanks, it's so large that thread, I hope to find something useful there.

Thanks again.

---

### Post by darco on 2009-08-09
A good way to learn conky is to compare your script with another script. There are many good ones in the thread I gave you...
Thats how I figured what was wrong w/mine...

good luck

darco

---

