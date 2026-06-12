---
title: "How Do I set Tuner Type in IVTV for PVR-150?"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-04-22
IVTV gives me an 'Invalid Argument' message and 'Cannot open capture device /dev/video0.

Mplayer just gives no picture with static.

This is the output from dmesg:

[ 41.072442] Linux video capture interface: v1.00
[ 41.088616] ivtv: ==================== START INIT IVTV ====================
[ 41.088620] ivtv: version 0.4.3 (tagged release) loading
[ 41.088623] ivtv: Linux version: 2.6.12-10-amd64-generic gcc-3.4
[ 41.088625] ivtv: In case of problems please include the debug info between
[ 41.088628] ivtv: the START INIT IVTV and END INIT IVTV lines, along with
[ 41.088631] ivtv: any module options, when mailing the ivtv-users mailinglist.
[ 41.089135] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[ 41.089459] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[ 41.089465] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[ 41.089474] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[ 41.129193] tveeprom: ivtv version
[ 41.129196] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 9344611
[ 41.129199] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[ 41.129203] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[ 41.129206] tveeprom: audio processor = CX25843 (type = 25)
[ 41.129208] tveeprom: decoder processor = CX25843 (type = 1e)
[ 41.129212] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[ 41.144809] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[ 41.144815] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[ 41.294526] cx25840 0-0044: ivtv driver
[ 41.294530] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 43.892251] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[ 43.939156] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[ 43.972256] wm8775 0-001b: ivtv driver
[ 43.972259] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[ 43.978912] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[ 44.680432] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[ 44.890399] ivtv0: Encoder revision: 0x02050032
[ 44.891015] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[ 44.891621] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[ 44.892245] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[ 44.892826] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[ 44.893061] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[ 45.077839] ivtv0: Initialized WinTV PVR 150, card #0

Thanks.

---

### Post by bper on 2006-04-22
Sorry, the errors in first line of my post is reported by TVTime, not IVTV.

---

