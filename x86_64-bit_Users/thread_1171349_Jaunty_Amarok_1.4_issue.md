---
title: "Jaunty: Amarok 1.4 issue"
date: 2009-05-27
forum: x86 64-bit Users
---

### Post by Fluffy13 on 2009-05-27
System is a Gateway FX6831 Intel based 64Bit laptop.

I upgraded to 64bit Jaunty in hopes that my speakers would work (they didnt in 32bit, did with hardy). Anyway i have now broken Amarok. I followed the same guide i used for 32 bit to remove Amarok 2 and install Amarok 1.4.

The problem is when i import my mp3's Amarok claims it has no mp3 support. Wether i click install or cancel Amarok crashes and gives me the following error via kmail. Audacious is working fine, but i really liked Amarok. I tried multiple times to completely remove and reinstall it, and nothing. Eveyrhting done via terminal if that matters.

Any ideas?

```

 p, li { white-space: pre-wrap; }  Amarok has crashed! We are terribly sorry about this :(
 
 But, all is not lost! You could potentially help us fix the crash. Information describing the crash is below, so just click send, or if you have time, write a brief description of how the crash happened first.
 
 Many thanks.
 
 
 
 
 
 
 
 The information below is to help the developers identify the problem, please do not modify it.
 
 
 
 ======== DEBUG INFORMATION  =======
 Version:    1.4.10
 Engine:     xine-engine
 Build date: Apr  5 2009
 CC version: 4.3.3
 KDElibs:    3.5.10
 Qt:         3.3.8b
 TagLib:     1.5.0
 CPU count:  2
 NDEBUG:     true
 ==== file `which amarokapp` =======
 /usr/bin/amarokapp: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
 
 
 ==== (gdb) bt =====================
 [Thread debugging using libthread_db enabled]
 [New Thread 0x7f9335ba57b0 (LWP 1216)]
 [New Thread 0x7f93195eb950 (LWP 3288)]
 [New Thread 0x7f9319dec950 (LWP 3287)]
 [New Thread 0x7f931a7ba950 (LWP 3286)]
 [New Thread 0x7f931efbc950 (LWP 3273)]
 [New Thread 0x7f932665a950 (LWP 3272)]
 0x00007f933439592f in waitpid () from /lib/libc.so.6
 #0  0x00007f933439592f in waitpid () from /lib/libc.so.6
 #1  0x0000000000405ed1 in Amarok::Crash::crashHandler ()
 #2  <signal handler called>
 #3  0x00007f9333ca9891 in QListViewItem::itemAbove ()
    from /usr/lib/libqt-mt.so.3
 #4  0x00007f9335698b2f in PlaylistItem::PlaylistItem ()
    from /usr/lib/libamarok.so.0
 #5  0x00007f93356a80d7 in UrlLoader::customEvent ()
    from /usr/lib/libamarok.so.0
 #6  0x00007f9333bd6f61 in QObject::event () from /usr/lib/libqt-mt.so.3
 #7  0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 #8  0x00007f9333b7a27a in QApplication::notify () from /usr/lib/libqt-mt.so.3
 #9  0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 #10 0x00007f9333b7b2c9 in QApplication::sendPostedEvents ()
    from /usr/lib/libqt-mt.so.3
 #11 0x00007f9333b29795 in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 #12 0x00007f93356a3ad9 in UrlLoader::recurse () from /usr/lib/libamarok.so.0
 #13 0x00007f93356a43ae in UrlLoader::UrlLoader () from /usr/lib/libamarok.so.0
 #14 0x00007f933562aef4 in Playlist::insertMediaInternal ()
    from /usr/lib/libamarok.so.0
 #15 0x00007f933563748b in Playlist::insertMedia ()
    from /usr/lib/libamarok.so.0
 #16 0x00007f93356b0e17 in PlaylistWindow::slotAddLocation ()
    from /usr/lib/libamarok.so.0
 #17 0x00007f93356b1210 in PlaylistWindow::qt_invoke ()
    from /usr/lib/libamarok.so.0
 #18 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #19 0x00007f9333bd9162 in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #20 0x00007f933264cda0 in KAction::slotPopupActivated ()
    from /usr/lib/libkdeui.so.4
 #21 0x00007f933264d0a8 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
 #22 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #23 0x00007f9333ee8a8d in QSignal::signal () from /usr/lib/libqt-mt.so.3
 #24 0x00007f9333bf09e4 in QSignal::activate () from /usr/lib/libqt-mt.so.3
 #25 0x00007f9333cd166d in QPopupMenu::mouseReleaseEvent ()
    from /usr/lib/libqt-mt.so.3
 #26 0x00007f9333c0b706 in QWidget::event () from /usr/lib/libqt-mt.so.3
 #27 0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 #28 0x00007f9333b7a497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
 #29 0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 #30 0x00007f9333b18271 in QETWidget::translateMouseEvent ()
    from /usr/lib/libqt-mt.so.3
 #31 0x00007f9333b16c4e in QApplication::x11ProcessEvent ()
    from /usr/lib/libqt-mt.so.3
 #32 0x00007f9333b2982a in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 #33 0x00007f9333b8fec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
 #34 0x00007f9333b8fd82 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
 #35 0x0000000000404b31 in ?? ()
 #36 0x00007f933430c5a6 in __libc_start_main () from /lib/libc.so.6
 #37 0x0000000000404399 in ?? ()
 #38 0x00007fff3dce96a8 in ?? ()
 #39 0x000000000000001c in ?? ()
 #40 0x0000000000000001 in ?? ()
 #41 0x00007fff3dce9bfb in ?? ()
 #42 0x0000000000000000 in ?? ()
 #0  0x00007f933439592f in waitpid () from /lib/libc.so.6
 No symbol table info available.
 #1  0x0000000000405ed1 in Amarok::Crash::crashHandler ()
 No symbol table info available.
 #2  <signal handler called>
 No symbol table info available.
 #3  0x00007f9333ca9891 in QListViewItem::itemAbove ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #4  0x00007f9335698b2f in PlaylistItem::PlaylistItem ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #5  0x00007f93356a80d7 in UrlLoader::customEvent ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #6  0x00007f9333bd6f61 in QObject::event () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #7  0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #8  0x00007f9333b7a27a in QApplication::notify () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #9  0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 No symbol table info available.
 #10 0x00007f9333b7b2c9 in QApplication::sendPostedEvents ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #11 0x00007f9333b29795 in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #12 0x00007f93356a3ad9 in UrlLoader::recurse () from /usr/lib/libamarok.so.0
 No symbol table info available.
 #13 0x00007f93356a43ae in UrlLoader::UrlLoader () from /usr/lib/libamarok.so.0
 No symbol table info available.
 #14 0x00007f933562aef4 in Playlist::insertMediaInternal ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #15 0x00007f933563748b in Playlist::insertMedia ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #16 0x00007f93356b0e17 in PlaylistWindow::slotAddLocation ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #17 0x00007f93356b1210 in PlaylistWindow::qt_invoke ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #18 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #19 0x00007f9333bd9162 in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #20 0x00007f933264cda0 in KAction::slotPopupActivated ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #21 0x00007f933264d0a8 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #22 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #23 0x00007f9333ee8a8d in QSignal::signal () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #24 0x00007f9333bf09e4 in QSignal::activate () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #25 0x00007f9333cd166d in QPopupMenu::mouseReleaseEvent ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #26 0x00007f9333c0b706 in QWidget::event () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #27 0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #28 0x00007f9333b7a497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #29 0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 No symbol table info available.
 #30 0x00007f9333b18271 in QETWidget::translateMouseEvent ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #31 0x00007f9333b16c4e in QApplication::x11ProcessEvent ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #32 0x00007f9333b2982a in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #33 0x00007f9333b8fec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #34 0x00007f9333b8fd82 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #35 0x0000000000404b31 in ?? ()
 No symbol table info available.
 #36 0x00007f933430c5a6 in __libc_start_main () from /lib/libc.so.6
 No symbol table info available.
 #37 0x0000000000404399 in ?? ()
 No symbol table info available.
 #38 0x00007fff3dce96a8 in ?? ()
 No symbol table info available.
 #39 0x000000000000001c in ?? ()
 No symbol table info available.
 #40 0x0000000000000001 in ?? ()
 No symbol table info available.
 #41 0x00007fff3dce9bfb in ?? ()
 No symbol table info available.
 #42 0x0000000000000000 in ?? ()
 No symbol table info available.
 ==== (gdb) thread apply all bt ====
 Thread 6 (Thread 0x7f932665a950 (LWP 3272)):
 #0  0x00007f9332f8856d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
    from /lib/libpthread.so.0
 #1  0x00007f9324a1ef91 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f9332f843ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f93343d3fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 Thread 5 (Thread 0x7f931efbc950 (LWP 3273)):
 #0  0x00007f93343ca496 in poll () from /lib/libc.so.6
 #1  0x00007f931f3e9e3d in ?? () from /usr/lib/libpulse.so.0
 #2  0x00007f931f3dc5a9 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
 #3  0x00007f931f3ddbf8 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
 #4  0x00007f931f3ddcc0 in pa_mainloop_run () from /usr/lib/libpulse.so.0
 #5  0x00007f931f3e9c3d in ?? () from /usr/lib/libpulse.so.0
 #6  0x00007f931f40de10 in ?? () from /usr/lib/libpulse.so.0
 #7  0x00007f9332f843ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007f93343d3fcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 Thread 4 (Thread 0x7f931a7ba950 (LWP 3286)):
 #0  0x00007f9332f882e9 in pthread_cond_wait@@GLIBC_2.3.2 ()
    from /lib/libpthread.so.0
 #1  0x00007f9324a30353 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f9332f843ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f93343d3fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 Thread 3 (Thread 0x7f9319dec950 (LWP 3287)):
 #0  0x00007f9332f882e9 in pthread_cond_wait@@GLIBC_2.3.2 ()
    from /lib/libpthread.so.0
 #1  0x00007f9324a22afb in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f9324a29b1e in ?? () from /usr/lib/libxine.so.1
 #3  0x00007f9332f843ba in start_thread () from /lib/libpthread.so.0
 #4  0x00007f93343d3fcd in clone () from /lib/libc.so.6
 #5  0x0000000000000000 in ?? ()
 Thread 2 (Thread 0x7f93195eb950 (LWP 3288)):
 #0  0x00007f9332f882e9 in pthread_cond_wait@@GLIBC_2.3.2 ()
    from /lib/libpthread.so.0
 #1  0x00007f9324a3302b in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f9332f843ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f93343d3fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 Thread 1 (Thread 0x7f9335ba57b0 (LWP 1216)):
 #0  0x00007f933439592f in waitpid () from /lib/libc.so.6
 #1  0x0000000000405ed1 in Amarok::Crash::crashHandler ()
 #2  <signal handler called>
 #3  0x00007f9333ca9891 in QListViewItem::itemAbove ()
    from /usr/lib/libqt-mt.so.3
 #4  0x00007f9335698b2f in PlaylistItem::PlaylistItem ()
    from /usr/lib/libamarok.so.0
 #5  0x00007f93356a80d7 in UrlLoader::customEvent ()
    from /usr/lib/libamarok.so.0
 #6  0x00007f9333bd6f61 in QObject::event () from /usr/lib/libqt-mt.so.3
 #7  0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 #8  0x00007f9333b7a27a in QApplication::notify () from /usr/lib/libqt-mt.so.3
 #9  0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 #10 0x00007f9333b7b2c9 in QApplication::sendPostedEvents ()
    from /usr/lib/libqt-mt.so.3
 #11 0x00007f9333b29795 in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 #12 0x00007f93356a3ad9 in UrlLoader::recurse () from /usr/lib/libamarok.so.0
 #13 0x00007f93356a43ae in UrlLoader::UrlLoader () from /usr/lib/libamarok.so.0
 #14 0x00007f933562aef4 in Playlist::insertMediaInternal ()
    from /usr/lib/libamarok.so.0
 #15 0x00007f933563748b in Playlist::insertMedia ()
    from /usr/lib/libamarok.so.0
 #16 0x00007f93356b0e17 in PlaylistWindow::slotAddLocation ()
    from /usr/lib/libamarok.so.0
 #17 0x00007f93356b1210 in PlaylistWindow::qt_invoke ()
    from /usr/lib/libamarok.so.0
 #18 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #19 0x00007f9333bd9162 in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #20 0x00007f933264cda0 in KAction::slotPopupActivated ()
    from /usr/lib/libkdeui.so.4
 #21 0x00007f933264d0a8 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
 #22 0x00007f9333bd6e3f in QObject::activate_signal ()
    from /usr/lib/libqt-mt.so.3
 #23 0x00007f9333ee8a8d in QSignal::signal () from /usr/lib/libqt-mt.so.3
 #24 0x00007f9333bf09e4 in QSignal::activate () from /usr/lib/libqt-mt.so.3
 #25 0x00007f9333cd166d in QPopupMenu::mouseReleaseEvent ()
    from /usr/lib/libqt-mt.so.3
 #26 0x00007f9333c0b706 in QWidget::event () from /usr/lib/libqt-mt.so.3
 #27 0x00007f9333b794a5 in QApplication::internalNotify ()
    from /usr/lib/libqt-mt.so.3
 #28 0x00007f9333b7a497 in QApplication::notify () from /usr/lib/libqt-mt.so.3
 #29 0x00007f9334fdc3b2 in KApplication::notify ()
    from /usr/lib/libkdecore.so.4
 #30 0x00007f9333b18271 in QETWidget::translateMouseEvent ()
    from /usr/lib/libqt-mt.so.3
 #31 0x00007f9333b16c4e in QApplication::x11ProcessEvent ()
    from /usr/lib/libqt-mt.so.3
 #32 0x00007f9333b2982a in QEventLoop::processEvents ()
    from /usr/lib/libqt-mt.so.3
 #33 0x00007f9333b8fec1 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
 #34 0x00007f9333b8fd82 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
 #35 0x0000000000404b31 in ?? ()
 #36 0x00007f933430c5a6 in __libc_start_main () from /lib/libc.so.6
 #37 0x0000000000404399 in ?? ()
 #38 0x00007fff3dce96a8 in ?? ()
 #39 0x000000000000001c in ?? ()
 #40 0x0000000000000001 in ?? ()
 #41 0x00007fff3dce9bfb in ?? ()
 #42 0x0000000000000000 in ?? ()
 #0  0x00007f933439592f in waitpid () from /lib/libc.so.6
 
 
 ==== kdBacktrace() ================
 

```

---

### Post by Fluffy13 on 2009-05-27
did a launch from terminal as well for good measure:

```

steve@steve-laptop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
    StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4000004
steve@steve-laptop:~$ TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Properties::read() -- Page headers were invalid.
TagLib: ID3v2.4 no longer supports the frame type RVA.  It will be discarded from the tag.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Properties::read() -- Page headers were invalid.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: MPEG::Header::parse() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
/bin/sh: /usr/lib/amarok/install-mp3: not found
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type RVAD.  It will be discarded from the tag.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x420009e
DCOP aborting call from 'anonymous-16192' to 'amarok'



```

---

### Post by nikgare on 2009-05-27
How did you install 1.4 - via a PPA (which) or some other method?

---

### Post by Fluffy13 on 2009-05-28
Via PPA, three different ones at this point. The first one is the same PPA i had used on Jaunty 32bit without issue.

---

### Post by nikgare on 2009-05-28
This is my sources.list, including the ppa for amarok.  I have 1.4 running fine here on Jaunty x64.

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty main restricted
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates main restricted
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty universe
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty universe
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates universe
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty multiverse
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty multiverse
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates multiverse
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security main restricted
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security main restricted
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security universe
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security universe
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security multiverse
deb [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-backports restricted main multiverse universe
deb-src [http://ftp.telfort.nl/ubuntu/](http://ftp.telfort.nl/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main #Amarok 1.4 PPA
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main #avant-window-navigator
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free #opera
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free #skype
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main #midori
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main #gnome-do
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #google
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main #ubuntu-tweak
deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) jaunty main #transmission-gtk
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) jaunty main #shutter

deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main #XBMC

deb [http://apt.boxee.tv](http://apt.boxee.tv) jaunty main
deb [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) jaunty main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free #Virtualbox
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/specto/ppa/ubuntu](http://ppa.launchpad.net/specto/ppa/ubuntu) jaunty main #specto

---

### Post by Fluffy13 on 2009-05-31
Sorry for the late reply. I'm a bondsman/recovery agent/PI so my 24/7 schedule gets a little insane. It appears we are using the same one, here is my sources file:

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by nickdbliss on 2009-05-31
I am using Jaunty 64-bit edition. I had amarok broken as well. My amarok version is 2.02. Problem is, it doesn't install mp3 support by default as in 32-bit. Seems some problem is there. Anyway, so I installed mp3 support and used this command for the same.

 sudo apt-get install libxine1-ffmpeg

End result was, I am having working Amarok. I don't think there was any need to revert to older version. But anyway, try it and I hope you will have working Amarok as well.

---

### Post by Fluffy13 on 2009-05-31
Already did that, but i double checked to be sure. Thanks for posting, using audacious is making me nutty lol

> 
steve@steve-laptop:~$ sudo apt-get install libxine1-ffmpeg
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
libxine1-ffmpeg set to manually installed.
The following packages were automatically installed and are no longer required:
  python2.5-minimal nspluginwrapper python2.5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steve@steve-laptop:~$

---

### Post by nickdbliss on 2009-05-31
Well, i am sorry it didn't work. I recently switched to 64bit from 32bit ubuntu on my laptop. So this was the first problem that i faced on my fresh install. That lil command did the trick for me. Maybe you should have tried 2.02 version as well. But then maybe it is some other issue. Anyway good luck buddy.

---

### Post by Fluffy13 on 2009-05-31
Amarok 2 is horrid. The GUI leaves A LOT to be desired. I'm not quite sure what the developers were thinking, but its clear that the majority can't stand the changes at all. That is why so many of us have gone back to 1.4 on Jaunty. I had no issues on the 32 Bit, but 64 is being difficult.

I appreciate the help, though.

---

