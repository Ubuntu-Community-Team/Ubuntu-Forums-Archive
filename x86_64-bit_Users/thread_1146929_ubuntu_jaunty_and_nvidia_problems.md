---
title: "ubuntu jaunty and nvidia problems"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by ankscorek on 2009-05-03
hi fellow ubuntu users..i upgraded from intrepid to jaunty..i am using amd64 with nvidia..i am trying to play 3d games..but they become choppy the movement becomes really bad and choppy..i tried lowering the settings but of no use..

i also removed and reinstalled compiz no use

[COLOR="Red"]skal@skal-laptop:~$ lspci | grep -i vga
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
skal@skal-laptop:~$ glxinfo | grep -i direct
direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord,[/COLOR]

[COLOR="Black"]are there any conflict issues i am using nvidia 180 driver for linux any help will be appreciated[/COLOR]

i never saw this problem in 7.10/8.04..i am facing this problem since 8.10 and then to 9.04

---

### Post by dcstar on 2009-05-03
> **ankscorek said:**
> hi fellow ubuntu users..i upgraded from intrepid to jaunty..i am using amd64 with nvidia..i am trying to play 3d games..but they become choppy the movement becomes really bad and choppy..i tried lowering the settings but of no use..

i also removed and reinstalled compiz no use

[COLOR="Red"]skal@skal-laptop:~$ lspci | grep -i vga
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
skal@skal-laptop:~$ glxinfo | grep -i direct
direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord,[/COLOR]

[COLOR="Black"]are there any conflict issues i am using nvidia 180 driver for linux any help will be appreciated[/COLOR]

i never saw this problem in 7.10/8.04..i am facing this problem since 8.10 and then to 9.04

Does doing this make a difference?:

```
sudo chmod 666 /dev/nvidia*
```

---

### Post by GerMulvey on 2009-05-03
Cool - for me this has allowed counterstrike 1.6 to work with Jaunty. Up 'til now it just failed to start.

Also as a footnote syncing the compiz default display rate to my lcd at 60Hz fixed the video tearing on playback too (it defaults to 50Hz)

---

### Post by ankscorek on 2009-05-03
sudo chmod 666 /dev/nvidia*

doe snot help the problem still persists..do i have to make some group or something

there is no node by the name of nvidia in /dev/

---

