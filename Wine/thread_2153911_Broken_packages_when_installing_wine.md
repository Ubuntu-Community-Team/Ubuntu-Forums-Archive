---
title: "Broken packages when installing wine?"
date: 2013-06-12
forum: Wine
---

### Post by caistio on 2013-06-12
Hello this is my first time here so I'm not fond of the forums and such. 

I have no idea on what to do maybe you nice people could help me out with installing wine? 
Wine decided to be difficult -__-
I have Ubuntu 12.10


[IMG]http://i43.tinypic.com/2rrs9cw.png[/IMG]

---

### Post by Petro Dawg on 2013-06-12
Try this...

Copy and paste the following codes into terminal one at a time.

```
***sudo add-apt-repository ppa:ubuntu-wine/ppa***
```


```
***sudo apt-get update***
```

to get the most current (beta) version type this...

```
***sudo apt-get install wine1.5***
```

otherwise use the older version (might be more stable)...

```
***sudo apt-get install wine1.4***
```

---

### Post by caistio on 2013-06-12
> **Petro Dawg said:**
> Try this...

Copy and paste the following codes into terminal one at a time.

```
***sudo add-apt-repository ppa:ubuntu-wine/ppa***
```


```
***sudo apt-get update***
```

to get the most current (beta) version type this...

```
***sudo apt-get install wine1.5***
```

otherwise use the older version (might be more stable)...

```
***sudo apt-get install wine1.4***
```


It all seemed to be working until the very end I tried both wine1.5 and wine1.4 and with both it said, "Unable to correct problems, you have held broken packagees."

---

### Post by Petro Dawg on 2013-06-12
Perhaps try the following first...

```
[SIZE=2][FONT=arial][COLOR=#333333]sudo apt-get install -f[/COLOR][/FONT][/SIZE]
```

and

```
[SIZE=2][FONT=arial]sudo apt-get upgrade[/FONT][/SIZE]
```

and then try re-installing wine using the previously given commands.



If that doesn't work try running...

```
sudo apt-get clean
```

and then try re-installing wine.

---

