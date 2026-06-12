---
title: "errors reganding dc++"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tzepu on 2008-03-01
hello all i am a rookie in using ubuntu(that is why please explain as good as you can how to solve my problems
i have an acer laptop and using on it ubuntu 7.10 for AMD64(dual boot with vista 64)
i try for a week now(i read dozens of threads ) to make my dc++ client work 
the only one that i solved is valknut(it works good but i am not pleased about it (ugly gui, very few options, hard to work with it)
i tried to use linuxdcpp, i installed it, but the program closes after it loads users list
if i run it in terminal this it what it happens
Loading: Hash database
Loading: Shared Files
Loading: Download Queue

** ERROR **: file gailtreeview.c: line 3724 (traverse_cells): assertion failed: (row_path != NULL)
aborting...
Aborted (core dumped)
and this is it
i reinstalled it few times i got the same error
once(sorry but  i do not remember what i did then) it game me another error (i mean that the program starts, but in the next second it stops loading anything, i see only a window with the name of the program on top, and hat is it, i have to force stop the program)

i tried to run apexdc++ under wine but i got 2 errors depending on hells now what an the program behave like this
i start the apexdc++ from wine and all i get is a black window that pops up few seconds and vanishes after this
after updating wine today it allowed me to open it but all buttons were black, but after seting it up, now i tells me that apexdc++ has crashed and i have to report this

this window pops up sometimes

Code: 80000100 ()
Version: 1.0.0B5 (2008-01-19)
Major: 6
Minor: 0
Build: 6000
SP: 0
Type: 1
Time: 2008-03-01 13:38:14
TTH: DG4ICKXKUNA6R2YF2HMKZYRSDKEU6HQMB4IE44Y

kernel32!0x7B84174A: RaiseException
gdiplus!0x7E468E35: ?
gdiplus!0x7E459E34: ?
apexdc!0x0042F597: ATL::CImage::Load
apexdc!0x0042F67F: ExCImage::LoadFromResource
apexdc!0x0042F5F5: ExCImage::ExCImage
apexdc!0x00453A49: MainFrame::createWinampToolbar
apexdc!0x00452AA0: MainFrame::OnCreate
apexdc!0x0044BEB9: MainFrame::ProcessWindowMessage
apexdc!0x0046139A: WTL::CMDIFrameWindowImpl<MainFrame=0x00000000,WTL::CMDIWindow=0x00000001,ATL::CWinTraits<114229248=0x00000000,262400> >::MDIFrameWindowProc
user32!0x7EC8168A: WINPROC_wrapper
user32!0x7EC81A15: WINPROC_wrapper
user32!0x7EC88293: ?
user32!0x7EC4C9D6: ?
user32!0x7EC5014D: ?
user32!0x7EC5062C: SendMessageW
user32!0x7EC79E42: ?
user32!0x7EC7B02D: CreateWindowExW
apexdc!0x00448603: WTL::CMDIFrameWindowImpl<MainFrame=0x0000C037,WTL::CMDIWindow=0x0032F0F0,ATL::CWinTraits<114229248=0x0032EED0,262400> >::Create
apexdc!0x0044854D: WTL::CMDIFrameWindowImpl<MainFrame=0x0032F0F0,WTL::CMDIWindow=0x00040100,ATL::CWinTraits<114229248=0x0032FE44,262400> >::CreateEx
apexdc!0x00448020: Run
apexdc!0x0044844D: wWinMain
apexdc!0x00545065: __tmainCRTStartup
kernel32!0x7B8708B1: ?
can anybody help me with this?
i need linuxdcpp or apexdc++
if anyone know how to solve this please be as detailed as posible
thank you in advance
ah and i noticed that even if i uninstall apex i keep seeing its icon in wine

---

