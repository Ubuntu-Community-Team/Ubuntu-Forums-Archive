---
title: "[SOLVED] Invisible mouse in Wine"
date: 2008-11-10
forum: Wine
---

### Post by bimasakti85 on 2008-11-10
I'm using Ubuntu 8.04. When I use wine, I cant see my mouse pointer as it is being invisible. It's still functioning. If I point my mouse to the outside of the wine box, if will appear, then dissapear again if I enter to the wine zone. Is there anyone knows how to solve this ?

Thanx

---

### Post by loell on 2008-11-10
do you? by any chance, using a VIA on board video? cause i've seen cases like that.

---

### Post by Ape3000 on 2008-11-10
You are probably using an application that wants to use animated cursors. Currently Wine lacks support for those, but they have already wrote the code, so you can patch your Wine and get it working. The support will probably also come the main code and for the future releases.

For more information read this: [http://bugs.winehq.org/show_bug.cgi?id=10708](http://bugs.winehq.org/show_bug.cgi?id=10708)

---

### Post by bimasakti85 on 2008-11-10
> **loell said:**
> do you? by any chance, using a VIA on board video? cause i've seen cases like that.

Yes, I'm using VIA based board. Is there any relation between VIA board with this problem ? And is there already any solution for this matter ?

---

### Post by loell on 2008-11-10
> **bimasakti85 said:**
> Yes, I'm using VIA based board. Is there any relation between VIA board with this problem ? And is there already any solution for this matter ?

unfortunately there is no solution yet :(
(other than to use a dedicated video card which is an overkill just to make the problem go away)

**VIA chrome** the display driver that you are using, is the one causing it.

the chrome driver is a work in progress, it may address this bug later.

---

### Post by bimasakti85 on 2008-12-13
Now solved by adding : 
Option          "SWCursor" "true"

under the "Device" section in xorg.conf

---

### Post by loell on 2008-12-14
great! :) you can mark the thread as solved. :)

---

