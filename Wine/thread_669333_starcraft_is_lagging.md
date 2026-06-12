---
title: "starcraft is lagging"
date: 2008-01-16
forum: Wine
---

### Post by slopis on 2008-01-16
i ma  noobs to linux. now i have secound pc linux, and i wanted to try starcraft on it. i dont have install cd, but usualy sc work perfecly if i just copy all SC folder.. so i did this time, and when i luncked it via wine, it work but is lagging like hell. cannt even play.
any sugestion how i can  make mine sc working with out lags?

---

### Post by sauronsmatrix on 2008-01-18
you most probably did not install the graphics drivers properly.

if you have nvidia, search in synaptics package manager and install the proper one depending on your card,

then in command line run:
```
sudo nvidia-glx-config enable 
```

---

