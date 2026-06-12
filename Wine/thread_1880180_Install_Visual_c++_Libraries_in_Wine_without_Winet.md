---
title: "Install Visual c++ Libraries in Wine without Winetricks"
date: 2011-11-13
forum: Wine
---

### Post by darkeale on 2011-11-13
Hi,

I am trying to get Visual c++ 2003, 2005 and 2008 libraries into my Wine.  However the computer I am trying to do this on has no internet connection so I can't use Winetricks.  Can anyone send me links to where I can download these packages so that I can then transfer them on a USB.

Thanks

---

### Post by Toz on 2011-11-19
winetricks is actually a bash script file. The information you're looking for is located in there.
> #----------------------------------------------------------------

w_metadata vcrun2003 dlls \
    title="Visual C++ 2003 libraries (mfc71,msvcp71,msvcr71)" \
    publisher="Microsoft" \
    year="2003" \
    media="download" \
    file1="BZEditW32_1.6.5_Installer.exe" \
    installed_file1="$W_SYSTEM32_DLLS_WIN/msvcp71.dll"

load_vcrun2003()
{
    # Load the Visual C++ 2003 runtime libraries
    # Sadly, I know of no Microsoft URL for these
    echo "Installing BZFlag (which comes with the Visual C++ 2003 runtimes)"
    w_download $WINETRICKS_SOURCEFORGE/bzflag/BZEditW32_1.6.5_Installer.exe bdd1b32c4202fd77e6513fd507c8236888b09121
    w_try $WINE "$W_CACHE"/vcrun2003/BZEditW32_1.6.5_Installer.exe $W_UNATTENDED_SLASH_S
    w_try cp "$W_PROGRAMS_X86_UNIX/BZEdit1.6.5"/m*71* "$W_SYSTEM32_DLLS"
}

#----------------------------------------------------------------

w_metadata vcrun2005 dlls \
    title="Visual C++ 2005 libraries (mfc80,msvcp80,msvcr80)" \
    publisher="Microsoft" \
    year="2011" \
    media="download" \
    file1="vcredist_x86.EXE" \
    installed_file1="c:/windows/winsxs/x86_Microsoft.VC80.MFC_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_150c9e8b/mfc80.dll"

load_vcrun2005()
{
    # June 2011 security update, see 
    # [http://www.microsoft.com/technet/security/bulletin/MS11-025.mspx](http://www.microsoft.com/technet/security/bulletin/MS11-025.mspx) or
    # [http://support.microsoft.com/kb/2538242](http://support.microsoft.com/kb/2538242)
    w_download [http://download.microsoft.com/download/8/B/4/8B42259F-5D70-43F4-AC2E-4B208FD8D66A/vcredist_x86.EXE](http://download.microsoft.com/download/8/B/4/8B42259F-5D70-43F4-AC2E-4B208FD8D66A/vcredist_x86.EXE) b8fab0bb7f62a24ddfe77b19cd9a1451abd7b847

    cd "$W_CACHE"/vcrun2005
    w_override_dlls native,builtin msvcr80
    w_try $WINE $file1 $W_UNATTENDED_SLASH_Q
}

#----------------------------------------------------------------

w_metadata vcrun2008 dlls \
    title="Visual C++ 2008 libraries (mfc90,msvcp90,msvcr90)" \
    publisher="Microsoft" \
    year="2011" \
    media="download" \
    file1="vcredist_x86.exe" \
    installed_file1="C:/windows/winsxs/x86_Microsoft.VC90.MFC_1fc8b3b9a1e18e3b_9.0.30729.6161_x-ww_028bc148/mfc90.dll"

load_vcrun2008()
{
    # June 2011 security update, see 
    # [http://www.microsoft.com/technet/security/bulletin/MS11-025.mspx](http://www.microsoft.com/technet/security/bulletin/MS11-025.mspx) or
    # [http://support.microsoft.com/kb/2538242](http://support.microsoft.com/kb/2538242)
    w_download [http://download.microsoft.com/download/5/D/8/5D8C65CB-C849-4025-8E95-C3966CAFD8AE/vcredist_x86.exe](http://download.microsoft.com/download/5/D/8/5D8C65CB-C849-4025-8E95-C3966CAFD8AE/vcredist_x86.exe) 470640aa4bb7db8e69196b5edb0010933569e98d
    w_override_dlls native,builtin msvcr90
    cd "$W_CACHE"/vcrun2008
    w_try $WINE $file1 $W_UNATTENDED_SLASH_Q
}

#----------------------------------------------------------------

w_metadata vcrun2010 dlls \
    title="Visual C++ 2010 libraries (mfc100,msvcp100,msvcr100)" \
    publisher="Microsoft" \
    year="2010" \
    media="download" \
    file1="vcredist_x86.exe" \
    installed_file1="$W_SYSTEM32_DLLS_WIN/mfc100.dll"

load_vcrun2010()
{
    # See [http://www.microsoft.com/downloads/details.aspx?FamilyID=a7b7a05e-6de6-4d3a-a423-37bf0912db84](http://www.microsoft.com/downloads/details.aspx?FamilyID=a7b7a05e-6de6-4d3a-a423-37bf0912db84)
    w_download [http://download.microsoft.com/download/5/B/C/5BC5DBB3-652D-4DCE-B14A-475AB85EEF6E/vcredist_x86.exe](http://download.microsoft.com/download/5/B/C/5BC5DBB3-652D-4DCE-B14A-475AB85EEF6E/vcredist_x86.exe) 372d9c1670343d3fb252209ba210d4dc4d67d358

    if w_workaround_wine_bug 23427 ""  1.3.5,
    then
        w_call msxml3
    fi

    w_override_dlls native,builtin msvcr100
    cd "$W_CACHE"/vcrun2010
    w_try $WINE vcredist_x86.exe $W_UNATTENDED_SLASH_Q
}

#-------------------------------------------------------------

**vcrun2010** = [http://download.microsoft.com/download/5/B/C/5BC5DBB3-652D-4DCE-B14A-475AB85EEF6E/vcredist_x86.exe]("http://download.microsoft.com/download/5/B/C/5BC5DBB3-652D-4DCE-B14A-475AB85EEF6E/vcredist_x86.exe")

**vcrun2008** = [http://download.microsoft.com/download/5/D/8/5D8C65CB-C849-4025-8E95-C3966CAFD8AE/vcredist_x86.exe]("http://download.microsoft.com/download/5/D/8/5D8C65CB-C849-4025-8E95-C3966CAFD8AE/vcredist_x86.exe")

**vcrun2005** = [http://download.microsoft.com/download/8/B/4/8B42259F-5D70-43F4-AC2E-4B208FD8D66A/vcredist_x86.EXE]("http://download.microsoft.com/download/5/B/C/5BC5DBB3-652D-4DCE-B14A-475AB85EEF6E/vcredist_x86.exe")

**vcrun2003** = $WINETRICKS_SOURCEFORGE/bzflag/BZEditW32_1.6.5_Installer.exe 
...where $WINETRICKS_SOURCEFORGE resolves to either:
- "http://surfnet.dl.sourceforge.net/sourceforge"   or 
- "http://downloads.sourceforge.net". 

Therefore:
[http://surfnet.dl.sourceforge.net/sourceforge/bzflag/BZEditW32_1.6.5_Installer.exe]("http://surfnet.dl.sourceforge.net/sourceforge/bzflag/BZEditW32_1.6.5_Installer.exe")
...or
[http://downloads.sourceforge.net/bzflag/BZEditW32_1.6.5_Installer.exe]("http://downloads.sourceforge.net/bzflag/BZEditW32_1.6.5_Installer.exe")

Note from the file:
>     # Sadly, I know of no Microsoft URL for these
    echo "Installing BZFlag (which comes with the Visual C++ 2003 runtimes)"

---

### Post by perpetuus.flamma on 2011-11-21
Is it still not possible to install visual studio (c#) on ubuntu using wine?

---

### Post by Toz on 2011-11-21
> **perpetuus.flamma said:**
> Is it still not possible to install visual studio (c#) on ubuntu using wine?

According to wine appdb, it doesn't look promising. See: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=892]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=892") Your better bet maybe to run windows/visual studio in a virtualbox instance (vm).

---

