---
title: "[WINE] Trying to run FlashDevelop"
date: 2011-11-30
forum: Wine
---

### Post by 3rlend on 2011-11-30
Hey!

I'm new to Linux Ubuntu, (any linux at all actually), and what I wanna get started with, is FlashDevelop, so I can develop my game.

I installed Wine, then I installed FlashDevelop in Wine and tried to run it. It said I needed to install Mono in order to run NET 2.0 programs. So I did.
Downloaded installation file [here]("http://www.go-mono.com/mono-downloads/download.html"); clicked Windows and the first link.

Now when I run FlashDevelop.exe in the terminal:

```
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"runtime" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"disableCachingBindingFailures" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"assemblyBinding" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"probing" in state 3

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for PluginCore.Utilities.SingleInstanceApp ---> System.ArgumentException: Value was invalid.
  at System.Security.Principal.SecurityIdentifier.ParseSddlForm (System.String sddlForm) [0x00000] in <filename unknown>:0 
  at System.Security.Principal.SecurityIdentifier..ctor (System.String sddlForm) [0x00000] in <filename unknown>:0 
  at System.Security.AccessControl.MutexAccessRule..ctor (System.String identity, MutexRights eventRights, AccessControlType type) [0x00000] in <filename unknown>:0 
  at PluginCore.Utilities.SingleInstanceApp..ctor () [0x00000] in <filename unknown>:0 
  at PluginCore.Utilities.SingleInstanceApp..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at FlashDevelop.Program.Main (System.String[] arguments) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for PluginCore.Utilities.SingleInstanceApp ---> System.ArgumentException: Value was invalid.
  at System.Security.Principal.SecurityIdentifier.ParseSddlForm (System.String sddlForm) [0x00000] in <filename unknown>:0 
  at System.Security.Principal.SecurityIdentifier..ctor (System.String sddlForm) [0x00000] in <filename unknown>:0 
  at System.Security.AccessControl.MutexAccessRule..ctor (System.String identity, MutexRights eventRights, AccessControlType type) [0x00000] in <filename unknown>:0 
  at PluginCore.Utilities.SingleInstanceApp..ctor () [0x00000] in <filename unknown>:0 
  at PluginCore.Utilities.SingleInstanceApp..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at FlashDevelop.Program.Main (System.String[] arguments) [0x00000] in <filename unknown>:0 

```

Do you know how to fix it, and make FlashDevelop work?

Thank you very much!

---

### Post by Mark Phelps on 2011-11-30
If your plan is to use Ubuntu to develop Windows games -- that is doomed to failure -- for two reasons.

First, you will need to have a NATIVE Windows environment, at the very least, for testing the games you have developed.  Let's say you've written the game and some aspect of it doesn't work right in Ubuntu.  Is that a Wine problem?  Or is it a problem with your game?  Using Wine, there is really no way to tell.

Second, if your development environment is dependent on .NET components, that is likely to present problems as well.  .NET stuff doesn't work well in Wine -- so you're handicapping yourself in the development environment as well.

---

### Post by mörgæs on 2011-11-30
Moved to the Wine forum.

---

### Post by 3rlend on 2011-11-30
> **Mark Phelps said:**
> If your plan is to use Ubuntu to develop Windows games -- that is doomed to failure -- for two reasons.

First, you will need to have a NATIVE Windows environment, at the very least, for testing the games you have developed.  Let's say you've written the game and some aspect of it doesn't work right in Ubuntu.  Is that a Wine problem?  Or is it a problem with your game?  Using Wine, there is really no way to tell.

Second, if your development environment is dependent on .NET components, that is likely to present problems as well.  .NET stuff doesn't work well in Wine -- so you're handicapping yourself in the development environment as well.

Well Flash Player isn't really Windows only? And right now I'm downloading another editor&compiler called FDT5, so I'll see how that works.

---

