---
title: "Index a .chm help file quickly and efficiently with a script - possible?"
date: 2013-01-30
forum: Wine
---

### Post by ntzrmtthihu777 on 2013-01-30
Hello Ubuntu collective!

Just learned the technique of creating .chm help file, cranked out a Ruby Scripting guide using it and am amazed at how tiny the resultant file is. The reason I learned is because, to be quite frank, the rpg maker community I am also a member of is rooted in windows as RPG maker cannot run under wine even (I use a virtual machine) and the format is a convenient method of documenting projects, considering you need windows anyway so may as well take advantage of the tools available.

Problem is the indexing ](*,) so many pages, so many keywords OTZ its too much to do by hand... 

And so I turn to the collective wisdom of the masses, as this is beyond my current skills. The file is in essence an xml file, containing the keyword and help page info. some sample text is below:
```
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<HTML>
<HEAD>
<meta name="GENERATOR" content="Microsoft&reg; HTML Help Workshop 4.1">
<!-- Sitemap 1.0 -->
</HEAD><BODY>
<UL>
    <LI> <OBJECT type="text/sitemap">
        <param name="Name" value="Bar">
        <param name="Name" value="Ruby.new">
        <param name="Local" value="intro.html">
        <param name="Name" value="Interactive Ruby Shell">
        <param name="Local" value="irb.html">
        </OBJECT>
    <LI> <OBJECT type="text/sitemap">
        <param name="Name" value="Foo">
        <param name="Name" value="Contents">
        <param name="Local" value="index.html">
        </OBJECT>
</UL>
</BODY></HTML>

``` where foo and bar are keywords, and the *.html files are individual pages in the help file, and the non-keyword strings are the titles of the page.

I am thinking something that can count occurances of uncommon words (no of, the, a, is, etc) within the *.html files and make a list indexed by filename, the internal title (always withine <h1></h1> tags).

Anyone got the chops to do it? It is, as I said, beyond me at the moment, but I will still have a shot at it. Maybe I'll figure it out before someone posts a response.

---

### Post by ntzrmtthihu777 on 2013-02-01
Seems I figured a way, but it will not likely be applicable to all situations because I already found an index to the site I compiled it from.

---

