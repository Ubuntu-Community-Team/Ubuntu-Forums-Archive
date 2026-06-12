---
title: "problem using wine &amp; steam"
date: 2008-04-14
forum: Wine
---

### Post by 068139 on 2008-04-14
**SOLVED but read below please.**

---

### Post by 068139 on 2008-04-14
**SOLVED but read below please.**

---

### Post by 068139 on 2008-04-14
**SOLVED but read below please.**

---

### Post by 068139 on 2008-04-14
I've worked around the 26% error bug now...but I have a new problem, once it gets to 100% updated (steam), it quits and spits this error in terminal:

```
jamie@jamie-desktop:~/.wine/drive_c/Program Files/Steam$ wine steam
fixme:event:wait_for_withdrawn_state window 0x10034/3600005 wait timed out
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
[email]jamie@jamie-desktop:~/.wine[/email]/drive_c/Program Files/Steam$ 
[email]jamie@jamie-desktop:~/.wine[/email]/drive_c/Program Files/Steam$ 
```

any help? please..

---

### Post by 068139 on 2008-04-14
> **Jamdude80 said:**
> Lol Jamie you noob

you don't know how to get it working so give a constructive response.

---

### Post by 068139 on 2008-04-15
> **Jamdude80 said:**
> Look!

that's not a solution and i love the screen capture window :P lol plus you're running a diff vershin of ubuntu.

---

### Post by aoanla on 2008-04-15
> **068139 said:**
> I
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution..

You see what it's telling you there?

So, can you try installing the winbind package in Synaptic, please?

---

### Post by 068139 on 2008-04-15
> **aoanla said:**
> You see what it's telling you there?

So, can you try installing the winbind package in Synaptic, please?

thanks, i've installed it now. I'm new to ubuntu/debian & linux...
still getting the 26% bug error...

here's the lines that im running:
```

cd ~/.wine/drive_c/Program\ Files/Steam
jamie@jamie-desktop:~/.wine/drive_c/Program Files/Steam$
wine SteamTmp.exe SelfUpdate "Steam.exe" 14
```
and the error after it crashes at 26% updating:

```
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
jamie@jamie-desktop:~/.wine/drive_c/Program Files/Steam$ 

```

---

### Post by aoanla on 2008-04-16
Hrm. And you've tried deleting ClientRegistry.blob before using that command?

If not, try that.

If so, try:

chattr -R +S ~/.wine/drive_c/Program\ Files/Steam

and then running the command you tried before.

---

