---
title: "Problem compiling Amarok 1.3-beta 3 against KDE 3.4.2"
date: 2005-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anes Lihovac on 2005-08-08
Hi

I compiled and installed KDE via Konstruct.
It works pretty well. Now I have a problem building Amarok.
It fails with this error:

if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../amarok/src/amarokcore -I../../amarok/src/amarokcore -I../../amarok/src/analyzers -I../../amarok/src/engine -I../../amarok/src/plugin -I../../amarok/src/statusbar -I/home/al/kde3.4.2/include/arts -I/home/al/kde3.4.2/include/taglib -I../../amarok/src/sqlite   -I/home/al/kde3.4.2/include -I/usr/X11R6/include   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT trackpickerdialogbase.o -MD -MP -MF ".deps/trackpickerdialogbase.Tpo" -c -o trackpickerdialogbase.o trackpickerdialogbase.cpp; \
then mv -f ".deps/trackpickerdialogbase.Tpo" ".deps/trackpickerdialogbase.Po"; else rm -f ".deps/trackpickerdialogbase.Tpo"; exit 1; fi
/bin/sh ../../libtool --silent --tag=CXX --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION    -o amarokapp -L/home/al/kde3.4.2/lib64 -L/usr/X11R6/lib    -R /home/al/kde3.4.2/lib64 -R /home/al/kde3.4.2/lib64 -R /home/al/kde3.4.2/lib64 -R /usr/X11R6/lib actionclasses.o app.o browserbar.o clicklineedit.o collectionbrowser.o collectiondb.o collectionreader.o configdialog.o contextbrowser.o coverfetcher.o covermanager.o cuefile.o directorylist.o effectwidget.o enginecontroller.o engineobserver.o equalizergraph.o equalizersetup.o fht.o filebrowser.o k3bexporter.o kbookmarkhandler.o ktrm.o mediabrowser.o metabundle.o multitabbar.o osd.o party.o playerwindow.o playlist.o playlistbrowser.o playlistbrowseritem.o playlistitem.o playlistloader.o playlistwindow.o pluginmanager.o podcastsettings.o queuemanager.o scriptmanager.o scrobbler.o sliderwidget.o smartplaylisteditor.o socketserver.o streamprovider.o systray.o tagdialog.o threadweaver.o tracktooltip.o trackpickerdialog.o DbSetup.o Options1.o Options2.o Options4.o Options5.o Options7.o Options8.o firstrunwizard.o partydialogbase.o partyinfobox.o podcastsettingsbase.o scriptmanagerbase.o tagdialogbase.o trackpickerdialogbase.o ../../amarok/src/amarokcore/libamarokcore.la ../../amarok/src/analyzers/libanalyzers.la ../../amarok/src/engine/libengine.la ../../amarok/src/plugin/libplugin.la ../../amarok/src/ipod/libipod.la ../../amarok/src/ipod/itunesdb/libitunesdb.la ../../amarok/src/statusbar/libstatusbar.la -lkutils -lkio -lkdeui -lkdecore -lkhtml -lknewstuff -L/home/al/kde3.4.2/lib64 -ltag -lGL  ../../amarok/src/sqlite/libsqlite.la
/usr/bin/ld: warning: libstdc++.so.5, needed by /usr/lib/libqt-mt.so, may conflict with libstdc++.so.60
../../amarok/src/statusbar/.libs/libstatusbar.a(progressBar.o)(.text+0x334): In function `KDE::ProgressBar::~ProgressBar()':
: undefined reference to `QProgressBar::~QProgressBar()'
../../amarok/src/statusbar/.libs/libstatusbar.a(progressBar.o)(.text+0x7d4): In function `KDE::ProgressBar::~ProgressBar()':
: undefined reference to `QProgressBar::~QProgressBar()'
../../amarok/src/statusbar/.libs/libstatusbar.a(progressBar.o)(.text+0xc64): In function `KDE::ProgressBar::~ProgressBar()':
: undefined reference to `QProgressBar::~QProgressBar()'
collect2: ld returned 1 exit status
make[4]: *** [amarokapp] Error 1

Hope someone has an idea.

g++ Version is 3.4.4

Best Regards and thanks in advance
Anes

---

### Post by manicka on 2005-08-08
My guess would be problems with the Konstruct build of 3.4.2. I'd remove it and update to 3.4.2 via apt-get. The repo is posted in [this thread](http://www.ubuntuforums.org/showthread.php?t=52499&highlight=kde+3.4.2)

---

### Post by Anes Lihovac on 2005-08-09
Hi

There are no AMD64 Packages for KDE 3.4.2, thats why I did it via Konstruct.

Regards
Anes

---

### Post by manicka on 2005-08-09
Ah OK, didn't notice the forum this post was in when sending off the reply

sorry :)

So, I'm assuming that this error is from the make process. Were there any errors during ./configure

---

### Post by Anes Lihovac on 2005-08-09
@Manicka

No problem.

Yes, configure ran through, otherwise I wouldn't be able to start the compile
and get the errormessage.

I solved it now by apt-get removing kde and qt. So only KDE and Qt which where
compiled via Konstruct and reside in my HomeDir are available on my machine
and Amarok builded successfully aginst it.

Thanks and best regards
Anes

---

