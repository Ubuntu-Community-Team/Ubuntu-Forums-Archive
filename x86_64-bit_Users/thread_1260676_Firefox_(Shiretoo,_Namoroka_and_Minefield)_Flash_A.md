---
title: "Firefox (Shiretoo, Namoroka and Minefield) Flash AMD64 &quot;Illegal Instuction&quot; crash"
date: 2009-09-07
forum: x86 64-bit Users
---

### Post by Anusiya on 2009-09-07
Hi there,

I got the latest libflashplayer.so (10.0 r32), works decent in YouTube, pretty much crashes in almost every other site (Hulu etc.). I have attached the output of cat /proc/cpuinfo. Any suggestions?
$ cat /proc/cpuinfo

processor       : 0                                
vendor_id       : GenuineIntel                     
cpu family      : 15                               
model           : 4                                
model name      : Intel(R) Xeon(TM) CPU 3.20GHz    
stepping        : 3                                
cpu MHz         : 3191.677                         
cache size      : 2048 KB                          
physical id     : 0                                
siblings        : 2                                
core id         : 0                                
cpu cores       : 1                                
apicid          : 0                                
initial apicid  : 0                                
fpu             : yes                              
fpu_exception   : yes                              
cpuid level     : 3                                
wp              : yes                              
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr                                                                                     
bogomips        : 6383.35                                                                                                                            
clflush size    : 64                                                                                                                                 
cache_alignment : 128                                                                                                                                
address sizes   : 36 bits physical, 48 bits virtual                                                                                                  
power management:                                                                                                                                    

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15          
model           : 4           
model name      : Intel(R) Xeon(TM) CPU 3.20GHz
stepping        : 3                            
cpu MHz         : 3191.677                     
cache size      : 2048 KB                      
physical id     : 3                            
siblings        : 2                            
core id         : 0                            
cpu cores       : 1                            
apicid          : 6                            
initial apicid  : 6                            
fpu             : yes                          
fpu_exception   : yes                          
cpuid level     : 3                            
wp              : yes                          
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr                                                                                     
bogomips        : 6384.03                                                                                                                            
clflush size    : 64                                                                                                                                 
cache_alignment : 128                                                                                                                                
address sizes   : 36 bits physical, 48 bits virtual                                                                                                  
power management:                                                                                                                                    

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15          
model           : 4           
model name      : Intel(R) Xeon(TM) CPU 3.20GHz
stepping        : 3                            
cpu MHz         : 3191.677                     
cache size      : 2048 KB                      
physical id     : 0                            
siblings        : 2                            
core id         : 0                            
cpu cores       : 1                            
apicid          : 1                            
initial apicid  : 1                            
fpu             : yes                          
fpu_exception   : yes                          
cpuid level     : 3                            
wp              : yes                          
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr                                                                                     
bogomips        : 6383.96                                                                                                                            
clflush size    : 64                                                                                                                                 
cache_alignment : 128                                                                                                                                
address sizes   : 36 bits physical, 48 bits virtual                                                                                                  
power management:                                                                                                                                    

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.20GHz
stepping        : 3
cpu MHz         : 3191.677
cache size      : 2048 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 7
initial apicid  : 7
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nxlm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
bogomips        : 6384.04
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

Thanks,
Anusiya

---

### Post by michael37 on 2009-09-08
Need more info.

Close firefox.  Open terminal and run "/usr/bin/firefox" from terminal.

Go to website where flash crashes.  Post here whatever you saw in the terminal.

---

### Post by Anusiya on 2009-09-09
Thanks for your reply. The error was indicated in the subject of my post. 

$ firefox 
Illegal instruction

I contacted Adobe and it seems that the problem is related to Xeon procs. Anybody else facing it? I isolated the problem to Flash by disabling Java and other plugins. As mentioned earlier, I am using flash 64 10.0 r32.

Thanks,
Anusiya

---

### Post by michael37 on 2009-09-09
> **Anusiya said:**
> Thanks for your reply. The error was indicated in the subject of my post. 

$ firefox 
Illegal instruction

I contacted Adobe and it seems that the problem is related to Xeon procs. Anybody else facing it? I isolated the problem to Flash by disabling Java and other plugins. As mentioned earlier, I am using flash 64 10.0 r32.

Thanks,
Anusiya

Very surprising, but I am not convinced Adobe diagnosis is on the money.

Please run [thread=1259102]script from this thread[/thread] to make sure you clean everything else up.

After that, are you saying that if you 
"sudo mv /usr/lib/mozilla/plugins/libflashplayer.so /tmp"

(plugin may also be in /usr/lib/firefox-addons/plugins/libflashplayer.so)

then firefox starts as if nothing happens? 
and when you put the flash back in it crashes?

---

### Post by Anusiya on 2009-09-10
Same deal. Flash crashes out with illegal instruction error. Works perfectly in my Core 2 Quad system but crashes out in the dual Xeon system. Both running Jaunty, Shiretoko and Flash 10.0 r32. Weird!

Anusiya

UPDATE: I do not think it is the Xeon proc issue. I think it is the nVidia card. It is a not-too-old nVidia Quadro FX 540, using the latest nVidia drivers. Got my friend to get flash working really well in his Xeon machine running RHEL.

---

### Post by Anusiya on 2009-09-11
Well, got the latest linux driver for nVidia cards (not yet available on repos) from the website and built it into the kernel. No luck with flash though. This is extremely disappointing, probably will wait for Flash beta from Adobe. Seems like some people in the forums have complained about the same issue, but none got back...

Thanks for your help,
Anusiya

---

### Post by Anusiya on 2009-09-11
The problem was Xeon as Adobe had mentioned to me. Earlier Xeons do not have the LAHF/SAHF instruction set hence flash does not work. The fix has been posted in [HTML]http://ubuntuforums.org/showthread.php?t=1263905[/HTML]

Thanks,

Anusiya

---

