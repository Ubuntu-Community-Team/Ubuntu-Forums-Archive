---
title: "Confusing message in ivtv"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mckryptyk on 2006-01-14
Hello I'm not sure where to post this but I'm running Breezy AMD64.
My kernel is 2.6.12-10-amd64-k8 and my TV card is a Hauppauge PVR-350.
Any help would be appreciated, thank you in advance,

The relevant dmesg /var/log/dmesg is:
 

[   35.556632] ivtv:  ==================== START INIT IVTV ====================
[   35.556636] ivtv:  version 0.4.1 (tagged release) loading
[   35.556638] ivtv:  Linux version: 2.6.12-10-amd64-k8 gcc-3.4
[   35.556640] ivtv:  In case of problems please include the debug info between
[   35.556642] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   35.556645] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   35.559573] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[   35.559619] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   35.559628] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   35.582819] ivtv0: i2c attach to card #0 ok [client=eeprom, addr=50]
[   35.616653] ivtv0 warning: i2c client addr: 0x50 not found for command 0x0!
[   35.616657] ivtv0: Error -19 reading Hauppauge eeprom.
[   35.616660] ivtv0: Possible causes: the tveeprom module was not loaded, or
[   35.616663] ivtv0: the eeprom kernel module was loaded before the tveeprom module.
[   35.627614] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[   35.627620] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   35.669226] saa7115 3-0021: ivtv driver
[   35.669229] saa7115 3-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[   35.841661] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[   35.901294] saa7127 3-0044: ivtv driver
[   35.904306] saa7127 3-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   35.906825] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[   35.953676] msp3400 3-0040: ivtv driver
[   35.953679] msp3400 3-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radio mode=simpler
[   35.953787] msp3400 3-0040: msp34xxg daemon started
[   35.960249] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[   36.006999] tda9887 3-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[   36.007004] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[   36.023803] ivtv0: Could not detect tuner standard, defaulting to NTSC.
[   36.749835] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   36.823393] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   37.033024] ivtv0: Encoder revision: 0x02050032
[   37.043037] ivtv0: Decoder revision: 0x02020023
[   37.043809] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   37.044673] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[   37.045579] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[   37.046434] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   37.047513] ivtv0: Create encoder radio stream
[   37.048234] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024KB total)
[   37.048970] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (1024KB total)
[   37.050030] ivtv0: Create decoder VOUT stream
[   37.050134] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (1024KB total)
[   37.156356] ivtv0: loaded v4l-cx2341x-init-mpeg.bin firmware (155648 bytes)
[   37.432612] tuner: tuner type not set
[   37.586182] ivtv0: Initialized WinTV PVR 350, card #0
[   37.586191] ivtv:  ====================  END INIT IVTV  ====================

---

