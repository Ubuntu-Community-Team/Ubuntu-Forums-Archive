---
title: "TrrntZipUI300 loading issue on Wine."
date: 2022-09-23
forum: Wine
---

### Post by KingHanco on 2022-09-23
It just giving errors whenever I tried to load it.
```

mitchell@mitchell-Lenovo-G780:~$ wine start "C:\Program Files\TrrntZipUI\TrrntZipUI.exe"
mitchell@mitchell-Lenovo-G780:~$ 
Unhandled Exception:
System.ArgumentException: The requested FontFamily could not be found [GDI+ status: FontFamilyNotFound]
  at System.Drawing.GDIPlus.CheckStatus (System.Drawing.Status status) [0x001ce] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.FontFamily..ctor (System.Drawing.Text.GenericFontFamilies genericFamily) [0x0004d] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.FontFamily..ctor(System.Drawing.Text.GenericFontFamilies)
  at System.Drawing.FontFamily.get_GenericSansSerif () [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font.CreateFont (System.String familyName, System.Single emSize, System.Drawing.FontStyle style, System.Drawing.GraphicsUnit unit, System.Byte charSet, System.Boolean isVertical) [0x00011] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font..ctor (System.String familyName, System.Single emSize, System.Drawing.FontStyle style, System.Drawing.GraphicsUnit unit, System.Byte gdiCharSet, System.Boolean gdiVerticalFont) [0x00011] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font..ctor (System.String familyName, System.Single emSize, System.String systemName) [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.Font..ctor(string,single,string)
  at System.Drawing.SystemFonts.get_DefaultFont () [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Windows.Forms.Control.get_DefaultFont () [0x0000e] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control.get_Font () [0x00088] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control.AssignParent (System.Windows.Forms.Control value) [0x00026] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control+ControlCollection.Add (System.Windows.Forms.Control value) [0x0011d] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.WindowsFormsUtils+ReadOnlyControlCollection.AddInternal (System.Windows.Forms.Control value) [0x00000] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.SplitContainer..ctor () [0x0013f] in <5733f93bb22240d29f87471942e9a982>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.SplitContainer..ctor()
  at TrrntZipUI.FrmTrrntzip.InitializeComponent () [0x0001c] in <cd9757b4343e44cbba3aeedb32f4e9e2>:0 
  at TrrntZipUI.FrmTrrntzip..ctor () [0x00039] in <cd9757b4343e44cbba3aeedb32f4e9e2>:0 
  at (wrapper remoting-invoke-with-check) TrrntZipUI.FrmTrrntzip..ctor()
  at TrrntZipUI.Program.Main () [0x0000e] in <cd9757b4343e44cbba3aeedb32f4e9e2>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.ArgumentException: The requested FontFamily could not be found [GDI+ status: FontFamilyNotFound]
  at System.Drawing.GDIPlus.CheckStatus (System.Drawing.Status status) [0x001ce] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.FontFamily..ctor (System.Drawing.Text.GenericFontFamilies genericFamily) [0x0004d] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.FontFamily..ctor(System.Drawing.Text.GenericFontFamilies)
  at System.Drawing.FontFamily.get_GenericSansSerif () [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font.CreateFont (System.String familyName, System.Single emSize, System.Drawing.FontStyle style, System.Drawing.GraphicsUnit unit, System.Byte charSet, System.Boolean isVertical) [0x00011] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font..ctor (System.String familyName, System.Single emSize, System.Drawing.FontStyle style, System.Drawing.GraphicsUnit unit, System.Byte gdiCharSet, System.Boolean gdiVerticalFont) [0x00011] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Drawing.Font..ctor (System.String familyName, System.Single emSize, System.String systemName) [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.Font..ctor(string,single,string)
  at System.Drawing.SystemFonts.get_DefaultFont () [0x00000] in <fc2ea6474c6d4315858618f13de6e72a>:0 
  at System.Windows.Forms.Control.get_DefaultFont () [0x0000e] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control.get_Font () [0x00088] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control.AssignParent (System.Windows.Forms.Control value) [0x00026] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.Control+ControlCollection.Add (System.Windows.Forms.Control value) [0x0011d] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.WindowsFormsUtils+ReadOnlyControlCollection.AddInternal (System.Windows.Forms.Control value) [0x00000] in <5733f93bb22240d29f87471942e9a982>:0 
  at System.Windows.Forms.SplitContainer..ctor () [0x0013f] in <5733f93bb22240d29f87471942e9a982>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.SplitContainer..ctor()
  at TrrntZipUI.FrmTrrntzip.InitializeComponent () [0x0001c] in <cd9757b4343e44cbba3aeedb32f4e9e2>:0 
  at TrrntZipUI.FrmTrrntzip..ctor () [0x00039] in <cd9757b4343e44cbba3aeedb32f4e9e2>:0 
  at (wrapper remoting-invoke-with-check) TrrntZipUI.FrmTrrntzip..ctor()

```

[https://www.romvault.com/trrntzip/](https://www.romvault.com/trrntzip/)

---

### Post by KingHanco on 2022-09-23
Never mind. I installed winetricks and then installed all of the Microsoft fonts from it. Fixed now.

---

