---
title: "Boa-Constructor / Python"
date: 2005-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by chadauld on 2005-06-18
Hello all,

Has anyone had success getting Boa-Constructor working in Hoary 64?  I have installed and uninstalled it several times from Synaptic, but I keep getting errors when trying to launch it.  I was gonna try and roll my own, but I figured I would see if anyone had any other suggestions.  I know Boa requires both wxPython/Python to be installed and they are.

Error window says - 'NoneType' object has no attribute 'Destroy'.

The terminal message during startup:

Starting Boa Constructor v0.3.0
importing wxPython
reading user preferences
running main...
creating Palette
importing Palette
importing PropertyEditors
importing Companions
importing Companions.FrameCompanions
importing Companions.WizardCompanions
importing Companions.ContainerCompanions
importing Companions.SizerCompanions
importing Companions.BasicCompanions
importing Companions.ButtonCompanions
importing Companions.ListCompanions
importing Companions.GizmoCompanion
importing Companions.LibCompanions
importing Companions.UtilCompanions
importing Companions.DialogCompanions
importing ZopeLib.ZopeCompanions
importing Explorers.ExplorerNodes
/usr/lib/python2.4/whrandom.py:38: DeprecationWarning: the whrandom module is deprecated; please use the random module
  DeprecationWarning)
importing Models.PythonControllers
importing Models.Controllers
importing Models.EditorModels
importing Views
importing Views.SourceViews
importing PythonEditorModels
importing Views.AppViews
importing Views.PySourceView
importing Views.ProfileView
importing Views.OGLViews
importing Explorers.FileExplorer
importing Models.wxPythonControllers
importing Models.wxPythonEditorModels
importing Views.Designer
importing Views.InspectableViews
importing Views.CollectionEdit
importing Views.DataView
importing Views.SizersView
importing Models.ConfigSupport
importing Models.CPPSupport
importing Models.HTMLSupport
importing Models.XMLSupport
importing ZopeLib.ZopeEditorModels
executing plug-ins...
importing Explorers
importing ZopeLib.ZopeViews
importing ZopeLib.ZopeExplorer
importing Explorers.PrefsExplorer
creating Inspector
importing Inspector
creating Editor
importing Editor
importing Explorers.CVSExplorer
importing Explorers.ZipExplorer
importing Explorers.FTPExplorer
importing Explorers.DAVExplorer
importing Explorers.SSHExplorer
Traceback (most recent call last):
  File "/usr/bin/boa-constructor", line 659, in ?
    main()
  File "/usr/bin/boa-constructor", line 641, in main
    app = BoaApp()
  File "/usr/bin/boa-constructor", line 460, in __init__
    wxApp.__init__(self, false)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "/usr/bin/boa-constructor", line 495, in OnInit
    self.main.componentSB, self, self.main)
  File "/usr/share/boa-constructor/Editor.py", line 296, in __init__
    self.setupToolBar(viewIdx = 0)
  File "/usr/share/boa-constructor/Editor.py", line 481, in setupToolBar
    Utils.duplicateMenu(self.blankEditMenu), 'Edit').Destroy()
AttributeError: 'NoneType' object has no attribute 'Destroy'


Let me know.  Thanks in advance!

---

### Post by chadauld on 2005-06-18
Well I never did get the pre-built package to install correctly through Synaptic, but I manually downloaded it and followed the instructions [here](http://boa-constructor.sourceforge.net/Installation.html) .  Works fine now.   :)

---

