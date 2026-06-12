---
title: "wine woes, nvidia driver, no text"
date: 2008-11-10
forum: Wine
---

### Post by Amerinidiot1231 on 2008-11-10
I have managed to correct all of my critical ibex issues after upgrading; however there is on my next highest priority a wine issue.  I nearly leaped in joy after I succeeded in getting my nvidia driver (version 96, geforce4 mx 440 agp8x), until I fired up wine.  I have no text visible in any wine program including wine config.  Here are some visual combos I have come up with.

-With nvidia driver & desktop effects:  No text
-With nvidia driver : jumbled text 
-No driver: All clear text (but no direct3d because no driver)

*Ibex 8.10
*wine 1.0.1
Any ideas?

---

### Post by Amerinidiot1231 on 2008-11-11
fixed

[http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf](http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf)

---

### Post by SqRt7744 on 2008-11-24
any idea how to get this to work with picasa? It runs its own implementation of wine without regards to the settings in your wine folder registry....

ok i found the solution on a Russian page:
[http://translate.google.ca/translate?hl=en&sl=ru&u=http://mike4people.blogspot.com/2008/11/wine-picasa.html&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3D%2522ClientSideWithRender%2522%253D%2522N%2522%2Bpicasa%26hl%3Den%26sa%3DG](http://translate.google.ca/translate?hl=en&sl=ru&u=http://mike4people.blogspot.com/2008/11/wine-picasa.html&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3D%2522ClientSideWithRender%2522%253D%2522N%2522%2Bpicasa%26hl%3Den%26sa%3DG)

basically just add the line
"ClientSideWithRender" = "N"
to the bottom of ~/.google/picasa/3.0/user.reg

..and it will work.

---

