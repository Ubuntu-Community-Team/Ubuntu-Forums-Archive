---
title: "Uninstall Ubuntu 7.04 64Bit"
date: 2007-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by DB6150 on 2007-09-29
Hello, 

I am having an issue similar to many i searched far , but a little diffrent 
i installed Ubuntu linux 7.04 64bit onto my secondary 250Gb harddrive 
I have xp professonal 32bit on my primary 160GB drive 
i tried formattting to clear the drive with ubuntu and i get an error when i boot with gnome and  i cannot load any os. 
so what i did was reinstall linux to the 250gb harddrive and then booted into xp pro and looked around for ways to remove ubuntu . here is my issue

I do not have XP restore cd's 
and command.exe does not work when i type run in -( was a way i read to do at another forum) 

so if anyone could help , it would be appriciated

thanks in advance 

Dylan

---

### Post by Kilz on 2007-09-29
Just a question. Why do you want to uninstall Ubuntu?

---

### Post by cinajohn on 2007-09-29
So what execatly are you trying to do?...Just uninstall ubuntu completely and have use of the HD space?

---

### Post by DB6150 on 2007-09-29
im uninstalling it because it is alot more difficult to do normal things than windows is , windows works better with my server setup and i just dont have the time to learn a new os .  
and  i want to use the hard drive linux is on to house xp because my xp drive is giving signs of death .

---

### Post by DB6150 on 2007-09-29
im uninstalling it because it is alot more difficult to do normal things than windows is , windows works better with my server setup and i just dont have the time to learn a new os .  
and  i want to use the hard drive linux is on to house xp because my xp drive is giving signs of death .

---

### Post by rsambuca on 2007-09-29
This will do it for you.

[http://ubuntuforums.org/showpost.php?p=3075438&postcount=1](http://ubuntuforums.org/showpost.php?p=3075438&postcount=1)

---

### Post by DB6150 on 2007-09-29
Thank you so much for the assitance 

i will still contiunue to use ubuntu on my older desktop when i have the spare time , because it is a very nice os on older machines 


Thanks

---

### Post by Kilz on 2007-09-29
Ubuntu is even better on new computers. XP is so, so , bland and cant be configured as much. Id never be able to change Windows like I did Ubuntu (Screenshot).
Not to mention all the inferior applications you have to use with Windows that actually cost you money! To bad your first post wasnt to ask questions, but to ask how to uninstall.

---

### Post by DB6150 on 2007-09-30
well when ubuntu actually becomes worth my time  and is able to run all of my applications with out using extra programs to modify them . but since i doubt that will happen for a long time. windows will continue to control my systems.

---

### Post by Kilz on 2007-09-30
> **DB6150 said:**
> well when ubuntu actually becomes worth my time  and is able to run all of my applications with out using extra programs to modify them . but since i doubt that will happen for a long time. windows will continue to control my systems.

When Ubuntu runs what applications? Windows ones? Why would it, and how do you know it doesnt when the first post to the forums wasnt to ask questions, other than how to uninstall. You might want to take a look at some of the icons in that screenshot. 
New users who want to cling to windows applications are kind of setting themselves up for failure.
Have fun in virus/malware city.  :D

---

### Post by DB6150 on 2007-09-30
i know ubuntu cannot run these programs because they are not designed for anything but the windows xp professonal platform ... i know this because i help design the programs for my work for monitoring server systems over the web. 
believe what you want about windows... but it still controls over 96% of the pc market ... what does linux control .60%  

but im not going to fight about it ... linux is a great os.. but when it cant do what i need it to do , i can only use it in certain places, like older machines....

---

### Post by Kilz on 2007-09-30
> **DB6150 said:**
> i know ubuntu cannot run these programs because they are not designed for anything but the windows xp professonal platform ... i know this because i help design the programs for my work for monitoring server systems over the web. 
believe what you want about windows... but it still controls over 96% of the pc market ... what does linux control .60%  

but im not going to fight about it ... linux is a great os.. but when it cant do what i need it to do , i can only use it in certain places, like older machines....

You know this because you asked questions, right? You tried, that wasnt your first post asking how to uninstall, right? The forum software must be malfunctioning and put that as your first post, right?  :roll:

---

### Post by DB6150 on 2007-10-01
i know it wont run  my work software because i designed it not to as it causes major issues with our server which i know it soooo bad , but it runs windows , ill admit linux is a far better server os than win , but then again ..... it cant run our factory the way windows can :(. 

But i fixed my drive issue and recently orderd a new 80gb drive for my main machine and it will house linux for me to learn on ... i just mainly couldent have it on  that drive

---

### Post by HilliBilly on 2007-10-02
@kilz

how did you get this transparent system monitor on your desktop?

---

### Post by Kilz on 2007-10-02
> **HilliBilly said:**
> @kilz

how did you get this transparent system monitor on your desktop?

[Thats conky. ]("http://conky.sourceforge.net/"), there is a package in the repos. But configuring it is a job in itself.

---

### Post by HilliBilly on 2007-10-02
(i know it's of the topic, sorry to the thread owner)

conky rocks. but you're right, configuration seems to be 'sophisticated'. first i filled up my desktop with several system monitors (didnt want that, dont know why it happened), later on i somehow killed my desktop with the .conkyrc sample file, nothing disappeared anymore, had to restart. is your's running stable?

---

### Post by John.Michael.Kane on 2007-10-02
> **HilliBilly said:**
> (i know it's of the topic, sorry to the thread owner)

conky rocks. but you're right, configuration seems to be 'sophisticated'. first i filled up my desktop with several system monitors (didnt want that, dont know why it happened), later on i somehow killed my desktop with the .conkyrc sample file, nothing disappeared anymore, had to restart. is your's running stable?


These should help you.
[Howto: Get a beautiful Conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")
[HowTo: Conky hddtemp]("http://ubuntuforums.org/showthread.php?t=282353&highlight=conky")
[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

Note: after you install conky you can use the command below to extract a basic conky.rc.
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

Then run
```
gedit ~/yourname/.conkyrc
```

---

### Post by rsambuca on 2007-10-02
It might be easier to go by some other peoples' conky setups.  Check out [this thread]("http://ubuntuforums.org/showthread.php?t=281865") for the desktop and setups.

---

