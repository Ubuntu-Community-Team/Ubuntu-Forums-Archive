---
title: "Multi-button mouse for World of Warcraft / problems"
date: 2008-01-17
forum: Wine
---

### Post by bjorn.haaland on 2008-01-17
Hello, rest assured I've spent some time browsing the web for this particular problem, but I haven't been able to find a solution to this particular problem. 
That is, there are threads on it around the place, but what I'm able to find is still a bit off target.

[Gamer Mouse Optical GM-4200](http://www.trust.com/products/product_detail.aspx?item=14463) is what I use.

xorg.conf :
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option		"ButtonsMapping" "1 2 3 6 7"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons" "7"
	Option		"Emulate3Buttons"	"false"
```

I've tried a few different combinations, after suggestions I've seen while browsing. But again, I haven't been able to find a solution. When I open up WoW and start binding keys, I'm unable to make WoW recognize my side buttons. Now, what I have to do in WXP, is to assign those buttons to F10, F11, F12 (just picked those because I can 'spare' them) and then when binding stuff in WoW, the bindings would show up as bound to F10,  F11, F12 respectively. That was fine, and worked fine. This binding was, for the record, done in Trust's configuration program, the one shipping with the mouse. But now I'm clueless.

---

### Post by bjorn.haaland on 2008-01-23
Gentle bump here.

I'm finding I have to play WoW on WXP until I sort this out.. will keep looking and report back here if I find a solution.

EDIT, solved:

```
Section "InputDevice"                                                                               
        Identifier      "Configured Mouse"                                                          
        Driver          "mouse"                                                                     
        Option          "CorePointer"                        
        Option          "Device"                "/dev/input/mice"                                 
        Option          "Protocol"              "ExplorerPS/2"                                      
        Option          "ZAxisMapping"          "4 5"
	Option 		"Buttons"		"7"
	Option		"ButtonMapping"	"1 2 3 7 6 4 5"
        Option          "Emulate3Buttons"       "false"
EndSection
```
- Well, it's good enough for me. I'm still missing one button, but now WoW is playable again, yay!

---

