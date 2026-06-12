---
title: "Getting a Kernel Panic with 2.6.15-4"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocozz on 2006-02-28
Hi, I just recompiled a new kernel (2.6.15-4-powerpc) on my own, buy when booting it gives me one error:

kernel panic - not syncing: VFS: Unable to moun root fs on unknown-block(0,0)

I also notice that I already saw this sometimes when testing Dapper realeases.

Hope you'll be able to help me,
Greets.

---

### Post by DonVla on 2006-02-28
hello,

that can be almost everything... have you compiled the file-system drivers (ext3, reiserfs, etc) as modules or into the kernel ?? 
have you read this:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=kernel&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=kernel&titlesearch=Titles)
or this:
[http://www.ubuntuforums.org/showthread.php?t=43065?](http://www.ubuntuforums.org/showthread.php?t=43065?)

vlad

---

### Post by cocozz on 2006-03-01
Yes, I have REISERFS (my root FS) and HFSPLUS built-in in kernel. 

Also say that I get this other error before the kernel panic one:

pmac_zilog: Error registering serial device, disabling pmac_zilog

And I do not more use the initrd, I commented it in /etc/yaboot.conf and did a ybin -v

Greets.

---

### Post by Cloun on 2006-03-10
I do have the same on my ibook G3. I have no clue what is up:cry: 
Let me know if you will find a way to work it out.

---

### Post by BoneKracker on 2006-03-10
Is a NewWorld boot partition HFS+ or just HFS?

---

### Post by Cloun on 2006-03-10
[QUOTE=BoneKracker]Is a NewWorld boot partition HFS+ or just HFS?[/QUOTE]
Is it may be a reason for ours problems ?

---

### Post by Cloun on 2006-03-10
[QUOTE=BoneKracker]Is a NewWorld boot partition HFS+ or just HFS?[/QUOTE]
My NEWWORLD is HFS.

---

### Post by exohuman on 2006-03-13
Anyone know how to solve this problem? Everytime I use **any** of the Ubuntu upgrade kernels I get this problem. Recently, I upgraded to dapper 2.6.15-18 and it happened.

When I try to boot using the "recovery" mode it says that the "root=" part needs to be changed. However, on my system "root=" is set to the correct value and works in Breezy 2.6.10. Argh...

I noticed that the initrd file is smaller for 2.6.15-18 than it is for 2.6.10, by quite an amount. Is it missing modules? How do I fix it? I want my Ubuntu back.  :cry:

---

### Post by Cloun on 2006-03-16
I compiled new kernel 2.6.15.6 with oldconfg. Its the SAME:( 
Kernel PANIC.....................................
Can't mount root fs, dev/hda#.... not exist
Brizzly 5.6.12 boot just FINE.

That is up???

---

### Post by Heliix on 2006-03-16
i think i have it!
what kind of file system is your root partition? reiserfs? then it must be compilled right in the kernel, NOT as a module: afaik, the modules are loaded AFRER the kernel ;) 
btw, do you have any reasons why reiserfs and not ext2 or ext3?
so, recompile your kernel, say "yes" instead of "module" to reiserfs (and all others fs you intend to use)
let me know whether it worked ;-)
Heliix

---

### Post by Cloun on 2006-03-17
I do not know whay but we do choose the RAISERFS. May be it is not good, BUT IT IS NOT THE CASE OF OUR PROBLEMS.

Here config of my kernel that I insaled fron breezly CD.
#
# Automatically generated make config: don't edit
# Linux kernel version: 2.6.12-9-powerpc
# Mon Oct 10 15:25:45 2005


# File systems
#
CONFIG_EXT2_FS=m
# CONFIG_EXT2_FS_XATTR is not set
CONFIG_EXT3_FS=m
CONFIG_EXT3_FS_XATTR=y
# CONFIG_EXT3_FS_POSIX_ACL is not set
# CONFIG_EXT3_FS_SECURITY is not set
CONFIG_JBD=m
# CONFIG_JBD_DEBUG is not set
CONFIG_FS_MBCACHE=m
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
CONFIG_JFS_STATISTICS=y
CONFIG_FS_POSIX_ACL=y

#
# XFS support
#
CONFIG_XFS_FS=m
CONFIG_XFS_EXPORT=y
# CONFIG_XFS_RT is not set
CONFIG_XFS_QUOTA=y
# CONFIG_XFS_SECURITY is not set
CONFIG_XFS_POSIX_ACL=y
CONFIG_OCFS2_FS=m
CONFIG_MINIX_FS=m
# CONFIG_ROMFS_FS is not set
CONFIG_INOTIFY=y
# CONFIG_QUOTA is not set
CONFIG_QUOTACTL=y
CONFIG_DNOTIFY=y
# CONFIG_AUTOFS_FS is not set
CONFIG_AUTOFS4_FS=m

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_ZISOFS_FS=m
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=m
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=m
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_SYSFS=y
CONFIG_DEVFS_FS=y
# CONFIG_DEVFS_MOUNT is not set
# CONFIG_DEVFS_DEBUG is not set
# CONFIG_DEVPTS_FS_XATTR is not set
CONFIG_TMPFS=y
CONFIG_TMPFS_XATTR=y
CONFIG_TMPFS_SECURITY=y
# CONFIG_HUGETLB_PAGE is not set
CONFIG_RAMFS=y
CONFIG_CONFIGFS_FS=m
CONFIG_FUSE=m

#
# Miscellaneous filesystems
#
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ASFS_FS=m
CONFIG_ASFS_DEFAULT_CODEPAGE=""
CONFIG_ASFS_RW=y
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
CONFIG_CRAMFS=y
CONFIG_SQUASHFS=m
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3
# CONFIG_SQUASHFS_VMALLOC is not set
CONFIG_VXFS_FS=m
CONFIG_HPFS_FS=m
CONFIG_QNX4FS_FS=m
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set

#
# Network File Systems
#
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V4=y
# CONFIG_NFS_DIRECTIO is not set
CONFIG_NFSD=m
CONFIG_NFSD_V3=y
CONFIG_NFSD_V4=y
CONFIG_NFSD_TCP=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_RPCSEC_GSS_SPKM3=m
CONFIG_SMB_FS=m
CONFIG_SMB_NLS_DEFAULT=y
CONFIG_SMB_NLS_REMOTE="iso8859-1"
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
# CONFIG_CIFS_XATTR is not set
# CONFIG_CIFS_EXPERIMENTAL is not set
CONFIG_NCP_FS=m
# CONFIG_NCPFS_PACKET_SIGNING is not set
# CONFIG_NCPFS_IOCTL_LOCKING is not set
# CONFIG_NCPFS_STRONG is not set
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
# CONFIG_CODA_FS_OLD_API is not set
CONFIG_AFS_FS=m
CONFIG_RXRPC=m
CONFIG_LOCK_HARNESS=m
CONFIG_GFS_FS=m
CONFIG_LOCK_NOLOCK=m
CONFIG_LOCK_DLM=m
CONFIG_LOCK_GULM=m

I can perfectly boot from this kernel.

---

### Post by Cloun on 2006-03-17
I build new kernel 2.6.15.6 using OLDCONFIG. Reiserfs in kernel (Y).
Resalt as post #1.

KERNEL PANIC:cry: :cry: :cry: :cry: :cry: :cry:

---

