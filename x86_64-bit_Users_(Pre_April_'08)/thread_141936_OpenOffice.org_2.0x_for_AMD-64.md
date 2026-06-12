---
title: "OpenOffice.org 2.0x for AMD-64?"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-03-09
When I first installed Breezy last year I was pleased that Synaptic finally listed OpenOffice.org 2.0 -- except that it was really 1.9.129. And that's still all that I find in Synaptic. Version 1.93 is reasonably stable, but there are some fixes and new features in the final 2.0. Is there any way to get the latest 2.02 version for 64-bit Breezy?

---

### Post by bonzodog on 2006-03-09
2.02 is now in Dapper, so you could upgrade to that...

---

### Post by John Jason Jordan on 2006-03-09
[QUOTE=bonzodog]2.02 is now in Dapper, so you could upgrade to that...[/QUOTE]
First, Dapper is not official yet, is it? And second, I'm not doing anything that major with finals coming week after next. Maybe during spring break. And third, if there is a 64-bit version of 2.02 available in Dapper, I don't understand why it can't be made available in Breezy as well. I just assumed that it was not available because no one had compiled it for AMD-64. Does it depend on things that Breezy doesn't have or can't do?

---

### Post by alesdoc on 2006-03-10
add this line

deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./

to your repositories. You will have the final stable version 2.0 of openoffice.

This repository come from the devel-list.

---

### Post by John Jason Jordan on 2006-03-10
[QUOTE=alesdoc]add this line

deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./

to your repositories. You will have the final stable version 2.0 of openoffice.

This repository come from the devel-list.[/QUOTE]
Thanks!

Unfortunately, it doesn't quite work. I added the above repository via Synaptic (Settings menu item), rather than directly editing the sources list. As soon as I did and updated Synaptic all my OpenOffice.org applications showed as upgradeable, plus the Upgrade icon in my Gnome panel came on. "Cool," I thought. "I'll just do the Upgrade icon in the panel rather than hunt through Synaptic."

So I shut down Synaptic (because from past experience direct stuff won't work if there is another installation tool open), and clicked on the Upgrade icon in the panel. This brought up a dialog box with list of all the OpenOffice.org files to upgrade. I told it to go ahead. And that's where it bombed. I got a long list of "we failed to fetch" error messages -- one for each OO.o file that was to be upgraded.

So I'm close, but not smoking the cigar quite yet. As I write this the Upgrade icon is still in the panel. But there must be something wrong with the repository I added. Any ideas?

---

### Post by alesdoc on 2006-03-11
I think i can't help you.

I use this repository four month ago and it works fine. Maybe you can try using aptitude.

From a console:

sudo aptitude

than click on "u" (update). If you have packages that have to be upgraded you will see a message on your window...something like that: "Upgradable packges". Click "shift+u" that "g" (now you can see the packges, that will be upgraded) and than "g". Maybe you wil receive a message such as....these packages are untrusted or something like that....you have only to proceed with the installation.

Try it

---

### Post by John Jason Jordan on 2006-03-11
[QUOTE=alesdoc]I think i can't help you.
I use this repository four month ago and it works fine. Maybe you can try using aptitude.
Try it[/QUOTE]
I just tried it again from the Upgrade icon in the panel. Still getting the error message:

W: Failed to fetch [http://people.ubuntu.com/~doko/OOo2-amd64/./openoffice.org2-l10n-en-us_2.0.1-0breezy1_all.deb](http://people.ubuntu.com/~doko/OOo2-amd64/./openoffice.org2-l10n-en-us_2.0.1-0breezy1_all.deb)
  404 Not Found

This was the first error message  -- there was one for each OO.o module to be upgraded. Note the "404 Not Found" at the end of each error message. Doesn't this mean that the URL is bad?

Then I tried aptitude, but I couldn't figure out what it was telling me, so I left it alone. Besides, if the URL in the sources list is bad, aptitude won't be able to find it either.

And then I tried via Synaptic and got the same error message -- "W: Failed to fetch."

What I don't understand is why Synaptic found the packages as soon as I added the URL to the sources list, but when I go to install them it can't find them.

---

### Post by kaamos on 2006-03-11
Have you hit reload in synaptic or done a "sudo apt-get update" ?

---

### Post by John Jason Jordan on 2006-03-11
[QUOTE=kaamos]Have you hit reload in synaptic or done a "sudo apt-get update" ?[/QUOTE]
Yes, I did that right after adding the repository. And I did it again just now. Still getting the same error messages.

---

