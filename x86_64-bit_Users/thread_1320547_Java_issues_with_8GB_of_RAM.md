---
title: "Java issues with 8GB of RAM"
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by RichJacot on 2009-11-09
Hello,

I'm having an odd Java problem.  I am currently running:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

but I also had this exact same issue with:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"

Everything ran fine on 8.04 and 9.10 when my system has 2GB of RAM.  I upgraded to 8GB of RAM and Java started crashing.  I don't believe it is a DIMM issue because on both 8.04 and 9.10 I ran mprime for 48 hrs with no problems reported.  The system is stable until I run something with Java.  After a fresh install of 9.10 I let my system run nearly a week (with 8GB) before attempting for run something using Java and sure enough it locked up shortly afterwards. 

The two Java apps I use most are Ninan and PS3 Media Server.  

When running Ninan, the length of time before the system locks up varies.  Sometimes a few minutes and others up to a few hours.
When running PS3 Media server the appl. tends to die and not lock the system up, but it has locked the system before.

With Ninan this is the last message I see:

#
# A fatal error has been detected by the Java Runtime Environment:
#
# SIGSEGV (0xb) at pc=0x00007f39b595dcc2, pid=21748, tid=139885635598608
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.1-b02 mixed mode linux-amd64 )
# Problematic frame:
# V [libjvm.so+0x5dfcc2]

I've attached one of the error logs.  

Does anyone know what might be causing this or know of a workaround (besides dropping back to 2GB of RAM as I have already. ;) )?

TIA

---

