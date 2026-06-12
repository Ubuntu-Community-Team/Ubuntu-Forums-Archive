---
title: "Compiling webkit !!!"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by s_raghu20 on 2008-05-05
Hi,

I try to compile webkit from source.
Using suggestions from this page : 
[http://blog.kagou.fr/post/2008/04/21/Test-Webkit-on-Ubuntu-Gutsy-and-Hardy]("http://blog.kagou.fr/post/2008/04/21/Test-Webkit-on-Ubuntu-Gutsy-and-Hardy")

However, my attempt to compile it fails with the following message : 

```
In file included from WebCore/plugins/gtk/PluginViewGtk.cpp:63:
WebCore/plugins/gtk/gtk2xtbin.h:44:27: error: X11/Intrinsic.h: No such file or directory
In file included from WebCore/plugins/gtk/PluginViewGtk.cpp:63:
WebCore/plugins/gtk/gtk2xtbin.h:78: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:79: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:104: error: ‘String’ has not been declared
WebCore/plugins/gtk/gtk2xtbin.h:113: error: ‘XtTranslations’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:114: error: ‘XtBoundActions’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:120: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:121: error: ‘WidgetClass’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:122: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:124: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:125: error: ‘XtCallbackList’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:126: error: ‘XtPointer’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:127: error: ‘Position’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:128: error: ‘Dimension’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:129: error: ‘Dimension’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:130: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:131: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:132: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:133: error: ‘XtEventTable’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:135: error: ‘XtTranslations’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:136: error: ‘Pixel’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:138: error: ‘WidgetList’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:139: error: ‘Cardinal’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:140: error: ‘String’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:144: error: ‘Cardinal’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:145: error: ‘Pixel’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:147: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:148: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/PluginViewGtk.cpp: In member function ‘NPError WebCore::PluginView::getValue(NPNVariable, void*)’:
WebCore/plugins/gtk/PluginViewGtk.cpp:347: error: ‘XtDisplayToApplicationContext’ was not declared in this scope
./WebCore/plugins/PluginDebug.h: At global scope:
./WebCore/plugins/PluginDebug.h:32: warning: ‘errorStrings’ defined but not used
make[1]: *** [WebCore/plugins/gtk/libWebCore_la-PluginViewGtk.lo] Error 1
make[1]: Leaving directory `/media/sda8/homes/raghav/experiments/webkit/WebKit-r32862'
make: *** [all] Error 2

```

Any help ?

---

