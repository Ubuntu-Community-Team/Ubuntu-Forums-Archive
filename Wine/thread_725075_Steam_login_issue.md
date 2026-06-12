---
title: "Steam login issue"
date: 2008-03-15
forum: Wine
---

### Post by jabir667 on 2008-03-15
I'm having problems getting steam to work on wine.
I have the latest version of wine with gecko and all the fonts stuff
I can get it to update but when I try to login is says that my login doesn't exist blah blah blah

here is the stuff in terminal I am a noob so i don't know what is wrong

cd ~/.wine/drive_c/Program\ Files/Steam
[email]jabir667@jabir667-laptop:~/.wine[/email]/drive_c/Program Files/Steam$ nice -n 19 wine Steam.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
[email]jabir667@jabir667-laptop:~/.wine[/email]/drive_c/Program Files/Steam$ fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
registry.cpp (81) : Assertion Failed: REG_SZ == dwType
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:ViewObject_SetAdvise (0x1aadd0)->(1 00000002 0x1482310)
fixme:shdocvw:PersistStreamInit_InitNew (0x1aadd0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1aadd0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1aadd0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1abaa8)->(1 00000002 0x1482340)
fixme:shdocvw:PersistStreamInit_InitNew (0x1abaa8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1abaa8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1abaa8)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2003a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2003a,0x00000000,110,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2003a,0x00000000,110,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2003a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,56,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,56,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,238,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,238,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,172,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,172,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,123,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,79,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,64,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,32,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,20,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10040,0x00000000,0,2): stub!

thx for the help

---

