---
title: "Wine with COM ports"
date: 2008-07-19
forum: Wine
---

### Post by timswait on 2008-07-19
OK I use my laptop to read data from a lambda probe controller and data logger in my car (basically to help me tune the engine). Unfortunately I can't find any Linux program to do it, so I'm stuck with using Windows programs and Wine. I use wbUtil from Tech Edge (the makers of the hardware [here]("http://wbo2.com/sw/util.htm")) and Winlog from Devtechnics [here.]("http://www.devtechnics.com/winlog.htm"). The lambda controller connects via serial port.
My laptop has a serial port (refered to by Windows as COM1) and the docking station has another (refered to by Windows as COM4). When I run either program through Wine they can see COM ports 1-4 and 10-19. wbUtil can see and communicate with the lambda controller on COM10, but Winlog cannot see the controller on any COM port, and I tried all of them! Can anyone tell me how I can better set up the COM ports mapping in Wine? One time when I plugged in the controller the mouse cursor went funny and started moving on it's own. This sometimes happens if I boot the computer into Windows with the controller plugged in, I assume it thinks the controller is a serial mouse and so gets confusing signals. When this happens it cannot see the controller either.
ATM I have dual boot with Windows left on, but this logging software is the only thing I use Windows for, so I'd like to get it working in Linux and then get rid of Windows entirely.

---

### Post by timswait on 2008-08-26
Anyone - please?:)
Is it possible to use serial ports with Wine?

---

