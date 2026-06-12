---
title: "Audiosurf Crash"
date: 2014-07-28
forum: Wine
---

### Post by Chelidze on 2014-07-28
I am using Playonlinux and wine 1.7.23 if I just use system wine I can not get past [this]("http://bugs.winehq.org/show_bug.cgi?id=36896") 

However If I use POL I can start and play the game. however I have a problem (main) every time I try to log in and type a letter in the login box the game crashes 

backtrack

```
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x7e0c9ef0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e0c9ef0 ESP:00daf570 EBP:00daf6d8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e0cf128 ECX:00000000 EDX:00010132
 ESI:00000090 EDI:00174768
Stack dump:
0x00daf570:  00010132 00daf730 7ffd8000 00000040
0x00daf580:  7bc5ad19 7bcd0548 00daf5c8 7bc5ce13
0x00daf590:  7e0cfc22 7e972407 00000000 7bc3f903
0x00daf5a0:  00daf630 7e0b0000 7e0cf430 00010132
0x00daf5b0:  7e0cf24c 00000000 04090409 01450001
0x00daf5c0:  00daf5e0 7bcd0548 00daf628 7bc5f64a
Backtrace:
=>0 0x7e0c9ef0 ImmProcessKey+0x80() in imm32 (0x00daf6d8)
  1 0x7e8e341a in user32 (+0x83419) (0x192c7d50)
  2 0x7e8e5260 PeekMessageW+0x5f() in user32 (0x00dafa9c)
  3 0x1002a7d6 in gameoverlayrenderer (+0x2a7d5) (0x00dafab8)
  4 0x7e8e550e PeekMessageA+0xed() in user32 (0x00dafb08)
  5 0x1002a786 in gameoverlayrenderer (+0x2a785) (0x00dafb28)
  6 0x00401c76 in questviewer (+0x1c75) (0x7e8e5420)
  7 0x4c8d5d00 (0x71b165e9)
0x7e0c9ef0 ImmProcessKey+0x80 in imm32: movl	0xc(%eax),%edx
Modules:
Module	Address			Debug info	Name (404 modules)
PE	  400000-  412000	Export          questviewer
PE	 2110000- 2130000	Deferred        highpoly
PE	 2240000- 2247000	Deferred        fileloader
PE	 2250000- 2255000	Deferred        directory
PE	 2260000- 2265000	Deferred        0de141bf-025d-4313-94af-be13150cC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\0DE141BF-025D-4313-94AF-BE13150C6458.dll
PE	 2270000- 2281000	Deferred        7dfc389a-bdfd-4092-93ab-d0b93a03C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7DFC389A-BDFD-4092-93AB-D0B93A030DD6.dll
PE	 2290000- 2295000	Deferred        cbccc586-cae0-45ae-9689-f5c17936C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\CBCCC586-CAE0-45AE-9689-F5C179360700.dll
PE	 22a0000- 22a5000	Deferred        filesaver
PE	 22b0000- 22b5000	Deferred        9e2350d9-a93d-4cc1-bcce-930a60afC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\9E2350D9-A93D-4CC1-BCCE-930A60AF14A4.dll
PE	 22c0000- 22c5000	Deferred        0cc1d8c2-57eb-4427-842f-bcd32f2fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\0CC1D8C2-57EB-4427-842F-BCD32F2FCCF3.dll
PE	 22d0000- 22d5000	Deferred        be69ccc4-cfc1-4362-ac81-767d199bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BE69CCC4-CFC1-4362-AC81-767D199BBFC3.dll
PE	 22e0000- 22e8000	Deferred        aba92939-1b14-4a41-af8d-f2177945C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\ABA92939-1B14-4A41-AF8D-F217794512EE.dll
PE	 22f0000- 22f5000	Deferred        85642ff9-3940-4196-9596-90409af1C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\85642FF9-3940-4196-9596-90409AF1CDB4.dll
PE	 2300000- 230c000	Deferred        21a8923d-b908-4104-ae88-b6718d8aC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\21A8923D-B908-4104-AE88-B6718D8A8678.dll
PE	 2310000- 231a000	Deferred        e2d1c95b-1b84-4d94-a373-bebabadfC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\E2D1C95B-1B84-4D94-A373-BEBABADF7AEE.dll
PE	 2340000- 2347000	Deferred        f091dfc1-a51a-45c2-92d1-88ebdae6C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F091DFC1-A51A-45C2-92D1-88EBDAE6B48E.dll
PE	 2350000- 2355000	Deferred        bac7326d-6ddc-4ecf-b821-6a52c828C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BAC7326D-6DDC-4ECF-B821-6A52C8287DC7.dll
PE	 2360000- 2365000	Deferred        ad27535b-d89b-441b-86c2-5a4d22e6C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\AD27535B-D89B-441B-86C2-5A4D22E66943.dll
PE	 2370000- 2375000	Deferred        7cbfbe82-de01-4cee-90cf-c10e5a5bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7CBFBE82-DE01-4CEE-90CF-C10E5A5B82EE.dll
PE	 2380000- 2385000	Deferred        122557dc-cabf-4806-afa1-b0a0dd9cC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\122557DC-CABF-4806-AFA1-B0A0DD9C8C5F.dll
PE	 2390000- 2397000	Deferred        2dfc141f-b06c-47b3-b7f9-2abfb08cC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2DFC141F-B06C-47B3-B7F9-2ABFB08C190E.dll
PE	 23a0000- 23a5000	Deferred        69d8970f-e413-47bb-8e51-4c25b0f6C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\69D8970F-E413-47BB-8E51-4C25B0F65E51.dll
PE	 23b0000- 23b6000	Deferred        dd626e09-f497-4a34-9032-47ad4d2bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\DD626E09-F497-4A34-9032-47AD4D2BCBD7.dll
PE	 23c0000- 23c8000	Deferred        89e051ca-4273-4eb9-89c8-5fd0cda1C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\89E051CA-4273-4EB9-89C8-5FD0CDA1B026.dll
PE	 23d0000- 23f7000	Deferred        fb68cc7d-5b8e-4654-aecf-8d4a12e0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\FB68CC7D-5B8E-4654-AECF-8D4A12E020BC.dll
PE	 2400000- 2405000	Deferred        c06850b2-a74e-453f-adb7-2815d64cC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\C06850B2-A74E-453F-ADB7-2815D64CEA69.dll
PE	 2410000- 241e000	Deferred        59a93b79-c960-4e83-a1ae-6d381131C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\59A93B79-C960-4E83-A1AE-6D3811315C09.dll
PE	 2420000- 2429000	Deferred        4dd461d0-7c4e-45ef-91ab-f211f9b9C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\4DD461D0-7C4E-45EF-91AB-F211F9B920F2.dll
PE	 2430000- 2435000	Deferred        bass_precalcsong
PE	 2440000- 2447000	Deferred        3b1f74d6-65d7-4b91-9114-827027e4C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3B1F74D6-65D7-4B91-9114-827027E4500D.dll
PE	 2450000- 245c000	Deferred        tags
PE	 2460000- 2469000	Deferred        f26bb40b-b196-4ab9-b59e-fa7c8ff4C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F26BB40B-B196-4AB9-B59E-FA7C8FF436F9.dll
PE	 2470000- 2475000	Deferred        6e6fb247-4627-4fbe-8973-48344f23C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\6E6FB247-4627-4FBE-8973-48344F23881E.dll
PE	 2480000- 2488000	Deferred        10c20c0a-7a55-4084-8676-95e5699bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\10C20C0A-7A55-4084-8676-95E5699BCEC2.dll
PE	 2490000- 249a000	Deferred        3237cf29-db73-47d8-b4b9-a6ce2e1eC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3237CF29-DB73-47D8-B4B9-A6CE2E1E60F1.dll
PE	 24a0000- 24a7000	Deferred        d8386f07-7a2b-4dd3-ad23-8470b80bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\D8386F07-7A2B-4DD3-AD23-8470B80B7689.dll
PE	 24b0000- 24b5000	Deferred        1352b30c-2b0c-411f-8791-2107e78fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\1352B30C-2B0C-411F-8791-2107E78FF8E3.dll
PE	 24c0000- 24c6000	Deferred        376a9c13-8d66-49ec-bae5-d59be13bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\376A9C13-8D66-49EC-BAE5-D59BE13BC519.dll
PE	 24f0000- 2743000	Deferred        d3dx9_25
PE	 2850000- 285e000	Deferred        f31897fc-64c3-4ff7-96e0-854bb1e1C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F31897FC-64C3-4FF7-96E0-854BB1E13046.dll
PE	 2860000- 2865000	Deferred        mersenne_twister
PE	 2870000- 2876000	Deferred        18f9c150-2530-4b16-9d95-d31ecc69C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\18F9C150-2530-4B16-9D95-D31ECC69425F.dll
PE	 2880000- 2885000	Deferred        2f605354-314d-4775-86e4-1f733550C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2F605354-314D-4775-86E4-1F733550B227.dll
PE	 2890000- 2895000	Deferred        9d045960-eac2-4c40-9bbf-10f32f7fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\9D045960-EAC2-4C40-9BBF-10F32F7FA305.dll
PE	 28a0000- 28a8000	Deferred        f5bf6106-8544-495d-9bca-e69a6f42C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F5BF6106-8544-495D-9BCA-E69A6F42BF95.dll
PE	 28b0000- 28b7000	Deferred        78167fba-d3ff-4d4d-b6a3-51aab049C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\78167FBA-D3FF-4D4D-B6A3-51AAB049F11C.dll
PE	 29d0000- 29d8000	Deferred        bass_playquicktimestream
PE	 29e0000- 29e9000	Deferred        quicktime_core
PE	 29f0000- 29f7000	Deferred        quicktime_settime
PE	 2a00000- 2a07000	Deferred        quicktime_movierate
PE	 2a10000- 2a15000	Deferred        getprogrampath
PE	 2a20000- 2a25000	Deferred        buffervault_storefile
PE	 2a30000- 2a3a000	Deferred        buffervault
PE	 2a40000- 2a45000	Deferred        bass_setposition
PE	 2a50000- 2a57000	Deferred        17c5b19f-4273-423c-a158-ca6f7304C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\17C5B19F-4273-423C-A158-CA6F73046D43.dll
PE	 2a60000- 2a6a000	Deferred        xml_setchildnode
PE	 2a70000- 2a7f000	Deferred        languagepack_create
PE	 2a80000- 2a8f000	Deferred        unicode_currentdirectory
PE	 2a90000- 2a99000	Deferred        settext_unicode
PE	 2aa0000- 2aa5000	Deferred        cf3378b6-f19d-488d-9361-9c35f838C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\CF3378B6-F19D-488D-9361-9C35F8382722.dll
PE	 2ab0000- 2ab7000	Deferred        eacc7f74-0344-4c1f-9bc2-400ec0c7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\EACC7F74-0344-4C1F-9BC2-400EC0C7C499.dll
PE	 2ad0000- 2ad5000	Deferred        75eefb46-a56e-4248-908d-3354a0b9C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\75EEFB46-A56E-4248-908D-3354A0B96184.dll
PE	 2ae0000- 2ae6000	Deferred        registrydo
PE	 2af0000- 2afd000	Deferred        customtexture05
PE	 2c10000- 2c15000	Deferred        5fe055b0-4269-4b25-9f31-157c835eC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\5FE055B0-4269-4B25-9F31-157C835EC678.dll
PE	 2c20000- 2c26000	Deferred        894b077b-d372-4166-8f39-f188f9c3C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\894B077B-D372-4166-8F39-F188F9C3C237.dll
PE	 2c30000- 2c3c000	Deferred        4df6baf0-3aed-407a-926f-35b2bbb6C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\4DF6BAF0-3AED-407A-926F-35B2BBB62D0C.dll
PE	 2c40000- 2c45000	Deferred        3c0ed055-563b-4b10-8dc6-6eae2eeeC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3C0ED055-563B-4B10-8DC6-6EAE2EEEBE96.dll
PE	 2c50000- 2c58000	Deferred        2ee7e3c5-5969-4117-a8a4-074d7c99C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2EE7E3C5-5969-4117-A8A4-074D7C9986E3.dll
PE	 2c60000- 2c68000	Deferred        b973720e-2cc1-4f5c-a35a-33a152e2C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\B973720E-2CC1-4F5C-A35A-33A152E2453E.dll
PE	 2c70000- 2c75000	Deferred        83783433-179c-4997-a4a5-c6f820cbC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\83783433-179C-4997-A4A5-C6F820CBFDB6.dll
PE	 2c80000- 2c85000	Deferred        4b22839d-2545-400d-a5c9-d9770580C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\4B22839D-2545-400D-A5C9-D977058037AA.dll
PE	 2c90000- 2c95000	Deferred        f3d35a1e-f8cb-4330-b307-9557f9f7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F3D35A1E-F8CB-4330-B307-9557F9F73615.dll
PE	 2ca0000- 2ca5000	Deferred        8bb8f3a3-58fa-48a5-bdc3-e984862bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8BB8F3A3-58FA-48A5-BDC3-E984862BABBE.dll
PE	 2cb0000- 2cb5000	Deferred        00560937-855b-4df7-8b7a-48d321f7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\00560937-855B-4DF7-8B7A-48D321F7F819.dll
PE	 2cc0000- 2cc5000	Deferred        8a5b6098-82b6-4bf0-a6cc-c36770e1C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8A5B6098-82B6-4BF0-A6CC-C36770E10685.dll
PE	 2cd0000- 2cd5000	Deferred        1abc2216-3d9a-4b62-95ca-1aca029fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\1ABC2216-3D9A-4B62-95CA-1ACA029F703E.dll
PE	 2ce0000- 2ce9000	Deferred        a550bb21-be5c-4675-b53e-3fa246f7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A550BB21-BE5C-4675-B53E-3FA246F76538.dll
PE	 2cf0000- 2cf5000	Deferred        a1617bea-2e4a-4a92-b235-50924566C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A1617BEA-2E4A-4A92-B235-509245665AFC.dll
PE	 2d00000- 2d05000	Deferred        ab37dfca-32a2-4a4b-9dd9-09282ee3C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\AB37DFCA-32A2-4A4B-9DD9-09282EE3037A.dll
PE	 2d10000- 2d16000	Deferred        5a4a4c8d-81a4-4a1e-828d-53c15d3bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\5A4A4C8D-81A4-4A1E-828D-53C15D3B8E3C.dll
PE	 2d20000- 2d29000	Deferred        0a1c3637-a047-4740-a761-1247cef0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\0A1C3637-A047-4740-A761-1247CEF0E940.dll
PE	 2d30000- 2d37000	Deferred        1118038e-554c-492c-8e03-928f76a7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\1118038E-554C-492C-8E03-928F76A7EEC0.dll
PE	 2d40000- 2d48000	Deferred        f48570a2-d00b-4280-b381-bb9a952fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F48570A2-D00B-4280-B381-BB9A952FE8AA.dll
PE	 2d50000- 2d5a000	Deferred        customgeometry
PE	 2d60000- 2fc7000	Deferred        d3dx9_31
PE	 2fd0000- 2fd5000	Deferred        d30f7991-36ac-47cf-9879-78175913C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\D30F7991-36AC-47CF-9879-781759131388.dll
PE	 2fe0000- 2fe9000	Deferred        bc052c38-2d5d-4f0c-a0ca-654d0afcC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BC052C38-2D5D-4F0C-A0CA-654D0AFC584A.dll
PE	 2ff0000- 2ff8000	Deferred        3164909d-47f3-43ef-8df8-e8e95e8eC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3164909D-47F3-43EF-8DF8-E8E95E8E22ED.dll
PE	 3440000- 3445000	Deferred        3ff51e2f-6d04-4297-bc69-079c555fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3FF51E2F-6D04-4297-BC69-079C555FF765.dll
PE	 3450000- 3455000	Deferred        b6225961-01da-463d-b5f7-3ad6541fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\B6225961-01DA-463D-B5F7-3AD6541F5BD8.dll
PE	 3460000- 3467000	Deferred        04eb85eb-da14-4e18-9f9c-a0eff683C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\04EB85EB-DA14-4E18-9F9C-A0EFF6837B00.dll
PE	 3470000- 3475000	Deferred        ac73f78e-667d-4db5-b22b-bca1d98aC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\AC73F78E-667D-4DB5-B22B-BCA1D98A1540.dll
PE	 3480000- 3485000	Deferred        21b682fc-63bd-461c-a9ef-f533563aC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\21B682FC-63BD-461C-A9EF-F533563AAD47.dll
PE	 3490000- 3495000	Deferred        be8c55b0-3057-4f3d-ab5a-5791eea8C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BE8C55B0-3057-4F3D-AB5A-5791EEA8D946.dll
PE	 34a0000- 34aa000	Deferred        2ead7434-29d5-4ca1-9700-b6a770fbC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2EAD7434-29D5-4CA1-9700-B6A770FBD7F7.dll
PE	 34b0000- 34b9000	Deferred        keeprunning
PE	 34c0000- 3521000	Deferred        windowhandler
PE	 3530000- 3535000	Deferred        a488e6b9-0da7-4e32-a2e6-0510cbe8C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A488E6B9-0DA7-4E32-A2E6-0510CBE81B41.dll
PE	 3540000- 3545000	Deferred        145d3b82-fdc2-4925-a66b-7dcfff02C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\145D3B82-FDC2-4925-A66B-7DCFFF022A97.dll
PE	 3550000- 363a000	Deferred        sendwm_copydata
PE	 3640000- 3660000	Deferred        6514fe12-88cf-480b-a3d8-7730c0cdC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\6514FE12-88CF-480B-A3D8-7730C0CD23B3.dll
PE	 3660000- 3668000	Deferred        2346a6df-5942-4cb5-9908-e59cec72C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2346A6DF-5942-4CB5-9908-E59CEC72841F.dll
PE	 3670000- 3677000	Deferred        09f292f7-25db-49f7-a863-83dcd2abC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\09F292F7-25DB-49F7-A863-83DCD2ABC616.dll
PE	 3680000- 3692000	Deferred        texter_unicode
PE	 36a0000- 36b1000	Deferred        texter_unicode_draw
PE	 36c0000- 36cf000	Deferred        languagepack_translate
PE	 36d0000- 39f6000	Deferred        languagepack
PE	 3a00000- 3a07000	Deferred        0e43f737-c7aa-491d-b3a5-c6b0d9dcC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\0E43F737-C7AA-491D-B3A5-C6B0D9DC6483.dll
PE	 3a10000- 3a15000	Deferred        bdac0fbf-aee8-4e6c-918c-2672f890C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BDAC0FBF-AEE8-4E6C-918C-2672F89026E4.dll
PE	 3a20000- 3a25000	Deferred        e34823ce-646e-46fe-8b36-0b9483abC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\E34823CE-646E-46FE-8B36-0B9483ABB6F5.dll
PE	 3a30000- 3a38000	Deferred        4de5b0c2-ddac-4927-ac0f-73d42286C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\4DE5B0C2-DDAC-4927-AC0F-73D422863D69.dll
PE	 3a40000- 3a4b000	Deferred        nvapi_query
PE	 3a50000- 3d40000	Deferred        http_fetch_unicode
PE	 3d40000- 3d49000	Deferred        7805644a-fb2c-4ba2-8a8b-3d73d441C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7805644A-FB2C-4BA2-8A8B-3D73D441D338.dll
PE	 3d50000- 3d56000	Deferred        xinput_poll
PE	 3d60000- 3d76000	Deferred        xinput1_3
PE	 3e90000- 3e95000	Deferred        b028b538-d554-434b-88ce-aa79a717C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\B028B538-D554-434B-88CE-AA79A717C396.dll
PE	 4720000- 4807000	Deferred        xml_setrootnode
PE	 4810000- 4822000	Deferred        awesomiumquest
PE	 4830000- 4b1f000	Deferred        steamuserdata
PE	 6d40000- 6e13000	Deferred        steam
PE	 6fc0000- 6fc5000	Deferred        6918910a-f8ba-43c4-b8d4-cd6587d0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\6918910A-F8BA-43C4-B8D4-CD6587D0F67C.dll
PE	 6fd0000- 6fd6000	Deferred        092004e6-c5df-4027-8855-4825dd85C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\092004E6-C5DF-4027-8855-4825DD8527BC.dll
PE	 6fe0000- 6fe7000	Deferred        bed6ea12-2615-49cb-bbbf-67ee0ec7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BED6EA12-2615-49CB-BBBF-67EE0EC7AF8B.dll
PE	 6ff0000- 6ffc000	Deferred        steamstatdata
PE	 7000000- 7007000	Deferred        df5bf7f7-c204-4f6e-bdb8-666a53dfC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\DF5BF7F7-C204-4F6E-BDB8-666A53DFCC58.dll
PE	 7010000- 7015000	Deferred        7af0080e-c5c3-4be5-8fb9-a9e2cf6fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7AF0080E-C5C3-4BE5-8FB9-A9E2CF6FC9F1.dll
PE	 7020000- 7113000	Deferred        crypt
PE	 7120000- 720d000	Deferred        unicode_merge
PE	 7210000- 7217000	Deferred        fbb1d22b-cbb2-4a2a-aac3-4bb57f14C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\FBB1D22B-CBB2-4A2A-AAC3-4BB57F144FD4.dll
PE	 7220000- 7225000	Deferred        c0ef3703-84d2-4c4d-b9ff-bd8ade7eC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\C0EF3703-84D2-4C4D-B9FF-BD8ADE7E9AE4.dll
PE	 7230000- 7235000	Deferred        59283614-4e90-42b0-83a1-8fd22500C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\59283614-4E90-42B0-83A1-8FD225004619.dll
PE	 7240000- 7246000	Deferred        5f672c7f-7f68-408e-88ae-286a3f2fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\5F672C7F-7F68-408E-88AE-286A3F2F873A.dll
PE	 7250000- 7255000	Deferred        a19f6c27-85a3-45f3-a17b-9c1107e7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A19F6C27-85A3-45F3-A17B-9C1107E7A09A.dll
PE	 8230000- 8317000	Deferred        xml_nodetext
PE	 8320000- 8326000	Deferred        7d101bc8-e798-42ff-95e7-21690273C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7D101BC8-E798-42FF-95E7-216902731C0E.dll
PE	 8330000- 8335000	Deferred        2690162e-a224-4267-ae70-413d8c09C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2690162E-A224-4267-AE70-413D8C0912A8.dll
PE	 8350000- 8357000	Deferred        8a6078ed-69d4-4db4-9adb-a3987b26C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8A6078ED-69D4-4DB4-9ADB-A3987B26369A.dll
PE	 8360000- 836b000	Deferred        tune_forest
PE	 97a0000- a015000	Deferred        awesomium
PE	 a350000- a355000	Deferred        interpolaterotationquaternions
PE	 a360000- a36a000	Deferred        8c3d0983-cc73-4a3d-ab5a-9d40d9fdC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8C3D0983-CC73-4A3D-AB5A-9D40D9FD6E1D.dll
PE	 a730000- aa55000	Deferred        xml_node
PE	 c010000- c017000	Deferred        tunethruster
PE	 c020000- c02a000	Deferred        d5de69e6-690d-4a06-ace7-96bb1433C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\D5DE69E6-690D-4A06-ACE7-96BB143367DD.dll
PE	 c030000- c036000	Deferred        dccea252-c4a3-41ec-a6bd-c0517524C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\DCCEA252-C4A3-41EC-A6BD-C05175242006.dll
PE	 c040000- c045000	Deferred        c57a9d3f-0c29-41e0-b11e-bbed4c17C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\C57A9D3F-0C29-41E0-B11E-BBED4C17AAF8.dll
PE	 c050000- c059000	Deferred        cca74882-f05d-44d4-b07f-644a5550C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\CCA74882-F05D-44D4-B07F-644A55500151.dll
PE	 c060000- c067000	Deferred        2b10bae4-83a1-41f5-87cd-eb69473dC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2B10BAE4-83A1-41F5-87CD-EB69473D6538.dll
PE	 c090000- c095000	Deferred        a38dec0a-4740-452c-9832-41cb9332C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A38DEC0A-4740-452C-9832-41CB93324B4D.dll
PE	 c0e0000- c0ed000	Deferred        fb4b1f9a-ab55-4b60-98e2-e63d9ff5C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\FB4B1F9A-AB55-4B60-98E2-E63D9FF501D2.dll
PE	 c0f0000- c0f8000	Deferred        6ca8b1b9-2b59-4b6b-bd21-3755f934C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\6CA8B1B9-2B59-4B6B-BD21-3755F934DBFB.dll
PE	 c100000- c10c000	Deferred        tunewall
PE	 c110000- c116000	Deferred        87c266fd-5a43-419d-b402-44e1b0ffC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\87C266FD-5A43-419D-B402-44E1B0FFBE8F.dll
PE	 c220000- c225000	Deferred        bass_getlevels
PE	 c230000- c235000	Deferred        bass_getsongposition
PE	 c240000- c245000	Deferred        getfileattributes
PE	 c250000- c256000	Deferred        highwayfiledo
PE	 c260000- c26a000	Deferred        quicktime_getfft
PE	 f5f0000- f5f5000	Deferred        writeerror
PE	 f600000- f60f000	Deferred        18616469-e3a9-4ad7-af1b-c3fabc25C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\18616469-E3A9-4AD7-AF1B-C3FABC25E831.dll
PE	 f610000- f619000	Deferred        624fafe1-326d-4444-8768-d0d405feC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\624FAFE1-326D-4444-8768-D0D405FE0D23.dll
PE	 f620000- f626000	Deferred        8360311b-789b-4c30-896e-d3b77775C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8360311B-789B-4C30-896E-D3B77775044A.dll
PE	 f630000- f63f000	Deferred        customtexture_getvalidationstatuC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\CustomTexture_GetValidationStatus.dll
PE	 f640000- f645000	Deferred        ffd5db8c-e56b-49de-943e-0a7bf998C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\FFD5DB8C-E56B-49DE-943E-0A7BF998824F.dll
PE	 f650000- f655000	Deferred        ef1644cb-c99e-44b9-b07c-ec8a9e9fC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\EF1644CB-C99E-44B9-B07C-EC8A9E9F2CBA.dll
PE	 fe90000- fe96000	Deferred        customtexture_update
PE	 fea0000- fea6000	Deferred        customtexture
PE	 feb0000- feb6000	Deferred        f7709f2f-62cf-4d08-a1dc-bc736f85C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F7709F2F-62CF-4D08-A1DC-BC736F85E6DC.dll
PE	 fec0000- fed1000	Deferred        keyboardcapture_unicode
PE	 fee0000- fee5000	Deferred        3423dad4-77ed-4b4c-9f00-59cb5333C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\3423DAD4-77ED-4B4C-9F00-59CB533388C6.dll
PE	10000000-100c0000	Export          gameoverlayrenderer
PE	101d0000-101df000	Deferred        texter_unicode_command
PE	101e0000-101e5000	Deferred        8b1013fa-72c7-4794-817c-fe5178ecC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8B1013FA-72C7-4794-817C-FE5178EC7A24.dll
PE	101f0000-101f5000	Deferred        collisionobject_createtree
PE	10200000-1020c000	Deferred        basscd
PE	10fb0000-10fcf000	Deferred        eb69314c-9a02-43d7-bb94-ea27a32aC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\EB69314C-9A02-43D7-BB94-EA27A32AA120.dll
PE	10fd0000-10fd5000	Deferred        98813502-f9e2-4ddd-bb21-02762cf9C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\98813502-F9E2-4DDD-BB21-02762CF9583A.dll
PE	10fe0000-10fe5000	Deferred        ef17c559-44e9-49ca-9f8a-e2e5a7b0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\EF17C559-44E9-49CA-9F8A-E2E5A7B015EB.dll
PE	10ff0000-10ff9000	Deferred        xml_numchildnodes
PE	11000000-11062000	Deferred        bass
PE	181b0000-18298000	Deferred        readfileunicode
PE	18360000-18365000	Deferred        8dae38a8-c189-45dc-b634-f7f98ea0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8DAE38A8-C189-45DC-B634-F7F98EA0B43D.dll
PE	184f0000-184f6000	Deferred        8b959d25-5101-437b-a908-359e2ae3C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8B959D25-5101-437B-A908-359E2AE36CF2.dll
PE	18500000-18505000	Deferred        63c9809d-f615-4fed-a77c-b8f071aaC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\63C9809D-F615-4FED-A77C-B8F071AA3DB0.dll
PE	18510000-18515000	Deferred        bass_getdriveinfocd
PE	18520000-18525000	Deferred        2013b2a6-9cb0-4956-8080-d7efdbd5C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\2013B2A6-9CB0-4956-8080-D7EFDBD5386F.dll
PE	18530000-18535000	Deferred        f9ceb566-e5c4-4b13-9ddf-908fe6b6C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\F9CEB566-E5C4-4B13-9DDF-908FE6B6AFA4.dll
PE	18540000-18545000	Deferred        676d2de0-210e-4a1f-81aa-11cdb316C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\676D2DE0-210E-4A1F-81AA-11CDB316796A.dll
PE	18550000-18555000	Deferred        95117cd9-4859-4c6e-bc58-4f817e9dC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\95117CD9-4859-4C6E-BC58-4F817E9D5D4F.dll
PE	18560000-18565000	Deferred        04e1045f-0dcf-4fea-89a6-a1b4eb85C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\04E1045F-0DCF-4FEA-89A6-A1B4EB85ECFA.dll
PE	18570000-18575000	Deferred        getlogicaldrives
PE	18580000-18585000	Deferred        d7b36419-8613-49fe-ba20-27eef00bC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\D7B36419-8613-49FE-BA20-27EEF00BA7A5.dll
PE	18590000-185af000	Deferred        folderexploder
PE	185b0000-185bf000	Deferred        fetchunixtime
PE	185c0000-185c5000	Deferred        913c08c8-2386-4fb8-a21d-9ffba789C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\913C08C8-2386-4FB8-A21D-9FFBA789761A.dll
PE	185d0000-185d6000	Deferred        8ba3fb7b-c452-4ed1-bac4-52987724C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\8BA3FB7B-C452-4ED1-BAC4-529877249C28.dll
PE	185e0000-185e5000	Deferred        bb520aa0-6270-4ba9-ae0a-6863eb38C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\BB520AA0-6270-4BA9-AE0A-6863EB388CFE.dll
PE	185f0000-185f7000	Deferred        ebd84e0b-137a-45e2-a63e-ec1d9885C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\EBD84E0B-137A-45E2-A63E-EC1D98852828.dll
PE	18600000-18605000	Deferred        97e389c0-b889-4896-922c-843aadb0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\97E389C0-B889-4896-922C-843AADB02D7B.dll
PE	18610000-18615000	Deferred        bass_listen
PE	18620000-18629000	Deferred        bass_stop
PE	18630000-18635000	Deferred        bass_gettags
PE	18640000-18649000	Deferred        bass_setglobalvolume
PE	18650000-18657000	Deferred        quicktime_gettags
PE	18660000-1866a000	Deferred        bass_playbuffer
PE	18670000-18680000	Deferred        tagreader
PE	18680000-1868a000	Deferred        associativearray_value
PE	18690000-1869c000	Deferred        1bd8a232-b080-491b-a614-dbca30a7C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\1BD8A232-B080-491B-A614-DBCA30A77063.dll
PE	187a0000-187a7000	Deferred        tune_car
PE	187b0000-187ba000	Deferred        694fd196-d575-4e3e-ba5c-67d889a0C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\694FD196-D575-4E3E-BA5C-67D889A072DD.dll
PE	187c0000-18821000	Deferred        quicktime_loadmovie
PE	18830000-188b5000	Deferred        taglib
PE	188c0000-188c5000	Deferred        associativearray_value_clear
PE	188d0000-188da000	Deferred        bass_stream_loadorplay
PE	188e0000-188e9000	Deferred        bass_stream
PE	188f0000-188f5000	Deferred        dd2cd91d-2928-4324-bb1e-36dec301C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\DD2CD91D-2928-4324-BB1E-36DEC301E63C.dll
PE	18900000-18905000	Deferred        98012b2b-bf6c-4d22-bede-267f5901C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\98012B2B-BF6C-4D22-BEDE-267F5901889B.dll
PE	18910000-18915000	Deferred        clipcursortowindow
PE	18920000-18926000	Deferred        c682a43c-22b3-4cdd-a0ea-cf1b3faeC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\C682A43C-22B3-4CDD-A0EA-CF1B3FAE63D5.dll
PE	18b50000-18b55000	Deferred        a879b0b6-a589-4094-8a5a-9f3ddd19C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\A879B0B6-A589-4094-8A5A-9F3DDD191C0C.dll
PE	18c00000-18c07000	Deferred        9d28cd4b-2103-4e99-b1ee-c338242eC:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\9D28CD4B-2103-4E99-B1EE-C338242E165D.dll
PE	18c10000-18c17000	Deferred        809fd14e-c408-4de6-bc3d-ab69c472C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\809FD14E-C408-4DE6-BC3D-AB69C47238F6.dll
PE	18c30000-18c37000	Deferred        7a4813b2-0be6-408b-bd46-8a20e747C:\Program Files\Steam\steamapps\common\Audiosurf\engine\channels\7A4813B2-0BE6-408B-BD46-8A20E747A47E.dll
PE	1bf40000-1c027000	Deferred        xml_nodeattribute
PE	30000000-302c1000	Deferred        steam2
PE	38000000-38893000	Deferred        steamclient
PE	3b400000-3b41e000	Deferred        steam_api
PE	3f000000-3f0b2000	Deferred        tier0_s
PE	3f600000-3f64f000	Deferred        vstdlib_s
PE	4ad00000-4b547000	Deferred        icudt38
PE	60000000-60021000	Deferred        cserhelper
ELF	750ec000-751e0000	Deferred        comdlg32<elf>
  \-PE	750f0000-751e0000	\               comdlg32
ELF	773e8000-77434000	Deferred        dsound<elf>
  \-PE	773f0000-77434000	\               dsound
ELF	77434000-77533000	Deferred        quartz<elf>
  \-PE	77450000-77533000	\               quartz
ELF	786a9000-78800000	Deferred        msvcp80<elf>
  \-PE	786f0000-78800000	\               msvcp80
ELF	7892c000-78a00000	Deferred        msvcr80<elf>
  \-PE	78940000-78a00000	\               msvcr80
ELF	78b04000-78b4b000	Deferred        winspool<elf>
  \-PE	78b10000-78b4b000	\               winspool
ELF	78b4b000-78b8c000	Deferred        winhttp<elf>
  \-PE	78b50000-78b8c000	\               winhttp
ELF	78cd0000-78d1c000	Deferred        usp10<elf>
  \-PE	78ce0000-78d1c000	\               usp10
ELF	792b3000-7b800000	Deferred        libnvidia-glcore.so.337.25
ELF	7b800000-7ba6a000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba6a000	\               kernel32
ELF	7ba88000-7bc00000	Deferred        libvorbisenc.so.2
ELF	7bc00000-7bced000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bced000	\               ntdll
ELF	7bcf3000-7bd0a000	Deferred        midimap<elf>
  \-PE	7bd00000-7bd0a000	\               midimap
ELF	7be0a000-7bf00000	Deferred        libasound.so.2
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf19000-7bf45000	Deferred        libvorbis.so.0
ELF	7bf45000-7bf79000	Deferred        libflac.so.8
ELF	7bf79000-7bfeb000	Deferred        libsndfile.so.1
ELF	7c306000-7c31e000	Deferred        msacm32<elf>
  \-PE	7c310000-7c31e000	\               msacm32
ELF	7c31e000-7c38d000	Deferred        libpulsecommon-4.0.so
ELF	7c38d000-7c400000	Deferred        dbghelp<elf>
  \-PE	7c390000-7c400000	\               dbghelp
ELF	7c40b000-7c45a000	Deferred        libpulse.so.0
ELF	7c45a000-7c48b000	Deferred        netapi32<elf>
  \-PE	7c460000-7c48b000	\               netapi32
ELF	7c48b000-7c4c0000	Deferred        secur32<elf>
  \-PE	7c490000-7c4c0000	\               secur32
ELF	7c4c0000-7c4d9000	Deferred        imagehlp<elf>
  \-PE	7c4d0000-7c4d9000	\               imagehlp
ELF	7c4d9000-7c501000	Deferred        iphlpapi<elf>
  \-PE	7c4e0000-7c501000	\               iphlpapi
ELF	7c501000-7c573000	Deferred        setupapi<elf>
  \-PE	7c510000-7c573000	\               setupapi
ELF	7c573000-7c658000	Deferred        crypt32<elf>
  \-PE	7c580000-7c658000	\               crypt32
ELF	7c658000-7c7a2000	Deferred        msvcp71<elf>
  \-PE	7c6a0000-7c7a2000	\               msvcp71
ELF	7c7a6000-7c7ad000	Deferred        libnss_dns.so.2
ELF	7c7ad000-7c7b6000	Deferred        libogg.so.0
ELF	7c7b6000-7c7c0000	Deferred        libwrap.so.0
ELF	7c7c6000-7c7da000	Deferred        t2embed<elf>
  \-PE	7c7d0000-7c7da000	\               t2embed
ELF	7c7da000-7c7e1000	Deferred        libasound_module_pcm_pulse.so
ELF	7c7e8000-7c819000	Deferred        winealsa<elf>
  \-PE	7c7f0000-7c819000	\               winealsa
ELF	7c819000-7c83b000	Deferred        mmdevapi<elf>
  \-PE	7c820000-7c83b000	\               mmdevapi
ELF	7c83b000-7c872000	Deferred        uxtheme<elf>
  \-PE	7c840000-7c872000	\               uxtheme
ELF	7c872000-7c9a0000	Deferred        comctl32<elf>
  \-PE	7c880000-7c9a0000	\               comctl32
ELF	7c9a0000-7c9f0000	Deferred        dinput<elf>
  \-PE	7c9b0000-7c9f0000	\               dinput
ELF	7cb71000-7cb8e000	Deferred        libgcc_s.so.1
ELF	7cb8e000-7cbc6000	Deferred        ws2_32<elf>
  \-PE	7cba0000-7cbc6000	\               ws2_32
ELF	7cbc6000-7cbe1000	Deferred        dinput8<elf>
  \-PE	7cbd0000-7cbe1000	\               dinput8
ELF	7cc75000-7cca1000	Deferred        msvfw32<elf>
  \-PE	7cc80000-7cca1000	\               msvfw32
ELF	7cca1000-7ccc9000	Deferred        devenum<elf>
  \-PE	7ccb0000-7ccc9000	\               devenum
ELF	7d1c7000-7d2d2000	Deferred        libgl.so.1
ELF	7d2d2000-7d3e6000	Deferred        opengl32<elf>
  \-PE	7d2f0000-7d3e6000	\               opengl32
ELF	7d3e6000-7d3ea000	Deferred        libgpg-error.so.0
ELF	7d3ea000-7d402000	Deferred        libresolv.so.2
ELF	7d402000-7d44d000	Deferred        libdbus-1.so.3
ELF	7d44d000-7d4c1000	Deferred        libgcrypt.so.11
ELF	7d4c1000-7d4d1000	Deferred        libtasn1.so.3
ELF	7d4d1000-7d4dd000	Deferred        libkrb5support.so.0
ELF	7d4dd000-7d50d000	Deferred        libk5crypto.so.3
ELF	7d50d000-7d5cb000	Deferred        libkrb5.so.3
ELF	7d5cb000-7d5dd000	Deferred        libavahi-client.so.3
ELF	7d5dd000-7d675000	Deferred        libgnutls.so.26
ELF	7d675000-7d6ba000	Deferred        libgssapi_krb5.so.2
ELF	7d6ba000-7d727000	Deferred        libcups.so.2
ELF	7d72b000-7d736000	Deferred        libjson-c.so.2
ELF	7d77a000-7d796000	Deferred        jsproxy<elf>
  \-PE	7d780000-7d796000	\               jsproxy
ELF	7d813000-7d817000	Deferred        libkeyutils.so.1
ELF	7d819000-7d820000	Deferred        libasyncns.so.0
ELF	7d89e000-7d8a3000	Deferred        libnvidia-tls.so.337.25
ELF	7d8cb000-7da32000	Deferred        wined3d<elf>
  \-PE	7d8e0000-7da32000	\               wined3d
ELF	7da32000-7da70000	Deferred        d3d9<elf>
  \-PE	7da40000-7da70000	\               d3d9
ELF	7da70000-7db3a000	Deferred        msvcrt<elf>
  \-PE	7da90000-7db3a000	\               msvcrt
ELF	7db3a000-7dbfd000	Deferred        msvcr71<elf>
  \-PE	7db50000-7dbfd000	\               msvcr71
ELF	7dc08000-7dc1c000	Deferred        avicap32<elf>
  \-PE	7dc10000-7dc1c000	\               avicap32
ELF	7dc62000-7dc68000	Deferred        libxfixes.so.3
ELF	7dc68000-7dc73000	Deferred        libxcursor.so.1
ELF	7dc73000-7dc84000	Deferred        libxi.so.6
ELF	7dc84000-7dc88000	Deferred        libxcomposite.so.1
ELF	7dc88000-7dc93000	Deferred        libxrandr.so.2
ELF	7dc93000-7dc9e000	Deferred        libxrender.so.1
ELF	7dc9e000-7dca4000	Deferred        libxxf86vm.so.1
ELF	7dca4000-7dca8000	Deferred        libxinerama.so.1
ELF	7dca8000-7dcaf000	Deferred        libxdmcp.so.6
ELF	7dcaf000-7dcb3000	Deferred        libxau.so.6
ELF	7dcb3000-7dcd5000	Deferred        libxcb.so.1
ELF	7dcd5000-7de09000	Deferred        libx11.so.6
ELF	7de09000-7de1c000	Deferred        libxext.so.6
ELF	7de1c000-7de21000	Deferred        libcom_err.so.2
ELF	7de21000-7de2f000	Deferred        libavahi-common.so.3
ELF	7de2f000-7de42000	Deferred        psapi<elf>
  \-PE	7de30000-7de42000	\               psapi
ELF	7de44000-7dee5000	Deferred        winex11<elf>
  \-PE	7de50000-7dee5000	\               winex11
ELF	7df57000-7df80000	Deferred        libexpat.so.1
ELF	7df80000-7dfbb000	Deferred        libfontconfig.so.1
ELF	7dfbb000-7dfe3000	Deferred        libpng12.so.0
ELF	7dfe3000-7e083000	Deferred        libfreetype.so.6
ELF	7e0ab000-7e0d1000	Dwarf           imm32<elf>
  \-PE	7e0b0000-7e0d1000	\               imm32
ELF	7e0d1000-7e0fc000	Deferred        msacm32<elf>
  \-PE	7e0e0000-7e0fc000	\               msacm32
ELF	7e0fc000-7e1ba000	Deferred        winmm<elf>
  \-PE	7e100000-7e1ba000	\               winmm
ELF	7e1ba000-7e1e1000	Deferred        mpr<elf>
  \-PE	7e1c0000-7e1e1000	\               mpr
ELF	7e1e1000-7e1f5000	Deferred        libz.so.1
ELF	7e1f5000-7e27e000	Deferred        wininet<elf>
  \-PE	7e200000-7e27e000	\               wininet
ELF	7e27e000-7e2fa000	Deferred        shlwapi<elf>
  \-PE	7e290000-7e2fa000	\               shlwapi
ELF	7e2fa000-7e539000	Deferred        shell32<elf>
  \-PE	7e310000-7e539000	\               shell32
ELF	7e539000-7e689000	Deferred        oleaut32<elf>
  \-PE	7e550000-7e689000	\               oleaut32
ELF	7e689000-7e717000	Deferred        rpcrt4<elf>
  \-PE	7e690000-7e717000	\               rpcrt4
ELF	7e717000-7e851000	Deferred        gdi32<elf>
  \-PE	7e720000-7e851000	\               gdi32
ELF	7e851000-7e9d4000	Dwarf           user32<elf>
  \-PE	7e860000-7e9d4000	\               user32
ELF	7e9d4000-7ea48000	Deferred        advapi32<elf>
  \-PE	7e9e0000-7ea48000	\               advapi32
ELF	7ea48000-7eb98000	Deferred        ole32<elf>
  \-PE	7ea60000-7eb98000	\               ole32
ELF	7eb98000-7ec42000	Deferred        urlmon<elf>
  \-PE	7eba0000-7ec42000	\               urlmon
ELF	7ec42000-7ec4f000	Deferred        libnss_files.so.2
ELF	7ec4f000-7ec68000	Deferred        libnsl.so.1
ELF	7ec76000-7ec90000	Deferred        version<elf>
  \-PE	7ec80000-7ec90000	\               version
ELF	f73a1000-f73ad000	Deferred        libnss_nis.so.2
ELF	f73af000-f73f5000	Deferred        libm.so.6
ELF	f73f5000-f73fa000	Deferred        libdl.so.2
ELF	f73fa000-f75a9000	Deferred        libc.so.6
ELF	f75a9000-f75c5000	Deferred        libpthread.so.0
ELF	f75c7000-f75d0000	Deferred        libnss_compat.so.2
ELF	f75e5000-f75ee000	Deferred        librt.so.1
ELF	f75ee000-f77a5000	Dwarf           libwine.so.1
ELF	f77a7000-f77c9000	Deferred        ld-linux.so.2
ELF	f77c9000-f77ca000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 Steam.exe
	00000016    0
	0000002d    0
	0000002c    0
	00000029    0
	00000028    0
	00000027    0
	00000026    0
	0000001c    0
	00000030    0
	0000002e    0
	0000002f    0
	00000024    0
	00000025    0
	0000000d    0
	0000000c    0
	00000047    0
	00000046    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
	0000003d    0
	0000003c    0
	0000003b    0
	0000003a    0
	00000039    0
	00000038    0
	00000037    0
	00000036    0
	00000009    0
0000000e services.exe
	00000031    0
	0000001b    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001f    0
	00000018    0
	00000017    0
	00000013    0
00000019 plugplay.exe
	0000001e    0
	0000001d    0
	0000001a    0
00000022 explorer.exe
	00000023    0
00000033 (D) C:\Program Files\Steam\SteamApps\common\Audiosurf\engine\QuestViewer.exe
	00000055    0
	0000005e    0
	0000005d    0
	0000005c    0
	0000005b    0
	0000002a    0
	00000045    0
	00000032    0
	0000002b    0 <==
00000034 GameOverlayUI.exe
	00000053    0
	00000051    0
	00000050    0
	0000004f    0
	0000004e    0
	0000004d    0
	0000004c    0
	0000004b    0
	0000004a    0
	00000049    0
	00000048    0
	00000035    0
System information:
    Wine build: wine-1.7.23
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-24-generic

```

So does anyone knows a solution, I love audiosurf and linux, I do not want to use windows :D 

Thank you for your time

---

