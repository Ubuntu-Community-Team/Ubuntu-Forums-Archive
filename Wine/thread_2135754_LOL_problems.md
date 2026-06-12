---
title: "LOL problems"
date: 2013-04-15
forum: Wine
---

### Post by chiblazer on 2013-04-15
Hello i installed LOL via playonlinux everything download and updated but now when i tried to open it to day  a window pops up (pic of screen added) then nothing normally it would pull up the game after that but now it does nothing. i debugged and go this

(  DEBUG)[08:40:55.589] RADS::Common::RegistryHelp::RegKeyValueString::RegKeyValueString: (Software\Riot Games\RADS, LocalRootFolder, c:\rads)
(  ERROR)[08:40:55.802] RADS::User::PandoManager::start: StartPMB failed, returned error 6
(  ERROR)[08:40:55.817] RADS::User::CreateProcessA: File not found.
(  ERROR)[08:40:55.817] RADS::User::CreateProcessA: CreateProcess failed with return value 0.
(  ERROR)[08:40:55.818] RADS::UserKernel::`anonymous-namespace'::WaitForProcessToTerminate: Invalid parameter.
(  ERROR)[08:40:55.818] RADS::UserKernel::`anonymous-namespace'::WaitForProcessToTerminate: OpenProcess failed
(  ERROR)[08:40:55.818] RADS::UserKernel::UserCommandThread::ThreadProc: Failure while waiting for process to terminate.
(  ERROR)[08:40:55.822] RADS::UserKernel::NamedPipe::ConnectionThread::ThreadProc: The handle that was passed to the API has been either invalidated or closed.
(  ERROR)[08:40:55.822] RADS::UserKernel::NamedPipe::ConnectionThread::ThreadProc: ConnectNamedPipe failed.
(  ERROR)[08:40:55.839] RADS::Common::HTTPConnection::GetFile: perform request failed with code 7
(  ERROR)[08:40:55.839] RADS::Common::HTTPConnection::GetFile: Failed on /rest/getToken?format=xml&ClientID=PMB_Client
(  ERROR)[08:40:55.846] RADS::Common::HTTPConnection::GetFile: perform request failed with code 7
(  ERROR)[08:40:55.846] RADS::Common::HTTPConnection::GetFile: Failed on /rest/getToken?format=xml&ClientID=PMB_Client
(  ERROR)[08:40:55.853] RADS::Common::HTTPConnection::GetFile: perform request failed with code 7
(  ERROR)[08:40:55.853] RADS::Common::HTTPConnection::GetFile: Failed on /rest/shutdown?format=xml&netToken=
 did  the repair said it was fixed but still same been try to play LOL for a week now since i converted to ubuntu plz help.

---

### Post by myromance123 on 2013-04-15
Try changing the Wine version you are using. It's possible that an update in LoL has caused this problem.

To do this in PlayOnLinux, click the Configure text on the right. Once it opens up, it will have a dropdown menu where you can select the Wine version. Just click that and select a different Wine version.

The latest Wine at the moment is 1.5.28. The last stable Wine release is 1.4.1. I urge you to try between these two. If the dropdown menu only has System or one other Wine, then you need to install the newer Wine versions in PlayOnLinux. This is very easy to do.

At the top, just click on Tools and click on Manage Wine versions. Now you'll have two panels, left and right. Select any Wine version on the left, and click the > button in the middle. Once the selected Wine version is in the right panel, you have it installed. Now just go back to Configure, and open the drop down menu. Select that newly installed Wine version.

---

### Post by howefield on 2013-04-15
Thread moved to the "*Wine"* forum.

---

### Post by chiblazer on 2013-04-15
hello and ty for the reply i did the steps listed but still with no  change it loads a window saying wine undate username same one i posted  with this thread. But still does not load the game i uninstalled it  again for the 20th time and reinstalled. and still have same problem

---

### Post by myromance123 on 2013-04-16
Alright, can you tell me how you installed LOL into PlayOnLinux? Was it by the automated installer available in PlayOnLinux?

In your errors, it says this:
> ( ERROR)[08:40:55.817] RADS::User::CreateProcessA: File not found.
Just to be sure, you haven't accidentally deleted your LOL game files? You can right click LOL inside PlayOnLinux and click "Go to programs directory" (or something like that, I forget the exact wording). Once you're inside the directory, is everything there?

---

