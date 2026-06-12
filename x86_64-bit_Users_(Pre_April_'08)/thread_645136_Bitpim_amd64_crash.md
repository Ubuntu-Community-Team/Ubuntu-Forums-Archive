---
title: "Bitpim amd64 crash"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdean on 2007-12-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/177569](https://bugs.launchpad.net/ubuntu/+source/bitpim/+bug/177569) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The error, generated when Bitpim was loading my list of contacts from the phone to merge with my previous list:

```
BitPim version: 1.0.0-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/phonebook.py", line 1481, in Draw
    text, font=self.facename, size=self.facesize)
  File "/usr/share/bitpim/code/bphtml.py", line 490, in drawhtml
    hdc.Render(rect.x, rect.y, 0, False)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/html.py", line 1265, in Render
    return _html.HtmlDCRenderer_Render(*args, **kwargs)
TypeError: Sequence of integers expected.

Variables by last 8 frames, innermost last

Frame Draw in /usr/share/bitpim/code/phonebook.py at line 1481
           attr =  <wx.grid.GridCellAttr; proxy of <Swig Object of type 'wxGridCellAttr *' at 0x40a
           text =  u'<font color="#101010">48368</font>'
         colour =  wx.Colour(16, 16, 16, 255)
             dc =  <wx._gdi.PaintDC; proxy of <Swig Object of type 'wxPaintDC *' at 0x7fffb7297b60>
           self =  <phonebook.ImportCellRenderer; proxy of <Swig Object of type 'wxPyGridCellRender
     isSelected =  0
        rowtype =  1
           grid =  <wx.grid.Grid; proxy of <Swig Object of type 'wxGrid *' at 0x3e5f3b0> >
            col =  4
           rect =  wx.Rect(320, 682, 80, 22)
            row =  31

Frame drawhtml in /usr/share/bitpim/code/bphtml.py at line 490
       basepath =  ''
             dc =  <wx._gdi.PaintDC; proxy of <Swig Object of type 'wxPaintDC *' at 0x7fffb7297b60>
           html =  u'<font color="#101010">48368</font>'
            hdc =  <wx.html.HtmlDCRenderer; proxy of <Swig Object of type 'wxHtmlDCRenderer *' at 0
           rect =  wx.Rect(322, 683, 76, 20)
              x =  1.6000000000000001
           font =  u'FreeSans'
      origscale =  (1.0, 1.0)
           size =  10

Frame Render in /usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/html.py at line 1265
           args =  (<wx.html.HtmlDCRenderer; proxy of <Swig Object of type 'wxHtmlDCRenderer *' at 
         kwargs =  Keys []
                   {}

```

The solution is to download the newest i386 deb from Bitpim's Sourceforge repository and install it with dpkg:

```
sudo dpkg -i --force-architecture bitpim##########.deb
```
[size=1](Obviously, replace the #s with the full name of the package, probably best done using tab completion).[/size]

This should probably be fixed.

---

