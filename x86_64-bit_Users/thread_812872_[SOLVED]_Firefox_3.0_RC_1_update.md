---
title: "[SOLVED] Firefox 3.0 RC 1 update"
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by mhenriday on 2008-05-30
I installed the Update Manager update from **Firefox 3.0 beta 5** to **3.0 RC 1** yesterday, and to my surprise discovered that the **FF 3**-compatible add-ons (14 of the 28 add-ons in total I've been using with **FF 2.0.0.x**) which I had been using on the former no longer worked ; they simply do not appear when the browser is opened, even though no incompatibility notice appears and they are marked as installed under «Tools» &#8594; «Add-ons». All these add-ons work perfectly well with [**_Swiftweasel 3.0 RC 1_**]("http://sourceforge.net/project/showfiles.php?group_id=195473"). Anyone else noticed something similar ? If so, any chance that this bug will be corrected soon ? Some of these add-ons, like Giorgio Maone's **NoScript** and Wladimir Palant's **Adblock Plus** belong to the category «Essential»....

Henri

---

### Post by John Jason Jordan on 2008-05-30
I have been using the FF 3.0 that was installed with the upgrade from Gutsy to Hardy over a month ago. I immediately realized that it had none of my add-ons and extensions. I asked here and discovered that the problem is not FF but the lack of versions for FF 3.0. Since then I have everything working. Have you been to the FF site to see what is currently available?

On a related issue, the other day suddenly some text blocks are appearing huge. I think it is a problem with cascading styles. For example, on the top of the page for this thread it says:

Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories
x86 64-bit Users

The "Ubuntu Forums" line appears normally, but the "x86 64-bit Users" line appears in enormous text. On the page where I am writing this the "Reply to Thread" text also appears in a similar enormous font. And the user names in the threads (e.g. where it says "John Jason Jordan" and "mhenriday") are also really huge. And it's not just Ubuntu sites - a google search page shows the same enormous text where it says "1 2 3 4 5 Next."

I've fiddled with everything I can find, but can't resolve the problem.

Curiously, the upgrade from Gutsy to Hardy left my old FF 2.0 installed. I tried it just now and it also has the same enormous text in various places.

It's really ugly. I hope someone knows what happened and how to fix it.

---

### Post by mhenriday on 2008-05-30
Hullo **John Jason**, and thanks for your reply ! The difficulties I encountered in connexion with the update to **Firefox 3.0 RC 1** are, I repeat, precisely those I described above - _none_ of my add-ons, not even those which functioned perfectly well with **Firefox 3.0 beta 4** and **Firefox 3.0 beta 5** previously provided with **Hardy**, work after the update to **3.0 RC 1**. Interestingly enough, when I upgraded from **Gusty** to **Hardy**, those of my add-ons for which a version compatible with **FF 3** builds had already been released worked from the get go. Since then updated versions for other add-ons have been released, and these all worked for me in **3.0 beta 5**. Thus my surprise - and the inspiration for this thread - when I noticed that no add-ons were working in **3.0 RC 1**....

As a further confirmation that even users running very similar systems don't always observe the same phenomena, I note that I don't see the text problems you describe above (see the attached screenshot). You observe them using both **FF 2.0.0.x** and **FF 3.0** pre-release browsers ; have you tried the **_Swiftweasel_** builds to which I provide a link, *supra* ? My experience over the past couple of years is that they work better with **Ubuntu** than the ubuntuised **Firefox** builds....

Henri

---

### Post by twright on 2008-05-30
RC1 doesn't seem to be in my repos

---

### Post by cubeist on 2008-05-30
> **twright said:**
> RC1 doesn't seem tp be in my repos

Not to point out the obvious, but, change your repositories to the main server (usually updates first) and enable proposed/backports (not sure which one RC1 stems from)...

---

### Post by philinux on 2008-05-30
It's in proposed.

---

### Post by twright on 2008-05-30
i already had RC1 from a ppa with done of the mentioned problems :), just wondering how they had got it

---

### Post by mhenriday on 2008-06-14
Still more problems with the **FF3** builds ! As can be seen from the attached screendump, I have the latest build, **3.0nobinonly-0ubuntu0.8.0.4.1** (as well as old faithful, 2.0.0.14) installed om my box, but when I click «Applications» &#8594; «Internet» &#8594; «Firefox browser», it is still a defective version (e g, without updated add-ons) of **Firefox 3.0 beta 5** which loads. The same thing happens when I enter ```
firefox
``` in a terminal. I've uninstalled and re-installed *ad nauseam*, but have had no luck in getting the **Firefox** version whichSynaptic insists, is in fact installed on my box to display on my screen ! Installation failures in **Firefox** are, as we know, often due to corrupt extension files in the profiles folder, but look as I might under «home/.mozilla», I haven't been able to find that elusive folder. Any suggestions as to what can be going on here ?...

Henri

---

### Post by mhenriday on 2008-06-17
Interested parties - if there be any - are directed to [this thread]("**_http://ubuntuforums.org/showthread.php?p=5204291#post5204291_**"). Many thanks to those who posted here !...

Henri

---

### Post by John Jason Jordan on 2008-06-17
> **mhenriday said:**
> Interested parties - if there be any - are directed to [this thread]("**_http://ubuntuforums.org/showthread.php?p=5204291#post5204291_**"). Many thanks to those who posted here !...Henri
Your link is slightly wrong. Here is the correct link:

[[/B]"]http://ubuntuforums.org/showthread.php?p=5204291#post5204291[/U][/B]]("http://ubuntuforums.org/showthread.php?p=5204291#post5204291[/U)

---

