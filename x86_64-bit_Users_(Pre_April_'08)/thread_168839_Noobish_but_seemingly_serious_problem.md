---
title: "Noobish but seemingly serious problem"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lethal_Appetite on 2006-05-01
I just started using Ubuntu AMD64 style and the more I use it the more I see a problem.  I figured out my problem by looking at the properties of files I'm denied authority to change.  My friend helped me install Ubuntu (using his CD) and we installed it with a username and password I don't prefer, so when it was up and running, I made a new account in the same group with full privilages and deleted the original.

Now I find by checking the properties of files I'm denied access to change, that my account is not the "Owner" so I am having alot of trouble installing things.  Is there any way to make my account the Owner, or must I re-install Ubuntu?

---

### Post by jazzmuzik on 2006-05-01
The solution is simple. Run this at the command line (Terminal program):

Incorrect (oops):
sudo chown: -R user:user /home/user

Correct:
sudo chown -R user:user /home/user

where 'user' is your account/login name

---

### Post by Lethal_Appetite on 2006-05-01
I entered that, and got this message:

sudo: chown:: command not found

---

### Post by jazzmuzik on 2006-05-01
Oops. Sorry, my fault. I added a colon. Try this:

sudo chown -R user:user /home/user

---

### Post by Lethal_Appetite on 2006-05-01
now I am getting this message:

chown: cannot access `/home/user': No such file or directory

I think its not finding it because it is only looking inside my account file,
(/Home/user/Myaccount)/home/user

But I don't know  :'[

I tried:
cd ~/home
and it just says "/home/myaccount/home" doesnt exist

---

### Post by jazzmuzik on 2006-05-01
do this and report the results:

ls -l /home

I think you need this:

sudo chown -R myaccount:myaccount /home/myaccount

---

### Post by Lethal_Appetite on 2006-05-01
ls -l /home returned:

total 8
drwx------  22 lethalappetite not 4096 2006-04-29 02:00 lethalappetite
drwxr-xr-x  18 lethalappetite not 4096 2006-04-27 17:58 not
---
I have been doing:
sudo chown -R lethalappetite:not /home/user

inputing lethalappetite:lethalappetite returns:
chown: `lethalappetite:lethalappetite': invalid group
(so i use 'not', my group name)

sudo chown -R lethalappetite:not /home/lethalappetite
this ^ showed no result

---

### Post by jazzmuzik on 2006-05-01
Oh. That explains it. If lethalapeitite is your login in name, try this:

sudo chown -R lethalappetite:lethalappetite /home/lethalappetite

What is 'not' for ?

---

### Post by Lethal_Appetite on 2006-05-01
'not' is my accounts group name, the group that was made for my first account while installing ubuntu.

sudo chown -R lethalappetite:lethalappetite /home/lethalappetite
returns:" chown: `lethalappetite:lethalappetite': invalid group"

So I replaced it with lethalappetite:not and it simply returns nothing, and changes nothing :'[

---

### Post by jazzmuzik on 2006-05-01
Weird.

I think you need to create a new user account. I don't understand why you've combined the two accounts with the user name and group name.

I would:

1. create a new account
2. move files from the old accounts to the new account
3. fix ownership with chown
3. remove old accounts

---

### Post by Lethal_Appetite on 2006-05-01
I spoke to my friend, I'll just get that disk and reinstall,

Thanks for your help, though it didn't solve my screwy problem, you've helped me get more experience screwing around with the command line, and thats just as good :]

---

