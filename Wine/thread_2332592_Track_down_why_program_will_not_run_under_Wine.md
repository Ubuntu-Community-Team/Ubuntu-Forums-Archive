---
title: "Track down why program will not run under Wine"
date: 2016-08-02
forum: Wine
---

### Post by 4kh3RAm on 2016-08-02
Is there a way to track down why a program will not run correctly under Wine ?

I have Ollydbg.

This is one example that does not run correctly.

```
;Telephone.asm 
;              Simulate telephone ringing
;              Help from SuperDave -- a.k.a. DednDave, 
;
;              PRODUCE 1 KHz TONE FOR 54.9 mS 
;              PRODUCE 800 Hz TONE FOR 54.9 mS 

.486                       ; create 32 bit code
.model flat, stdcall       ; 32 bit memory model
option casemap :none       ; case sensitive

include \masm32\include\windows.inc
include \masm32\include\masm32.inc
include \masm32\include\user32.inc
include \masm32\include\kernel32.inc
include \masm32\include\shell32.inc
includelib \masm32\lib\masm32.lib
includelib \masm32\lib\user32.lib
includelib \masm32\lib\kernel32.lib
includelib \masm32\lib\shell32.lib
include \masm32\macros\macros.asm

.data

.code  
                  
start:

mov ecx, 15
@@:
push ecx
invoke Beep, 1000, 55 ; Frequency in hertz and sound duration
invoke Beep, 800, 55   
pop ecx
dec ecx
jnz @B
invoke Sleep, 1500    

mov ecx, 15
@@:
push ecx
invoke Beep, 1000, 55 ; Frequency in hertz and sound duration
invoke Beep, 800, 55   
pop ecx
dec ecx
jnz @B
invoke Sleep, 1500

invoke ExitProcess,0

end start



 							
 							[IMG]http://masm32.com/board/Themes/default/images/icons/modify_inline.gif[/IMG] 						 						 							 							


```

---

### Post by deadflowr on 2016-08-02
*Thread moved to **Wine**.*

---

### Post by howefield on 2016-08-02
> **4kh3RAm said:**
> Is there a way to track down why a program will not run correctly under Wine ?

The Wine website and database can be a good place to start, albeit many of the database entries have only a few tests, and can be dated.

[https://www.winehq.org/](https://www.winehq.org/)
[https://appdb.winehq.org/](https://appdb.winehq.org/)

---

### Post by 4kh3RAm on 2016-08-02
thanks.

---

