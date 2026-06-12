---
title: "IE9 on Ubuntu"
date: 2011-08-20
forum: Wine
---

### Post by oneadvent on 2011-08-20
This page says they have beta support for ie9:

[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

I for the life of me have no idea how to make that happen. Even an option would be a start. Can I get pointed in the correct direction?

I need this for website work, NOT because I like IE.

---

### Post by pqwoerituytrueiwoq on 2011-08-20
virtualbox count?
if it does not work on IE8 and works on IE9 likely it will work in firefox if you use the user agent switcher addon to tell them you are IE9

---

### Post by oneadvent on 2011-08-20
Thats my next step. I'm just avoiding it. 

I need to emulate ie9 so I can make sure the page isn't messed up for IE users. Just because I use linux doesn't mean everyone does. Its just frustrating cause their site says they do it but I see no option at all for it.

---

### Post by pqwoerituytrueiwoq on 2011-08-20
[http://browsershots.org/]("http://browsershots.org/") may work for you

---

### Post by oneadvent on 2011-08-20
The problem is that I am working on an offnet site. Where I have to login with my credentials to see the site. It is not available to the public. Once I'm sure my code is working I svn commit changes and it goes live. I have to see it before that happens.

Sorry to be such a pain.

---

### Post by pqwoerituytrueiwoq on 2011-08-20
aside from using virtualbox you could slap a banner on the page
Can you tell me if everything is working by emailing oneadvent (at) mysite.com
using if IE9 tags
```
<!--[if IE 9]> Can you tell me if everything is working by emailing oneadvent (at) mysite.com <![endif]-->
```

---

### Post by oneadvent on 2011-08-20
What the...

that's a terrible idea....


terrible.

---

### Post by eltonw on 2011-08-20
> **oneadvent said:**
> This page says they have beta support for ie9:

[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

I for the life of me have no idea how to make that happen. Even an option would be a start. Can I get pointed in the correct direction?

I need this for website work, NOT because I like IE.
... just a thought...
How about installing **WINE**, and running the **native windows IE** *within* it?

IMVHO _running beta software to do your work_ is pretty risky. All beta software generally comes with the caveat that running the code for mission-critical work is AYOR.

---

### Post by oneadvent on 2011-08-20
> **eltonw said:**
> ... just a thought...
How about installing **WINE**, and running the **native windows IE** *within* it?

IMVHO _running beta software to do your work_ is pretty risky. All beta software generally comes with the caveat that running the code for mission-critical work is AYOR.

I actually tried this, but it wont install. I went to winehq.org and they just say garbage and what I found when trying. I know running beta is risky, but its better than basically nothing, which is what I have right now.

Thanks!

---

### Post by b2zeldafreak on 2011-08-20
Seems like no one in this thread has given much attention to virtual-box for this one. Can you test the web page from within a Windows VM?

---

### Post by oneadvent on 2011-08-20
> **b2zeldafreak said:**
> Seems like no one in this thread has given much attention to virtual-box for this one. Can you test the web page from within a Windows VM?

Well that is where this is heading...but I would like to avoid it, I was hoping someone had experience with Ies4linux and could tell me how to get ie9 going in that.

---

### Post by holycow131415 on 2011-08-20
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

[http://www.tatanka.com.br/ies4linux/page/How_does_IEs_4_Linux_work](http://www.tatanka.com.br/ies4linux/page/How_does_IEs_4_Linux_work)

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

So the script (./ies4linux) installs all the IEs.

---

### Post by oneadvent on 2011-08-20
I ran the script, but the only options it gives are 6, 5.5, and 5 and then 7 as beta. I see no option or controls for ie 8 or 9, yet their page says it is possible.

Can you link me to a howto just for those? or a lead.

Thanks!

---

### Post by .... on 2011-08-20
I don't understand why you're having such a hard time:
```
sudo apt-get install wine cabextract
```
Then follow the directions here:  [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)
(Don't follow the Ubuntu-specific directions as they're ancient/obsolete)

---

### Post by in·ter·punct on 2011-08-20
This an extract from a white paper by Microsoft:

> Because Internet Explorer is integrated into the operating system, application virtualization options are not appropriate for virtualizing Internet Explorer 7 and Internet Explorer 6.

It is necessary to virtualize the entire operating system to obtain a previous version of Internet Explorer. By doing so, you prevent system conflicts that can occur if Internet Explorer is treated as an application.Source: [https://www.microsoft.com/download/en/details.aspx?displaylang=en&id=9242](https://www.microsoft.com/download/en/details.aspx?displaylang=en&id=9242)
Here is some more information: [http://support.microsoft.com/kb/2020599](http://support.microsoft.com/kb/2020599)
> **oneadvent said:**
> Can I get pointed in the correct direction?
Try this page: [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation).

I also need to test in IE and I'm taking the VM route. You might be interested in this thread: [http://ubuntuforums.org/showthread.php?t=1828892](http://ubuntuforums.org/showthread.php?t=1828892)

Edit: I'm slow.

---

### Post by oneadvent on 2011-08-20
I am not having trouble installing Ies4linux, I'm having trouble installing ie9 with Ies4linux. I understand virtualbox, and I will go down that route if I have to, but I would rather not.

---

### Post by Mark Phelps on 2011-08-21
I understand the problem, but I don't have a solution.  Wish I did...

And, it aggravates ME TOO when we keep telling folks that what we've tried doesn't work, and then one poster after another -- keeps telling us to do the same thing, over and over again!  It's like they don't bother to read the other posts before they respond.

---

### Post by cwwilson721 on 2011-08-21
Some things to think about:
[LIST]
[*]IE9 is designed to run in Windows, with all it's closed source hooks, DLLs, code, registry entries, etc.
[*]wine does an admirable job of 'simulating' those same processes, but can't do it all.
[*]You want to install a non-native and closed-source program into Ubuntu, and find you cannot.
[*]You then ignore the ONLY way to actually acomplish what you want to do, which is install a VM program (VMWare Player, VirtualBox, or any other), then install Windows itself, WHICH WILL WORK, albeit with much more complexity.
[/LIST]
If you HAVE to run IE9, the ONLY way right now (without going off on your own, and going to Alpha or lower level releases, or rewriting IE9 itself) is to install a VM/Windows/IE9. While wine is doing a FINE job, IT IS NOT WINDOWS. You cannot install everything you can in Windows, and expect it to work. wine is not a "Windows Install". ie4linux is partly older wine. Some things just don't work.

Sometimes, you have to bite the bullet, and actually use Windows.

And, by the same token, try getting a Linux-native program to work in Windows...Some you can, most you can't. You just have to accept the realities of the situation.

---

### Post by oneadvent on 2011-08-23
I resorted to VMware. Virtualbox kept freezing my system.

Its a shame that they say they can do it but cannot. Thanks for the help guys.

---

