---
title: "Wine 1.3 requieres to uninstall LMMS"
date: 2011-07-04
forum: Wine
---

### Post by checoimg on 2011-07-04
I don't know why is it happening but I want to know how can I have both software installed.

Thank you in advance for your help and time.

---

### Post by Garrote2010r on 2011-07-15
TTT.  I just fired up LMMS only to find out it somehow deleted itself and research said it does that when Wine 1.3 is installed.  

Does anybody know a work around to this?

---

### Post by checoimg on 2011-07-15
> **Garrote2010r said:**
> TTT.  I just fired up LMMS only to find out it somehow deleted itself and research said it does that when Wine 1.3 is installed.  

Does anybody know a work around to this?

how did you installed 1.3 because Synaptic says it before you install Wine. I want to know why is happening and of course if there is a Workaround that would be great.

Should we report this as a Bug?

---

### Post by Garrote2010r on 2011-07-17
> **checoimg said:**
> how did you installed 1.3 because Synaptic says it before you install Wine. I want to know why is happening and of course if there is a Workaround that would be great.

Should we report this as a Bug?

I had installed LMMS first on basically a fresh machine.  I updated Wine only because I wanted to run the Amazon Kindle app.  I'm thinking it's not worth having the Kindle App.  The only reason I'm running the Kindle app is to view a book I bought and I wouldn't know how else to view it.

---

### Post by checoimg on 2011-07-17
> **Garrote2010r said:**
> I had installed LMMS first on basically a fresh machine.  I updated Wine only because I wanted to run the Amazon Kindle app.  I'm thinking it's not worth having the Kindle App.  The only reason I'm running the Kindle app is to view a book I bought and I wouldn't know how else to view it.

Maybe you can find another app that can read that file. Tell me the file format or extension and we check to see how to open it.

---

### Post by marin123 on 2011-07-19
do you need vestige in lmms? vst support requires wine1.2 and thats why it doesnt work with 1.3.

---

### Post by firereaperd on 2012-01-11
To restore LMMS on your system you can run the following command:

```
sudo apt-get install wine1.2
sudo apt-get install lmms
```

This will force a roll back to wine 1.2. if you have any dependencies on Wine 1.3+ they may complain or even prevent this downgrade and may have to be uninstalled first. I do not know if the Amazon Kindle App requires Wine 1.3 but I doubt it.

---

