---
title: "Photoshop 8 cs works brilliantly - menu fonts distorted"
date: 2008-11-10
forum: Wine
---

### Post by ade234uk on 2008-11-10
Photoshop 8 CS works brilliantly. Better than I expected. The only issue I have is with some of the menu fonts. They look all distorted. Does anyone know how to fix this issue?

Take a look at my screenshot.

---

### Post by dyssident on 2009-01-17
Apparently the Tahoma font is missing from wine, so Photoshop reverts to a junky system font. Just download this font

[http://www.dsource.org/projects/bindings/browser/trunk/freetype/examples/Tahoma.ttf?format=raw](http://www.dsource.org/projects/bindings/browser/trunk/freetype/examples/Tahoma.ttf?format=raw)

and copy it to /home/<yourusername>/.wine/drive_c/windows/fonts.

An explanation is here: [http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml](http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml)

---

