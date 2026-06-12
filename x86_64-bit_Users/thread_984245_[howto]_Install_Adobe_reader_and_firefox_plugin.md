---
title: "[howto] Install Adobe reader and firefox plugin"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by bash on 2008-11-16
**About**

If you like me are not happy with the default Evince document viewer for displaying PDFs and want to also be able to display PDFs within your browser window, then you should try the official Adobe Reader for Linux. This installation is quite easy and does **not** require any complicated steps like installing a different version of Firefox and so on.

There is the possibility to use the [Medibuntu](http://www.medibuntu.org/) repository, but some of you like me, might not like to use it. The Medibuntu version of "Adobe Reader" is only in English. So if you want a different language it will be no use for you.

*This is only tested with Ubuntu 8.10. I don't know if it works on older versions as well*



**Step by step explanation**

First of, we need to get the Adobe Reader .deb package from the Adobe website. For this just click on the following link:

[http://www.adobe.com/products/acrobat/readstep2_allversions_nojs1.html](http://www.adobe.com/products/acrobat/readstep2_allversions_nojs1.html)

Select the "Linux - x86 (.deb)" package and of course the language of your liking. Then proceed to download the package.

Now we need to get that thing installed. As this is a 32bit package we can't just use the graphic installer. So open a Terminal and navigate to the directory where you saved the .deb. Normally that should be "/home/yourusername/Desktop". If that is the case just type the following in the Terminal:

```
cd ~/Desktop
```

Now that we are in the right folder on to the installation:

```
sudo dpkg -i --force-all AdobeReader*.deb
```

It should install the Adobe Reader package now. When that is done, we just need to add support for the Firefox plugin, by executing the following command:

```
sudo nspluginwrapper -i /opt/Adobe/Reader8/Browser/intellinux/nppdf.so
```

That's it you should be all set. Restart Firefox and enjoy the fancy PDF reading experience.

---

### Post by Arup on 2008-11-16
The Acroreader along with browswer plugin can be found in the repos if you enable Medibuntu repos. I installed it via this method and it works quite good, yesterday there was an update to it as well. All PDF can be easily displayed in my Opera browser.

---

### Post by bash on 2008-11-17
As said in my first post, of course you can use Medibuntu. But it is only in English. So if you want a non English version of Adobe Reader, Medibuntu won't help you.

---

### Post by Arup on 2008-11-17
> **bash said:**
> As said in my first post, of course you can use Medibuntu. But it is only in English. So if you want a non English version of Adobe Reader, Medibuntu won't help you.

Thanks for the clarification, btw, acroreader plugin is x32 so nsplugin wrapper is needed for that.

---

