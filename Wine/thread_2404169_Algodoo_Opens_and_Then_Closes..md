---
title: "Algodoo Opens and Then Closes."
date: 2018-10-20
forum: Wine
---

### Post by katido on 2018-10-20
Hello! I am using WINE to run Algodoo. I use Kubuntu 18.10. The problem is that whenever I open algodoo, it closes right after. Do you know how I could fix this? It does say that it expects Ugly Look from no good fonts. But I don't think that is bad. Thank you!

Edit: When Installing there is one error:
[B]003f:err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
0040:err:mscoree:LoadLibraryShim error reading registry key for installroot
0040:err:mscoree:LoadLibraryShim error reading registry key for installroot
0040:err:mscoree:LoadLibraryShim error reading registry key for installroot
0040:err:mscoree:LoadLibraryShim error reading registry key for installroot
*@*-Inspiron-15-7000-Gaming:~/Downloads$ 

[/B]

---

### Post by Holger_Gehrke on 2018-10-23
According to the [Appdb at winehq]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=28812") it's rated as 'Platinum', meaning it runs and runs well. But when I tried to install it, it behaved the way you describe. So I called it from a terminal
```
cd ~/.wine/drive_c/Program\ Files\ \(x86\)/Algodoo
wine Algodoo.exe

```
and got this error after the end of a long list of minor complaints wine always gives me:
```

0009:err:ole:CoGetClassObject class {77a1c827-fcd2-4689-8915-9d613cc5fa3e} not registered
0009:err:ole:CoGetClassObject no class object {77a1c827-fcd2-4689-8915-9d613cc5fa3e} could be created for context 0x1

```
After a bit of searching on the web a post on the forum at winehq told me to install the Visual C runtime from 2008 by running
```
winetricks vcrun2008
```
After that Algodoo works on my system.

The message about fonts will probably go away if you install the Microsoft Core Fonts with ```
winetricks corefonts
```

Holger

---

