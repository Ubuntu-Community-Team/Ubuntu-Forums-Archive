---
title: "error with install wine"
date: 2008-09-06
forum: Wine
---

### Post by iraqb on 2008-09-06
Hello,
i have this error 

[COLOR="Red"][SIZE="7"]please help[/SIZE][/COLOR]

---

### Post by pytheas22 on 2008-09-06
It looks like you tried to do an offline installation of wine.  It would be better to use the repositories.  Please try opening a terminal and typing:
```

sudo apt-get update
sudo apt-get install wine
```

If that gives errors, please post the output.  It should work, though.

---

### Post by iraqb on 2008-09-06
> admin@test-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package wine 


now what ?

---

### Post by pytheas22 on 2008-09-06
It looks like you don't have all of the repositories enabled (sorry, I should have mentioned that before).  Go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, make sure that all the boxes are checked.  Then close the window; if you're asked to reload the sources list, say yes.

Then run again:
```

sudo apt-get update
sudo apt-get install wine
```

If that doesn't work, what is the output of:
```

cat /etc/apt/sources.list
```

---

### Post by iraqb on 2008-09-06
thanks a lote
it is work fine now

bay :)

---

