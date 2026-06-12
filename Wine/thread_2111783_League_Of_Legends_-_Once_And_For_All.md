---
title: "League Of Legends - Once And For All"
date: 2013-02-02
forum: Wine
---

### Post by Toliot on 2013-02-02
(Intro)

Good evening fellow Ubuntu community! I am glad to admit my full transition over to linux as of yesterday, undoubtedly  I expected things to roll in my favor and having read a few forum posts prior to switching over; I believed that I could get League of Legends(LoL) to run. 
I used to dual-boot ubuntu(10.something) and windows 7 but like I said I fully switched over to Ubuntu 12.10 yesterday, for reasons being that windows got so fragmented/malwared and ubuntu found problems I had no way of fixing, and too complex to be described. I also remembered that I had successfully installed Heroes of Newerth(if anyone's familiar with it, it's a relatively similar game to LoL, both variants of DotA) on ubuntu before but now I'm trying to get into the LoL scene.

(What I've done which might work for others)
So I didn't want to post here until I had done everything I could on my own, short of compiling wine myself(I don't know seemed beyond me, but if that's a feasible solution please link me how I could please!).

sources:

This youtube video claims you can get LoL to run through PlayOnLinux;
Look in install>testing, im guessing since its beta still it doesn't work 
for everyone: 
[https://www.youtube.com/watch?v=pz4eWUXsojw&list=UUDd39wOar9fVJM6qp4pyOOQ&index=5&feature=plcp](https://www.youtube.com/watch?v=pz4eWUXsojw&list=UUDd39wOar9fVJM6qp4pyOOQ&index=5&feature=plcp) (I got angry with how loud this boys coughs were relative to the sound quality, kinda turned me off the whole PlayOnLinux scene :p)
Furthermore with this method I get through the installer, and am able to update to about 33%, and everytime it crashes... :confused:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141)
This is probably the link most people will use with success, you simply update your wine, and run the script Install-Lol-on-wine, I tried to configure this install method with 2 versions of wine(1.5.22,1.5.18 but neither functioned but I oddly think it's because the launcher file that is created in the installation process:

```
 #!/bin/bash

export WINEPREFIX=$HOME/LoL_wine-1.5.22/LoL_Prefix  #wineprefix location
WINE=$HOME/LoL_wine-1.5.22/bin/wine                 #location of wine executable

cd $WINEPREFIX/drive_c/Riot\ Games/League\ of\ Legends/game/ *(right here)*
$WINE "rads_user_kernel.exe"*(and this jargon)* run lol_launcher $(ls ../projects/lol_launcher/releases/) lol.Launcher.exe &

```



there's also an option to recompile wine manually, some stuff on how to make LoL work on 64 bit, and something to do with ACE client, don't know if I should look into that.
:cry:
There's this post on LoL forums: 
[http://na.leagueoflegends.com/board/showthread.php?t=973373](http://na.leagueoflegends.com/board/showthread.php?t=973373) 
(all of the steps I followed!) :confused:
although the ppa/repositories are outdated and my machine doesn't install when I try to do wineloldebs, and I've also updated all the necessary Wine components that I apparently need to get LoL to work but have yet to get anywhere near a login screen even!

      Specs:
Ubuntu quatzal quantal 12.10; Gnome classic; Gallium 0.4 on AMD CYPRESS; 8 gigs DDR3; ATI radeon 5870; i7, any other specs please ask if you feel it would help in you aiding me ! D: pretty desperate/ fiending ma LoL :p

Anything Anyone Could Recommend To Me Would Be Grately appreciated, I forgot I wasn't alone in all this, dur dur 

I think I read someone got their version of LoL to run on a vmware machine, does anyone think that would be a good option?(I'm assuming I would still need to get the utilities and such)

 :KS :KS  THANK YOU UBUNTU COMMUNITY; LOVE FROM CANADA  :KS

Sorry this post is a little sloppy, I promise I will clean it up if I manage to get this to work

---

### Post by Bucky Ball on 2013-02-02
*Thread moved to **Gaming & Leisure**.*

---

### Post by Toliot on 2013-02-03
Bump:
I get this error when I install LoL
anyone know what it means?(the install finishes still and ive yet to try to launch it)
```

fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {2b5d27f5-03bc-448a-82bc-91b65c0e48d2}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {239281de-7192-4736-85c8-24e8a81e85b6}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-4b01-00004a010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {3a905d3e-730a-4680-a51a-5135f62fa211}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {2a762b9e-d787-4b77-9404-610f9573bbc1}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2001-000021010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {75f227ea-3c2d-4fc1-9fcd-3d1aa70525ca}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3801-000028010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {28ec0ec1-d236-4d4b-8c2d-3405bddbaa3a}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-4301-000034010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {849aa0ff-4276-41e5-a46b-7c7991d225b0}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {812d1a71-ea6b-4380-8266-d6feed86e5e8}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2201-00004a010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {54d790a0-8e2b-4ba6-9426-4109c58afeb6}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706ba
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {8bbdb54f-83bd-458b-a91a-fda00a8e31c5}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3b01-000021010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {2b4ef898-9441-4c5f-8254-bbaeb53b1d3c}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {b402ab04-c132-4e80-b1a8-00b808c2ef7f}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {2984f9f0-da8a-4e21-9426-114fc4efecc2}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2401-00003f010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {bf843ea7-a062-4895-a092-29276656a7e1}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2b01-00004a010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {9ba6f65b-f42b-4ab1-bd25-a212b76d8a80}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {6fd8f6fa-166d-4ff0-8614-aafb8511eef7}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {6a157704-47b7-4a7d-8cc2-07d1bd86da81}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-f200-000028010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {85a01ab6-ad38-4d79-8c7a-7a3ec35ab4b6}, hres is 0x80040155
err:ole:marshal_object couldn't get IPSFactory buffer for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155
err:ole:CoMarshalInterface Failed to marshal the interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5}, 80040155
err:rpc:I_RpcReceive we got fault packet with status 0x80040155
fixme:ole:NdrClearOutParameters (0x94d244,0x7e8852a0,0x94d51c): stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1e01-000034010000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
fixme:ole:CoCreateInstance no instance created for interface {5c6fb596-4828-4ed5-b9dd-293dad736fb5} of class {51871e60-0c4e-42e1-9293-6f30ebcd1b60}, hres is 0x80040155
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000457,(nil),0x0001,0x00000000,0x94e20c,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime Optimization Service (clr_optimization_v2.0.50727_32) - Service reached limit of transient errors. Will shut down. Last error returned from Service Manager: 0x80040155.\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0x10529908): stub
fixme:thread:ReleaseSRWLockShared (0x10529908): stub
fixme:thread:AcquireSRWLockExclusive (0x10529908): stub
fixme:thread:ReleaseSRWLockExclusive (0x10529908): stub
fixme:thread:AcquireSRWLockShared (0x5de6cfe4): stub
fixme:thread:ReleaseSRWLockShared (0x5de6cfe4): stub
fixme:thread:AcquireSRWLockShared (0x5de6cfe4): stub
fixme:thread:ReleaseSRWLockShared (0x5de6cfe4): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0x10529908): stub
fixme:thread:ReleaseSRWLockShared (0x10529908): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xadc0248): stub
fixme:thread:ReleaseSRWLockExclusive (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xadc0248): stub
fixme:thread:ReleaseSRWLockExclusive (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0x5de6cfe4): stub
fixme:thread:ReleaseSRWLockShared (0x5de6cfe4): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xadc0248): stub
fixme:thread:ReleaseSRWLockExclusive (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xadc0248): stub
fixme:thread:ReleaseSRWLockExclusive (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xadc0248): stub
fixme:thread:ReleaseSRWLockExclusive (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockShared (0xad7ce74): stub
fixme:thread:ReleaseSRWLockShared (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:advapi:EventEnabled (deadbeef, 0x6303ffe8): stub
fixme:advapi:EventEnabled (deadbeef, 0x6303ffe8): stub
fixme:thread:AcquireSRWLockShared (0xadc0248): stub
fixme:thread:ReleaseSRWLockShared (0xadc0248): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:thread:AcquireSRWLockExclusive (0xad7ce74): stub
fixme:thread:ReleaseSRWLockExclusive (0xad7ce74): stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:EventUnregister deadbeef: stub
toliot@Allah-OEM:~/Downloads$ fixme:thread:InitializeSRWLock (0x5de6b680): stub
fixme:thread:InitializeSRWLock (0x5de6cfe4): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockExclusive (0x5de6b680): stub
fixme:thread:ReleaseSRWLockExclusive (0x5de6b680): stub
fixme:thread:AcquireSRWLockExclusive (0x5de6b680): stub
fixme:thread:ReleaseSRWLockExclusive (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:thread:AcquireSRWLockExclusive (0x5de6b680): stub
fixme:thread:ReleaseSRWLockExclusive (0x5de6b680): stub
fixme:thread:AcquireSRWLockExclusive (0x5de6b680): stub
fixme:thread:ReleaseSRWLockExclusive (0x5de6b680): stub
fixme:thread:AcquireSRWLockShared (0x5de6b680): stub
fixme:thread:ReleaseSRWLockShared (0x5de6b680): stub
fixme:advapi:RegisterTraceGuidsA (0x6307379f, 0x630b1cf8, {0cfe0455-93ba-440d-a3fe-553973d0b723}, 1, 0x33fc98, (null), (null), 0x630b1d00,): stub
fixme:advapi:RegisterTraceGuidsA (0x6307379f, 0x630b1d18, {797fabac-7b58-4796-b924-d51178a59ce4}, 1, 0x33fc98, (null), (null), 0x630b1d20,): stub
fixme:advapi:EventRegister {43d1a55c-76d6-4f7e-995c-64c711e5cafe}, 0x6309ce28, (nil), 0x630b1500
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:apphelp:ApphelpCheckInstallShieldPackage stub: 0x33f1ec L"C:\\users\\toliot\\Desktop\\League of Legends\\data1.hdr"
fixme:ole:CoCreateInstance no instance created for interface {ea1afb91-9e28-4b86-90e9-9e9f8a5eefaf} of class {56fdf344-fd6d-11d0-958a-006097c9a090}, hres is 0x80004002
fixme:shell:IShellLinkW_fnGetPath (0x21160b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkW_fnGetPath (0x21160b8): WIN32_FIND_DATA is not yet filled.
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
fixme:shell:IShellLinkW_fnGetPath (0x2a0d958): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkW_fnGetPath (0x2a0d958): WIN32_FIND_DATA is not yet filled.
fixme:advapi:EventUnregister deadbeef: stub

```

trying this guide: [http://na.leagueoflegends.com/board/showthread.php?t=2020528](http://na.leagueoflegends.com/board/showthread.php?t=2020528)

edit: just tried to run lol and my wine  window crashed along with nautilus... -_- wtf

---

### Post by Dread Knight on 2013-02-03
You bother yourself way too much for a game.
I just play Heroes of Newerth because it runs flawlessly on linux; no headaches at all.
Just something to consider, feel free to ignore this...

---

### Post by Toliot on 2013-02-03
> **Dread Knight said:**
> You bother yourself way too much for a game.
I just play Heroes of Newerth because it runs flawlessly on linux; no headaches at all.
Just something to consider, feel free to ignore this...

Yeah I used to play HoN but it doesn't satisfy me graphically/customization, anyone who has any ideas on what I'm doing wrong please give me your advice!!! Should I be trying to reset my wine everytime I install a version of LoL???

---

### Post by bud986 on 2013-02-05
Hopefully [iLOL]("http://www.boompje.net/news/post/72/future-plans-for-boompjenet-and-the-ilol-team") is coming to Linux soon!
They decided wo get to work on a Linux client since the native mac beta was announced by riot.
In the mean time id suggest you to have a look at [the post about lol on winedb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141") or playonlinux.
Asfasr as I know the information on the legue of legends forum is dated, and the ace client isnt really needed anymore.

---

### Post by Zirts on 2013-02-06
Just install it via PlayonLinux. It works now almoust perfectly, only shop is missing.

---

