---
title: "Shaiya and black screen"
date: 2008-05-21
forum: Wine
---

### Post by ilcontegis on 2008-05-21
Hi everyone, I converted another friend to Ubuntu :guitar:
Just he's playing to this MMORPG Shaiya..
I read on WineHQ website that it should work, and I followed their suggestions.
Now the game start but the screen is black....i can see the mouse cursor (that becomes with the theme of the game) i can hear the music of the game..i can hear when I'm writing the user ID and pass...so it means that the only problem is that the screen is black..

Do you have any solution ot this?

I used wine 0.9.59 Ubuntu 8.04 32bit
The laptop is Asus A6000 series with centrino 1.7ghz, 512 ram and ati 9700 mobility.

Here last part of the wine konsole output while running the game
```
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
```

If you need other info please tell me

Thank you for your help
:popcorn:

---

### Post by ilcontegis on 2008-06-09
up:popcorn:

---

### Post by kestal on 2008-06-15
Unfortunetely, if I am not mistaken. At this point of time Shaiya will not work in Linux. WineHQ does not show any platinum ratings for the current client.

Ubuntu does come pretty close however it looks like GameGuard is thwarting efforts. There are hex edits which bypass gameguard and the game loads up, but crashes seconds after (not only that, but the hex edit is a violation of the TOS, or at least I would assume it is).

There are a few people that will try to work on this sometime in the next month (from what I was told), but not sure if anything will help or not.

Hopefully someone will come out with something promising, soon... I really wish to focus on Linux and not have to switch back to Windows in order to play Shaiya, or any other MMO that has gameguard, or something similiar.

---------

However, it sounds like you came across a different way (I say that because I have never heard of that problem yet). Mind giving me a bit more info of what you did?

---

