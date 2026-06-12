---
title: "COM was not initialized - How to debug"
date: 2008-11-24
forum: Wine
---

### Post by Ocye on 2008-11-24
Starting the last Windows tool I need (Statistica) I get the message

> err:ole:CoRegisterClassObject COM was not initialized
fixme:atl:AtlModuleInit SEMI-STUB (0x66538398 0x66538220 0x66520000)
err:ole:create_server class {d54a9130-732e-11d3-9c0d-aa915434eb3c} not registered
err:ole:CoGetClassObject no class object {d54a9130-732e-11d3-9c0d-aa915434eb3c} could be created for context 0x4
wine: Unhandled page fault on read access to 0x0000130b at address 0x5f402550 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x5f402550 

The program starts, UI pops up correctly but the about dialogue is weird and the prog freezes completely. Now I looking for any debugging idea.

TIA, Ocye.

---

