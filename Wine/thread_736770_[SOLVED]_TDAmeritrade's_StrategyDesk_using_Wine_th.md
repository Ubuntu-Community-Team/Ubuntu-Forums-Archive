---
title: "[SOLVED] TDAmeritrade's StrategyDesk using Wine throws error NETCON_secure_connect"
date: 2008-03-27
forum: Wine
---

### Post by dsauxier on 2008-03-27
I'm a long-time linux desktop user, but I'm new to wine.

I'm running Ubuntu 7.10 with all patches applied, and wine 0.9.46 was installed from the repositories.
I've downloaded Ameritrade's StrategyDesk utility and used wine to install it.
([downloadable from here ]("http://www.tdameritrade.com/tradingtools/strategydesk.html")only if you have an account)

I had to grab a couple of DLL's from a Windows XP computer : mfc42.dll and msvcp60.dll
I copied those to /home/user/.wine/drive_c/windows/system
(I also tried moving them to the system32 directory instead)

Ive also used winecfg to add those DLL's to the "libraries" tab.  I've  tried both (builtin, native) and (native,builtin) for order of precedence.
I've tried setting the wine preferences to both Windows 2000 and Windows XP

I run it with command 
```
env WINEPREFIX="/home/user/.wine" wine "C:\Program Files\TD AMERITRADE\StrategyDesk\StrategyDesk.exe"
```

In the gui that pops up, I enter my username and password, then click "OK" and it tries to connect.
Eventually it comes back and says it was unable to connect.

Back on the terminal there are these errors :

[INDENT]
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
err:wininet:NETCON_secure_connect couldn't verify the security of the connection, 20
[/INDENT]

---

### Post by johnbuck on 2008-03-30
I have the same problem as you.

---

### Post by dmstumpf on 2008-04-29
Did you guys ever resolve this issue?

I'm in the same boat - StrategyDesk 2.3 and Wine 0.9.59. After supplying the two DLLs mentioned above, I get to the login window but fail with a "cannot verify your account information" type error:

```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
```

Looks like something needs to be configured to allow StrategyDesk to connect via HTTPS.

---

### Post by dsauxier on 2008-04-30
No, it's still not working.

---

### Post by deefster on 2008-07-04
I know this thread is old now, but in case there are others that pull this thread up in a web search, here is how I got it working:
**Summary: Strategy Desk is heavily integrated with the IE browser.**
[LIST=1]
[*]download winetricks - [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

[*]Install ies4linux - [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

[*]Start with an untainted wine directory:
[*]```
mkdir /some/new/directory
```
[*]```
cd /some/new/directory
```

[*]```
ies4linux --basedir $PWD --bindir ${PWD}/bin --downloaddir ${PWD}/download --no-flash --no-desktop-icon --no-menu-icon --no-gui
```

[*]```
cd ie6
```
[*]```
export WINEPREFIX=$PWD
```

[*]Now use winetricks to install mfc42 stuff.
[*]```
/path/to/winetricks.sh mfc42
```

[*]Install strategy desk
[/LIST]
You're done

---

### Post by Daniel Song on 2008-07-25
> **deefster said:**
> I know this thread is old now, but in case there are others that pull this thread up in a web search, here is how I got it working:
**Summary: Strategy Desk is heavily integrated with the IE browser.**
[LIST=1]
[*]download winetricks - [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

[*]Install ies4linux - [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

[*]Start with an untainted wine directory:
[*]```
mkdir /some/new/directory
```
[*]```
cd /some/new/directory
```

[*]```
ies4linux --basedir $PWD --bindir ${PWD}/bin --downloaddir ${PWD}/download --no-flash --no-desktop-icon --no-menu-icon --no-gui
```

[*]```
cd ie6
```
[*]```
export WINEPREFIX=$PWD
```

[*]Now use winetricks to install mfc42 stuff.
[*]```
/path/to/winetricks.sh mfc42
```

[*]Install strategy desk
[/LIST]
You're done

Thank you so much, deefster. I have been looking the way to use the StrategyDesk in ubuntu long time. Thanks again.

---

### Post by dsauxier on 2008-12-02
Thanks ... that solved it!

---

### Post by yuriry on 2009-04-05
Thank you for your post, deefster!

---

### Post by trailofdead on 2009-08-07
can someone help me with this?  using wine-1.1.26, latest version of strategydesk

i got wine installed, downloaded winetricks, downloaded ies4linux.  

Not sure what to do with the new directories.  are they supposed to be in my .wine folder, or does it not matter.  i created them inside the .wine folder

I followed the instructions on the ies4linux site ```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```

then did ```
ies4linux --basedir $PWD --bindir ${PWD}/bin --downloaddir ${PWD}/download --no-flash --no-desktop-icon --no-menu-icon --no-gui
```

when i got to step 10, i did ```
sh directory/winetricks mfc42
```

i got some errors ```
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:module:import_dll Library msvcrt.dll (which is needed by L"C:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\winemenubuilder.exe") not found
err:module:import_dll Library msvcrt.dll (which is needed by L"C:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\winemenubuilder.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winemenubuilder.exe" failed, status c0000135
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:SetupDefaultQueueCallbackA notification 262144 params 32e818,0
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP000.TMP\\comcat.dll" -> "C:\\windows\\system32\\comcat.dll"
fixme:setupapi:vcpUICallbackProc16 (0xae20, 0705, 0000, 00000000, 003452b4) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xae20, 070f, 0000, 00000000, 003452b4) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xae20, 0710, 0000, 00000000, 003452b4) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xae20, 070b, 0000, 00000000, 003452b4) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xae20, 070c, 0000, 00000000, 003452b4) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
Executing cabextract /home/richard/.winetrickscache/vcredist.exe
Extracting cabinet: /home/richard/.winetrickscache/vcredist.exe
  extracting VCRedist.inf
  extracting PreSetup.exe
  extracting 50comupd.exe
  extracting asycfilt.dll
  extracting atla.dll
  extracting comcat.dll
  extracting mfc42.dll
  extracting mfc42u.dll
  extracting msvcirt.dll
  extracting msvcp60.dll
  extracting msvcrt.dll
  extracting oleaut32.dll
  extracting olepro32.dll
  extracting stdole2.tlb
  extracting atlu.dll
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Using native,builtin override for following DLLs: msvcrt
Executing wine regedit /home/richard/.wine/ies4linux-2.99.0.1/ie6/drive_c/winetrickstmp/override-dll.reg
Install of mfc42 done
winetricks done.

```

what did i do wrong?


edit: i tried running strategydesk from the terminal and it works somewhat.  i can log in and look at stuff but i keep getting errors. this in the terminal before the program launches ```
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703

```
and when in the program, when i click things such as chart i'll get i dialogue box that says "Could not load chart layout from Z:\home\username\Layouts\default.chl"  
other items like the "color bar chart" dont work properly.  for me the color bar chart is a candle stick chart w/o color.

any suggestions?  
it only works from the terminal, how do i fix the launcher that wine automatically created?
should i post this in my own thread because this one is already marked solved?

---

### Post by sotologist on 2009-09-04
can someone help me with this? Just installed wine with latest version of strategydesk 2.3

After i  installed wine, I downloaded winetricks, downloaded ies4linux but I don't understand how number 4 as a new directories you describe and what exactly should I do. I have been using Ubuntu since summer and I love it! Much better than Microsoft!

It is Ubuntu 9.04.

Hope you can help me how to make it works. I really need to start working on strategydesk. I am very new to it.

Thanks.

---

### Post by kenp1730 on 2010-03-13
I have written a blog showing how to install StrategyDesk on Ubuntu 9.10
I hope this will help anyone still having trouble. 

[http://tradingwithlinux.blogspot.com/p/setting-up-td-ameritrade-strategydesk.html]("http://tradingwithlinux.blogspot.com/p/setting-up-td-ameritrade-strategydesk.html")

---

