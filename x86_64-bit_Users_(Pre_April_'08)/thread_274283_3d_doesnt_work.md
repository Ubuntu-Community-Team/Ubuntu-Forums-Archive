---
title: "3d doesnt work"
date: 2006-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Over1ord on 2006-10-09
I installed the newest drivers for my x800xt and have the xorg.conf set up to use the fglrx drivers so now I have proper screen resolution but nothing in 3d works and videos I can only play at about half of full screen.  My videocard should be able to do full 3d graphics at 50+ fps so whats the deal?  Here are my fglrxinfo results:

urs1ne@0ver1ord:~$ fglrxinfo display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.6065 (8.29.6)


Any suggestions?  I want to go back to the "ati" driver but I dont want to give up my 1440x900 resolution but I remember seeing another driver option in some walkthrough aside from "ati" and "fglrx" but I dont remember what it was.  Any help would be greatly appreciated, I really dont want to have to go back to microsoft but if I cant get this to work I am about to give up.  Maybe someone that could help me out can email me at brandenk(at)gmail(dot)com

---

### Post by bulldog on 2006-10-09
If I could I help you out,but I have no ATI experience however.

The only thing I know is that the ATI driver is 'less' good as the nVidia driver.

You need to search an ATI user who can and will help you.

I'm sorry.

---

### Post by siersmak on 2006-10-09
The output you've posted from fglrxinfo looks just like mine, except I have an X1300.  My driver is working properly.  Can you post the contents of the file /var/log/Xorg.0.log?  This file should contain some direction as to any problems with the driver.

-Ken

---

### Post by Over1ord on 2006-10-09
- Output from `fglrxinfo`

urs1ne@0ver1ord:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.6065 (8.29.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ARB_draw_buffers, GL_ATI_draw_buffers,
    GL_ATI_element_array, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None

---

### Post by Over1ord on 2006-10-09
- Output from `lsmod`

urs1ne@0ver1ord:~$ lsmod
Module                  Size  Used by
tsdev                   9600  0
usbhid                 42400  0
binfmt_misc            14608  1
rfcomm                 44512  0
l2cap                  29376  5 rfcomm
bluetooth              58244  4 rfcomm,l2cap
ipt_limit               3392  8
iptable_mangle          3840  0
ipt_LOG                 8192  8
ipt_MASQUERADE          4736  0
ip_nat                 23640  1 ipt_MASQUERADE
ipt_TOS                 3328  0
ipt_REJECT              6976  1
ip_conntrack_irc        8416  0
ip_conntrack_ftp        9448  0
ipt_state               2816  6
ip_conntrack           60200  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               8200  2 ip_nat,ip_conntrack
iptable_filter          4032  1
ip_tables              25536  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                  10760  0
fglrx                 465844  8
cpufreq_userspace       8544  0
cpufreq_stats           7624  0
freq_table              5888  1 cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_ondemand        9128  0
cpufreq_conservative    10408  0
video                  18248  0
tc1100_wmi              8520  0
sony_acpi               6548  0
pcc_acpi               15488  0
hotkey                 13128  0
dev_acpi               14724  0
container               5696  0
button                  8288  0
acpi_sbs               24024  0
battery                11656  1 acpi_sbs
ac                      6600  1 acpi_sbs
i2c_acpi_ec             6400  1 acpi_sbs
dm_mod                 62536  1
lp                     14464  0
ipv6                  298240  12
snd_ca0106             39108  2
snd_rawmidi            31072  1 snd_ca0106
snd_seq_device         10704  1 snd_rawmidi
snd_ac97_codec        109820  1 snd_ca0106
snd_pcm_oss            58784  0
snd_mixer_oss          19968  2 snd_pcm_oss
snd_pcm               104008  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  10 snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  2 snd
snd_ac97_bus            3456  1 snd_ac97_codec
snd_page_alloc         13328  2 snd_ca0106,snd_pcm
parport_pc             40176  1
pcspkr                  3016  0
psmouse                39748  0
parport                43532  3 ppdev,lp,parport_pc
serio_raw               9156  0
shpchp                 50720  0
pci_hotplug            32592  1 shpchp
floppy                 73544  0
i2c_nforce2             8640  0
i2c_core               26048  2 i2c_acpi_ec,i2c_nforce2
af_packet              27020  2
evdev                  13888  1
ext3                  145616  1
jbd                    70312  1 ext3
raid0                   8960  1
md_mod                 76152  1 raid0
ide_generic             2176  0
forcedeth              33868  0
ehci_hcd               35592  0
ohci_hcd               23044  0
usbcore               146556  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 35104  0
cdrom                  40568  1 ide_cd
ide_disk               18880  6
generic                 6724  0
amd74xx                16496  0 [permanent]
sata_nv                11972  0
libata                 84960  1 sata_nv
scsi_mod              159928  1 libata
thermal                15884  0
processor              29160  1 thermal
fan                     5832  0
capability              6536  0
commoncap               9088  1 capability
vga16fb                14480  1
cfbcopyarea             4544  1 vga16fb
vgastate                9792  1 vga16fb
cfbimgblt               3584  1 vga16fb
cfbfillrect             5184  1 vga16fb
fbcon                  42496  72
tileblit                3520  1 fbcon
font                    9344  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3136  1 bitblit

---

### Post by Over1ord on 2006-10-09
I couldnt include all the contents of my xorg.0.log file because its too big, any suggestions on how I can include it?

---

### Post by siersmak on 2006-10-09
Copy /var/log/Xorg.0.log to /tmp, then gzip it and attach it to a post using the attach button (paperclip) in the Reply window.

-Ken

---

### Post by Over1ord on 2006-10-09
LOL, I cant believe I didnt think of that, here it is but converted to .txt

---

### Post by siersmak on 2006-10-10
Well, I don't see anything wrong with your driver config, or it's at least the same as mine.  What programs are you trying to use that make you think there's something wrong with 3D?  I can try them on my machine to see how they do.

-Ken

---

### Post by Over1ord on 2006-10-10
For starters none of the 3d screen savers work.  Before I could use any of them they were just slow, now only a couple of them display at all but usually jumpy.  I also cant watch any videos at full screen, I can barely go half screen without it just stopping on me.

---

### Post by siersmak on 2006-10-10
Yeah, I'm not seeing problems with my 3D screensavers, or the 3D apps I develop.  I did have some correspondence with someone a few months ago about issues that seem very similar to yours.  Believe it or not, he simply rebooted his machine and tried the screensavers again and they ran perfectly smooth.  We decided that there must have been other processes getting in the way of the 3D apps, and rebooting must have killed those rogue processes.  

This solution may work for you, although I doubt it...

---

