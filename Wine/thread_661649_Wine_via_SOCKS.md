---
title: "Wine via SOCKS"
date: 2008-01-08
forum: Wine
---

### Post by trebor147 on 2008-01-08
Hey,

I have Wine installed and World of Warcraft.  In order for me to play I have to somehow route wow.exe to a SOCKS server.

I used to use FreeCap on Windows and Putty.  

On my Ubuntu 7.10 box I have opened an SSH connection and started a server,

```
ssh -D 1080 user@myhost
```

It connects fine and I can tunnel my apps to this, Firefox etc.


I have installed tsocks and tried to run

```
tsocks
wine wow.exe
```

I have configured tsocks to;
```
server = 127.0.0.1
server_port = 1080
```

I assume its not working because Wine doesnt support the tsocks command.

Is there anyway to make Wine tunnel requests to my local SOCKS server?

Thanks

Robert

---

