---
title: "CaseNotes by QCC Information Security and Wine"
date: 2011-11-05
forum: Wine
---

### Post by felixdzerzhinsky on 2011-11-05
I am trying to install CaseNotes by QCC Information Security  using Wine. I have already installed .Net using winetricks with no errors.

[http://computer-forensics.sans.org/blog/2010/08/19/digital-forensics-reporting-casenotes-walkthroughreview/](http://computer-forensics.sans.org/blog/2010/08/19/digital-forensics-reporting-casenotes-walkthroughreview/)

[http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)

When I run CaseNotes I get the following error message.

Is this fixable?



> See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.NotImplementedException: Not implemented.
   at System.Drawing.Drawing2D.LinearGradientBrush.TranslateTransform(Single dx, Single dy, MatrixOrder order)
   at System.Drawing.Drawing2D.LinearGradientBrush.TranslateTransform(Single dx, Single dy)
   at System.Windows.Forms.ToolStripProfessionalRenderer.RenderBackgroundGradient(Graphics g, Control control, Color beginColor, Color endColor, Orientation orientation)
   at System.Windows.Forms.ToolStripProfessionalRenderer.RenderMenuStripBackground(ToolStripRenderEventArgs e)
   at System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBackground(ToolStripRenderEventArgs e)
   at System.Windows.Forms.ToolStripRenderer.DrawToolStripBackground(ToolStripRenderEventArgs e)
   at System.Windows.Forms.ToolStrip.OnPaintBackground(PaintEventArgs e)
   at System.Windows.Forms.Control.PaintWithErrorHandling(PaintEventArgs e, Int16 layer, Boolean disposeEventArgs)
   at System.Windows.Forms.Control.WmPaint(Message& m)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ScrollableControl.WndProc(Message& m)
   at System.Windows.Forms.ToolStrip.WndProc(Message& m)
   at System.Windows.Forms.MenuStrip.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
CaseNotes
    Assembly Version: 1.3.2010.6
    Win32 Version: 1.3.2010.6
    CodeBase: file:///C:/Program%20Files/QCC/CaseNotes/CaseNotes.exe
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.3053 (netfxsp.050727-3000)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.




---

