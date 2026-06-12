---
title: "[SOLVED] Applications menu entry missing"
date: 2008-11-02
forum: Wine
---

### Post by Interpreter on 2008-11-02
Hi there, I can make use of .exes, I do have it installed. So says synaptic.

I am however missing the starters in my applications menu as shown in the below picture. The question is, how do I getm 'em back?

[IMG]http://i36.tinypic.com/301fwix.png[/IMG]

PS: The attachment feature in this board causes my opera browser to eat itself, which renders it useless, any ideas on that one are just as appreciated ;)

---

### Post by Interpreter on 2008-11-04
Fixed it myself...
The easiest way is to go to /home/<username>/.config/menus and delete the file applications.menu
Note: .config is a hidden fil.e, use Ctrl+h while in home or enable under view. The system will recreate the file applications.menu and properly populate it!

---

