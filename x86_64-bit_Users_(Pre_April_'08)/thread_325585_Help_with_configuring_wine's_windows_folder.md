---
title: "Help with configuring wine's windows folder"
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by pennyantics on 2006-12-26
Let me preface by saying I'm a huge ubuntu noob, I installed it for the first time last night. I do have a fair amount of tech, CLI and programming experience though so I'm catching on quickly. I wanted to get wine .9.28 amd version working and, after extensive package downloading, I finally have it running consistently. However I got greedy.

See, I was intending to use my /home to store all of my files, including my windows programs and windows information. Once I found out that all the files were being stored on the root I was concerned, because I intentionally left a small amount of space on that partition.

I went into Wine and mapped the C: drive to /home/username/windows. big mistake. I get this now every time I run winecfg:

```
$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Video"'.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\My Video"'.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
fixme:shell:SHCreateDirectoryExW Show system error message, creating path L"c:\\windows\\profiles\\evan\\Desktop", failed with error 3
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\evan\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
wine: Unhandled page fault on read access to 0x00000000 at address 0x7eed2564 (thread 0009), starting debugger...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]


```

if anyone knows how I can fix this please tell me. Ideally this fix will involve wine defaulting to my home folder but beggars can't be choosers, or something like that.

---

### Post by pennyantics on 2006-12-26
I fixed this problem but I appear to be having a little bit of a problem with using Steam, when it is run none of the text or GUI elements are loaded except the extreme basics i.e. the steam logo. Any suggestions?

---

### Post by marx2k on 2007-01-04
can you post how you fixed this problem?

---

