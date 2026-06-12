---
title: "I can't quit Wine Configuration"
date: 2011-09-19
forum: Wine
---

### Post by PayPaul on 2011-09-19
I was in the Audio tab and testing the sound when the program stalled on me. It won't quit and I don't even get the force quit dialog. How do I get it to close?

---

### Post by ergo-proxy on 2011-09-20
Check the FAQ: [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
Kill the process (kill -9 pid) or (wineserver -k)

---

### Post by PayPaul on 2011-09-20
> **ergo-proxy said:**
> Check the FAQ: [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
Kill the process (kill -9 pid) or (wineserver -k)
Found the **killall** command code yesterday. Worked like a charm. Of course there was another command I needed too in order to find the correct process name. Yet this was an instantaneous kill compared to the capriciousness of Windoze Task Manager. I'm guessing your response with commands to use are alternatives?

---

### Post by ergo-proxy on 2011-09-20
> **PayPaul said:**
> Found the **killall** command code yesterday. Worked like a charm. Of course there was another command I needed too in order to find the correct process name. Yet this was an instantaneous kill compared to the capriciousness of Windoze Task Manager. I'm guessing your response with commands to use are alternatives?
 
It's one of many possibilites :)
 
killall procesname (killall starcract) -> kills all processes with starcraft string
 
You can also use ps -ef|grep processname to find out process id then run kill -9 pid to kill the process
 
Find out more by checking for kill, pkill, killall commands

---

