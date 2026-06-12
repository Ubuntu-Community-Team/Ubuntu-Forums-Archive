---
title: "Help needed in installing Matlab"
date: 2008-02-08
forum: Wine
---

### Post by junaid02 on 2008-02-08
I have installed the Matlab R2007b using wine on my system 
but when i try to run the matlab i get the following error:


err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library libut.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_dispatcher.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\xerces-c_2_7.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\xerces-c_2_7.dll") not found
err:module:import_dll Library xerces-c_2_7.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\icuin36.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\icuin36.dll") not found
err:module:import_dll Library icuin36.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library icuio36.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\libut.dll") not found
err:module:import_dll Library libut.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mpath.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mpath.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mpath.dll") not found
err:module:import_dll Library mpath.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_dispatcher.dll") not found
err:module:import_dll Library xerces-c_2_7.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_dispatcher.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_dispatcher.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_dispatcher.dll") not found
err:module:import_dll Library m_dispatcher.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library m_ir.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library m_parser.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library m_pcodegen.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library m_pcodeio.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library mcos.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library mpath.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library profiler.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library xerces-c_2_7.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library boost_thread-vc80-mt-1_33_1.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\m_interpreter.dll") not found
err:module:import_dll Library m_interpreter.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\bridge.dll") not found
err:module:import_dll Library mpath.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\bridge.dll") not found
err:module:import_dll Library udd.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\bridge.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\bridge.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\bridge.dll") not found
err:module:import_dll Library bridge.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library comcli.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library hg.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library iqm.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library jmi.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library libmex.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library libmwgui.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library libmwservices.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library libmx.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library libut.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library m_dispatcher.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library m_interpreter.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mcos.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mlautoregister.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mpath.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mwoles05.DLL (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library udd_mi.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mcr.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\MATLAB.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\MATLAB.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MATLAB\\R2007b\\bin\\win32\\MATLAB.exe" failed, status c0000135

i can't figure out what  should i install in order to run matlab so can anybody help me with this 
any help in this regards will be appreciated 
Thanx in advance

---

### Post by jrib on 2008-02-08
Why use wine?  There's a native linux program on the cd.  See:
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by tshearman on 2008-03-01
bump

I'm having the same issue...

Is the native version free?  I already have the Windows version though school.  If so, where do i get it?!

Else, is there another solution so I can run MATLAB R2007B though wine?

Thanks

---

### Post by jrib on 2008-03-02
> **tshearman said:**
> 
Is the native version free?  I already have the Windows version though school.  If so, where do i get it?!


It is on the same set of CDs last time I used it.  Check the link in my last post

---

### Post by amd-64 on 2008-03-02
If you insist on installing the windows version, I suggest creating a windows virtual machine on virtualbox.  The virtualbox deb is in the repos, use synaptic or adept to install. You will need the install media for windows xp or win2k. I dont know if matlab will run on anything older than that.

---

