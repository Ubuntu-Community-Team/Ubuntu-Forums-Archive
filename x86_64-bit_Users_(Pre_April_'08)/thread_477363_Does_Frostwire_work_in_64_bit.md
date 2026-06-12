---
title: "Does Frostwire work in 64 bit ?"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by dptxp on 2007-06-18
I need some nice P2P, used Ares Galaxy in Windows.
Does Frostwire work in 64 bit ?

---

### Post by jamesford on 2007-06-18
yup

---

### Post by Kilz on 2007-06-18
> **dptxp said:**
> I need some nice P2P, used Ares Galaxy in Windows.
Does Frostwire work in 64 bit ?

You have to force install it.

---

### Post by jamesford on 2007-06-18
nah, doubleclicking the deb is enough for me

---

### Post by Kilz on 2007-06-18
> **jamesford said:**
> nah, doubleclicking the deb is enough for me

Looks like they fixed that. When I installed it some time ago, you had to force it in. But it worked without adding anything.

---

### Post by dptxp on 2007-06-18
Thanks.
So I shall just go to their site and click on the one and only one Ubuntu i586 version.

---

### Post by jamesford on 2007-06-18
yep

---

### Post by sambehera on 2007-06-20
i got it installed... it shows up in my kmenu under internet... but it disappears after loading for a while... i presume its a java issue... can anybody help me out with the instalation of java? will the default installation from sun's website [the .bin file for x64] work?

---

### Post by Kilz on 2007-06-20
> **sambehera said:**
> i got it installed... it shows up in my kmenu under internet... but it disappears after loading for a while... i presume its a java issue... can anybody help me out with the instalation of java? will the default installation from sun's website [the .bin file for x64] work?

It should.

---

### Post by jamesford on 2007-06-20
i dont recall exactly if this tweak solves this problem, cos its been a long time since i applied, i dont recall what my problem was, anyway
open frostwire.props in your .froswtire dir
find the  line CHAT_IRC_NICK
and change it to CHAT_IRC_NICK=nochat

i guess this disables the chat module, which might be causing the problem
frostwire has behaved perfectly since i did this a few months ago anyway, worth a try

---

### Post by sambehera on 2007-06-21
installed sun java 1.6 and it still did not work.... and i cant seem to find those files you are talking about...

the .frostwire directory and the .props file

i really want to get this gnutella client running on my (k)ubuntu x64:(.... help would be greatly appreciated.

---

### Post by Kilz on 2007-06-21
> **sambehera said:**
> installed sun java 1.6 and it still did not work.... and i cant seem to find those files you are talking about...

the .frostwire directory and the .props file

i really want to get this gnutella client running on my (k)ubuntu x64:(.... help would be greatly appreciated.

If you havent already install[ ia32-sun-java5-bin]("http://packages.ubuntu.com/feisty/libs/ia32-sun-java5-bin"). Then setup a symlink to one of the places frostwire looks for java. Here is the command I used on Dapper. You might have to edit it as the java folder might be named differently at  /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.06 because it adds a version number. I think the version for Feisty is 1.5.0.11.

```
sudo ln -s /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.06 /usr/java
```

Other places frostwire looks for a folder named java are
/usr/lib/ 
/opt/
In case you would rather place the symlink there  instead.

---

### Post by jamesford on 2007-06-21
its a hidden dir...i dont know how to enable viewing of hidden dirs in kde..
maybe 
nano ~/.frostwire/frostwire.props 
will work

---

### Post by sambehera on 2007-06-21
managed to fix it... 

dug into the frostwire forums and searched for "feisty"

got some info about "/usr/lib/frostwire/runFrostwire.sh"

it WAS a java problem as i later found out by running it in terminal... i should have done this in the beginning..

my 64 bit java was installed in /usr/local/java as per the sun installation instructions for x64.. [1.6.0_01]
 
i also had 1.6.0.00 32 bit in  /usr/lib/jvm/ia32-java-6-sun-1.6.0.00/ (for my 32 bit browsers <opera and ff2 x32>)

i thought about adding a line in "runFrostwire.sh"  pointing to the 64 bit java folder or adding a symlink like Kilz had suggested ... i figured i should use the symlink coz there might be java apps i download in the future which might default to < /usr/java>

so eventually i did this

```
sudo ln -s /usr/local/java /usr/java
```

and it worked.. 

thanks a lot for your help guys :popcorn:.... btw i tried real hard to look for .frostwire and frostwire.props but they dont exist in the filesystem...

---

### Post by sambehera on 2007-06-21
sorry .. i did eventually find .frostwire but it was created only after frostwire started correctly...

---

### Post by fakie_flip on 2007-06-22
Anyone figured out how to block the ads in the new Frostwire? I'm trying to find out where they are coming from Wireshark, so I can block them with the /etc/hosts file.

---

### Post by jamesford on 2007-06-22
there are ads in frostwire?
ive never seen any

---

### Post by fakie_flip on 2007-06-23
> **jamesford said:**
> there are ads in frostwire?
ive never seen any

If you have the newest Frostwire, click on "Community Chat", and you will see ads from the internet appearing on the right. If I knew where they were coming from, I could block them.

---

### Post by jamesford on 2007-06-23
oh yeah, its just ads asking u to donate isnt it?
but kinda annoying
never used the chat feature before so didnt see them
but frostwire is gpl isnt it? that should mean that anyone with the skills are allowed to take the code, remove the ads and release it as freezewire or something

---

### Post by dptxp on 2007-06-24
I loved Ares Galaxy. Small download, simple, and absolutely no ads.
I do not like the feel of frostwire, I have it in 32-bit ubuntu on desktop
but am reluctant to load on 64-bit laptop. Now with reports of ads, I am
more discouraged.

---

### Post by fakie_flip on 2007-06-25
I've got Frostwire working great in 64 bit Ubuntu, but I use Ktorrent most of the time instead. It's a much better program for P2P.

---

### Post by benplanet on 2007-07-03
disabling beryl completely has solved the problem for me!!!

wow took a while to figure out .. lol

---

### Post by fakie_flip on 2007-07-05
That's because Frostwire uses the java swing library for its gui. There's a way to get programs that use java swing to work with Beryl. I'm sure you can find out how if you search this forum or google.

---

