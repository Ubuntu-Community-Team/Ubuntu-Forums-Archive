---
title: "Problem in Wine with Kurdish fonts"
date: 2015-06-29
forum: Wine
---

### Post by Hezha on 2015-06-29
[COLOR=#111111][FONT=Ubuntu]when I install Wine on Ubuntu 15.04 I have a problem with my fonts.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have downloaded all Winetricks fonts, but this has not fixed my font problem.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How can I remove all Wine fonts? Or how can I fix my problem?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I want my fonts back to the way they were before I installed Wine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the picture of my problem:[/FONT][/COLOR]
[IMG]http://i.stack.imgur.com/2LIJl.png[/IMG]

[IMG]http://i.imgur.com/9MI9I9R.png[/IMG]

---

### Post by tgalati4 on 2015-06-30
I'm not familiar with Kurdish, but is your problem related to the "kerning" or spacing between the letters?

To see what font-related programs are on your system, open a terminal:

```
apropos font
```

To see what fonts you have on your system:

```
fc-list
```

To see any fonts with "Kurdish"

```
fc-list | grep Kurdish
```

There are several commands:  fc-scan, fc-query, fc-match.

The frameworks used to store, organize and render fonts is complicated, so if you are having a font problem, it helps to read about how fonts are handled in Ubuntu:  [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Was the Kurdish font rendered correctly before you installed WINE?  What version of WINE?  Perhaps you need to latest version from [http://winehq.org](http://winehq.org)

---

### Post by Hezha on 2015-06-30
> **tgalati4 said:**
> I'm not familiar with Kurdish, but is your problem related to the "kerning" or spacing between the letters?

To see what font-related programs are on your system, open a terminal:

```
apropos font
```

To see what fonts you have on your system:

```
fc-list
```

To see any fonts with "Kurdish"

```
fc-list | grep Kurdish
```

There are several commands:  fc-scan, fc-query, fc-match.

The frameworks used to store, organize and render fonts is complicated, so if you are having a font problem, it helps to read about how fonts are handled in Ubuntu:  [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Was the Kurdish font rendered correctly before you installed WINE?  What version of WINE?  Perhaps you need to latest version from [http://winehq.org](http://winehq.org)
..........

thanks bro for your replay, but your information not fix my problem yet :(

---

