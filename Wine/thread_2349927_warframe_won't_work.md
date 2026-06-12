---
title: "warframe won't work"
date: 2017-01-19
forum: Wine
---

### Post by hotpocky on 2017-01-19
I'm using Ubuntu 16.04 LTS, PlayOnLinux version 4.2.10, Wine-2.0-rc3,  and typing "Winetricks --version" returns "20160329 - sha1sum:  3373b943b372153431e01246811d0d3aa4765b42". When I was using Windows 7  Ultimate on its own, I could play Warframe no problem, I understand that  warframe isn't natively compatible with Linux, and I now greatly regret  fully wiping Windows and replacing it with Linux. Short of buying a  copy (for apparently far less than I thought) and a disk drive / usb  disk drive to use it, I'm having a lot of trouble getting this one game  to work. At least it's finally downloaded! (My sister's PS4 hogs most of  the bandwidth).

I've followed the suggestions at [WineHQ (Warframe)]("https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+forums&ie=utf-8&oe=utf-8")  but I can't seem to get the version with the 'Staging' tab to work, and  so I can't enable CMST or VAAPI. I've followed the suggestions at [Warframe on Linux with Wine]("https://www.forums.warframe.com/topic/41660-guide-warframe-on-linux-with-wine/?page=14")  but at step 4, the launcher doesn't open, despite doing everything as  told. I've boiled down the issues to one, but it's a doozy, and frankly  I'm basically inept at Linux (E.g: It took me at least two hours to  figure out how to open the terminal on my first day using it), so I legitimately have no idea  what the problem is, but it's definitely in there... somewhere.

```
   samantha@sam-pc:~$ env WINEPREFIX="/home/samantha/.wine" wine C:\\users\\samantha\\Local\ Settings\\Application\ Data\\Warframe\\Downloaded\\Public\\Tools\\Launcher.exe  
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
 fixme:heap:RtlSetHeapInformation 0x110000 0 0x33f7ec 4 stub
 fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
 fixme:process:SetProcessDEPPolicy (3): stub
 fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
 fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x100c4220, 0x12d387f0, 0x12e0dbf0) stub.
 [0119/181759:ERROR:main_delegate.cc(724)] Could not load locale pak for en-US
 fixme:imm:ImmDisableTextFrameService Stub
 fixme:nls:GetThreadPreferredUILanguages 00000038, 0x33e86c, (nil) 0x33e870
 fixme:nls:get_dummy_preferred_ui_language (0x38 0x33e86c (nil) 0x33e870) returning a dummy value (current locale)
 fixme:nls:GetThreadPreferredUILanguages 00000038, 0x33e86c, 0x1d8338 0x33e870
 fixme:nls:get_dummy_preferred_ui_language (0x38 0x33e86c 0x1d8338 0x33e870) returning a dummy value (current locale)
 fixme:winsock:WSALookupServiceBeginW (0x33e580 0x00000ff0 0x33e5bc) Stub!
 [0119/181759:ERROR:network_change_notifier_win.cc(155)] WSALookupServiceBegin failed with: 8
 fixme:iphlpapi:NotifyAddrChange (Handle 0x33e700, overlapped 0x1d99dc): stub
 fixme:win:RegisterDeviceNotificationW (hwnd=0x1006e, filter=0x33e6d4,flags=0x00000000) returns a fake device notification handle!
 fixme:win:RegisterDeviceNotificationW (hwnd=0x1006e, filter=0x33e6d4,flags=0x00000000) returns a fake device notification handle!
 fixme:win:EnumDisplayDevicesW ((null),0,0x33e1dc,0x00000000), stub!
 [0119/181759:ERROR:proxy_service_factory.cc(136)] Cannot use V8 Proxy resolver in single process mode.
 fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10070 0x00000000
 fixme:gdi:GdiInitializeLanguagePack stub
 fixme:file:K32EnumPageFilesW (0x422988, (nil)) stub
 fixme:hnetcfg:fwpolicy2_get_CurrentProfileTypes 0x1569e8 0x15b56c
 fixme:wininet:InternetAttemptConnect Stub
 fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
 fixme:ver:GetCurrentPackageId (0x4a7e9a8 (nil)): stub
 fixme:wininet:query_global_option Stub for 3
 fixme:wininet:InternetSetOptionW Option 77 STUB
 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
 wine: Unhandled page fault on write access to 0x00000000 at address 0x1075f55b (thread 003e), starting debugger...
 Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x1075f55b).
 Register dump:
  CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
  EIP:1075f55b ESP:0454d868 EBP:0454db70 EFLAGS:00210246(  R- --  I  Z- -P- )
  EAX:00000000 EBX:3ca1c05c ECX:2503df00 EDX:00000000
  ESI:25119300 EDI:3ca1c05c
 Stack dump:
 0x0454d868:  0454dcd7 3ca1c05c 00000000 00000005
 0x0454d878:  423fa600 0000ffff 00000000 2503df00
 0x0454d888:  00000100 250b7950 3ca1c05c 00000005
 0x0454d898:  00000001 423fa600 0000f890 00000005
 0x0454d8a8:  00000000 00000005 00000065 00000000
 0x0454d8b8:  00000000 00000000 00000005 0454dbcc
 Backtrace:
 =>0 0x1075f55b in libcef (+0x75f55b) (0x0454db70)
   1 0x1075de67 in libcef (+0x75de66) (0x0454dc2c)
   2 0x1076815b in libcef (+0x76815a) (0x0454dce0)
   3 0x107010d4 in libcef (+0x7010d3) (0x0454dd08)
   4 0x10701368 in libcef (+0x701367) (0x0454dd28)
   5 0x106a4598 in libcef (+0x6a4597) (0x0454dd34)
   6 0x106c9d1a in libcef (+0x6c9d19) (0x0454dd88)
   7 0x10701368 in libcef (+0x701367) (0x0454dda8)
   8 0x106a45c8 in libcef (+0x6a45c7) (0x0454ddb4)
   9 0x106abb69 in libcef (+0x6abb68) (0x0454ddd4)
   10 0x106ac064 in libcef (+0x6ac063) (0x0454de10)
   11 0x106ab807 in libcef (+0x6ab806) (0x0454dea4)
   12 0x106a796f in libcef (+0x6a796e) (0x0454deec)
   13 0x106a76f0 in libcef (+0x6a76ef) (0x0454df1c)
   14 0x106fddbc in libcef (+0x6fddbb) (0x0454df30)
   15 0x106ca59e in libcef (+0x6ca59d) (0x0454dfa4)
   16 0x106fdce5 in libcef (+0x6fdce4) (0x0454dfb8)
   17 0x106fee4c in libcef (+0x6fee4b) (0x0454e028)
   18 0x10725179 in libcef (+0x725178) (0x0454e09c)
   19 0x10724af2 in libcef (+0x724af1) (0x0454e104)
   20 0x106fdce5 in libcef (+0x6fdce4) (0x0454e118)
   21 0x1071cd87 in libcef (+0x71cd86) (0x0454e1d8)
   22 0x10475f8e in libcef (+0x475f8d) (0x0454e234)
   23 0x104767c1 in libcef (+0x4767c0) (0x0454e328)
   24 0x1047adda in libcef (+0x47add9) (0x0454e358)
   25 0x1047a61f in libcef (+0x47a61e) (0x0454e3ac)
   26 0x105a66db in libcef (+0x5a66da) (0x0454e3cc)
   27 0x113f4d90 in libcef (+0x13f4d8f) (0x0454e3d8)
   28 0x113e22ee in libcef (+0x13e22ed) (0x0454e40c)
   29 0x11645d50 in libcef (+0x1645d4f) (0x0454e50c)
   30 0x10a6d2a7 in libcef (+0xa6d2a6) (0x0454e52c)
   31 0x100c2540 in libcef (+0xc253f) (0x0454e58c)
   32 0x11706350 in libcef (+0x170634f) (0x0454e638)
   33 0x11705e4d in libcef (+0x1705e4c) (0x0454e764)
   34 0x116edaa4 in libcef (+0x16edaa3) (0x0454e780)
   35 0x11706486 in libcef (+0x1706485) (0x0454e79c)
   36 0x100c2540 in libcef (+0xc253f) (0x0454e7f8)
   37 0x1007eef5 in libcef (+0x7eef4) (0x0454e864)
   38 0x1007f9a0 in libcef (+0x7f99f) (0x0454e8bc)
   39 0x100c1717 in libcef (+0xc1716) (0x0454e8f4)
   40 0x100c141d in libcef (+0xc141c) (0x0454e914)
   41 0x1007ec85 in libcef (+0x7ec84) (0x0454e938)
   42 0x1009a769 in libcef (+0x9a768) (0x0454e960)
   43 0x100a3342 in libcef (+0xa3341) (0x0454e98c)
   44 0x100a34d3 in libcef (+0xa34d2) (0x0454e9c8)
   45 0x1007d3f7 in libcef (+0x7d3f6) (0x0454e9e8)
   46 0x7bc806ec call_thread_func_wrapper+0xb() in ntdll (0x0454e9f8)
   47 0x7bc836bd call_thread_func+0xfc() in ntdll (0x0454eaf8)
   48 0x7bc806ca RtlRaiseException+0x21() in ntdll (0x0454eb18)
   49 0x7bc8b48f in ntdll (+0x7b48e) (0x0454f368)
   50 0xf753a295 start_thread+0xe4() in libpthread.so.0 (0x0454f428)
   51 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   52 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   53 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   54 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   55 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   56 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   57 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   58 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   59 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   60 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   61 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   62 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   63 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   64 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   65 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   66 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   67 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   68 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   69 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   70 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   71 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   72 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   73 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   74 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   75 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   76 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   77 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   78 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   79 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   80 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   81 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   82 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   83 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   84 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   85 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   86 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   87 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   88 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   89 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   90 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   91 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   92 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   93 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   94 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   95 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   96 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   97 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   98 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   99 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   100 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   101 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   102 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   103 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   104 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   105 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   106 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   107 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   108 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   109 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   110 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   111 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   112 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   113 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   114 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   115 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   116 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   117 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   118 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   119 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   120 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   121 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   122 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   123 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   124 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   125 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   126 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   127 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   128 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   129 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   130 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   131 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   132 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   133 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   134 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   135 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   136 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   137 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   138 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   139 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   140 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   141 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   142 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   143 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   144 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   145 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   146 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   147 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   148 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   149 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   150 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   151 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   152 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   153 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   154 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   155 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   156 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   157 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   158 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   159 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   160 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   161 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   162 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   163 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   164 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   165 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   166 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   167 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   168 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   169 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   170 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   171 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   172 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   173 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   174 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   175 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   176 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   177 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   178 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   179 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   180 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   181 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   182 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   183 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   184 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   185 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   186 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   187 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   188 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   189 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   190 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   191 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   192 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   193 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   194 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   195 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   196 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   197 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   198 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   199 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
   200 0xf7463eee __clone+0x6d() in libc.so.6 (0x00000000)
 0x1075f55b: movb    %al,0x00000000
 Modules:
 Module    Address            Debug info    Name (154 modules)
 PE      400000-  51b000    Deferred        launcher
 PE    10000000-12f89000    Export          libcef
 ELF    7ac00000-7ac7c000    Deferred        riched20<elf>
   \-PE    7ac10000-7ac7c000    \               riched20
 ELF    7b400000-7b7e0000    Deferred        kernel32<elf>
   \-PE    7b410000-7b7e0000    \               kernel32
 ELF    7bc00000-7bcf6000    Dwarf           ntdll<elf>
   \-PE    7bc10000-7bcf6000    \               ntdll
 ELF    7c000000-7c004000    Deferred        <wine-loader>
 PE    7cdeb000-7ce00000    Deferred        api-ms-win-appmodel-runtime-l1-1
 PE    7cdf0000-7ce00000    Deferred        api-ms-win-appmodel-runtime-l1-1C:\windows\system32\api-ms-win-appmodel-runtime-l1-1-1.dll
 ELF    7cf12000-7cf39000    Deferred        hnetcfg<elf>
   \-PE    7cf20000-7cf39000    \               hnetcfg
 ELF    7cf39000-7cf4f000    Deferred        winejoystick<elf>
   \-PE    7cf40000-7cf4f000    \               winejoystick
 ELF    7cf4f000-7cfbc000    Deferred        setupapi<elf>
   \-PE    7cf60000-7cfbc000    \               setupapi
 ELF    7d044000-7d04b000    Deferred        libnss_dns.so.2
 ELF    7d04b000-7d061000    Deferred        libgpg-error.so.0
 ELF    7d061000-7d0d6000    Deferred        libpcre.so.3
 ELF    7d0d6000-7d0f3000    Deferred        libgcc_s.so.1
 ELF    7d0f3000-7d1a2000    Deferred        libgcrypt.so.20
 ELF    7d1a2000-7d1c8000    Deferred        liblzma.so.5
 ELF    7d1c8000-7d1d1000    Deferred        librt.so.1
 ELF    7d1d1000-7d1f7000    Deferred        libselinux.so.1
 ELF    7d1f7000-7d285000    Deferred        libsystemd.so.0
 ELF    7d285000-7d28e000    Deferred        libffi.so.6
 ELF    7d28e000-7d2a7000    Deferred        libresolv.so.2
 ELF    7d2a7000-7d2ac000    Deferred        libkeyutils.so.1
 ELF    7d2ac000-7d306000    Deferred        libdbus-1.so.3
 ELF    7d306000-7d392000    Deferred        libgmp.so.10
 ELF    7d392000-7d3c7000    Deferred        libhogweed.so.4
 ELF    7d3c7000-7d403000    Deferred        libnettle.so.6
 ELF    7d403000-7d418000    Deferred        libtasn1.so.6
 ELF    7d418000-7d44c000    Deferred        libidn.so.11
 ELF    7d44c000-7d4ad000    Deferred        libp11-kit.so.0
 ELF    7d4ad000-7d4ba000    Deferred        libkrb5support.so.0
 ELF    7d4ba000-7d4eb000    Deferred        libk5crypto.so.3
 ELF    7d4eb000-7d5c2000    Deferred        libkrb5.so.3
 ELF    7d5c2000-7d5d6000    Deferred        libavahi-client.so.3
 ELF    7d5d6000-7d5e4000    Deferred        libavahi-common.so.3
 ELF    7d5e4000-7d73c000    Deferred        libgnutls.so.30
 ELF    7d73c000-7d78e000    Deferred        libgssapi_krb5.so.2
 ELF    7d78e000-7d815000    Deferred        libcups.so.2
 ELF    7d819000-7d833000    Deferred        msftedit<elf>
   \-PE    7d820000-7d833000    \               msftedit
 ELF    7d833000-7d903000    Deferred        crypt32<elf>
   \-PE    7d840000-7d903000    \               crypt32
 ELF    7d903000-7d92c000    Deferred        iphlpapi<elf>
   \-PE    7d910000-7d92c000    \               iphlpapi
 ELF    7d92c000-7d95c000    Deferred        netapi32<elf>
   \-PE    7d930000-7d95c000    \               netapi32
 ELF    7d95c000-7d98e000    Deferred        secur32<elf>
   \-PE    7d960000-7d98e000    \               secur32
 ELF    7d98e000-7d9eb000    Deferred        oleacc<elf>
   \-PE    7d9a0000-7d9eb000    \               oleacc
 ELF    7d9eb000-7da00000    Deferred        dhcpcsvc<elf>
   \-PE    7d9f0000-7da00000    \               dhcpcsvc
 ELF    7da00000-7da9d000    Deferred        urlmon<elf>
   \-PE    7da10000-7da9d000    \               urlmon
 ELF    7da9d000-7dab5000    Deferred        userenv<elf>
   \-PE    7daa0000-7dab5000    \               userenv
 ELF    7dab5000-7dad2000    Deferred        jsproxy<elf>
   \-PE    7dac0000-7dad2000    \               jsproxy
 ELF    7dad2000-7db0e000    Deferred        winhttp<elf>
   \-PE    7dae0000-7db0e000    \               winhttp
 ELF    7db0e000-7dbf8000    Deferred        comdlg32<elf>
   \-PE    7db10000-7dbf8000    \               comdlg32
 ELF    7dbf8000-7dc37000    Deferred        winspool<elf>
   \-PE    7dc00000-7dc37000    \               winspool
 ELF    7dc37000-7dc7c000    Deferred        usp10<elf>
   \-PE    7dc40000-7dc7c000    \               usp10
 ELF    7dc7c000-7dc90000    Deferred        api-ms-win-core-sysinfo-l1-2-1<e
 PE    7dc80000-7dc90000    Deferred        api-ms-win-core-sysinfo-l1-2-1
 PE    7dc90000-7dca5000    Deferred        api-ms-win-core-localization-l1-
 PE    7dca0000-7dca5000    Deferred        api-ms-win-core-localization-l1-C:\windows\system32\api-ms-win-core-localization-l1-2-1.dll
 ELF    7dca5000-7dcb9000    Deferred        api-ms-win-core-fibers-l1-1-1<el
 PE    7dcb0000-7dcb9000    Deferred        api-ms-win-core-fibers-l1-1-1
 ELF    7dcb9000-7dcc0000    Deferred        libxfixes.so.3
 ELF    7dcc0000-7dccb000    Deferred        libxcursor.so.1
 ELF    7dccb000-7dcde000    Deferred        libxi.so.6
 ELF    7dcde000-7dce2000    Deferred        libxcomposite.so.1
 ELF    7dce2000-7dcef000    Deferred        libxrandr.so.2
 ELF    7dcef000-7dcfb000    Deferred        libxrender.so.1
 ELF    7dcfb000-7dd02000    Deferred        libxxf86vm.so.1
 ELF    7dd02000-7dd06000    Deferred        libxinerama.so.1
 ELF    7dd06000-7dd0d000    Deferred        libxdmcp.so.6
 ELF    7dd0d000-7dd11000    Deferred        libxau.so.6
 ELF    7dd11000-7dd37000    Deferred        libxcb.so.1
 ELF    7dd37000-7de82000    Deferred        libx11.so.6
 ELF    7de82000-7de97000    Deferred        libxext.so.6
 ELF    7de99000-7de9e000    Deferred        libcom_err.so.2
 ELF    7de9e000-7deb2000    Deferred        api-ms-win-core-synch-l1-2-0<elf
 PE    7dea0000-7deb2000    Deferred        api-ms-win-core-synch-l1-2-0
 ELF    7deb5000-7df42000    Deferred        winex11<elf>
   \-PE    7dec0000-7df42000    \               winex11
 ELF    7df42000-7df66000    Deferred        imm32<elf>
   \-PE    7df50000-7df66000    \               imm32
 ELF    7dfbe000-7dfe8000    Deferred        libexpat.so.1
 ELF    7dfe8000-7e031000    Deferred        libfontconfig.so.1
 ELF    7e031000-7e05c000    Deferred        libpng12.so.0
 ELF    7e05c000-7e10c000    Deferred        libfreetype.so.6
 ELF    7e10c000-7e12f000    Deferred        libtinfo.so.5
 ELF    7e12f000-7e155000    Deferred        libncurses.so.5
 ELF    7e173000-7e1ad000    Deferred        ws2_32<elf>
   \-PE    7e180000-7e1ad000    \               ws2_32
 ELF    7e1ad000-7e1d5000    Deferred        mpr<elf>
   \-PE    7e1b0000-7e1d5000    \               mpr
 ELF    7e1d5000-7e1f0000    Deferred        libz.so.1
 ELF    7e1fa000-7e20e000    Deferred        psapi<elf>
   \-PE    7e200000-7e20e000    \               psapi
 ELF    7e20e000-7e286000    Deferred        wininet<elf>
   \-PE    7e220000-7e286000    \               wininet
 ELF    7e286000-7e29e000    Deferred        wtsapi32<elf>
   \-PE    7e290000-7e29e000    \               wtsapi32
 ELF    7e29e000-7e2d5000    Deferred        uxtheme<elf>
   \-PE    7e2a0000-7e2d5000    \               uxtheme
 ELF    7e2d5000-7e2e9000    Deferred        msimg32<elf>
   \-PE    7e2e0000-7e2e9000    \               msimg32
 ELF    7e2e9000-7e3e4000    Deferred        comctl32<elf>
   \-PE    7e2f0000-7e3e4000    \               comctl32
 ELF    7e3e4000-7e40f000    Deferred        msacm32<elf>
   \-PE    7e3f0000-7e40f000    \               msacm32
 ELF    7e40f000-7e4c7000    Deferred        winmm<elf>
   \-PE    7e420000-7e4c7000    \               winmm
 ELF    7e4c7000-7e5f9000    Deferred        oleaut32<elf>
   \-PE    7e4e0000-7e5f9000    \               oleaut32
 ELF    7e5f9000-7e679000    Deferred        rpcrt4<elf>
   \-PE    7e600000-7e679000    \               rpcrt4
 ELF    7e679000-7e7b2000    Deferred        ole32<elf>
   \-PE    7e690000-7e7b2000    \               ole32
 ELF    7e7b2000-7e829000    Deferred        shlwapi<elf>
   \-PE    7e7c0000-7e829000    \               shlwapi
 ELF    7e829000-7ea6b000    Deferred        shell32<elf>
   \-PE    7e840000-7ea6b000    \               shell32
 ELF    7ea6b000-7eae2000    Deferred        advapi32<elf>
   \-PE    7ea80000-7eae2000    \               advapi32
 ELF    7eae2000-7ec12000    Deferred        gdi32<elf>
   \-PE    7eaf0000-7ec12000    \               gdi32
 ELF    7ec12000-7ed66000    Deferred        user32<elf>
   \-PE    7ec20000-7ed66000    \               user32
 ELF    7ef66000-7ef79000    Deferred        libnss_files.so.2
 ELF    7ef79000-7ef86000    Deferred        libnss_nis.so.2
 ELF    7ef86000-7efa1000    Deferred        libnsl.so.1
 ELF    7efa1000-7efab000    Deferred        libnss_compat.so.2
 ELF    7efab000-7f000000    Deferred        libm.so.6
 ELF    f7378000-f737d000    Deferred        libdl.so.2
 ELF    f737d000-f7533000    Dwarf           libc.so.6
 ELF    f7534000-f7551000    Dwarf           libpthread.so.0
 ELF    f7554000-f756e000    Deferred        version<elf>
   \-PE    f7560000-f756e000    \               version
 ELF    f756f000-f7726000    Dwarf           libwine.so.1
 ELF    f7728000-f774d000    Deferred        ld-linux.so.2
 ELF    f774f000-f7750000    Deferred        [vdso].so
 Threads:
 process  tid      prio (all id:s are in hex)
 00000008 (D) C:\users\samantha\Local Settings\Application Data\Warframe\Downloaded\Public\Tools\Launcher.exe
     00000048    0
     00000047    0
     00000046    0
     00000045    0
     00000044    0
     00000042    0
     00000041    0
     00000040    0
     0000003f    0
     0000003e    0 <==
     0000003d    0
     0000003c    0
     0000003b    0
     0000003a    0
     00000039    0
     00000038    0
     00000037    0
     00000036    0
     00000035    0
     00000034    0
     00000033    0
     00000032    0
     00000031    0
     00000030    0
     0000002f    0
     0000002e    0
     0000002d    0
     0000002c    0
     0000002b    0
     0000002a    0
     00000029    0
     00000009    0
 0000000e services.exe
     00000020    0
     0000001f    0
     00000014    0
     00000010    0
     0000000f    0
 00000012 winedevice.exe
     0000001e    0
     00000019    0
     00000018    0
     00000013    0
 0000001c plugplay.exe
     00000022    0
     00000021    0
     0000001d    0
 00000023 explorer.exe
     00000028    0
     00000027    0
     00000026    0
     00000025    0
     00000024    0
 System information:
     Wine build: wine-2.0-rc3
     Platform: i386 (WOW64)
     Version: Windows XP
     Host system: Linux
     Host version: 4.4.0-59-generic
 samantha@sam-pc:~$  


```

---

### Post by wildmanne39 on 2017-01-19
*Thread moved to **Wine**.*

---

### Post by hotpocky on 2017-01-20
I'd like to give the users who edited/moved my post a quick thank you. You are unsung heroes.

---

### Post by hotpocky on 2017-01-22
I've given up and am currently downloading Windows 7 to dual boot, but I'd like to keep this thread open for the sake of others who have the same problem, and because I don't like being intellectually bested by an inanimate object.

---

