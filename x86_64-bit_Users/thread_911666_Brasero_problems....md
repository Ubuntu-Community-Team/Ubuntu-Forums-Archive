---
title: "Brasero problems..."
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by exploder on 2008-09-05
I am having problems burning iso files with Brasero in Hardy and was wondering if anyone had some ideas on where the problem lies.

I can burn iso files to CD or DVD but I can not leave the speed at max in Hardy. If I do not drop the speed the drive spins too fast and the application will lock up.

If I lower the speed I can burn an iso to a CD with no problem.The same solution will produce an error with a DVD but the burned disk will still work.

I have searched for a solution and read all of the bug reports with no luck K3b and Gnomebaker behave similarly. I tried upgrading Brasero to version 0.8.1 and still had the issue.

The same hardware worked with no problems in Gutsy, so I know the hardware is fine and the pc is only about six months old.

The bug reports suggest that the  kernel or wodim could be the cause of the problem. I tested for the problem with Intrepid Alpha 5 yesterday and the problem remains.

Has anyone been able to resolve this?

---

### Post by exploder on 2008-09-06
I get this when I use a DVD to burn.


ero_burn_check_session_consistency burn.c:1794)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1892)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_MA66GU toc = nil
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=dao
    -dvd-compat
    -use-the-force-luke=tracksize:200990
    -use-the-force-luke=tty
    -Z
    /dev/scd0=/home/don/Desktop/antiX-M7.5.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/don/Desktop/antiX-M7.5.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 200990 blocks
BraseroGrowisofs stderr: , warning for short DAO recording
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stdout:           0/411627520 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/411627520 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/411627520 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/411627520 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:    13139968/411627520 ( 3.2%) @2.8x, remaining 9:05 RBU  98.8% UBU  76.5%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    45088768/411627520 (11.0%) @6.9x, remaining 2:50 RBU  96.6% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:    77561856/411627520 (18.8%) @7.0x, remaining 1:47 RBU  93.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   110559232/411627520 (26.9%) @7.1x, remaining 1:16 RBU  88.4% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   144080896/411627520 (35.0%) @7.3x, remaining 0:57 RBU  85.2% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   178126848/411627520 (43.3%) @7.4x, remaining 0:45 RBU  82.2% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   212697088/411627520 (51.7%) @7.5x, remaining 0:35 RBU  80.4% UBU  88.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   247726080/411627520 (60.2%) @7.6x, remaining 0:27 RBU  76.9% UBU  97.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   283344896/411627520 (68.8%) @7.7x, remaining 0:20 RBU  73.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   319389696/411627520 (77.6%) @7.8x, remaining 0:13 RBU  69.1% UBU  82.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   356024320/411627520 (86.5%) @7.9x, remaining 0:07 RBU  64.7% UBU  91.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   389316608/411627520 (94.6%) @7.2x, remaining 0:03 RBU  61.5% UBU  94.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_written_session
BraseroGrowisofs called brasero_job_set_rate
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @4.8x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=31110h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 1
    message    = "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stdout:   411598848/411627520 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2384)


I burned the same iso to an old 650 MB CDRW with no errors.

I also had noticed that if I started Brasero from the terminal I would get IO errors. I gave the root account a password and the IO errors from the terminal are gone.(This is a temporary measure to try and resolve this.) I noticed that I could leave the max speed setiing this time and the DVD did burn to 100% before the error appeared. The DVD is fine and will work.

---

### Post by exploder on 2008-09-06
One more thing. I installed Brasero 0.8.1-1 from GetDeb.net for my testing. I went with the newer version because you can actually turn off the plugins and the changes will stick.

---

### Post by exploder on 2008-09-06
bump

---

### Post by Npl on 2008-09-07
dunno if thats your problem, but Ubuntu uses a buggy fork of the cdrtools package and theres no trace of the original version in the repos to easily replace it (yeah opensource and "choice" :( ). Read about it [here]("http://cdrecord.berlios.de/old/private/linux-dist.html").

---

### Post by django0909 on 2008-09-09
I really need to burn DVD images, and I'm getting the same errors. Can anyone help?

---

