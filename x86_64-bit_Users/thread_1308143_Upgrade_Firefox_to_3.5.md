---
title: "Upgrade Firefox to 3.5"
date: 2009-10-16
forum: x86 64-bit Users
---

### Post by netlaptop on 2009-10-16
> **running_rabbit07 said:**
> You may also try downloading the install file from mozilla.com and moving it from your desktop to your Home folder, then copy and paste this command in a terminal. ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```A lot of wording there, but easy to copy and paste.

Which is pretty much the same thing the AYSIU's site says to do.

I also wanna upgrade Firefox to 3.5.x. I am running Ubuntu 64 bits, should the same above method work?

Thanks.

---

### Post by disophisis on 2009-10-16
> **running_rabbit07 said:**
> You may also try downloading the install file from mozilla.com and moving it from your desktop to your Home folder, then copy and paste this command in a terminal. ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```A lot of wording there, but easy to copy and paste.

Which is pretty much the same thing the AYSIU's site says to do.

Thanks for this.

---

### Post by aysiu on 2009-10-16
> **netlaptop said:**
> I also wanna upgrade Firefox to 3.5.x. I am running Ubuntu 64 bits, should the same above method work?

Thanks.
It may not. I don't have 64-bit so can't test it myself.

---

### Post by caue.rego on 2009-10-16
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) ? really? It (seems like it) doesn't even have a date to know if it's outdated, although it talks about Firefox 3.5

C'mon, I could follow those steps no big problem, but that ain't simple. I'm astonished on how complicated it is to just upgrade firefox. Can't recall of this being that difficult before.

I did like the op and **installed 3.5 from synaptic**, actually after trying to follow the warning to upgrade which lead me to this page [http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html) and a packed file which I could not install! So now I also have that weird-looking Shiretoko along with Firefox 3.0

Plus on Synaptic it's even weirder that there are the 3.6 and 3.2 with support from Canonical while the 3.5 does not!

Granted, all un-information aside, it did a pretty nice job copying my profiles and add-ons (still except google gears, but that's a case apart), tho, and I just had to update my icons on the panel - but - why it just didn't upgrade the "firefox" package along with the update manager? Why changed the name just on linux? - I had no problem upgrading firefox on mac and windows, since I actually use all of them.

Look, I understand Ubuntu, and love it, but I can see no reason for this getting so complicated **and** unexplained on the process itself.

edit: just wanted to clarify - I wrote this only to express an opinion, after the long ride to do something that should be even simplier than it already is once we know about it a little more than what's displayed on the regular upgrade method.

But, since I'm here, let me give someone a hand...

> **aysiu said:**
> It may not. I don't have 64-bit so can't test it myself.

I don't know about the method, but I'm on 64 bit and it's all right to just **install from synaptic the 3.5 package**. And then look for **Shiretoko** on the Applications / Internet menu. That's about it. All your stuff will work just as fine as you would expect from an upgrade, except 3.0 will still be installed.

---

### Post by aysiu on 2009-10-16
> **caue.rego said:**
> [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) ? really? It (seems like it) doesn't even have a date to know if it's outdated, although it talks about Firefox 3.5 It talks about Firefox 3.5 because it isn't outdated. Firefox 3.5 came out in, what, early August? There hasn't been a new Ubuntu release since early August, so obviously it's up to date.

> C'mon, I could follow those steps no big problem, but that ain't simple. Of course it's simple. Open a terminal using your mouse. Highlight the text with your mouse. Copy and paste with your mouse. Please explain what's so difficult about it? > I'm astonished on how complicated it is to just upgrade firefox. Can't recall of this being that difficult before. It's always been this "difficult" before, because Ubuntu is designed to upgrade package versions every six months. So if you decide to upgrade one package on your own before six months, you have to use weird workarounds for it.

If you have a problem with waiting six months for new software or with doing weird workarounds to get new software sooner, then you should be using a rolling release distro (PCLinuxOS, Debian, Arch).

---

### Post by Yellow Pasque on 2009-10-16
It's not difficult at all; I'll repeat it:
> Do not use physchocats or ubuntuzilla if you're on 64-bit Ubuntu (they install a 32-bit browser). Simply install firefox-3.5 package. One more trick to make Shiretoko compatible with sites that check the user agent: start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the general.useragent.extra.firefox key. Modify the Shiretoko part of this key to say Firefox. You may need to restart the browser for the change to take effect.

---

### Post by caue.rego on 2009-10-17
You both missed my point and I don blame ya. It was a very long (and difficult) post and I'd miss my point too! :P

You both say it's not difficult **to you**. It's not all that difficult **to me** either. I can understand that, and I've tried to illustrate it. **But it's not natural to its own environment**! Thus it becomes hard to comprehend unless you do some research. And I think although Linux is great for it always can be further researched to make any tweaks you may dream, even if that comes at great price of spending much time learning about it, research should not be obligatory to keep the system updated.

The upgrade system with centralized sources is so great that we get used to not worry about keeping the system updated, and the browser is the main point on it. When there comes this and it changes firefox name among other things I've said before, it all gets confusing, complicated. Difficult!

I'll just give up to try to explain further after this. Too much effort for no results. :D

But I do hope you get the point this time.


Sorry if I offended you, **aysiu**, and I have no idea what you meant about other distros.

Finally, thanks for the (repeated) hint on the useragent, **Temüjin** (although I haven't had any problems with it so far)!

---

### Post by lovinglinux on 2009-10-17
> **caue.rego said:**
> You both missed my point and I don blame ya. It was a very long (and difficult) post and I'd miss my point too! :P

You both say it's not difficult **to you**. It's not all that difficult **to me** either. I can understand that, and I've tried to illustrate it. **But it's not natural to its own environment**! Thus it becomes hard to comprehend unless you do some research. And I think although Linux is great for it always can be further researched to make any tweaks you may dream, even if that comes at great price of spending much time learning about it, research should not be obligatory to keep the system updated.

The upgrade system with centralized sources is so great that we get used to not worry about keeping the system updated, and the browser is the main point on it. When there comes this and it changes firefox name among other things I've said before, it all gets confusing, complicated. Difficult!

I'll just give up to try to explain further after this. Too much effort for no results. :D

But I do hope you get the point this time.


Sorry if I offended you, **aysiu**, and I have no idea what you meant about other distros.

Finally, thanks for the (repeated) hint on the useragent, **Temüjin** (although I haven't had any problems with it so far)!

This has been discussed already over and over. Firefox, is always updated, with security releases. The upgrade from Firefox 3.0.x to 3.5.x is a whole different story, since it's a major upgrade of Firefox code and involves not only security patches but also feature changes. This kind of update only occurs in Ubuntu when a new Ubuntu version is released. If you want to have major releases of Firefox in your Ubuntu, then you need to do it manually or move to a rolling distro.

---

### Post by fingret on 2009-10-18
[http://ubuntuforums.org/showthread.php?t=1225754](http://ubuntuforums.org/showthread.php?t=1225754) 

Works great for 64bit

---

### Post by Yellow Pasque on 2009-10-18
Nvm

---

### Post by tridentblack on 2009-10-24
> **aysiu said:**
> It talks about Firefox 3.5 because it isn't outdated. Firefox 3.5 came out in, what, early August? There hasn't been a new Ubuntu release since early August, so obviously it's up to date.

 Of course it's simple. Open a terminal using your mouse. Highlight the text with your mouse. Copy and paste with your mouse. Please explain what's so difficult about it?  It's always been this "difficult" before, because Ubuntu is designed to upgrade package versions every six months. So if you decide to upgrade one package on your own before six months, you have to use weird workarounds for it.

If you have a problem with waiting six months for new software or with doing weird workarounds to get new software sooner, then you should be using a rolling release distro (PCLinuxOS, Debian, Arch).

I relate to the person you're responding to here. I've had similar experiences being unable to upgrade Firefox. Eventually I gave up, and just installed a Firefox 3.5 without the aid of synaptic, just by downloading it from Mozilla and installing it in my home dir. I had to manually set up new links to it on the top bar. 

So far Firefox is the ONLY program I do this with, I've been happy with Synaptic in every other way. The issue here is that the browser is probably the most threatened piece of software on my computer, so I feel unnerved seeing I'm running 3.0.14 when the current version is 3.5.3, and having heard how important these security updates can be. I'm also unnerved when I see the 'Check for Updates' choice disabled from the help menu, knowing this is part of how Firefox responds to new security threats. 

Maybe 3.0.14 is secure, I don't know. But I find it unerving that it seems cut off from Mozilla.

---

### Post by nanotube on 2009-10-27
> **aysiu said:**
> It may not. I don't have 64-bit so can't test it myself.

Hey aysiu
your method /will/ work on 64bit ubuntu, but requires some additional 32bit compatibility libraries, and some fiddling with the plugins to get them to work.

Check out the ubuntuzilla faq for 64bit users for details - everything there should be directly applicable to your 'psychocats' method, since both it and ubuntuzilla do the same thing.

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users)

---

### Post by phillw on 2009-10-27
Gee... I guess I've been lucky.... A couple of months back, firefox changed into Shietoko (I just accept updates) - It was a WTF moment for me !!

However, it's been perfectly behaved, never put a foot wrong, supports NoScript, WOT, Web Developer... etc, etc....

It's locked up on 3 occaisions - when my mate had his IRC server all messed up & I was using ChatZilla.

Apart from that, it's been great to use. The ONLY issue EVER I've had with it, and I've mentioned this before, is on sites that are badly written and don't comply with the standards that they claim to, and I can hardly blame the browser for being unhappy with a site that reports some 200 errors in it's html code !!!

I'll kinda miss Shiretoko when it reverts back to FF in koala ( I know it's the same engine), it's been a loyal and un-erring servant to me, as I write, test & debug my sites - The Web Developer is an awesome add-on !!!

Just my tuppence-worth.

Regards,

Phill.

---

