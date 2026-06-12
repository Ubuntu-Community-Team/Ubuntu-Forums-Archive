---
title: "Flash Software - Mouse Moves, But Won't Click"
date: 2013-02-08
forum: Wine
---

### Post by Kirk Schnable on 2013-02-08
I have been asked to get one of those "full screen Windows Flash programs" (you know the type of software I mean...) to work on Linux.  I do not usually have issues getting them working, but I've hit a bit of an issue this time around.

The software I'm trying to get working is Hampton Brown Online Coach.

I am using **PlayOnLinux 4.1.9** and 32-bit **WINE 1.5.23**.

When you first start the software, you get a full screen splash page as expected. 

[img]http://binaryimpulse.com/wp-content/uploads/2013/02/Screenshot-02082013-083929-AM.png[/img]

However, then, the Start button can't be clicked.  The only way to get past the splash screen is to highlight it with the mouse and press the Enter key.

[img]http://binaryimpulse.com/wp-content/uploads/2013/02/Screenshot-02082013-083942-AM.png[/img]

On the next screen, I have not found a way to get anything on this interface to actually function.  As you can see from the Options button on top, mouse-over text captions appear, etc... the mouse movement works, it just won't click.

[img]http://binaryimpulse.com/wp-content/uploads/2013/02/Screenshot-02082013-084010-AM.png[/img]


You can view the PlayOnLinux debug log [here]("http://binaryimpulse.com/wp-content/uploads/2013/02/hbedge-debug.txt") or below.

As with any WINE run, there are plenty of errors... hopefully one of these will help us to identify the problem with the mouse.

```
[02/08/13 08:37:55] - Running wine-1.5.23 SUPReaderMain.exe (Working directory : /home/user/.PlayOnLinux/wineprefix/HBEdge/drive_c/Program Files/Hampton-Brown/Online Coach)
fixme:ieframe:OleObject_Advise (0x146290)->(0x899e98, 0x899ee4)
fixme:ieframe:ViewObject_SetAdvise (0x146290)->(1 00000000 0x899e98)
fixme:ieframe:ViewObject_Draw (0x146290)->(1 -1 (nil) (nil) (nil) 0x2a0044 0x899efc 0x899efc (nil) 00000000)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f100,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {f9d8d64e-a144-47dc-8ee0-f53498372c29} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {728dcf55-128f-4dd1-ad22-becfa66ce7aa} could be created for context 0x1
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {00000003-0000-0000-c000-000000000046}
fixme:quartz:Parser_QueryInterface No interface for {2dd74950-a890-11d1-abe8-00a0c905f375}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:strmbase:TransformFilterImpl_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:secur32:schan_imp_create_session Using hardcoded "NORMAL" priority
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_UpdatePositions Underrun of data occurred!
ALSA lib pcm.c:7339:(snd_pcm_recover) underrun occurred
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea70,0x00000000), stub!
fixme:secur32:schan_imp_create_session Using hardcoded "NORMAL" priority
fixme:secur32:schan_imp_create_session Using hardcoded "NORMAL" priority
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {f9d8d64e-a144-47dc-8ee0-f53498372c29} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {728dcf55-128f-4dd1-ad22-becfa66ce7aa} could be created for context 0x1
fixme:strmbase:MemInputPin_NotifyAllocator Read only flag not handled yet!
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {00000003-0000-0000-c000-000000000046}
fixme:quartz:Parser_QueryInterface No interface for {2dd74950-a890-11d1-abe8-00a0c905f375}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:strmbase:TransformFilterImpl_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
err:quartz:ACMWrapper_Receive Error sending sample (80040227)
fixme:ieframe:ViewObject_SetAdvise (0x146290)->(1 00000000 (nil))
fixme:ieframe:OleObject_Unadvise (0x146290)->(1802465100)
```

Anybody have any suggestions on how to proceed?

Thanks!
Kirk

---

