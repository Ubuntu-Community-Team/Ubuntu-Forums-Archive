---
title: "dotnet 20 fails to install"
date: 2011-12-17
forum: Wine
---

### Post by uh20 on 2011-12-17
when running dotnet 2.0 from normal setup, it gets an error about after unregistering a component,it then comes up with a windows error, i have followed steps on avoiding a possible regression but the error is still the same

i got a terminal and here is every err that shows up
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
err:mscoree:LoadLibraryShim error reading registry key for installroot (a lot of these show up)
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize

--
installed mono because it said something about it in the lines, nothing happened
--

---

### Post by mlentink on 2011-12-17
I assume the installer was run by Wine.
dot net does not run on Ubuntu.

There is a package for running some dotnet apps, which is mono

Is in Software Center

---

