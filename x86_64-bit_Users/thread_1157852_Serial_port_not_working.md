---
title: "Serial port not working"
date: 2009-05-13
forum: x86 64-bit Users
---

### Post by sanket_rambhia on 2009-05-13
Serial port on my KUBUNTU, which I upgraded few days ago doesn't seem to be working. This is the first time I am trying to use serial port on Linux so I might be doing something stupid.

I have attached a loop-back on my serial port to check if data is actually transmitted and received. From looking at /proc/tty/driver/serial it looks like data is being transmitted but nothing is being recieved, however voltmeter doesn't show any fluctuation when data is being transmitted so I doubt if any data is 'actually' being transmitted.

Here are the results of dmesg, setserial, stty, etc

dmesg | grep tty:
[    0.010000] console [tty0] enabled
[    1.551851] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.552105] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

ls -l /dev/ttyS*:
crw-rw-rw- 1 sanket dialout 4, 64 2009-05-13 13:17 /dev/ttyS0
crw-rw---- 1 root   dialout 4, 65 2009-05-13 11:38 /dev/ttyS1
crw-rw---- 1 root   dialout 4, 66 2009-05-13 11:38 /dev/ttyS2
crw-rw---- 1 root   dialout 4, 67 2009-05-13 11:38 /dev/ttyS3

stty -F /dev/ttyS0 -a:
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke

setserial /dev/ttyS0:
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
    Baud_base: 9600, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal auto_irq

lspnp -v:
00:0c PNP0501 16550A-compatible serial port
    state = active
    io 0x3f8-0x3ff
    irq 4
    dma disabled

lspci:
.
.
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
.
.

vim /proc/tty/driver/serial:
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:67963 rx:0
1: uart:unknown port:000002F8 irq:3
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3

As you can see this shows transmitted data but recieved data is 0, which cant be the case as all the data transmitted should be recieved due to loopback.

I have checked BIOS and it shows serial port on IRQ 4 and address 0x3F8.
I am transmitting data using echo test_message > /dev/ttyS0, cp filename /dev/ttyS0 and by using minicom, cutecom.

I am trying to recieve data using tail -f /dev/ttyS0, cat /dev/ttyS0 and using cutecom application. 
I have wasted two days with this without any progress.
Please help. 

thanks.

---

