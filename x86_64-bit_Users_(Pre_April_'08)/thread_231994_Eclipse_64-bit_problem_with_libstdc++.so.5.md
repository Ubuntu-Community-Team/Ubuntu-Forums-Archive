---
title: "Eclipse 64-bit problem with libstdc++.so.5"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jayesh_ecs on 2006-08-08
Hi all,

I have installed ubuntu 64-bit desktop on amd64 bit machine. Using Eclipse 3.2 (64bit) GTK on it. 
Problem is with SWT browser component.

I have tried ldd on libswt-mozilla-gtk-3232.so and found that libstdc++.so.5 library could not be found. This library is present in /usr/lin32 folder which is symbolic link to libstdc++.so.5.0.7 present in same folder. I have tried ldconfig to add /usr/lib32 in ld library path but it is not working and giving same error. I have also checked its execution permissions.

Why it is not finding libstdc++.so.5 libary ?
Please help me out.

On trying to open Internal Browser Viewer to view an HTML page it shows me following exception in browser view.
```

No more handles (java.lang.UnsatisfiedLinkError: libswt-mozilla-gtk-3232: libswt-mozilla-gtk-3232.so: cannot open shared object file: No such file or directory)
org.eclipse.swt.SWTError: No more handles (java.lang.UnsatisfiedLinkError: libswt-mozilla-gtk-3232: libswt-mozilla-gtk-3232.so: cannot open shared object file: No such file or directory)
   at org.eclipse.swt.SWT.error(SWT.java:3400)
   at org.eclipse.swt.SWT.error(SWT.java:3298)
   at org.eclipse.swt.browser.Browser.<init>(Browser.java:170)
   at org.eclipse.ui.internal.browser.BrowserViewer.<init>(BrowserViewer.java:224)
   at org.eclipse.ui.internal.browser.WebBrowserView.createPartControl(WebBrowserView.java:48)
   at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:334)
   at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.Perspective.showView(Perspective.java:1675)
   at org.eclipse.ui.internal.WorkbenchPage.busyShowView(WorkbenchPage.java:987)
   at org.eclipse.ui.internal.WorkbenchPage.access$13(WorkbenchPage.java:968)
   at org.eclipse.ui.internal.WorkbenchPage$13.run(WorkbenchPage.java:3497)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3503)
   at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3470)
   at org.eclipse.ui.handlers.ShowViewHandler.openView(ShowViewHandler.java:148)
   at org.eclipse.ui.handlers.ShowViewHandler.openOther(ShowViewHandler.java:104)
   at org.eclipse.ui.handlers.ShowViewHandler.execute(ShowViewHandler.java:70)
   at org.eclipse.ui.internal.ShowViewMenu$3.run(ShowViewMenu.java:114)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:500)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:541)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:404)
   at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:62)
   at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1087)
   at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3150)
   at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2840)
   at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1914)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1878)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:419)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:281)
   at org.eclipse.core.launcher.Main.run(Main.java:978)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.UnsatisfiedLinkError: libswt-mozilla-gtk-3232: libswt-mozilla-gtk-3232.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.7)
   at java.lang.Runtime.loadLibrary(libgcj.so.7)
   at java.lang.System.loadLibrary(libgcj.so.7)
   at org.eclipse.swt.internal.Library.loadLibrary(Library.java:124)
   at org.eclipse.swt.browser.Browser.<init>(Browser.java:151)
   ...39 more

```

---

