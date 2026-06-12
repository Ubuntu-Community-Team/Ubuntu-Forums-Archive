---
title: "X_CreateWindow Badmatch"
date: 2011-08-18
forum: Wine
---

### Post by LeDechaine on 2011-08-18
Hello.

Well, to  be brief, almost everything I try to run in wine gives this error. I've just bought Chessmaster, and it doesn't work, same error message.

```
$ wine game.exe 
fixme:imm:ImmDisableIME (-1): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  1051
  Current serial number in output stream:  1053
```

After a little bit of search, i've found this in a "Xlib Programming Manual" page.

> The border_width for an InputOnly window must be zero, or a **BadMatch** error results. For class InputOutput, the visual type and depth must be a combination supported for the screen, or a **BadMatch** error results. The depth need not be the same as the parent, but the parent must not be a window of class InputOnly, or a **BadMatch** error results. For an InputOnly window, the depth must be zero, and the visual must be one supported by the screen. If either condition is not met, a **BadMatch** error results. The parent window, however, may have any depth and class. If you specify any invalid window attribute for a window, a **BadMatch** error results. 

Yeah right. Way to have a working and perfectly versatile program. Please tell me how to fix this. I want a computer, not a doll that says "no".

I'm running Jaunty with an ATI Radeon 9250 (and don't tell me to upgrade, I want a mechanic, not a car reseller). And being sick of computers in general, if the easiest thing to do is the dirtiest possible hack, i'll prefer it to anything else. Thanks in advance.

---

