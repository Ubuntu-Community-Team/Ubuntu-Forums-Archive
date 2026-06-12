---
title: "vlc"
date: 2009-04-05
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-04-05
Dear pals,
 After reinstallation of my vlc player in intrepid it resist to start by giving the error"VLC could not open the file "/usr/share/vlc/skins2/text.bmp".Could any friend help me to solve this problem?.
Thank you.

---

### Post by kestrel1 on 2009-04-05
Have you checked to see if the file it is complaining about exists?

---

### Post by jayanramesh on 2009-04-06
Dear Kestrel 1,
I am neither an engineering student nor a professional.Being a medico I don't know much about it so please whatever explanation you provide -it should be in explicit way.And could you tell me how to check it.

Thank you

---

### Post by andrew.46 on 2009-04-06
Hi jayanramesh,

> **jayanramesh said:**
> I am neither an engineering student nor a professional.Being a medico I don't know much about it so please whatever explanation you provide -it should be in explicit way.And could you tell me how to check it.

Well I am a registered nurse so between us we should be able to work it out :-). Paste the following into a terminal:


```
sudo find /usr -name 'text.bmp'
```

and post the output here. BTW did you install a 'skins' pack with vlc?

All the best,

Andrew

---

### Post by jayanramesh on 2009-04-06
Dear Andrew.46
I did what you had asked me to do but I have not got any sort of output at terminal .Yes I have changed my vlc skin

---

### Post by andrew.46 on 2009-04-06
Hi jayanramesh,

There is a configuration file that controls all of this and if it is renamed or deleted vlc will start with the defaults, this will get you out of trouble.

Your file may very well be in a different location to mine so could you also run the following command, which I have outlined in red,:

```

andrew@skamandros~$ **[COLOR="Red"]find $HOME -name 'vlcrc'[/COLOR]**
/home/andrew/.config/vlc/vlcrc

```

and when the file is located if you like I can demonstrate the command to *rename* this file and allow vlc to start with all of the defaults.

All the best,

Andrew

---

### Post by jayanramesh on 2009-04-06
Dear Andrew.46
Something went wrong whenever I click on places to open  folders vlc player starts automatically and giving an error report as
'File reading failed:
VLC could not open the file "/usr/share/vlc/skins2/text.bmp".
VLC can't recognize the input's format:
The format of 'file:///home/jayanr/Desktop/filezilla_3.2.3.1-1~getdeb1_amd64.deb' cannot be detected. Have a look the log for details.
VLC can't recognize the input's format:
The format of 'file:///home/jayanr/Desktop/filezilla-locales_3.2.3.1-1~getdeb1_all.deb' cannot be detected. Have a look the log for details."
I don't see what went wrong.
Thank you

---

### Post by andrew.46 on 2009-04-06
Hi jayanramesh,

Have you been able to run the command:

```
find $HOME -name 'vlcrc'
```

Could you post the full terminal output by copying and pasting?

All the best,

Andrew

---

### Post by mc4man on 2009-04-06
just use from terminal
```
vlc --reset-config
```

---

### Post by jayanramesh on 2009-04-07
Dear pals,
Thanks for all-Problem was solved with the code provided by Mc4man.

---

