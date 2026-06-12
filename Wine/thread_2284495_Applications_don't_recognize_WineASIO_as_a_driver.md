---
title: "Applications don't recognize WineASIO as a driver"
date: 2015-06-29
forum: Wine
---

### Post by tdogmonster1337 on 2015-06-29
Hello, I am trying to get an ASIO application to work. I installed WineASIO from the KXStudio repositories:

```
sudo apt-get install wineasio
```

And have edited my /etc/security/limits.conf file and have added three lines:

```

@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19

```

I start my jack server like this:

```
killall jackd;killall pulseaudio;jackd -R -t 1000 -d alsa -P hw:0,0 -r 48000 -n2 -D
```

but in my application (I'm using tobybear's MiniHost), it does not recognize WineASIO as a driver, and quits.


Please help me to get this working! :confused:

---

### Post by Geothermal123 on 2015-07-08
I would suggest that you use PlayOnLinux and follow this guide [https://d4v33d.wordpress.com/2014/03/24/work-wineasio-on-ubuntu-14-04-with-flstudio/](https://d4v33d.wordpress.com/2014/03/24/work-wineasio-on-ubuntu-14-04-with-flstudio/). While the guide's for FLStudio, I used it for other apps and it works great. The guide uses the 32 bit version of wineasio, but I think it would apply to the 64 bit if the application you're using is 64 bit.

---

