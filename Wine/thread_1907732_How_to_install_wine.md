---
title: "How to install wine"
date: 2012-01-12
forum: Wine
---

### Post by madeel2 on 2012-01-12
I want to run some windows programs on lubuntu. I've read that wine does that for Ubuntu. How can I do it on lubuntu.

Actually I want to run an accounting software which was purchased for windows. 

Thanks in advance.

---

### Post by carl4926 on 2012-01-12
Install wine from the software centre or synaptic (v. 1.3)

After than do this in a terminal

```
winecfg
```
Just close the resulting box to accept the defaults

Or are you asking how to install your application as well?

---

### Post by raja.genupula on 2012-01-12
+1 to above post
 another way is just open your terminal and type wine then it will show you the list of versions and with what command.choose the version(better to pick new).then below that command for installation also will be there .

while coming to run y our application  for we have to set the application properties to execute , i mean 

chmod +x /path/to/your/app 

&
wine /youtapp/path/name.exe

it will be fine if you placed that app in  your home folder .

all the best.

---

### Post by carl4926 on 2012-01-12
It's worth checking here too
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Not all windows applications will work and or there may be tips and tricks there to help you

---

### Post by raja.genupula on 2012-01-12
yeah its must , First your application should be in wine supported app database. Then only wine will work to your application.

---

### Post by madeel2 on 2012-01-12
Thanks. That helped. Just another thing. Would it be enough wine internet explorer or I have to do some other trick as well?

---

### Post by carl4926 on 2012-01-12
> **madeel2 said:**
> Thanks. That helped. Just another thing. Would it be enough wine internet explorer or I have to do some other trick as well?

Are you asking about how to install IE?
If so why?
It's crud

---

### Post by mastablasta on 2012-01-12
only old IE works in wine. if your accounting software is browser based and uses IE7 and higher (or frame.net) you might be out of luck. if however it is just browser based (system independent) then you can simply use mozilla firefox or Chrome (chromium) to run it.

---

### Post by genzwebsolutions on 2012-01-12
where IE 8 comes in market then IE 7 is become older one how could that happened again which is not to be remarkable!

---

### Post by raja.genupula on 2012-01-12
Hi madeel2 , one small Question . you said you got one purchased product right ? ok that thing gonna run everytime or small amount of time & How much big it is ? will it deals with high much amount of RAM  ?

Because I think virtual BOX can help you if you are going to use the app for limited (1- 2 Hrs i think no problem ).So you can wake up that app when ever you want and there will be full functionality to you.

:):)

---

### Post by Rodney9 on 2012-01-12
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by amjjawad on 2012-01-12
> **madeel2 said:**
> I want to run some windows programs on lubuntu. I've read that wine does that for Ubuntu. How can I do it on lubuntu.

Actually I want to run an accounting software which was purchased for windows. 

Thanks in advance.

Hello and Welcome to Ubuntu Forum :)

Thanks for choosing and using Lubuntu!

Two things in Linux I personally avoid: Wubi and Wine. But that is me.

My theory is: For the ultimate expected performance for any application/program, it's better to run that on its native platform. Having that said, Dual-Booting with Windows could be the best option. However, there are other alternatives but nothing is prefect.

I have come across only one case where user had problem with Wine on Lubuntu. Otherwise, it should work.

---

### Post by amjjawad on 2012-01-12
> **carl4926 said:**
> It's worth checking here too
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Not all windows applications will work and or there may be tips and tricks there to help you

+1

That's why (as previously mentioned) Dual-Booting is recommended for the best performance for that application. However, if the application is listed and supported in Wine, then go for it :)

---

### Post by Mark Phelps on 2012-01-12
> **genzwebsolutions said:**
> where IE 8 comes in market then IE 7 is become older one how could that happened again which is not to be remarkable!

Huh?? Anyway ... market forces have nothing to do with it.  

The current version of IE is 9, and version 10 is already in Beta and available for download and use on MS Windows.

WINE, on the other hand, does NOT support versions 8 or newer.  

So, as already mentioned, if the app depends on IE versions 8 or newer, it's not going to work with Wine.

---

### Post by mikechant on 2012-01-12
> WINE, on the other hand, does NOT support versions 8 or newer. 

This person claims to have got it sort of working:
[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

Yes, there are various issues which probably make it unsuitable for general use; but it might do for one specific web based application.

---

### Post by madeel2 on 2012-01-14
> **raja.genupula said:**
> Hi madeel2 , one small Question . you said you got one purchased product right ? ok that thing gonna run everytime or small amount of time & How much big it is ? will it deals with high much amount of RAM  ?

Because I think virtual BOX can help you if you are going to use the app for limited (1- 2 Hrs i think no problem ).So you can wake up that app when ever you want and there will be full functionality to you.

:):)

Yes. It is a purchased product written in visual foxpro. It got installed with wine, however it doesn't come up in the program folder (located in wine:C Drive). In windows too it doesn't show up in program folder but we can create a launcher (short cut in windows) easily. Not sure, how can I do it in lubuntu. Any suggestion?

---

### Post by madeel2 on 2012-01-14
> **mikechant said:**
> This person claims to have got it sort of working:
[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

Yes, there are various issues which probably make it unsuitable for general use; but it might do for one specific web based application.

I almost hate IEx but government website forces one to use internet explorer. I require e-filing sales tax documents every month (usually last week). At the moment, user agent switch seems to work. 

If some feature would be using ActiveX controls, this masking may break down. 

BTW, is there any user agent switcher for chromium browser in lubunutu?

---

### Post by Elfy on 2012-01-14
Thread moved to Wine.

---

