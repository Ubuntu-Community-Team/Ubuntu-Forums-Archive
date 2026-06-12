---
title: "[SOLVED] Firefox 3.0 not loading"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by mhenriday on 2008-06-12
All the hype regarding **Firefox 3.0** (or **Firefox 3.0 RC 3**, depending upon how it is to be termed) makes me want to try it on my 64-bit setup. Alas, I haven't been able to make it beyond **Firefox 3.0 beta 5**, despite installing all the repository updates : when I look at «Synaptic», it would seem that **Firefox 3.0** has been duly installed (cf the first attached screenshot, below ; it will be noted that FF 2.0.0.14 is installed as well), replacing **RC 2**, which. like **RC 1**, I never was able to get on screen, but when I attempt to open the browser, I see **FF 3.0 beta 5** (cf screenshot #2). I am also unable, for example, to update my **FF** add-ons ; despite the usual notice that updates will be installed after rebooting **FF**, nothing happens. When I check the «Error Console» (cf screenshot #3), I see a great number of «warnings» which, unfortunately, I find distinctly unhelpful. This is not a vital problem for me, as I generally run **Swiftweasel**, a «Ubuntuised» version of **Firefox** which I find both speedier and more reliable than the **FF** included in the repositories, but I should dearly like to know what is going on. Any suggestions, particularly those which can lead to the problem being resolved, would be greatly appreciated....

Henri

---

### Post by Kilz on 2008-06-12
For linux users, RC3 is RC2. The only difference in RC3 is a [patch for the Mac osx]("http://wiki.mozilla.org/QA/Firefox3/TestResults/RC3#Firefox_3_RC3_Test_Results"). You might want to purge the install. That is right click on Firefox 3 in synaptic and tell it to remove everything. Then try and reinstall it.

---

### Post by mhenriday on 2008-06-13
Thanks, **Kilz**, for your speedy reply ! And let us hope that **RC 2** = **RC 3** (for **Linux** users) will also be **Firefox 3.0**, which is now scheduled tol be released to the general public on 17 June ! A lot of people have been waiting for this upgrade, which incorporates significant improvements in the **FF** browser....

As to my own particular problem with the release candidates, one of the first things I did when I discovered that the update from **3.0 beta 5** to **3.0 RC 1** had failed was to uninstall in Synaptic and then reinstall, alas to no avail. I repeated the procedure for **RC 2** and again for **Firefox 3.0+nobinonly-0ubuntu0.8.04.1** packages, but with no more success ; i e, after re-installation I still get a defective (add-ons cannot be updated) **beta 5** version. The first screendump below shows the relevant display in Synaptic, after these **FF-3**-related packages have been uninstalled....

I suspect that what needs to be done is to delete corrupt extension files from my Mozilla Firefox profile folder, in accordance with the [_instructions_]("http://tinyurl.com/3ct3hu") presented in the ***MozillaZine Knowledge Base***. Unfortunately, I haven't been able to locate this folder, which, according to the [_same source_]("http://tinyurl.com/yrnlxz"), is supposed to be found at **~/.mozilla/firefox/<profile folder>** When I open **~/.mozilla/firefox/** (Screenshot # 2 below), I see no «profile folder». Under **~/.mozilla/**, I do see a folder named «**extensions**», which contains an (empty) sub-folder with the preposessing - but hardly enlightening - name «**ec8030f7-c20a-464f-9b0e-13a3a9e97384**» (Screenshot #3 below)). I hoped that removing this folder and then re-installing the **FF-3**-related packages, would get me **FF 3.0**, but no joy - what I saw under «Application» &#8594; «Internet» was the same defective **FF 3.0 beta 5** (and the mysterious subfolder that I had deleted was now back again....

I've been considering trying to use ```
apt-get --purge remove
``` to see if this would prove more effective than simply uninstalling via Synaptic, but I'm not certain how to write the command in such a manner as to leave the **Firefox 2.0.0.14** builds unaffected. Perhaps ```
apt-get --purge remove Firefox 3.0+nobinonly-0ubuntu0.8.04.1
```would do ? Or should I try something else entirely ? As mentioned in my posting above, I should be most grateful for any suggestions....

Henri

---

### Post by mhenriday on 2008-06-17
Serendipity is a wonderful thing : I checked my **/opt** folder with regard to another matter entirely, and noticed that a subfolder called «Firefox_3.0beta5» was found there. Thinking that, despite the fact that the folder was empty, it might just possibly be interfering with the loading of the **FF3** build which had been installed from the proposed repository, I removed it with the «rm -r» command, uninstalled all **FF3**-related files in Synaptic, and then re-installed them. Lo and behold, I now have a fully functioning **FF 3.0** browser, and all my FF3-compatible add-ons are working. Sometimes one does luck out !...

Henri

---

