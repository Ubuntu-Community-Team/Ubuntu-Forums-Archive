---
title: "cisco anyconnect won't install"
date: 2017-01-18
forum: Wine
---

### Post by asb3 on 2017-01-18
I need to connect my linux computer (16.04 LTS) to my work network using vpn.  They seem to only support the software token.  For windows machines, they supply cisco anyconnect. I tried to install anyconnect using wine and it failed and threw the following error:
$ wine Setup.exe 
fixme:advapi:RegisterEventSourceA ((null),"acvpninstall"): stub
fixme:advapi:RegisterEventSourceW (L"",L"acvpninstall"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0001,0x24000002,(nil),0x0001,0x00000000,0x33f084,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0001,0x24000002,(nil),0x0001,0x00000000,0x158360,(nil)): stub
err:eventlog:ReportEventW L"Function: wWinMain\nFile: Setup.cpp\nLine: 159\nInvoked Function: ShellExecute\nReturn Code: 0 (0x00000000)\nDescription: Unable to invoke Z:\\home\\asb\\Downloads\\vpnclient4\\setup.hta\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

Any ideas for a fix?

---

