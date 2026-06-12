---
title: "Runtime error '5'"
date: 2014-09-13
forum: Wine
---

### Post by hansmaricou on 2014-09-13
Hi, i' m using Ubuntu for 4 years now and i can do almost everything that i used to do in my windows-time. Now, however i installed a program (WinToets, there is no alternative, it's connected to my educational profession and yes some windowscolleagues mentioned the joke: of course it doesn't work, it's 'Win'Toets). So, to proove them wrong and to continue doing everything on my Ubuntu-pc i would need some advice.
I installed it properly in playonlinux, i installed Windows Media Player 10 or 11 (there was an error about that) but now i have a new error
Runtime error '5': invalid procedure call or argument

Anyone who deal with this problem? Thanks in advance,

Hans

a log gave me this information:
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b72398,0x00000010,0x33eef0) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b72398,0x00000020,0x33eef0) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de50) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de50) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1b744e8,0x00000010,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1b744e8,0x00000020,0x33de40) stub[/FONT]
[FONT=arial]fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION[/FONT]
[FONT=arial]fixme:msxml:domdoctype_get_nextSibling (0x1b8f1d0)->(0x33ef1c): stub[/FONT]
[FONT=arial]fixme:msxml:domdoctype_get_nextSibling (0x1b84800)->(0x33ef1c): stub[/FONT]
[FONT=arial]fixme:msxml:domdoctype_get_nextSibling (0x1b85268)->(0x33ef1c): stub[/FONT]
[FONT=arial]fixme:msxml:domdoctype_get_nextSibling (0x1b82090)->(0x33ef1c): stub[/FONT]
[FONT=arial]fixme:msxml:domdoctype_get_nextSibling (0x1b92568)->(0x33ef1c): stub[/FONT]
[FONT=arial]err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered[/FONT]
[FONT=arial]err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,774,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f864), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x355e930), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x355c9c0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x355ca60), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35630a0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563140), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35631e0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563400), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35634a0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563540), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35635e0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563748), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35637e8), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563888), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35639f0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563ad8), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563b50), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563bf0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563da0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563e50), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3563f00), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3564258), partially implemented.[/FONT]
[FONT=arial]fixm[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35642d0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3564348), partially implemented.[/FONT]
[FONT=arial]fixm[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35643c0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3564460), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3564500), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35645a0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35646e0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x35647a8), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15a62ac,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=16,y=16,f=0,0x3564910), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OleLoadPictureEx (0x15bca3c,2822,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f4b0), partially implemented.[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...[/FONT]
[FONT=arial]fixme[/FONT][FONT=arial]:o[/FONT][FONT=arial]lepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons[/FONT]

---

### Post by EuclideanCoffee on 2014-09-15
Hi hans, are you installing [COLOR=#000000]WinToets or Windows Player 10 or 11?

Thanks![/COLOR]

---

