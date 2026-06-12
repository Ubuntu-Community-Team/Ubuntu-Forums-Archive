---
title: "SwiftKit under Wine?"
date: 2013-10-16
forum: Wine
---

### Post by DiscoDave95 on 2013-10-16
Swift Kit is an application built for Runescape that has tools, calculators, maps, and etc.

I am currently running Xubuntu 12.04.3 and attempted to install Swift Kit under wine. I followed these instructions:

```
It is possible to install SwiftKit on Linux using Wine and Winetricks.
1.  If you don't already have Wine, you're going to need to download it.  You can either get this from the Add/Remove panel in Ubuntu or from  Wine's repositories [here]("http://www.winehq.org/download/").
2. If you don't have Winetricks, install it. Wine is not the same as winetricks. To install Winetricks type:
    wget [http://www.kegel.com/wine/winetricks3](http://www.kegel.com/wine/winetricks3). You're going to need a few things from Winetricks to run SwiftKit. To install them type:
    sh winetricks vcrun6 wsh56 allfonts4. Download Java from [here]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=29219"). Run it with Wine.
5. Run the SwiftKit installer. It will give you an error, ignore it.
Congratulations! You've now installed SwiftKit on a Linux machine! 
*Credits to primefalcon.* (Taken from the SwiftKit website)


```

However, when I click the icon nothing will happen, so i tried running through the terminal and got these errors

```
david@david-laptop:~$ /home/david/Desktop/SwiftKit.desktop
/home/david/Desktop/SwiftKit.desktop: line 1: [Desktop: command not found
/home/david/Desktop/SwiftKit.desktop: line 3: syntax error near unexpected token `('
/home/david/Desktop/SwiftKit.desktop: line 3: `Exec=env WINEPREFIX="/home/david/.wine" wine C:\\\\Program\\ Files\\ \\(x86\\)\\\\SwiftKit\\\\SwiftKit.exe '

```

anyone have any thoughts?

Any and all help is appreciated :)

---

### Post by eliteazza on 2013-10-16
Hi im Simmo head of swiftkit support

The post that have read is about 5 years old. Swiftkit has changed a lot since then and is no longer a pre compiled single binary file. Swiftkit now heavly manipulates the windows api. Our own testing has shown that swiftkit is unable to work with wine. You may find it easier to get our osx version working with ubuntu.

That being said it may still be possible to get it to work and if you are able to we would like to know. 

To start off your comand line error is cause becuase you have a ( in the file path you need to escape it like you have done with the slashes.

---

### Post by DiscoDave95 on 2013-10-16
Hmm well do you think I would be better off using the 2007 version of Swift Switch? All I really want are the calculators and tools

---

### Post by oldos2er on 2013-10-18
Moved to Wine.

---

