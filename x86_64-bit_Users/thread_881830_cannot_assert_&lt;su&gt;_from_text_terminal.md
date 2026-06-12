---
title: "cannot assert &lt;su&gt; from text terminal"
date: 2008-08-06
forum: x86 64-bit Users
---

### Post by noshellswill on 2008-08-06
Gents:

From text terminal, When I try to assert  <su> "mypassword" 

I get the error message:      AUTHENTICATION FAILURE

That "mypassword" works just fine otherwise. What's the issue ??

---

### Post by tollboy on 2008-08-06
> **noshellswill said:**
> Gents:

From text terminal, When I try to assert  <su> "mypassword" 

I get the error message:      AUTHENTICATION FAILURE

That "mypassword" works just fine otherwise. What's the issue ??
are u sure this i9s ur root password 
actually when u tyoe ```
sudo
``` then its need superuser password



bt when u type ```
su
```

or

```
su -
```

then it means u r demanding root privillage
n for this u have to give ur root password

---

### Post by snowpine on 2008-08-06
Hi there, there's a lot of confusion out there about sudo vs. su vs. root. Hope this article clears things up for you: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ps to specifically answer your question, you would need to type 'sudo su' not just 'su' however it is not recommended--you can accomplish the same things with 'sudo'. :)

---

### Post by Jouke74 on 2008-08-06
If you really want to use "su" you need to change the root password under Administration > users & groups. Fill in a password with your own superuser account. Then you can use SU. 

Note that in the beta 2 of Ubuntu 8.04 this lead to lots of troubles with Nautilus etc. I have been using "sudo" ever since only.

---

### Post by noshellswill on 2008-08-10
Gents, the issue is:

I'm "1st user" ... that is I do all sysadmin under mu own name/passwd. The ROOT_usr is not enabled. I need to remove a directory created under ANOTHER users name/passwd. 

At terminal when I type <sudo> only I get lots of obscure text telling me howto enter  a  <sudo> syntax. I really, really do not want to deal with this. 

So ... do I need to creat a ROOT passwd ? Then I imagine I could enter in a terminal textbox:

    <ROOT>
    <rootpasswd>
    <cd> /home
    <rmdir> /home/girlfriendsbaddirectory
     <exit>

Do I have the clue ? Anything "special" about creating a ROOT passwd ?

---

### Post by baggins on 2008-08-10
No you do not need to set a root password, in fact I would recommend leaving it as it is.
To make sudo work just put it in front of the command you whish to execute as root.

To do what you are trying to do you enter the following (in a shell obviously :) )
```
 sudo rm -rf /home/girlfriendsbaddirectory.
```
you will be asked your password, this is the same one you use to log in.

I will however like to make two points: 
[LIST=1]
[*] You need rm -rf because I assume that the directory is not empty, rmdir will only remove empty folders. 
But you need to be carefull when using rm with -rf options as root or via sudo I.e if applied to &#733;/.* it will delete the entire system, as the star will expand all ../ (parent folders) recursively. Needless to say this is bad.
[*] As snowpine said you really should read: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
In the mean time the short version is 
su   : Log in as SuperUser
sudo : do the following command "as if" logged in as superuser
[/LIST]

-- Jon

---

### Post by Kilz on 2008-08-10
Alternately, you can open a terminal, type in ```
gksudo nautilus
``` and open nautilus as an admin, navigate to the directory and delete it.

---

### Post by cariboo on 2008-08-10
If you know the name and password of the user who's directory  you want to delete in a terminal simply type:

```
su <username>
```

This will prompt for <username>'s paswoord then you can delete to your hearts content.

---

### Post by baggins on 2008-08-11
> **cariboo907 said:**
> If you know the name and password of the user who's directory  you want to delete in a terminal simply type:

```
su <username>
```

This will prompt for <username>'s paswoord then you can delete to your hearts content.

And if you don't have the other users password 
```
sudo su <username>
```
will prompt for only your own password

-- Jon

---

### Post by noshellswill on 2008-08-13
> **baggins said:**
> No you do not need to set a root password, in fact I would recommend leaving it as it is.
To make sudo work just put it in front of the command you whish to execute as root.

To do what you are trying to do you enter the following (in a shell obviously :) )
```
 sudo rm -rf /home/girlfriendsbaddirectory.
```
you will be asked your password, this is the same one you use to log in.

I will however like to make two points: 
[LIST=1]
[*] You need rm -rf because I assume that the directory is not empty, rmdir will only remove empty folders. 
But you need to be carefull when using rm with -rf options as root or via sudo I.e if applied to &#733;/.* it will delete the entire system, as the star will expand all ../ (parent folders) recursively. Needless to say this is bad.
[*] As snowpine said you really should read: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
In the mean time the short version is 
su   : Log in as SuperUser
sudo : do the following command "as if" logged in as superuser
[/LIST]

-- Jon
Yes it worked:

<sudo>  rm -rf /home/girlfriendsbaddirectory

... all gone. Thanks gents for the info.

---

