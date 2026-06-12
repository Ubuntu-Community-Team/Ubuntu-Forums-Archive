---
title: "nividia 6600 problems on ubuntu 6.10"
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by moza on 2007-04-19
hello 

im running ubuntu 6.10 on my machine intel x86_64 and a graphics card 6600 nividia 

i have a problem with the driver......first i downloaded a driver from automatix and i 

downlaoded beryl and it worked one time very good then it crashed on the next 

restart and then i restored the x server.....i tried to install the driver from the terminal 

(the notes on ubuntu guide) but it didnt work and beryl didnt work too......so what 

shall i do to install this driver..thanks

---

### Post by katten on 2007-04-19
Well you should try and download and install the nvidia driver from [www.nvidia.com](www.nvidia.com) 


here is a litle howto install.

turns of the x-server 
```

sudo init 1

```

download the latest nvidia x86_64 driver
```

wget http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

```
execute the file
```

sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

```

if you get any error it may because you need the kernel source, g++, nvidia libs installed.

---

