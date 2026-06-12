---
title: "*** glibc detected *** /usr/bin/python: munmap_chunk(): invalid pointer"
date: 2008-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by vvinuv on 2008-02-24
Hi All
I am working with Intel 64 bit core 2 duo processor and having a RAM of 2GB. I am getting the following error when I tried to run a python module, pyraf.

*** glibc detected *** /usr/bin/python: munmap_chunk(): invalid pointer: 0x00002aaabfafe010 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2b1e3be58826]
/usr/lib/python2.5/site-packages/numpy/core/multiarray.so[0x2aaaaba3acbe]
/usr/bin/python[0x4434ec]
/usr/bin/python[0x421f73]
/usr/bin/python(PyEval_EvalFrameEx+0x3113)[0x485413]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python(PyEval_EvalFrameEx+0x5c32)[0x487f32]
/usr/bin/python(PyEval_EvalFrameEx+0x693e)[0x488c3e]
/usr/bin/python(PyEval_EvalFrameEx+0x693e)[0x488c3e]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python(PyEval_EvalFrameEx+0x5c32)[0x487f32]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python[0x4d437e]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
/usr/bin/python(PyEval_CallObjectWithKeywords+0x72)[0x481322]
/usr/bin/python[0x480c24]
/usr/bin/python(PyEval_EvalFrameEx+0x67f7)[0x488af7]
/usr/bin/python(PyEval_EvalFrameEx+0x693e)[0x488c3e]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python(PyEval_EvalFrameEx+0x5c32)[0x487f32]
/usr/bin/python(PyEval_EvalFrameEx+0x693e)[0x488c3e]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python[0x4d437e]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
/usr/bin/python(PyEval_EvalFrameEx+0x4697)[0x486997]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python[0x4d437e]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
/usr/bin/python[0x41e5ed]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
/usr/bin/python(PyEval_CallObjectWithKeywords+0x72)[0x481322]
/usr/lib/python2.5/lib-dynload/_tkinter.so[0x2b1e3e2f0b4c]
/usr/lib/libtcl8.4.so.0(TclInvokeStringCommand+0x69)[0x2b1e3ea55889]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x332)[0x2b1e3ea57162]
/usr/lib/libtcl8.4.so.0[0x2b1e3ea7ff29]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x2b1e3ea8338e]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjEx+0x70)[0x2b1e3ea58050]
/usr/lib/libtk8.4.so.0[0x2b1e3e781785]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x332)[0x2b1e3ea57162]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjv+0xe3)[0x2b1e3ea57ee3]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjEx+0x225)[0x2b1e3ea58205]
/usr/lib/libtcl8.4.so.0(Tcl_UplevelObjCmd+0x130)[0x2b1e3eaaba10]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x332)[0x2b1e3ea57162]
/usr/lib/libtcl8.4.so.0[0x2b1e3ea7ff29]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x2b1e3ea8338e]
/usr/lib/libtcl8.4.so.0(TclObjInterpProc+0x211)[0x2b1e3eaab291]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x332)[0x2b1e3ea57162]
/usr/lib/libtcl8.4.so.0(Tcl_EvalEx+0x38b)[0x2b1e3ea5765b]
/usr/lib/libtk8.4.so.0(Tk_BindEvent+0x82c)[0x2b1e3e75a83c]
/usr/lib/libtk8.4.so.0(TkBindEventProc+0x178)[0x2b1e3e75f878]
/usr/lib/libtk8.4.so.0(Tk_HandleEvent+0x311)[0x2b1e3e764d41]
/usr/lib/libtk8.4.so.0[0x2b1e3e7652cc]
/usr/lib/libtcl8.4.so.0(Tcl_ServiceEvent+0x75)[0x2b1e3eaa1945]
/usr/lib/libtcl8.4.so.0(Tcl_DoOneEvent+0x8e)[0x2b1e3eaa1bde]
/usr/lib/python2.5/lib-dynload/_tkinter.so[0x2b1e3e2eec47]
/usr/bin/python(PyEval_EvalFrameEx+0x67f7)[0x488af7]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python(PyEval_EvalFrameEx+0x5c32)[0x487f32]
/usr/bin/python(PyEval_EvalCodeEx+0x830)[0x489d60]
/usr/bin/python[0x4d437e]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
/usr/bin/python[0x41e5ed]
/usr/bin/python(PyObject_Call+0x13)[0x417e53]
======= Memory map: ========
00400000-00521000 r-xp 00000000 08:04 1815946                            /usr/bin/python2.5
00720000-00752000 rw-p 00120000 08:04 1815946                            /usr/bin/python2.5
00752000-05a00000 rw-p 00752000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rwxp 40001000 00:00 0 
2aaaaaaac000-2aaaaaaed000 rw-p 2aaaaaaac000 00:00 0 
2aaaaaaee000-2aaaaab2f000 rw-p 2aaaaaaee000 00:00 0 
2aaaaab2f000-2aaaaab3b000 r-xp 00000000 08:04 1930749                    /usr/lib/python2.5/lib-dynload/_socket.so
2aaaaab3b000-2aaaaad3a000 ---p 0000c000 08:04 1930749                    /usr/lib/python2.5/lib-dynload/_socket.so
2aaaaad3a000-2aaaaad3e000 rw-p 0000b000 08:04 1930749                    /usr/lib/python2.5/lib-dynload/_socket.so
2aaaaad3e000-2aaaaad42000 r-xp 00000000 08:04 1930751                    /usr/lib/python2.5/lib-dynload/_ssl.so
2aaaaad42000-2aaaaaf42000 ---p 00004000 08:04 1930751                    /usr/lib/python2.5/lib-dynload/_ssl.so
2aaaaaf42000-2aaaaaf43000 rw-p 00004000 08:04 1930751                    /usr/lib/python2.5/lib-dynload/_ssl.so
2aaaaaf5b000-2aaaaaf9f000 r-xp 00000000 08:04 1815859                    /usr/lib/libssl.so.0.9.8
2aaaaaf9f000-2aaaab19e000 ---p 00044000 08:04 1815859                    /usr/lib/libssl.so.0.9.8
2aaaab19e000-2aaaab1a4000 rw-p 00043000 08:04 1815859                    /usr/lib/libssl.so.0.9.8
2aaaab1a4000-2aaaab2ff000 r-xp 00000000 08:04 1815377                    /usr/lib/libcrypto.so.0.9.8
2aaaab2ff000-2aaaab4ff000 ---p 0015b000 08:04 1815377                    /usr/lib/libcrypto.so.0.9.8
2aaaab4ff000-2aaaab522000 rw-p 0015b000 08:04 1815377                    /usr/lib/libcrypto.so.0.9.8
2aaaab522000-2aaaab525000 rw-p 2aaaab522000 00:00 0 
2aaaab525000-2aaaab53b000 r-xp 00000000 08:04 3924674                    /usr/lib/libz.so.1.2.3.3
2aaaab53b000-2aaaab73b000 ---p 00016000 08:04 3924674                    /usr/lib/libz.so.1.2.3.3
2aaaab73b000-2aaaab73c000 rw-p 00016000 08:04 3924674                    /usr/lib/libz.so.1.2.3.3
2aaaab73c000-2aaaab7fd000 rw-p 2aaaab73c000 00:00 0 
2aaaab7fd000-2aaaab804000 r-xp 00000000 08:04 1930775                    /usr/lib/python2.5/lib-dynload/operator.so
2aaaab804000-2aaaaba04000 ---p 00007000 08:04 1930775                    /usr/lib/python2.5/lib-dynload/operator.so
2aaaaba04000-2aaaaba06000 rw-p 0000700Abort (core dumped)



Does anybody knows what is the reason? I have installed nspluginwrapper to play flash on my machine. Does it cause any problem? If it causes how I can I solve it?
Thanks
Vinu V

---

