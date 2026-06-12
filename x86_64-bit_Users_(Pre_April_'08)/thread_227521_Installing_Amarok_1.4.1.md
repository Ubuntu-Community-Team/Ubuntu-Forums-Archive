---
title: "Installing Amarok 1.4.1"
date: 2006-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Old Jimma on 2006-08-01
When I moved my son's iTunes library from his Win2000 machine to his
Dapper AMD64 machine, I learned that Amarok 1.3 didn't read mp3 or m4a
(I think it is m4a files... an iTunes proprietary file type). I learned
that Amarok 1.4 would and have been trying to install it.... and have
had trouble.

Could you help me? I've attached the install instructions from the
amarok web site:

([http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source](http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source))

I have attached the install commands from the amarok web site.

I have trouble with the         
        ./configure --prefix=`kde-config --prefix` 
step. the error message I get is:
        
[B]checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will
fail. So, check this please and use another prefix![/B]

I think that the ./configure command above (and in the attachment) is
somehow thinking that I am using kde... I'm not.. I use Gnome.

I looked for help on the amarok irc... that place is alot of weird
chatter.

Any suggestion will be greatly appreciated.

Thank you!
Phil Smith
Duluth, GA

---

### Post by Kilz on 2006-08-01
> **Phil Smith said:**
> When I moved my son's iTunes library from his Win2000 machine to his
Dapper AMD64 machine, I learned that Amarok 1.3 didn't read mp3 or m4a
(I think it is m4a files... an iTunes proprietary file type). I learned
that Amarok 1.4 would and have been trying to install it.... and have
had trouble.

Could you help me? I've attached the install instructions from the
amarok web site:

([http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source](http://amarok.kde.org/wiki/Installation_HowTo#Building_From_Source))

I have attached the install commands from the amarok web site.

I have trouble with the         
        ./configure --prefix=`kde-config --prefix` 
step. the error message I get is:
        
[B]checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will
fail. So, check this please and use another prefix![/B]

I think that the ./configure command above (and in the attachment) is
somehow thinking that I am using kde... I'm not.. I use Gnome.

I looked for help on the amarok irc... that place is alot of weird
chatter.

Any suggestion will be greatly appreciated.

Thank you!
Phil Smith
Duluth, GA

I use a few kde programs on my Ubuntu. Amarok is one of them. I have 1.4 installed, but I used Synaptic to install it. Adept would be the Kde or Kubuntu equivnent. There is a Kubuntu repository , its German, that has a lot of the latest versions of applications. You may want to add it. [Here is a link to there instruction page.]("http://www.kubuntu.de/index.php?option=com_content&task=view&id=48&Itemid=70") Its in German, but the repository address is in a shaded square. [Here is a bad google translate of the page into english if you want.]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.kubuntu.de%2Findex.php%3Foption%3Dcom_content%26task%3Dview%26id%3D48%26Itemid%3D70&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") Then you should be able to use adept to install amarok 1.4. [You could also just download the .deb file.]("http://archive.kubuntu.de/ubuntu/pool/dapper/main/amd64/") but it may need some dependancies from that repository.

---

