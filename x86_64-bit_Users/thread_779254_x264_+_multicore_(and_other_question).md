---
title: "x264 + multicore (and other question)"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by toodiesel on 2008-05-02
Hey all:

Has anyone compiled x264 for use with a multicore architecture?

Here is what I've used to configure x264:
./configure --enable-pthread --enabled-shared

I have a dual quadcore xeon system, with Ubuntu 8.04 server 64 edition and can only get around 25fps when encoding.  

I use the following command to get ouput video:

x264 --bitrate 500 --threads auto --thread-input --progress -o test.avi input.avi 1280x720

Also, I've tried this with 1080i, h264 input (.mov) content and the output does not play.  The frame count for the display is also way off, and only runs for about 5-15 seconds and ~100 or so frames.

Here is my output:

x264 [info]: using cpu capabilities: MMX MMX2 SSE SSE2 SSE3 SSSE3 Cache64
x264 [info]: slice I:1     Avg QP:51.00  size:172070  PSNR Mean Y:11.76 U:22.63 V:22.63 Avg:13.35 Global:13.35
x264 [info]: slice P:9     Avg QP:51.00  size:172083  PSNR Mean Y:11.69 U:22.59 V:22.60 Avg:13.28 Global:13.28
x264 [info]: mb I  I16..4: 99.7%  0.0%  0.3%
x264 [info]: mb P  I16..4: 98.7%  0.0%  0.0%  P16..4:  1.0%  0.3%  0.0%  0.0%  0.0%    skip: 0.0%
x264 [info]: final ratefactor: 100.55
x264 [info]: SSIM Mean Y:0.3806576
x264 [info]: PSNR Mean Y:11.698 U:22.598 V:22.599 Avg:13.286 Global:13.286 kb/s:34416.36

encoded 10 frames, 11.12 fps, 48013.24 kb/s

I'm unsure if anything looks wrong, but the input file isn't ever only 10 frames ( input is usually 720p or 1080i minute-2minutes in length ).

One more question:  I've been unable to find any methods of sending piped data to x264.  If I leave out the input filename I always get errors.

Thanks for any help, and this is a great forum

---

