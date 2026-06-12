---
title: "Jaunty turning off num lock"
date: 2009-06-30
forum: x86 64-bit Users
---

### Post by a2z on 2009-06-30
Hello everybody.

Jaunty 9.04 has just now started turning off my keyboard num lock.

I checked the keyboard with Intrepid on the same set up and it doesn't turn off. I have also hooked to a different keyboard where Jaunty still persistantly turns off numb lock.

I find it odd to all of the sudden start doing this.

Has anyone else experienced a simular problem? 
Any suggestions how to fix it?

I tried to get the latest updates, howver, several updates failed.
Not sure what to do. 

Thanks 
a2z

---

### Post by george.henne on 2009-07-01
I've had the same problem.  I don't know the reason for the change, but here is a simple way to fix it that I found here: [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

Assuming you are using the gnome desktop (standard for ubuntu)

----------------------------------------------------------------

Enabling NumLock in GDM (as used in Ubuntu Gnome and Xubuntu XFCE)

Open a terminal window and install numlockx

```
 $ sudo apt-get install numlockx 
```

edit /etc/gdm/Init/Default

```
 $ sudo gedit /etc/gdm/Init/Default 
```

Find the line

```
 exit 0 
```

Add the following code above that line

```

            if [ -x /usr/bin/numlockx ]; then
              /usr/bin/numlockx on
            fi

```

Save and close gedit.

The numlock will still turn off, but it will turn back on when the login screen loads.

---

### Post by a2z on 2009-07-01
Thanks for your advice!
I'll give it a try. 
Unusual how it all of the sudden started doing it.
At first on a regular basis. Now kind of intermittently.
Still annoying though. Especially when you come to depend on it being on! 

Cheers,

a2z

---

### Post by tbone7 on 2009-07-02
The same thing suddenly started happening to me. This solved it: 

*Also.. even if the numlock light on your keyboard is on.. there is a setting that can override it. System->Preferences->Keyboard.. then click the "Mouse Keys" tab and make sure to uncheck "Pointer can be controlled using the keypad".*

---

### Post by a2z on 2009-07-02
Thanks for the reply. 
I have not had much time to pursue correcting this yet. 
Even so, all info is knowledge, and greatly appreciated.

Good day/evening where ever you may be
a2z

---

