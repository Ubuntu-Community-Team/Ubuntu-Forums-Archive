---
title: "The Orange Box+Catalyst 7.11+Ubuntu Gutsy+WINE"
date: 2007-12-13
forum: Wine
---

### Post by quadomatic on 2007-12-13
I bought the Orange Box a couple weeks ago ($25, nice deal huh), and after playing the hell out of it in Windows, I'm going to give it a shot under Linux.

I figure it might be a nice test. I know that Enemy Territory: Quake Wars runs in Linux just about as well as it does in Windows for me, which is with mostly high settings (which is amazing to me). So, I figure I'd like to try Portal and Team Fortress 2 under the latest ATI Drivers for Linux (Catalyst 7.11) and the latest edition of WINE. While it'll probably be futile, I'd like to try anyway.

Does anyone have any tips for me before I get started?

Thanks

---

### Post by Beren Camlost on 2007-12-13
A guide to Team Fortress 2 in Wine: [http://ubuntuforums.org/showthread.php?t=587780&highlight=tf2](http://ubuntuforums.org/showthread.php?t=587780&highlight=tf2)

---

### Post by quadomatic on 2007-12-13
Hmmm....

I followed the instructions, but when I tried to run Portal or Team Fortress 2, the game would crash after the Valve intro.

Any ideas?

---

### Post by RemmyLee on 2007-12-14
I have the same problem with all of Orange Box and I'm convinced it's either because I am running a 64bit version of Ubuntu, or that it is a bug in wine. In the console window, I get an error about some GL extensions not being available, however they are.

---

### Post by Beren Camlost on 2007-12-14
Hmm, which version of Wine are you running? And I assume you followed the Howto in step one of the link I gave. This howto seemed to work great with Wine 0.9.46. 0.9.47-0.9.49 seems to have issues and crashed with TF2. No info on how it works with 0.9.50 or 0.9.51. (I don't have Orange Box so I'm not able to test it myself).

Also, pasting the terminal output you get when running TF2 (from a terminal) may help locate the problem.

---

### Post by azurelight1337 on 2007-12-15
I don't get any terminal output and it get the same crashing with wine 0.9.46

Anyway to run it via the terminal, because all it does is launch steam.exe

Alright, got terminal output... and **** it's long.

fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d85a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d85a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d85a0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d86d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d86d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d86d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8824)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8824)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8824)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8ad4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8ad4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8ad4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8ad4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8bd4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8bd4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8bd4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8bd4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8cc4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8cc4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8cc4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8cc4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8e64)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8e64)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8e64)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8e64)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8fd8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8fd8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d8fd8)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d91fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d91fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d91fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d91fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9330)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9330)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9330)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9330)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d94ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d94ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d94ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d94ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9b40)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9b40)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9b40)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9b40)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9c30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9c30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9c30)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9d04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9d04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9d04)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9df0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9df0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9df0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109d9df0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da024)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da024)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da024)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da1fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da1fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109da1fc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109da7d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109da7d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109da7d4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dacdc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dacdc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dacdc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dacdc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dacdc)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109db134)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109db134)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109db134)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e0190,symt:0x109dbaa4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e0190,symt:0x109dbaa4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e0190,symt:0x109dbaa4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dbe08)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dbe08)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e02bc,symt:0x109dbe08)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109dd38c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109dd38c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109dd38c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e09f8,symt:0x109dd38c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109e13d0,symt:0x109dd650)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cfde4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cfde4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cfde4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cff0c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cff0c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0220,symt:0x109cff0c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a01f8,symt:0x109dff94)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a01f8,symt:0x109dff94)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a01f8,symt:0x109dff94)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0040)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0124)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0208)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0208)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0208)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0208)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e02ec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e02ec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e02ec)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e08b4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e08b4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e08b4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e08b4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0cd0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0cd0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0cd0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0d84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0d84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0d84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0ed4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0ed4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e0ed4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1184)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1284)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1284)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1284)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1284)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e13f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e13f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e13f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e13f4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1594)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1594)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1594)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1594)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1688)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1688)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1688)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e18ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e18ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e18ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e18ac)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e19e0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e19e0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e19e0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e19e0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1b5c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1b5c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1b5c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e1b5c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2170)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2170)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2170)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2170)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2260)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2260)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2260)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2334)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2420)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2420)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2420)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2420)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e2654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e2654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e2654)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e282c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e282c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0a54,symt:0x109e282c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2e84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2e84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e2e84)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e330c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e330c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e330c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e330c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e330c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e37e4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e37e4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0324,symt:0x109e37e4)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e54f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e54f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e54f0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5a00)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x16 at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5a00)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5a00)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5a00)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5a00)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5e58)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5e58)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109f01fc,symt:0x109e5e58)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __gxx_exception_class (a)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e713c)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e6fc0)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a03d8,symt:0x109e7464)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e7710)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e7710)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a0234,symt:0x109e7710)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7760)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7884)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7884)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7884)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7884)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e7884)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x1c at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e78c4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e78c4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e78c4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e78c4)
fixme:dbghelp_dwarf:dwarf2_parse_udt_type Unhandled Tag type 0x2e at ctx(0x34b7fc,L"fglrx_dri.so"), for debug_info(abbrev:0x109a02e8,symt:0x109e78c4)
fixme:avifile:AVIFileExit (): stub!

And this part happens just as TF2 is starting:

fixme:shdocvw:ViewObject_SetAdvise (0x16615318)->(1 00000002 0x14ad500)
fixme:shdocvw:PersistStreamInit_InitNew (0x16615318)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x16615318)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x16615318)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x16615660)->(1 00000002 0x14ad568)
fixme:shdocvw:PersistStreamInit_InitNew (0x16615660)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x16615660)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x16615660)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c5b4,0x00000000), stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x165b85b0)->(1 00000002 0x14af788)
fixme:shdocvw:PersistStreamInit_InitNew (0x165b85b0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x165b85b0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x165b85b0)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e7e88) stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,215,2): stub!
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:win:EnumDisplayDevicesW ((null),0,0x34e2d8,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x165b85b0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x165b85b0)
fixme:shdocvw:OleObject_Close (0x165b85b0)->(1)
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

---

### Post by aoanla on 2007-12-15
> **RemmyLee said:**
> I have the same problem with all of Orange Box and I'm convinced it's either because I am running a 64bit version of Ubuntu, or that it is a bug in wine. In the console window, I get an error about some GL extensions not being available, however they are.

It's not either issue - I'm running Gutsy 64bit here, and have no problems playing any of the Orange Box games in Wine.

On the other hand, I did have horrible problems with my ATI card - my new nVidia card is rock solid with the 168.04 nvidia beta driver, but I got instant crashes with ATI's fglrx drivers and the new "Catalyst" driver on my old card.

I suspect, therefore, that the issue is ATI, not Wine or 64bit.

---

### Post by bastiegast on 2007-12-15
> **quadomatic said:**
> I bought the Orange Box a couple weeks ago ($25, nice deal huh), and after playing the hell out of it in Windows, I'm going to give it a shot under Linux.

I figure it might be a nice test. I know that Enemy Territory: Quake Wars runs in Linux just about as well as it does in Windows for me, which is with mostly high settings (which is amazing to me). So, I figure I'd like to try Portal and Team Fortress 2 under the latest ATI Drivers for Linux (Catalyst 7.11) and the latest edition of WINE. While it'll probably be futile, I'd like to try anyway.

Does anyone have any tips for me before I get started?

Thanks

And quake wars SHOULD run as well in linux as in windows since it has a native linux version.
About the high settings, I can run the orange box games in dx 81 without problems but in dxlevel 90(meaning HDR and other shiny effects) is much slower as it is in windows. It always hangs around 10 fps, lowering texture detail and model detail doesn't affect the fps.

I have a geforce 6800 and Im running gutsy amd64 version, latest wine.

---

### Post by quadomatic on 2007-12-15
Maybe it is ATI, but other people with ATI were able to get it working.

What did those of you with ATI have to do to get it to work?

---

### Post by azurelight1337 on 2007-12-15
Well... don't ask me how I did it, but I got it working. Although the game will still randomly freeze up sometimes... more often than I'd like...

But I have the latest version of wine, my restricted ATI drivers enabled, running in windowed wine following the howto.

Also, using directx **8.0** instead of 8.1, and it works... O_o

---

### Post by quadomatic on 2007-12-15
> **azurelight1337 said:**
> Well... don't ask me how I did it, but I got it working. Although the game will still randomly freeze up sometimes... more often than I'd like...

But I have the latest version of wine, my restricted ATI drivers enabled, running in windowed wine following the howto.

Also, using directx **8.0** instead of 8.1, and it works... O_o

How do you set it to Direct X 8.0?

---

### Post by azurelight1337 on 2007-12-15
set the launcher to

wine steam.exe -applaunch 440 -dxlevel 80

Although that might not be quite what got it to work... but I made progress when using 7.0 (got to the loading screen) and then it said a minimum of 8.0 is required, so I set it to 8.0 and it worked. O_o

---

### Post by azurelight1337 on 2007-12-15
Ugh... now for some reason I get "Failed to create D3D device!"

---

### Post by quadomatic on 2007-12-16
> **azurelight1337 said:**
> Ugh... now for some reason I get "Failed to create D3D device!"

I think that's the same error that I got.

Did you update to Catalyst 7.11?

---

### Post by azurelight1337 on 2007-12-16
> **quadomatic said:**
> I think that's the same error that I got.

Did you update to Catalyst 7.11?

Yeah... at least I think I did... I definitely didn't do it properly, I just installed the basic Linux thing they give you, but nothing distro specific.

It's probably wine screwing up, I'm not sure why though, since I got it working...

---

