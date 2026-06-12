---
title: "Problem with kvm and vista 64 bits"
date: 2007-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by mariano.pelizzari on 2007-11-11
Hi everyone,

I'm having a problem trying to start vista 64 bits with kvm. If I delete the kvm device (/dev/kvm) everithing go smoothly, but I don't have kvm support. If I enable the device I get this error:

exception 13 (0)
rax 0000000060000010 rbx 0000000000000000 rcx 00000000000200ff rdx 0000000000000001
rsi 0000000000000003 rdi 0000000000030201 rsp 0000000000001f34 rbp 0000000000001f68
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 0000000000009b3b rflags 00033006
cs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 77e0 (00077e00/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (7d850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt bc88/27
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 0f 09 66 25 ff ff ff df 0f 22 c0 e8 e7 00 f9 0f 84 bd 00 84 d2 74 04 e4 ee eb 04 30 c0 e6
Cancelado (core dumped)

I'm using this command:

kvm -m 2000 -cdrom /dev/cdrom -localtime -soundhw all -net nic,model=ne2k_pci -net user vista.img


Any thougths.

Olso I was wandering if I can get the resolutions for my wide monitor. I'm only getting 800x600, 1024x768 and 1280x1024

Thks in advance.

Mariano

---

### Post by kaivalagi on 2008-02-15
Hi,

I am have similar problems on gutsy 64 bit:

[COLOR="Navy"]exception 6 (0)
rax 0000000000000469 rbx 0000000000800001 rcx 0000000000004300 rdx 0000000000000000
rsi 000000000005961d rdi 000000000005961c rsp 00000000fffaa9cc rbp 000000000000200c
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000b04b rflags 00033006
cs 4143 (00041430/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 3002 (00030020/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (2f650000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt 40920/47
idt 0/ffff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aborted (core dumped)[/COLOR]

I am using the following (very basic, maybe wrong?) command:

[COLOR="Navy"] kvm -m 750 -cdrom /media/sdc1/Images/Linux/ubuntu-7.10-server-amd64.iso -boot d ./ubuntu-server.img[/COLOR]

Can anyone provide help, I have followed online help...:confused:

---

### Post by kaivalagi on 2008-03-18
bump

anyone?

---

### Post by ericy on 2008-03-18
Try this:

kvm -m 750 -cdrom /media/sdc1/Images/Linux/ubuntu-7.10-server-amd64.iso -boot d -hda ./ubuntu-server.img

---

### Post by kaivalagi on 2008-03-19
Thanks Ericy, unfortunately that didn't work either, I still get the same error I posted before...

Any other ideas?

I had this problem first with a dual code, since then I am now running quad, so my host cpu is not the issue.

Once 8.04 is stable I'll give it a go with that, if I get nowhere with 7.10 now

---

