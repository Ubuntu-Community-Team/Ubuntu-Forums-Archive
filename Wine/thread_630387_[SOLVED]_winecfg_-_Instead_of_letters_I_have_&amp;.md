---
title: "[SOLVED] winecfg - Instead of letters I have &amp;quot;:::&amp;quot; ??"
date: 2007-12-03
forum: Wine
---

### Post by b0rka7a on 2007-12-03
For the first time I have such a problem. I've attached a screenshot of winecfg and I hope you guys can help me out solving it :). My home PC is in English and there is no problem, but this PC is in Bulgarian. Only Wine 0.9.50 shows the font that way. Wine 0.9.46 shows it normal (I've tried only these two versions of Wine).

This is a 64-bit PC, and one friend of mine have the same problem with a 32-bit PC
(I mean, I don't think the type of the distro matters)

Thanks in advance! :)

---

### Post by cogadh on 2007-12-03
Wow, that's freakin' weird! :shock:

Usually when Wine encounters a text or language issue like that, the only way to fix it is to delete the .wine directory and start over again. However, it might be worth it to just rename the .wine directory, then build a new one to see if it happens again.

---

### Post by b0rka7a on 2007-12-03
OK, I'll try that.
I'll write tomorrow to tell you what's the result.
I hope this works.

---

### Post by b0rka7a on 2007-12-04
This didn't worked. I renamed '.wine' to '.wine-backup'. Next in a terminal I typed wineprefixcreate:
```
descom@descom-lab:~$ wineprefixcreate 
Could not load Mozilla. HTML rendering will be disabled.
/home/descom/.wine updated successfully.
descom@descom-lab:~$ 

```
I started winecfg and nothing... the same problem...

=================================
[Edit]: A minute ago I removed wine and msttcorefonts (with the hope it fix it, but it didn't), and at the end of the installation of msttcorefonts I've got these lines:
```
All done, no errors.
All fonts downloaded and installed.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
Couldn't get cwd: No such file or directory

```
I have the feeling that I shouldn't get that line "Couldn't get cwd: No such file or directory"
I've attached a .txt file that contains the installation process.

P.S: Tell me what are my spelling mistakes, so I remember them and hopefully type correct next time :)

---

### Post by dudeofthedead on 2007-12-04
I'm guessing it has to do with the character encoding.  Maybe Wine isn't very good at recognizing Bulgarian.  I would install it again with English as a supported language.

---

### Post by VladK on 2007-12-04
> **b0rka7a said:**
> For the first time I have such a problem. I've attached a screenshot of winecfg and I hope you guys can help me out solving it :). My home PC is in English and there is no problem, but this PC is in Bulgarian. Only Wine 0.9.50 shows the font that way. Wine 0.9.46 shows it normal (I've tried only these two versions of Wine).

This is a 64-bit PC, and one friend of mine have the same problem with a 32-bit PC
(I mean, I don't think the type of the distro matters)

Thanks in advance! :)

It's an encoding problem - you've got Russian interface, so it's trying to show all text in Russian,  but fail to display a language.

Actually I can't suggest anything, but definitely you should dig that way :)

Same in Russian:
&#1059; &#1090;&#1077;&#1073;&#1103; &#1089; &#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1086;&#1081; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099;. &#1048;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089; &#1090;&#1099; &#1089;&#1077;&#1073;&#1077; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081; &#1087;&#1086;&#1089;&#1090;&#1072;&#1074;&#1080;&#1083;, &#1072; &#1096;&#1088;&#1080;&#1092;&#1090;&#1086;&#1074; &#1085;&#1077;&#1090;. &#1093;.&#1079;. &#1095;&#1105; &#1076;&#1077;&#1083;&#1072;&#1090;&#1100;, &#1084;&#1086;&#1078;&#1077;&#1090; &#1087;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1081; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1088;&#1091;&#1089;&#1089;&#1082;&#1091;&#1102; &#1083;&#1086;&#1082;&#1072;&#1083;&#1100;...

---

### Post by b0rka7a on 2007-12-04
10x for the quick reply!
I'll change it to English :)

---

