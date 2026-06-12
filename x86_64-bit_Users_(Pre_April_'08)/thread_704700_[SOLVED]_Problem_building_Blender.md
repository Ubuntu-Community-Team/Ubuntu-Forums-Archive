---
title: "[SOLVED] Problem building Blender"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by stoneage on 2008-02-22
I just tried to build Blender on Gutsy and received the following error message. Can anyone help? I read in a Wiki page for Feisty that I could add a line to user-config.py but there is no file of that name. Solutions gratefully received.


intern/SoundSystem/openal/SND_OpenALDevice.cpp:53:21: error: AL/alut.h: No such file or directory
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual SND_WaveSlot* SND_OpenALDevice::LoadSample(const STR_String&, void*, int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:439: error: ‘alutLoadWAVMemory’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:454: error: ‘alutLoadWAVFile’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:482: error: ‘alutUnloadWAV’ was not declared in this scope
scons: *** [/home/organic/build/linux2/intern/SoundSystem/openal/SND_OpenALDevice.o] Error 1
scons: building terminated because of errors.

---

### Post by Kilz on 2008-02-22
> **stoneage said:**
> I just tried to build Blender on Gutsy and received the following error message. Can anyone help? I read in a Wiki page for Feisty that I could add a line to user-config.py but there is no file of that name. Solutions gratefully received.


intern/SoundSystem/openal/SND_OpenALDevice.cpp:53:21: error: AL/alut.h: No such file or directory
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual SND_WaveSlot* SND_OpenALDevice::LoadSample(const STR_String&, void*, int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:439: error: ‘alutLoadWAVMemory’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:454: error: ‘alutLoadWAVFile’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:482: error: ‘alutUnloadWAV’ was not declared in this scope
scons: *** [/home/organic/build/linux2/intern/SoundSystem/openal/SND_OpenALDevice.o] Error 1
scons: building terminated because of errors.

Is there a reason you are building Blender from source and not installing the version in the repositories with apt or Synaptic?

---

### Post by nixi on 2008-02-22
hi, why do you want to build it in the first place? Blender for Gutsy is in the repos.

EDIT too slow hehe

---

### Post by stoneage on 2008-02-22
I wanted to build an optimised version and root around in the Blender repository .

I was missing a couple of dependencies - python-dev - can you imagine...?

---

### Post by stoneage on 2008-02-23
For what it's worth:-

Standard build - 1m 30
2.45 from Ubuntu repository - 1m 20
SSE2 optimized - 1m 07

It's not a huge difference but if you were rendering a 5,000 frame animation it could save a day....out of 4...?

---

