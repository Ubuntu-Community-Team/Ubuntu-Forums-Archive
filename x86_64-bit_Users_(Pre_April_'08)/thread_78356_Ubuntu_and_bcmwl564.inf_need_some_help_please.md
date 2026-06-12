---
title: "Ubuntu and bcmwl564.inf need some help please"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by deathbyswiftwind on 2005-10-18
Hey everyone whats up. Heres my problem no matter what I do with ndiswrapper and wireless tools I cannot get my network card (Broadcom BCM4316) to work. Ndiswrapper will detect it and install the driver. When I do the list drivers command it gives me the driver present hardware present but I still can not connect with it. Any 32 bit linux works perfectly with my card. I love the way ubuntu64 runs on my machine but if i cannot connect to wifi the purpose of owning a laptop is kinda shot. Could someone please give me some advice. I am using the luxiant driver which is made for 64 bit. I have also tried the 32bit that came on my restore disk (which worked for all other distros of linux which were 32bit) Thanks

Rob

---

### Post by GuyveR800 on 2005-10-20
Did you convert the .inf to UTF8? That did it for me using ndiswrapper 1.1 from the ubuntu repositories.

---

### Post by neufena on 2005-10-20
It's a bit sketcy in my mind exactly what commands I used but here's how I got it working:

I could get it to work with the Ndiswrapper i the repos and the source wouldn't compile as it needed to use gcc 3.4 for the kernel module so I conected up to my network with the onboard wired lan (slung a LONG cable down the stairs!) and downloaded gcc 3.4 then compiled and installed Ndiswrapper following the instructin on the website.  What I can't remember is how I got it to use gcc 3.4, I *think* it was 

Export GCC = 3.4 but I'm probably wrong!

hope this helps,

---

### Post by mszombie on 2005-10-20
Hi there,

I just managed to get this working today.
Try this url for the ndis 1.4 install, and the drivers:
[http://www.cis.ksu.edu/~aruljohn/debian/](http://www.cis.ksu.edu/~aruljohn/debian/)

then finish with the ndiswrapper instructions here:
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

This was the way I got it working today.

MLS

---

### Post by HankB on 2005-10-25
[QUOTE=GuyveR800]Did you convert the .inf to UTF8? That did it for me using ndiswrapper 1.1 from the ubuntu repositories.[/QUOTE]

How did  do that? That file isn't even a text file. I googled for UTF8 convertors and didn't find anything.

I'm still struggling with this. The drivers loaded and appeared to work (iwlist scan reported APs) the very first time I tried it and has not worked since.

thanks,
hank

---

### Post by GuyveR800 on 2005-10-26
[QUOTE=HankB]How did  do that? That file isn't even a text file. I googled for UTF8 convertors and didn't find anything.[/QUOTE]
The .inf file *is* a text-file, but it's most probably in UTF-16 format. 
I used Windows to convert it to UTF-8, but I think the following command should work for you:
```
iconv -f utf-16 -t utf-8 bcmwl564.inf
```

---

