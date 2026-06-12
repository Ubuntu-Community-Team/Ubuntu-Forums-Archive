---
title: "[SOLVED] Wine Error during update"
date: 2008-09-24
forum: Wine
---

### Post by hoboy on 2008-09-24
Whenever I run Update Manager I get the following error, I have google, but not found any solution.

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by kostkon on 2008-09-24
> **hoboy said:**
> Whenever I run Update Manager I get the following error, I have google, but not found any solution.

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
oops! wrong repo!

---

### Post by david_kt on 2008-09-24
> **hoboy said:**
> Whenever I run Update Manager I get the following error, I have google, but not found any solution.

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Try to run below command:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

It might solve your problem.

DK

---

### Post by hoboy on 2008-09-24
> **david_kt said:**
> Try to run below command:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

It might solve your problem.

DK

the problem is solved.tks.

---

### Post by cloudstrifejr1 on 2009-01-10
> **david_kt said:**
> Try to run below command:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

It might solve your problem.

DK

This also worked for me too. Thanks!

---

### Post by spwnt on 2009-01-29
> **david_kt said:**
> Try to run below command:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

It might solve your problem.

DK

That fixed it for me on Intrepid aswell. Thanks much!

---

### Post by sinnadyr on 2009-03-06
Worked for my Intrepid too...

---

### Post by forestwalkerjoe on 2009-03-17
I used the first wget you have.. and it solved ONE of the problems i was getting but i have two more reposits that are doing the same thing. 
I tried to lift their address to the code you left and it says NO GO.. 
here are mine.. can some one help me validate these?
 ```
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
```
I cant recall what it was i was doing.. but there was a app i was trying to install that suggested  I use these repos and said there could be a public key issue.. and i thought i had that solved.. now i can not even recall what it was i was trying to install and there we now have these  fails that are in my way.. hope ya all can help me fix em. thanks. 
FWJ

---

### Post by david_kt on 2009-03-17
> **forestwalkerjoe said:**
> 
I cant recall what it was i was doing.. but there was a app i was trying to install that suggested  I use these repos and said there could be a public key issue.. and i thought i had that solved.. now i can not even recall what it was i was trying to install and there we now have these  fails that are in my way.. hope ya all can help me fix em. thanks. 
FWJ

You should recall what you want to install, and then follow below steps (watch the video):

[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

DK

---

