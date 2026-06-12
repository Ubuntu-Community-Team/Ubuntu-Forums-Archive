---
title: "imac 333 installs then white screen on boot"
date: 2005-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by oswaldkelso on 2005-12-25
imac 333 installs from the cd then white screen as it tries to run.

mc spec

imac 333 with three 7.95gb partitions and 4gb free for ubuntu

The first partition has osx 10.2 jaguar and boots fine(upgrading to panther as I type) the rest are empty

As I understand it on this model osx must be on the first partition and the partition must be under 8gb

Is this why Ubuntu wont boot as it tries start from a partition that is not the first?

I have tried holding the alt key on start up nothing happens

Any idea recieved with thanks 

oswald kelso

---

### Post by oswaldkelso on 2005-12-26
After much surfing I have found the answer and thought I'd leave it here to help anyone else with the same problem.

imac models from 233mhz through to 333mhz can only recognise the first 8gb (7.95gb) of a harddrive so even if you partition a larger harddrive into many smaller 7.95gb sections the mac can only boot from the **first** 7.95gb so **all ** os's osx, os 9, linux,must be within this first 7.95gb.

once booted you can use any other 8gb image to store your data

hope it helps

---

