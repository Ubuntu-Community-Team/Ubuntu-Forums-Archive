---
title: "foobar volume control from wireless keyboard [also winamp]"
date: 2019-05-31
forum: Wine
---

### Post by shantiq on 2019-05-31
With Ubuntu [and probably other distros too] If you have foobar playing on a computer and a wireless keyboard you use as a handset this is fun >>>




&#10122; ```
sudo apt-get install winbind
```


to facilitate processes


&#10123; sudo gedit ~/.config/openbox/lxde-rc.xml
&#10124; CTRL+F   to find where "keybind key" starts on page
&#10125; Create a new <keybind key> </keybind>  this way >>>




```
#foobar


<keybind key="A-f"><action name="Execute"><command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /playpause</command></action></keybind>


<keybind key="C-0"><action name="Execute"><command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /command:Up</command></action></keybind>


<keybind key="C-9"><action name="Execute"><command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /command:Down</command></action></keybind>
```


*Nota Bene*:   if you want other settings use:


[I][B]Modifier keys  
   
[/B][/I]S     Shift key
C     Control key
A     Alt key
W     Super key (Usually bound to the Windows key on keyboards which have one)
M     Meta key
H     Hyper key (If it is bound to something) 


&#10126; then run 
```
openbox --reconfigure && lxpanelctl restart
```
to validate the changes


NOW:   Take your wireless keyboard sit away from computer  hit Alt+F to playpause  or Ctrl+0  or 9 to see the volume cursor move


NJOI

---

### Post by shantiq on 2019-06-01
and run exactly in the same way for [Winamp]("http://forums.winamp.com/showthread.php?t=373755")  [there are other versions too knocking around]

but you will need to install a piece of kit called [CLEveR.exe]("http://www.etcwiki.org/dl/CLEveR.exe")   which i install inside the winamp folder


```
#winamp 


  <keybind key="A-b">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe playpause</command></action>
    </keybind>
    
  <keybind key="C-7">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe voldn</command></action>
    </keybind>   
    
  <keybind key="C-8">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe volup</command></action>
    </keybind>  

```

====


as we can see here many plugins handled here that other players would balk at including cuefile and many rare lossless formats

[[IMG]https://i.postimg.cc/YGhkmmfT/Screenshot-from-2019-06-02-08-05-59.png[/IMG]]("https://postimg.cc/YGhkmmfT")

---

