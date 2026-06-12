---
title: "Running a Windows screensaver through Wine"
date: 2012-07-21
forum: Wine
---

### Post by Stonecold1995 on 2012-07-21
I'm trying to run a Windows screensaver called [Bad Apple]("https://www.youtube.com/watch?v=so64S8XAySQ") through Wine, but I'm running into some difficulties.  Running "wine BadApple.scr /c" works (it brings up the [configuration dialog]("http://www.pictureshack.us/images/75394_badapple.png")), but it's the actual screensaver ("wine BadApple.scr /s") that doesn't.  When I try to run it, a single black box pops up, and when I right click on it an exit dialog opens ([screenshot]("http://www.pictureshack.us/images/26897_badapple2.png")).  The music that is suppose to be playing in the background works, but not the video.

The process's window title is "LayeredWindowForm" if that is of any help ([screenshot]("http://www.pictureshack.us/images/10072_badapple3.png")).

This is what I got from running it through Terminal (it's kind of long but I didn't know what was important so I didn't want to cut out anything):
```
alex@kubuntu:~/Bad Apple screensaver$ wine BadApple.scr /s
err:menubuilder:init_xdg error looking up the desktop directory
Screen Width:1920 Height:1080
Bitmap Width:1920 Height:1440
top:-180 left:0
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599

(process:14808): GThread-WARNING **: GThread system no longer supports custom thread implementations.

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpeg2enc.so': /usr/lib/gstreamer-0.10/libgstmpeg2enc.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaac.so': /usr/lib/gstreamer-0.10/libgstfaac.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpython.so': /usr/lib/gstreamer-0.10/libgstpython.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmplex.so': /usr/lib/gstreamer-0.10/libgstmplex.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpegscale.so': /usr/lib/gstreamer-0.10/libgstffmpegscale.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpostproc.so': /usr/lib/gstreamer-0.10/libgstpostproc.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstxvid.so': /usr/lib/gstreamer-0.10/libgstxvid.so: wrong ELF class: ELFCLASS64

(wine:14808): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: wrong ELF class: ELFCLASS64
fixme:gstreamer:unknown_type Could not find a filter for caps: audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)1, layer=(int)3, rate=(int)44100, channels=(int)2, parsed=(boolean)true
fixme:gstreamer:watch_bus decodebin20: Your GStreamer installation is missing a plug-in.
fixme:gstreamer:watch_bus decodebin20: Your GStreamer installation is missing a plug-in.
fixme:gstreamer:watch_bus mpegaudioparse0: GStreamer encountered a general stream error.
fixme:gstreamer:GST_Connect GStreamer could not find any streams
fixme:gstreamer:Gstreamer_FindMatch Could not find plugin for audio/mpeg, mpegversion=(int) 1
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {728dcf55-128f-4dd1-ad22-becfa66ce7aa}, hres is 0x80004005
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:strmbase:TransformFilterImpl_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {2dd74950-a890-11d1-abe8-00a0c905f375}!
fixme:quartz:Parser_QueryInterface No interface for {2dd74950-a890-11d1-abe8-00a0c905f375}!
fixme:quartz:Parser_QueryInterface No interface for {2dd74950-a890-11d1-abe8-00a0c905f375}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa52f0,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8e7d8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4ca0,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8e7f0,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4e10,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4e10,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4e28,0x32eb40: stub                                                                                                                                                                                                             
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa56f8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa57c8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa56f8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5938,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa56f8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5aa8,0x32eb40: stub                                                                                                                                                                                                             
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!                                                                                                                                                                          
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5b78,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5c48,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5b78,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5db8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5db8,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5b78,0x32eb40: stub                                                                                                                                                                                                             
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa47c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa5b78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4938,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4a08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4938,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4b78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa4b78,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93800,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf938d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93800,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93a40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93800,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93bb0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93800,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93d20,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93df0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93ec0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93df0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94030,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93df0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf941a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93df0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94288,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf942b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf942e8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94438,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf945a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe7a4d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbdf93c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe7a4d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b5c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf8edd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe45ed0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe46040,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a118,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a288,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe8b748,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a3f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a4c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a3f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9bd00,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a3f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9be70,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9bf40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9c010,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9c010,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9c028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a7c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9c028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a938,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a950,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a980,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9b0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9faf0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9fc60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9fdd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ff40,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9a9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa0010,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa0028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ac18,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfa0028,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ad88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ae58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ae58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ae88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94c40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ae88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94db0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94e80,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf91c28,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94e80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf91d98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94e80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf91f08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf94e80,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92078,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92148,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92078,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf922b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92078,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92428,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf924f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92078,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe065d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe066a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbe066a8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92b50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92b50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92b80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92bb0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92be0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92c10,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92c68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92d60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92c80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92ed0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92c80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93040,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93040,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93080,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ecc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9ee30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9efa0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf93098,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f110,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f128,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f2a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f128,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f418,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f128,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f588,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f588,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f5b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9e3e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f5d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9e558,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9f5d0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9e6c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9e798,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf9e798,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfaf868,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfaf868,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfaf9d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfaf868,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafb48,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfaf868,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafcb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafd88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafcb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafef8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafcb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0068,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfafcb8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb01d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb02d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb01f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0440,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb01f0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0680,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb07f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0960,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0ad0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0c68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0dd8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb0f48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb10b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb1228,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb1398,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb05b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb1508,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb15d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16a8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb30e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb33c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb16c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3538,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3858,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb39c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3b60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3cd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3e40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3fb0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb3620,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb41f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4360,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb44d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4640,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb47d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4948,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4120,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4ab8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4b88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4ab8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4cf8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4ab8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4e68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb50f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5268,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb53d8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb54a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5618,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb4f78,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5788,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5858,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5788,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb59c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5788,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5b38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5788,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5ca8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5788,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5e18,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5f10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5e30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6080,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5e30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb61f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5e30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6360,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb5e30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6640,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb67b0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6880,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb69f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6b60,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6c30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6da0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb6f10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7080,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb64d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb71f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb72c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb71f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7430,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb71f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7670,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb77e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7950,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7ac0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7c30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7da0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb75a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7f10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb7fe0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb82d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8448,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb85b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8728,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8898,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb80c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a30,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8be8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8d58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8ec8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9038,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb91a8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9278,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb93e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9558,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb8a48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb96c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9798,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb96c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9908,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb96c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9aa0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb96c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9c10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb96c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9d80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9e78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9d98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9fe8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9d98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba158,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfb9d98,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba398,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba508,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba678,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba7e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba958,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbaac8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfba2c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbac38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbac50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbac80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbae90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbac80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb000,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbac80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb170,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb240,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb170,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb3b0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb170,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb520,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb5f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb520,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb760,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb520,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb8d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb9a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb8d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbb10,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbb8d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbc80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbd50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbc80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbec0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbc80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc030,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbbc80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc3e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc550,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc6c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc830,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc9a0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbc1a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbcb10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbcbe0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbccb0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbccb0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbccc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbced8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbccc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd048,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbccc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd1b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd288,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd1b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd3f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd648,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd7b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd928,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbda98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbdc08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbddc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbdf30,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbd410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe0a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe170,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe0a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe2e0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe0a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe450,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe520,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe450,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe690,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe450,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe800,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe450,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe970,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbea40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe970,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1bc8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfbe970,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1d38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1e08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1d38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1f78,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc1d38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc21b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2498,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2778,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc28e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2a58,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc20e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2bc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2be0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2c10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2e20,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2c10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2f90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3060,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2f90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc31d0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc2f90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc36f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3860,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc39f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3b68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3d38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3ea8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4018,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4188,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4188,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc43c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4188,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4538,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4188,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc46a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4188,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4818,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc48e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4818,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4a58,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4818,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4bc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4c98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4bc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4e08,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4bc8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc51b8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc4f78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc53f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5568,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc56d8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5918,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5a88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5bf8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5d68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5ed8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc5848,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6118,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6288,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6358,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6370,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6370,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc66f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6370,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6860,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6a00,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6a00,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6c50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6dc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6f30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc70a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc6930,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7210,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7240,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7490,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7600,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7770,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc78e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7a50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7bc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7d78,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7e48,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7fb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8128,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8298,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8368,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc84d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8648,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc87e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8950,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8ac0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8c30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8da0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc8f10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc90a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc7258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9218,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9218,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc93d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9540,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc96b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9820,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc98f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9a60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9bd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9d40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9eb0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca020,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc9230,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca1b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca1b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca1d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca410,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca1d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca650,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca7c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcaaa0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcac38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfca580,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcada8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcada8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92668,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92800,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbf92970,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcbd60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcbed0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc040,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc1b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc1b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc5a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc710,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc880,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcc9f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcadc0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccb60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccb78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccba8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccdb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccba8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccf28,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd020,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccf40,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd190,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfccf40,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd470,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd5e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd778,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd8e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcda58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcdbc8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcd300,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcdd38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcde08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcdd38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcdf78,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce118,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce288,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce3f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce568,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce6d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce870,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9e0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfceb98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfced08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcee78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcefe8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf188,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf2f8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfce9f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf468,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf538,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf468,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf6a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf468,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf818,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf468,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf988,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfa58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf988,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfbc8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcf988,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfd38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfe08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfd38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcff78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfd38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd00e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfcfd38,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0328,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0498,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0258,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd06d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0848,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0608,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0a88,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0bf8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0d68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd0ed8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1048,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd09b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd11b8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd11b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1200,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1410,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1200,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1580,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1200,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd17c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1930,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1aa0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1c10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1d80,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd16f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1ef0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1f08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd1f38,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2148,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2218,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd22e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2218,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2458,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2218,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd25c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2218,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2738,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2808,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2738,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2978,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2738,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2ae8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2738,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2c58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2d28,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2c58,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2e98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2c58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3008,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd2c58,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3178,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3248,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3318,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3248,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd34a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3488,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd34a0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd36d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd37d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd36f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3940,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd36f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3ab0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3ab0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3c20,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3cf0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3dc0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3cf0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3f30,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3cf0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd40a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd3cf0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4210,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd42e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd43b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd42e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4520,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd42e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4690,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4760,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4690,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd48d0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd49a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4690,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4b10,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4690,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4c80,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4d50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4e20,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4d50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4f90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4d50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5100,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd4d50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5340,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd54b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5648,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd57b8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5928,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5a98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5c08,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5d78,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5ee8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd5270,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6080,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6080,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6098,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd62d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6448,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd65b8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6098,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6728,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd67f8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68c8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6af0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6c60,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6dd0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd68e0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd6f40,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7010,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd71c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7330,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd74a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7610,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7780,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7028,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd78f0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd79c0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7a90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7a90,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7aa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7cb8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7aa8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7e28,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7aa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7f98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd7aa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8108,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd81d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd82a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd81d8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8418,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd85c8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8738,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd88a8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8a18,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8bb0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8d20,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8e90,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd8430,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9000,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd90d0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9000,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9240,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9000,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd93b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9480,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd93b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd95f0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd93b0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9760,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9830,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9760,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd99a0,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9760,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9b10,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9760,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9c80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9d50,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9c80,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfd9ec0,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfdffa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0078,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfdffa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe01e8,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfdffa8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0428,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0598,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0708,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0878,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0358,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe09e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0ab8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe09e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0c28,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe09e8,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0d98,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0e68,0x32eb40: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0d98,0x32eb40: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0d98,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe4678,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea930,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2670,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2688,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe79d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7a00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe0fd8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe10a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe1190,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe11e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2c30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2c30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea458,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe73b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea6c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea6f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7570,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfc3c38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7250,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7348,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3f38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe4060,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3e70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe38c0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3990,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe39a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeef20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3a88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3a88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3bf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3c10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeed68,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeee60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeee90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef050,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef120,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef218,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef2e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef328,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef368,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef6f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef7f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef8e8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef9e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef9f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef9f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefad8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefba8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefc78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefd60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefdb8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff01a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0270,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0270,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0438,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0520,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0618,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff06e8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff07e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff07e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0838,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1010,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1108,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1938,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1a30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1a30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1a30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1618,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0a78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0a78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1788,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff17b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1278,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1370,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff12a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff12a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0cd8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8190,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8260,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8330,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8400,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe84e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe85e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe86b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8780,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8920,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe89f0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8a08,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8b78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8c70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8c70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8e50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8ea8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8f00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8f58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9708,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9e90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9f60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea058,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea058,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9ce0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9de0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9de0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9360,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9908,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9908,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0808,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0768,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0768,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0780,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefc00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe71d8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9ee8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9af8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9af8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9b28,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9b10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8218,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8218,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8230,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8218,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0df0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0df0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8230,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe10d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2b10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef818,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefb30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefb30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9fe0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9ff8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef378,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef748,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef748,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3fe8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeef98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeef98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe37a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe37a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe37a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe37e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeff20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefff0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe32b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8720,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe87c0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe87c0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe87d8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1670,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1740,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0f50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0fd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0128,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0fd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0128,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef280,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfea5a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3b60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3ba0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3ba0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe98d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe99a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9458,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9528,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe95f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9628,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0b90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0c88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef4c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef598,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef598,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8fa0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff42a0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff42a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff42a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3018,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3018,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe3030,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff3ee0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff3f10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff7cf0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff7de8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff7eb8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff7f88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8080,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff81f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff82c0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8390,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8488,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8558,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8628,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff86f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff86f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff89e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8ab8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8b88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8b88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8cd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8da0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8e98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9018,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9110,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff91e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff92e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff93e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff94b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9580,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9650,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9748,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9840,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9840,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9f20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9840,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa0f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa628,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa7d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa7d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa0f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa1e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa590,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa5a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa5a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa448,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa940,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa4a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffaa10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffab08,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffabd8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffabf0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffaf10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9ac8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9ac8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb188,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb1a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9d50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9d90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9da8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9dc0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb2c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb2e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb938,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb918,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb7b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb7d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb578,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb670,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffba40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffba40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc068,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc098,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbc28,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbd20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbdf0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbdf0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc170,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc240,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc310,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc310,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc458,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc550,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc620,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc790,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc888,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc958,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffca60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcb30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffccd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcda0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffce70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcf40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcf70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd138,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd230,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd300,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd420,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd4f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd5e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd6b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd788,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd888,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd980,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffda50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdb20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdbf0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdc20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdc78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe8d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe9f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffeac0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffeb90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe280,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe350,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe448,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe378,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe638,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe708,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe708,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdd68,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffde60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffde60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdfd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffec40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffed38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffee08,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffef00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffeff8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff0c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff1c0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff2b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff3b0,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff3c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff420,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff478,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff840,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff570,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff640,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff710,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000ba8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000040,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000b50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000b30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000b60,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000b48,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000b78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000a30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000880,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000990,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000978,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0009b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfffe80,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfffe98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfffe98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0003e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000370,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000388,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfffad8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000cd8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000da8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000ea0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000f70,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000f70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0011b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001170,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001148,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0013e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001400,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0015d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0016a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001770,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0018e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0018e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001a50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001b38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001cd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001da0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001e70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001da0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002048,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002118,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002148,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0021a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002298,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002298,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe8f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe81e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb120,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe8f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff0fd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9168,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9270,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9270,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe22f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7480,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe7498,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8958,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8970,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001008,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeecc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff97c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8f28,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef630,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfef1a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff88a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8248,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8248,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8260,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff1198,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff11b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe93e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9410,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe93f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9410,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfecbf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfecc10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9c10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc80,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc80,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcc80,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb928,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe978,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe978,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe810,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe828,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdb78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdba8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdba8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdb90,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdbc0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbd78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001280,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd570,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd1b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9368,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9380,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9380,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9098,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff90b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff90c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001c58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001c70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001c58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001c88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8970,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfefb30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001fd0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9880,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8168,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9880,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8158,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8158,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8158,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa188,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa188,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe008,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffe008,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001e20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001e20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001e20,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001310,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001310,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001310,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001340,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2fc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe2fc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffce30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffcdf8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff84e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff84f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeff20,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeff50,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeff38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfeff68,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff5c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff5c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9718,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe97e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9a00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa920,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff8be0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb360,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb348,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb5d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffbac0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffb5b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000d30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000e18,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffaf10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc1c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffc298,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd0a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffd0a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdc48,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdd18,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001558,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001570,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffef80,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xc001570,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0019a8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0019d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0019d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0019d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9b98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff9be0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffde88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffdea0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8ff8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8ff8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9010,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbff3d68,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9010,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8d58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8d58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe8d70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002220,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0022f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0023e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0024b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002588,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff8d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfff9c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfffa98,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000138,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000208,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0002d8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000670,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000768,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000838,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000908,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa2b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc000920,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa3d8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbffa3f0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0029d8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002aa8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002ad8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002ad8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002ad8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002ee8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002fb8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0030a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003198,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003268,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003338,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003408,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003438,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0038a0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003648,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003438,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0037b8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0039b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003a80,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003b78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003c48,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003d18,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003de8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003eb8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003f88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003f88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003f88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003f88,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc003fb8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004448,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004540,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004610,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004610,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004780,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004850,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004920,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004a78,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004b70,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004c40,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004c58,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004e10,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004ef8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc004ff0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0050e8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005228,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0052f8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0053c8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005740,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005810,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005810,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005828,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005650,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005940,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005a10,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005ae0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005c38,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005d30,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005e00,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005ed0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005fa0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006368,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xc005fa0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006110,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0061e0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0062b0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006500,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0065d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc0065d0,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006740,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006828,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc006920,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xc002b18,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_OutputPin_QueryInterface No interface for {56a868a5-0ad4-11ce-b03a-0020af0ba770}!
fixme:wincodecs:PngDecoder_Block_GetCount 0xbfe9bc8,0x32f190: stub
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
err:mscoree:expect_no_runtimes Process exited with a Mono runtime loaded.
alex@kubuntu:~/Bad Apple screensaver$ 

```

When I tried running it with Mono ("mono BadApple.scr /s") it worked even less.  It simply gave me this and exited (no window opened or anything):
```
alex@kubuntu:~/Bad Apple screensaver$ mono BadApple.scr /s
Screen Width:1920 Height:1080
Bitmap Width:1920 Height:1440
top:-180 left:0
System.EntryPointNotFoundException: ShowCursor
  at (wrapper managed-to-native) BadApple.LayeredWindowForm:ShowCursor (bool)
  at BadApple.LayeredWindowForm.LayeredWindowForm_Load (System.Object sender, System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] in <filename unknown>:0 
alex@kubuntu:~/Bad Apple screensaver$
```

Does anyone know how I can get this screensaver to work?

I couldn't find the screensaver's source code, but I was able to find an alternate version of the same screensaver which WAS open source ([link]("https://github.com/bcse/bad-apple-screensaver")).  It is for Windows, and I have no idea how to compile it to run on Linux (or if that's even possible without heavily modifying the source).  Is there a way to compile that one from source in case running the original screensaver through Wine isn't possible?

---

### Post by Stonecold1995 on 2012-07-22
Also, I've successfully run the screensaver in both Windows in VirtualBox and a true Windows install, so I know the screensaver works, I just don't know how to get it to run through Wine.

---

### Post by oldos2er on 2012-07-22
Moved to Wine.

---

### Post by kill o matic on 2012-07-28
The open source screensaver would be a lot more useful, since it can apparently work with whatever video you give it (probably depending on the format, but they don't say) and its options are not in Japanese, plus it supposedly uses less resources. No way it will just run on Linux with dependencies on .NET Framework and DirectX though. And good luck trying to find someone to rewrite the code, considering that Ubuntu is phasing out screensavers entirely.

As for wine, why not ask on their forums?

---

