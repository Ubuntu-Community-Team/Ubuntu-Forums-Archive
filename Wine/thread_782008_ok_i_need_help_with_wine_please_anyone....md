---
title: "ok i need help with wine please anyone..."
date: 2008-05-04
forum: Wine
---

### Post by amyfan on 2008-05-04
ok i have had this pro [http://ubuntuforums.org/showthread.php?t=780525](http://ubuntuforums.org/showthread.php?t=780525) so redownloaded wine .61 to recompile it but well i get this error in the code section```
:~/Desktop/wine-0.9.61$ make && make install
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/port'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/wine'
(GIT_DIR=../../.git git describe HEAD 2>/dev/null || echo "wine-0.9.61") | sed -n -e '$s/\(.*\)/const char wine_build[] = "\1";/p' >version-stamp || (rm -f version-stamp && exit 1)
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/wine'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/wpp'
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/widl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winebuild'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winedump'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winegcc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/wmc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/wrc'
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/include'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/loader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/loader'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/adsiid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/adsiid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr9'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr9'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxguid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxguid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/strmiids'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/strmiids'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/uuid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winecrt0'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winecrt0'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: `libdinput.def.a' is up to date.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/acledit'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/acledit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/activeds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/activeds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/actxprxy'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/actxprxy'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/advapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/advapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/advpack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/advpack'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/amstream'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/amstream'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/atl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/atl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/avicap32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/avicap32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/avifil32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/avifil32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/browseui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/browseui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cabinet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cabinet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/capi2032'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/capi2032'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cards'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cards'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cfgmgr32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cfgmgr32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/clusapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/clusapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comcat'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comcat'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comctl32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comctl32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comdlg32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comdlg32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/compstui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/compstui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/credui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/credui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/crtdll'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/crtdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/crypt32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/crypt32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdlg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdlg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdll'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptnet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptnet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ctapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ctapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ctl3d32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ctl3d32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d10'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d10'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d9'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d9'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dim'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dim'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3drm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3drm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_24'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_24'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_25'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_25'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_26'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_26'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_27'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_27'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_28'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_28'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_29'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_29'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_30'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_30'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_31'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_31'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_33'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_33'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_34'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_34'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_35'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_35'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_36'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_36'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_37'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_37'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dxof'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dxof'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dbghelp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dbghelp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dciman32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dciman32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ddraw'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ddraw'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ddrawex'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ddrawex'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/devenum'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/devenum'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmband'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmband'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmcompos'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmcompos'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmime'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmime'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmloader'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmloader'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmscript'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmscript'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmstyle'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmstyle'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmsynth'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmsynth'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dnsapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dnsapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dplay'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dplay'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dplayx'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dplayx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnaddr'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnaddr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnhpast'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnhpast'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnlobby'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnlobby'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dsound'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dsound'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dssenh'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dssenh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dswave'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dswave'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dwmapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dwmapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxdiagn'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxdiagn'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/faultrep'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/faultrep'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/fusion'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/fusion'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gdi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gdi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gdiplus'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gdiplus'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gphoto2.ds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gphoto2.ds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gpkcsp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gpkcsp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hal'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hal'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hhctrl.ocx'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hhctrl.ocx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hlink'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hlink'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hnetcfg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hnetcfg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/iccvid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/iccvid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/icmp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/icmp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ifsmgr.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ifsmgr.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imaadp32.acm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imaadp32.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imagehlp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imagehlp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imm32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imm32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inetcomm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inetcomm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/infosoft'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/infosoft'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/initpki'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/initpki'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inkobj'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inkobj'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inseng'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inseng'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/iphlpapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/iphlpapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/itircl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/itircl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/itss'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/itss'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/jscript'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/jscript'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/kernel32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/kernel32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/localspl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/localspl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/localui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/localui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/lz32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/lz32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciavi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciavi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mcicda'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mcicda'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciseq'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciseq'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciwave'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciwave'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/midimap'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/midimap'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mlang'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mlang'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mmdevldr.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mmdevldr.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/monodebg.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/monodebg.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mountmgr.sys'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mountmgr.sys'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mpr'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mpr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mprapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mprapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msadp32.acm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msadp32.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscat32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscat32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscms'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscms'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscoree'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscoree'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msdmo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msdmo'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msftedit'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msftedit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msg711.acm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msg711.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml.tlb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msimg32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msimg32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msimtf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msimtf'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msisys.ocx'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msisys.ocx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msnet32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msnet32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msrle32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msrle32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mssip32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mssip32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcirt'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcirt'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcr71'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcr71'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt20'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt20'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt40'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt40'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrtd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrtd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvfw32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvfw32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvidc32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvidc32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mswsock'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mswsock'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msxml3'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msxml3'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/nddeapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/nddeapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/netapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/netapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/newdev'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/newdev'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdll'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdsapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdsapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntoskrnl.exe'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntoskrnl.exe'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntprint'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntprint'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/objsel'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/objsel'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/odbc32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/odbc32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/odbccp32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/odbccp32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ole32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ole32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oleacc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oleacc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oleaut32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oleaut32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olecli32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olecli32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oledlg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oledlg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olepro32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olepro32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olesvr32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olesvr32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olethk32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olethk32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/pdh'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/pdh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/powrprof'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/powrprof'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/printui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/printui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/propsys'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/propsys'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/psapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/psapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/pstorec'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/pstorec'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qcap'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qcap'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qedit'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qedit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgr'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgrprxy'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgrprxy'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/quartz'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/quartz'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/query'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/query'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rasapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rasapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/resutils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/resutils'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/riched20'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/riched20'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/riched32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/riched32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rpcrt4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rpcrt4'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rsabase'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rsabase'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rsaenh'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rsaenh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sane.ds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sane.ds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sccbase'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sccbase'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/schannel'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/schannel'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/secur32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/secur32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/security'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/security'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sensapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sensapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/serialui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/serialui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/setupapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/setupapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc_os'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc_os'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shdoclc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shdoclc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shdocvw'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shdocvw'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shell32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shell32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shfolder'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shfolder'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shlwapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shlwapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/slbcsp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/slbcsp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/slc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/slc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/snmpapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/snmpapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/softpub'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/softpub'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/spoolss'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/spoolss'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole2.tlb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole2.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole32.tlb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole32.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sti'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sti'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/svrapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/svrapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sxs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sxs'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/tapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/tapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/twain_32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/twain_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/unicows'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/unicows'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/url'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/url'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/urlmon'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/urlmon'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/user32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/user32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/userenv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/userenv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/usp10'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/usp10'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/uxtheme'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/uxtheme'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vdhcp.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vdhcp.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vdmdbg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vdmdbg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/version'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/version'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vmm.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vmm.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vnbt.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vnbt.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vnetbios.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vnetbios.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vtdapi.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vtdapi.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vwin32.vxd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vwin32.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/w32skrnl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/w32skrnl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winealsa.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winealsa.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineaudioio.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineaudioio.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winecoreaudio.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winecoreaudio.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wined3d'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wined3d'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winedos'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winedos'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineesd.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineesd.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winejack.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winejack.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winejoystick.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winejoystick.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winemp3.acm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winemp3.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winenas.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winenas.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineoss.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineoss.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineps.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineps.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wing32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wing32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winhttp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winhttp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wininet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wininet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winmm'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winmm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winnls32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winnls32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winscard'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winscard'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winspool.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winspool.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wintab32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wintab32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wintrust'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wintrust'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wldap32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wldap32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wmi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wmi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wnaspi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wnaspi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wow32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wow32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ws2_32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ws2_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wsock32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wsock32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wtsapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wtsapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winex11.drv'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o ime.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o systray.o text.o window.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so -lcomctl32 -luser32 -lgdi32 -ladvapi32 -limm32 -lkernel32 -lntdll -Wb,-dcomctl32 -L/usr/lib  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls'
make: *** [dlls] Error 2
doug@doug:~/Desktop/wine-0.9.61$ sudo make install
[sudo] password for doug: 
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/port'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/wine'
(GIT_DIR=../../.git git describe HEAD 2>/dev/null || echo "wine-0.9.61") | sed -n -e '$s/\(.*\)/const char wine_build[] = "\1";/p' >version-stamp || (rm -f version-stamp && exit 1)
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/wine'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs/wpp'
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/libs'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/widl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winebuild'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winedump'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/winegcc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/wmc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools/wrc'
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/tools'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/include'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/include'
for f in stdole2.idl activaut.idl activdbg.idl activscp.idl amstream.idl amvideo.idl austream.idl bits.idl bits1_5.idl comcat.idl control.idl d3d10.idl ddstream.idl dimm.idl dispex.idl docobj.idl downloadmgr.idl dxgi.idl dxgitype.idl exdisp.idl fusion.idl hlink.idl htiframe.idl iads.idl icftypes.idl imnact.idl imnxport.idl indexsrv.idl mediaobj.idl mimeinfo.idl mimeole.idl mlang.idl mmstream.idl mscoree.idl mshtmhst.idl mshtml.idl msinkaut.idl msxml.idl msxml2.idl netfw.idl oaidl.idl objidl.idl objsafe.idl ocidl.idl ocmm.idl oleacc.idl oledb.idl oleidl.idl optary.idl propidl.idl pstore.idl qedit.idl richole.idl sensevts.idl servprov.idl shldisp.idl shobjidl.idl shtypes.idl strmif.idl tom.idl unknwn.idl urlhist.idl urlmon.idl wine/itss.idl wine/svcctl.idl wtypes.idl xmldom.idl xmldso.idl accctrl.h aclapi.h adshlp.h advpub.h appmgmt.h audevcod.h aviriff.h axcore.idl axextend.idl basetsd.h basetyps.h bcrypt.h bitsmsg.h cderr.h cfgmgr32.h cguid.h cierror.h clusapi.h commctrl.h commdlg.h compobj.h cor.h corerror.h cpl.h custcntl.h cvconst.h d3d.h d3d8.h d3d8caps.h d3d8types.h d3d9.h d3d9caps.h d3d9types.h d3dcaps.h d3dhal.h d3drm.h d3drmdef.h d3dtypes.h d3dvec.inl d3dx8.h d3dx8core.h d3dx8math.h d3dx8math.inl d3dx8mesh.h d3dx9.h d3dx9core.h d3dx9math.h d3dx9math.inl d3dx9tex.h dbghelp.h dbinit.idl dbprop.idl dbs.idl dbt.h dciddi.h dciman.h dde.h ddeml.h ddk/compstui.h ddk/hidsdi.h ddk/imm.h ddk/mountmgr.h ddk/ntddcdvd.h ddk/ntddk.h ddk/ntddser.h ddk/ntddtape.h ddk/wdm.h ddk/winddiui.h ddk/winsplp.h ddraw.h ddrawi.h devenum.idl devguid.h digitalv.h dinput.h dispdib.h dlgs.h dls1.h dls2.h dmdls.h dmerror.h dmo.h dmoreg.h dmort.h dmplugin.h dmusbuff.h dmusicc.h dmusicf.h dmusici.h dmusics.h dpaddr.h dplay.h dplay8.h dplobby.h dplobby8.h dpnathlp.h dsconf.h dsdriver.h dsgetdc.h dshow.h dsound.h dsrole.h dvdmedia.h dwmapi.h dxdiag.h dxerr8.h dxerr9.h dxfile.h dyngraph.idl errorrep.h errors.h evcode.h evntrace.h excpt.h exdispid.h fci.h fdi.h gdiplus.h gdipluscolor.h gdipluscolormatrix.h gdiplusenums.h gdiplusflat.h gdiplusgpstubs.h gdiplusimaging.h gdiplusinit.h gdiplusmem.h gdiplusmetaheader.h gdipluspixelformats.h gdiplustypes.h guiddef.h hlguids.h htmlhelp.h i_cryptasn1tls.h icm.h icmpapi.h idispids.h imagehlp.h imm.h initguid.h intshcut.h ipexport.h iphlpapi.h ipifcons.h iprtrmib.h iptypes.h isguids.h ks.h ksguid.h ksmedia.h lm.h lmaccess.h lmapibuf.h lmbrowsr.h lmcons.h lmerr.h lmjoin.h lmmsg.h lmserver.h lmshare.h lmstats.h lmuse.h lmuseflg.h lmwksta.h lzexpand.h mapi.h mapicode.h mapidefs.h mapiform.h mapiguid.h mapitags.h mapiutil.h mapival.h mapix.h mciavi.h mcx.h mediaerr.h midles.h minmax.h mmddk.h mmreg.h mmsystem.h mprapi.h msacm.h msacmdlg.h msacmdrv.h mscat.h mshtmcid.h mshtmdid.h msi.h msidefs.h msiquery.h mssip.h msvcrt/conio.h msvcrt/crtdbg.h msvcrt/ctype.h msvcrt/direct.h msvcrt/dirent.h msvcrt/dos.h msvcrt/eh.h msvcrt/errno.h msvcrt/fcntl.h msvcrt/float.h msvcrt/io.h msvcrt/limits.h msvcrt/locale.h msvcrt/malloc.h msvcrt/math.h msvcrt/mbctype.h msvcrt/mbstring.h msvcrt/process.h msvcrt/search.h msvcrt/setjmp.h msvcrt/share.h msvcrt/signal.h msvcrt/stddef.h msvcrt/stdio.h msvcrt/stdlib.h msvcrt/string.h msvcrt/sys/locking.h msvcrt/sys/stat.h msvcrt/sys/timeb.h msvcrt/sys/types.h msvcrt/sys/unistd.h msvcrt/sys/utime.h msvcrt/time.h msvcrt/unistd.h msvcrt/wchar.h msvcrt/wctype.h mswsock.h msxml2did.h msxmldid.h nb30.h ndrtypes.h npapi.h nspapi.h ntddcdrm.h ntddscsi.h ntddstor.h ntdsapi.h ntquery.h ntsecapi.h ntsecpkg.h ntstatus.h objbase.h objsel.h odbcinst.h ole2.h ole2ver.h oleauto.h olectl.h oledlg.h pdh.h pdhmsg.h pktdef.h poppack.h powrprof.h profinfo.h propvarutil.h prsht.h psapi.h pshpack1.h pshpack2.h pshpack4.h pshpack8.h ras.h reason.h regstr.h richedit.h rmxfguid.h rpc.h rpcasync.h rpcdce.h rpcdcep.h rpcndr.h rpcnterr.h rpcproxy.h scarderr.h schannel.h schemadef.h schnlsp.h sddl.h secext.h security.h sensapi.h setupapi.h sfc.h shellapi.h shlguid.h shlobj.h shlwapi.h sipbase.h slerror.h slpublic.h snmp.h softpub.h sql.h sqlext.h sqltypes.h sspi.h storage.h svrapi.h tapi.h tchar.h textserv.h tlhelp32.h tmschema.h twain.h userenv.h usp10.h uuids.h uxtheme.h vdmdbg.h ver.h vfw.h vfwmsgs.h wfext.h winbase.h wincon.h wincred.h wincrypt.h windef.h windns.h windows.h windowsx.h wine/debug.h wine/exception.h wine/library.h wine/unicode.h winerror.h wingdi.h winhttp.h wininet.h winineti.h winioctl.h winldap.h winnetwk.h winnls.h winnls32.h winnt.h winperf.h winreg.h winresrc.h winscard.h winsmcrd.h winsock.h winsock2.h winspool.h winsvc.h wintab.h wintabx.h winternl.h wintrust.h winuser.h winver.h wmistr.h wnaspi32.h wownt32.h ws2spi.h ws2tcpip.h wshisotp.h wsipx.h wsnwlink.h wtsapi32.h xcmc.h xmldomdid.h xmldsodid.h zmouse.h; do case $f in \
	  wine/*)   /usr/bin/install -c  -m 644  ./$f /usr/local/include/wine/`expr $f : 'wine/\(.*\)'` ;; \
	  msvcrt/*) /usr/bin/install -c  -m 644  ./$f /usr/local/include/wine/$f ;; \
	  *)        /usr/bin/install -c  -m 644  ./$f /usr/local/include/wine/windows/$f ;; \
	esac; done
for f in activaut.h activdbg.h activscp.h amstream.h amvideo.h austream.h bits.h bits1_5.h comcat.h control.h d3d10.h ddstream.h dimm.h dispex.h docobj.h downloadmgr.h dxgi.h dxgitype.h exdisp.h fusion.h hlink.h htiframe.h iads.h icftypes.h imnact.h imnxport.h indexsrv.h mediaobj.h mimeinfo.h mimeole.h mlang.h mmstream.h mscoree.h mshtmhst.h mshtml.h msinkaut.h msxml.h msxml2.h netfw.h oaidl.h objidl.h objsafe.h ocidl.h ocmm.h oleacc.h oledb.h oleidl.h optary.h propidl.h pstore.h qedit.h richole.h sensevts.h servprov.h shldisp.h shobjidl.h shtypes.h strmif.h tom.h unknwn.h urlhist.h urlmon.h wine/itss.h wine/svcctl.h wtypes.h xmldom.h xmldso.h stdole2.tlb; do case $f in \
	  wine/*)   /usr/bin/install -c  -m 644  $f /usr/local/include/wine/`expr $f : 'wine/\(.*\)'` ;; \
	  msvcrt/*) /usr/bin/install -c  -m 644  $f /usr/local/include/wine/$f ;; \
	  *)        /usr/bin/install -c  -m 644  $f /usr/local/include/wine/windows/$f ;; \
	esac; done
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/include'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/loader'
for f in wine-glibc wine-kthread wine-pthread wine-preloader; do \
	  if [ "wine-glibc" = "$f" ]; \
	  then /usr/bin/install -c   $f-installed /usr/local/bin/wine; \
	  else /usr/bin/install -c   $f-installed /usr/local/bin/$f; \
	  fi; \
	done
/usr/bin/install -c  -m 644  wine.man /usr/local/share/man/man1/wine.1
/usr/bin/install -c  -m 644  wine.de.man /usr/local/share/man/de.UTF-8/man1/wine.1
/usr/bin/install -c  -m 644  wine.fr.man /usr/local/share/man/fr.UTF-8/man1/wine.1
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/loader'
make[1]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls'
echo "avifil32.dll" >avifile.dll16
echo "kernel32.dll" >comm.drv16
echo "comdlg32.dll" >commdlg.dll16
echo "ole32.dll" >compobj.dll16
echo "ctl3d32.dll" >ctl3d.dll16
echo "ctl3d32.dll" >ctl3dv2.dll16
echo "user32.dll" >ddeml.dll16
echo "gdi32.dll" >dispdib.dll16
echo "user32.dll" >display.drv16
echo "gdi32.dll" >gdi.exe16
echo "imm32.dll" >imm.dll16
echo "user32.dll" >keyboard.drv16
echo "kernel32.dll" >krnl386.exe16
echo "lz32.dll" >lzexpand.dll16
echo "winmm.dll" >mmsystem.dll16
echo "user32.dll" >mouse.drv16
echo "msacm32.dll" >msacm.dll16
echo "msvfw32.dll" >msvideo.dll16
echo "ole32.dll" >ole2.dll16
echo "ole32.dll" >ole2conv.dll16
echo "oleaut32.dll" >ole2disp.dll16
echo "ole32.dll" >ole2nls.dll16
echo "ole32.dll" >ole2prox.dll16
echo "ole32.dll" >ole2thk.dll16
echo "olecli32.dll" >olecli.dll16
echo "olesvr32.dll" >olesvr.dll16
echo "rasapi32.dll" >rasapi16.dll16
echo "setupapi.dll" >setupx.dll16
echo "shell32.dll" >shell.dll16
echo "winmm.dll" >sound.drv16
echo "ole32.dll" >storage.dll16
echo "kernel32.dll" >stress.dll16
echo "kernel32.dll" >system.drv16
echo "kernel32.dll" >toolhelp.dll16
echo "twain_32.dll" >twain.dll16
echo "oleaut32.dll" >typelib.dll16
echo "user32.dll" >user.exe16
echo "version.dll" >ver.dll16
echo "w32skrnl.dll" >w32sys.dll16
echo "w32skrnl.dll" >win32s16.dll16
echo "kernel32.dll" >win87em.dll16
echo "wnaspi32.dll" >winaspi.dll16
echo "kernel32.dll" >windebug.dll16
echo "wineps.drv" >wineps16.drv16
echo "gdi32.dll" >wing.dll16
echo "winnls32.dll" >winnls.dll16
echo "kernel32.dll" >winoldap.mod16
echo "ws2_32.dll" >winsock.dll16
echo "wintab32.dll" >wintab.dll16
echo "winedos.dll" >wprocs.dll16
/usr/bin/install -c  -m 644  `basename __install__/avifile.dll16` /usr/local/lib/wine/`basename __install__/avifile.dll16`
/usr/bin/install -c  -m 644  `basename __install__/comm.drv16` /usr/local/lib/wine/`basename __install__/comm.drv16`
/usr/bin/install -c  -m 644  `basename __install__/commdlg.dll16` /usr/local/lib/wine/`basename __install__/commdlg.dll16`
/usr/bin/install -c  -m 644  `basename __install__/compobj.dll16` /usr/local/lib/wine/`basename __install__/compobj.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ctl3d.dll16` /usr/local/lib/wine/`basename __install__/ctl3d.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ctl3dv2.dll16` /usr/local/lib/wine/`basename __install__/ctl3dv2.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ddeml.dll16` /usr/local/lib/wine/`basename __install__/ddeml.dll16`
/usr/bin/install -c  -m 644  `basename __install__/dispdib.dll16` /usr/local/lib/wine/`basename __install__/dispdib.dll16`
/usr/bin/install -c  -m 644  `basename __install__/display.drv16` /usr/local/lib/wine/`basename __install__/display.drv16`
/usr/bin/install -c  -m 644  `basename __install__/gdi.exe16` /usr/local/lib/wine/`basename __install__/gdi.exe16`
/usr/bin/install -c  -m 644  `basename __install__/imm.dll16` /usr/local/lib/wine/`basename __install__/imm.dll16`
/usr/bin/install -c  -m 644  `basename __install__/keyboard.drv16` /usr/local/lib/wine/`basename __install__/keyboard.drv16`
/usr/bin/install -c  -m 644  `basename __install__/krnl386.exe16` /usr/local/lib/wine/`basename __install__/krnl386.exe16`
/usr/bin/install -c  -m 644  `basename __install__/lzexpand.dll16` /usr/local/lib/wine/`basename __install__/lzexpand.dll16`
/usr/bin/install -c  -m 644  `basename __install__/mmsystem.dll16` /usr/local/lib/wine/`basename __install__/mmsystem.dll16`
/usr/bin/install -c  -m 644  `basename __install__/mouse.drv16` /usr/local/lib/wine/`basename __install__/mouse.drv16`
/usr/bin/install -c  -m 644  `basename __install__/msacm.dll16` /usr/local/lib/wine/`basename __install__/msacm.dll16`
/usr/bin/install -c  -m 644  `basename __install__/msvideo.dll16` /usr/local/lib/wine/`basename __install__/msvideo.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2.dll16` /usr/local/lib/wine/`basename __install__/ole2.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2conv.dll16` /usr/local/lib/wine/`basename __install__/ole2conv.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2disp.dll16` /usr/local/lib/wine/`basename __install__/ole2disp.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2nls.dll16` /usr/local/lib/wine/`basename __install__/ole2nls.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2prox.dll16` /usr/local/lib/wine/`basename __install__/ole2prox.dll16`
/usr/bin/install -c  -m 644  `basename __install__/ole2thk.dll16` /usr/local/lib/wine/`basename __install__/ole2thk.dll16`
/usr/bin/install -c  -m 644  `basename __install__/olecli.dll16` /usr/local/lib/wine/`basename __install__/olecli.dll16`
/usr/bin/install -c  -m 644  `basename __install__/olesvr.dll16` /usr/local/lib/wine/`basename __install__/olesvr.dll16`
/usr/bin/install -c  -m 644  `basename __install__/rasapi16.dll16` /usr/local/lib/wine/`basename __install__/rasapi16.dll16`
/usr/bin/install -c  -m 644  `basename __install__/setupx.dll16` /usr/local/lib/wine/`basename __install__/setupx.dll16`
/usr/bin/install -c  -m 644  `basename __install__/shell.dll16` /usr/local/lib/wine/`basename __install__/shell.dll16`
/usr/bin/install -c  -m 644  `basename __install__/sound.drv16` /usr/local/lib/wine/`basename __install__/sound.drv16`
/usr/bin/install -c  -m 644  `basename __install__/storage.dll16` /usr/local/lib/wine/`basename __install__/storage.dll16`
/usr/bin/install -c  -m 644  `basename __install__/stress.dll16` /usr/local/lib/wine/`basename __install__/stress.dll16`
/usr/bin/install -c  -m 644  `basename __install__/system.drv16` /usr/local/lib/wine/`basename __install__/system.drv16`
/usr/bin/install -c  -m 644  `basename __install__/toolhelp.dll16` /usr/local/lib/wine/`basename __install__/toolhelp.dll16`
/usr/bin/install -c  -m 644  `basename __install__/twain.dll16` /usr/local/lib/wine/`basename __install__/twain.dll16`
/usr/bin/install -c  -m 644  `basename __install__/typelib.dll16` /usr/local/lib/wine/`basename __install__/typelib.dll16`
/usr/bin/install -c  -m 644  `basename __install__/user.exe16` /usr/local/lib/wine/`basename __install__/user.exe16`
/usr/bin/install -c  -m 644  `basename __install__/ver.dll16` /usr/local/lib/wine/`basename __install__/ver.dll16`
/usr/bin/install -c  -m 644  `basename __install__/w32sys.dll16` /usr/local/lib/wine/`basename __install__/w32sys.dll16`
/usr/bin/install -c  -m 644  `basename __install__/win32s16.dll16` /usr/local/lib/wine/`basename __install__/win32s16.dll16`
/usr/bin/install -c  -m 644  `basename __install__/win87em.dll16` /usr/local/lib/wine/`basename __install__/win87em.dll16`
/usr/bin/install -c  -m 644  `basename __install__/winaspi.dll16` /usr/local/lib/wine/`basename __install__/winaspi.dll16`
/usr/bin/install -c  -m 644  `basename __install__/windebug.dll16` /usr/local/lib/wine/`basename __install__/windebug.dll16`
/usr/bin/install -c  -m 644  `basename __install__/wineps16.drv16` /usr/local/lib/wine/`basename __install__/wineps16.drv16`
/usr/bin/install -c  -m 644  `basename __install__/wing.dll16` /usr/local/lib/wine/`basename __install__/wing.dll16`
/usr/bin/install -c  -m 644  `basename __install__/winnls.dll16` /usr/local/lib/wine/`basename __install__/winnls.dll16`
/usr/bin/install -c  -m 644  `basename __install__/winoldap.mod16` /usr/local/lib/wine/`basename __install__/winoldap.mod16`
/usr/bin/install -c  -m 644  `basename __install__/winsock.dll16` /usr/local/lib/wine/`basename __install__/winsock.dll16`
/usr/bin/install -c  -m 644  `basename __install__/wintab.dll16` /usr/local/lib/wine/`basename __install__/wintab.dll16`
/usr/bin/install -c  -m 644  `basename __install__/wprocs.dll16` /usr/local/lib/wine/`basename __install__/wprocs.dll16`
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/adsiid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/adsiid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr9'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxerr9'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxguid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxguid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/strmiids'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/strmiids'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/uuid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winecrt0'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winecrt0'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: `libdinput.def.a' is up to date.
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/acledit'
/usr/bin/install -c   acledit.dll.so /usr/local/lib/wine/acledit.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/acledit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/activeds'
/usr/bin/install -c   activeds.dll.so /usr/local/lib/wine/activeds.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/activeds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/actxprxy'
/usr/bin/install -c   actxprxy.dll.so /usr/local/lib/wine/actxprxy.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/actxprxy'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/advapi32'
/usr/bin/install -c   advapi32.dll.so /usr/local/lib/wine/advapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/advapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/advpack'
/usr/bin/install -c   advpack.dll.so /usr/local/lib/wine/advpack.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/advpack'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/amstream'
/usr/bin/install -c   amstream.dll.so /usr/local/lib/wine/amstream.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/amstream'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/atl'
/usr/bin/install -c   atl.dll.so /usr/local/lib/wine/atl.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/atl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/avicap32'
/usr/bin/install -c   avicap32.dll.so /usr/local/lib/wine/avicap32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/avicap32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/avifil32'
/usr/bin/install -c   avifil32.dll.so /usr/local/lib/wine/avifil32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/avifil32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/browseui'
/usr/bin/install -c   browseui.dll.so /usr/local/lib/wine/browseui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/browseui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cabinet'
/usr/bin/install -c   cabinet.dll.so /usr/local/lib/wine/cabinet.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cabinet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/capi2032'
/usr/bin/install -c   capi2032.dll.so /usr/local/lib/wine/capi2032.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/capi2032'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cards'
/usr/bin/install -c   cards.dll.so /usr/local/lib/wine/cards.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cards'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cfgmgr32'
/usr/bin/install -c   cfgmgr32.dll.so /usr/local/lib/wine/cfgmgr32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cfgmgr32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/clusapi'
/usr/bin/install -c   clusapi.dll.so /usr/local/lib/wine/clusapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/clusapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comcat'
/usr/bin/install -c   comcat.dll.so /usr/local/lib/wine/comcat.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comcat'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comctl32'
/usr/bin/install -c   comctl32.dll.so /usr/local/lib/wine/comctl32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comctl32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/comdlg32'
/usr/bin/install -c   comdlg32.dll.so /usr/local/lib/wine/comdlg32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/comdlg32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/compstui'
/usr/bin/install -c   compstui.dll.so /usr/local/lib/wine/compstui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/compstui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/credui'
/usr/bin/install -c   credui.dll.so /usr/local/lib/wine/credui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/credui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/crtdll'
/usr/bin/install -c   crtdll.dll.so /usr/local/lib/wine/crtdll.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/crtdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/crypt32'
/usr/bin/install -c   crypt32.dll.so /usr/local/lib/wine/crypt32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/crypt32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdlg'
/usr/bin/install -c   cryptdlg.dll.so /usr/local/lib/wine/cryptdlg.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdlg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdll'
/usr/bin/install -c   cryptdll.dll.so /usr/local/lib/wine/cryptdll.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptnet'
/usr/bin/install -c   cryptnet.dll.so /usr/local/lib/wine/cryptnet.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptnet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptui'
/usr/bin/install -c   cryptui.dll.so /usr/local/lib/wine/cryptui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/cryptui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ctapi32'
/usr/bin/install -c   ctapi32.dll.so /usr/local/lib/wine/ctapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ctapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ctl3d32'
/usr/bin/install -c   ctl3d32.dll.so /usr/local/lib/wine/ctl3d32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ctl3d32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d10'
/usr/bin/install -c   d3d10.dll.so /usr/local/lib/wine/d3d10.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d10'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d8'
/usr/bin/install -c   d3d8.dll.so /usr/local/lib/wine/d3d8.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d9'
/usr/bin/install -c   d3d9.dll.so /usr/local/lib/wine/d3d9.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3d9'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dim'
/usr/bin/install -c   d3dim.dll.so /usr/local/lib/wine/d3dim.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dim'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3drm'
/usr/bin/install -c   d3drm.dll.so /usr/local/lib/wine/d3drm.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3drm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx8'
/usr/bin/install -c   d3dx8.dll.so /usr/local/lib/wine/d3dx8.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_24'
/usr/bin/install -c   d3dx9_24.dll.so /usr/local/lib/wine/d3dx9_24.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_24'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_25'
/usr/bin/install -c   d3dx9_25.dll.so /usr/local/lib/wine/d3dx9_25.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_25'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_26'
/usr/bin/install -c   d3dx9_26.dll.so /usr/local/lib/wine/d3dx9_26.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_26'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_27'
/usr/bin/install -c   d3dx9_27.dll.so /usr/local/lib/wine/d3dx9_27.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_27'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_28'
/usr/bin/install -c   d3dx9_28.dll.so /usr/local/lib/wine/d3dx9_28.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_28'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_29'
/usr/bin/install -c   d3dx9_29.dll.so /usr/local/lib/wine/d3dx9_29.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_29'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_30'
/usr/bin/install -c   d3dx9_30.dll.so /usr/local/lib/wine/d3dx9_30.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_30'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_31'
/usr/bin/install -c   d3dx9_31.dll.so /usr/local/lib/wine/d3dx9_31.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_31'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_32'
/usr/bin/install -c   d3dx9_32.dll.so /usr/local/lib/wine/d3dx9_32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_33'
/usr/bin/install -c   d3dx9_33.dll.so /usr/local/lib/wine/d3dx9_33.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_33'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_34'
/usr/bin/install -c   d3dx9_34.dll.so /usr/local/lib/wine/d3dx9_34.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_34'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_35'
/usr/bin/install -c   d3dx9_35.dll.so /usr/local/lib/wine/d3dx9_35.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_35'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_36'
/usr/bin/install -c   d3dx9_36.dll.so /usr/local/lib/wine/d3dx9_36.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_36'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_37'
/usr/bin/install -c   d3dx9_37.dll.so /usr/local/lib/wine/d3dx9_37.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dx9_37'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dxof'
/usr/bin/install -c   d3dxof.dll.so /usr/local/lib/wine/d3dxof.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/d3dxof'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dbghelp'
/usr/bin/install -c   dbghelp.dll.so /usr/local/lib/wine/dbghelp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dbghelp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dciman32'
/usr/bin/install -c   dciman32.dll.so /usr/local/lib/wine/dciman32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dciman32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ddraw'
/usr/bin/install -c   ddraw.dll.so /usr/local/lib/wine/ddraw.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ddraw'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ddrawex'
/usr/bin/install -c   ddrawex.dll.so /usr/local/lib/wine/ddrawex.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ddrawex'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/devenum'
/usr/bin/install -c   devenum.dll.so /usr/local/lib/wine/devenum.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/devenum'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
/usr/bin/install -c   dinput.dll.so /usr/local/lib/wine/dinput.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput8'
/usr/bin/install -c   dinput8.dll.so /usr/local/lib/wine/dinput8.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dinput8'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmband'
/usr/bin/install -c   dmband.dll.so /usr/local/lib/wine/dmband.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmband'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmcompos'
/usr/bin/install -c   dmcompos.dll.so /usr/local/lib/wine/dmcompos.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmcompos'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmime'
/usr/bin/install -c   dmime.dll.so /usr/local/lib/wine/dmime.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmime'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmloader'
/usr/bin/install -c   dmloader.dll.so /usr/local/lib/wine/dmloader.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmloader'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmscript'
/usr/bin/install -c   dmscript.dll.so /usr/local/lib/wine/dmscript.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmscript'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmstyle'
/usr/bin/install -c   dmstyle.dll.so /usr/local/lib/wine/dmstyle.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmstyle'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmsynth'
/usr/bin/install -c   dmsynth.dll.so /usr/local/lib/wine/dmsynth.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmsynth'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic'
/usr/bin/install -c   dmusic.dll.so /usr/local/lib/wine/dmusic.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic32'
/usr/bin/install -c   dmusic32.dll.so /usr/local/lib/wine/dmusic32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dmusic32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dnsapi'
/usr/bin/install -c   dnsapi.dll.so /usr/local/lib/wine/dnsapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dnsapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dplay'
/usr/bin/install -c   dplay.dll.so /usr/local/lib/wine/dplay.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dplay'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dplayx'
/usr/bin/install -c   dplayx.dll.so /usr/local/lib/wine/dplayx.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dplayx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnaddr'
/usr/bin/install -c   dpnaddr.dll.so /usr/local/lib/wine/dpnaddr.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnaddr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnet'
/usr/bin/install -c   dpnet.dll.so /usr/local/lib/wine/dpnet.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnhpast'
/usr/bin/install -c   dpnhpast.dll.so /usr/local/lib/wine/dpnhpast.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnhpast'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnlobby'
/usr/bin/install -c   dpnlobby.dll.so /usr/local/lib/wine/dpnlobby.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dpnlobby'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dsound'
/usr/bin/install -c   dsound.dll.so /usr/local/lib/wine/dsound.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dsound'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dssenh'
/usr/bin/install -c   dssenh.dll.so /usr/local/lib/wine/dssenh.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dssenh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dswave'
/usr/bin/install -c   dswave.dll.so /usr/local/lib/wine/dswave.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dswave'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dwmapi'
/usr/bin/install -c   dwmapi.dll.so /usr/local/lib/wine/dwmapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dwmapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/dxdiagn'
/usr/bin/install -c   dxdiagn.dll.so /usr/local/lib/wine/dxdiagn.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/dxdiagn'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/faultrep'
/usr/bin/install -c   faultrep.dll.so /usr/local/lib/wine/faultrep.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/faultrep'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/fusion'
/usr/bin/install -c   fusion.dll.so /usr/local/lib/wine/fusion.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/fusion'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gdi32'
/usr/bin/install -c   gdi32.dll.so /usr/local/lib/wine/gdi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gdi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gdiplus'
/usr/bin/install -c   gdiplus.dll.so /usr/local/lib/wine/gdiplus.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gdiplus'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gphoto2.ds'
/usr/bin/install -c   gphoto2.ds.so /usr/local/lib/wine/gphoto2.ds.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gphoto2.ds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/gpkcsp'
/usr/bin/install -c   gpkcsp.dll.so /usr/local/lib/wine/gpkcsp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/gpkcsp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hal'
/usr/bin/install -c   hal.dll.so /usr/local/lib/wine/hal.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hal'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hhctrl.ocx'
/usr/bin/install -c   hhctrl.ocx.so /usr/local/lib/wine/hhctrl.ocx.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hhctrl.ocx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hid'
/usr/bin/install -c   hid.dll.so /usr/local/lib/wine/hid.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hlink'
/usr/bin/install -c   hlink.dll.so /usr/local/lib/wine/hlink.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hlink'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/hnetcfg'
/usr/bin/install -c   hnetcfg.dll.so /usr/local/lib/wine/hnetcfg.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/hnetcfg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/iccvid'
/usr/bin/install -c   iccvid.dll.so /usr/local/lib/wine/iccvid.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/iccvid'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/icmp'
/usr/bin/install -c   icmp.dll.so /usr/local/lib/wine/icmp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/icmp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ifsmgr.vxd'
/usr/bin/install -c   ifsmgr.vxd.so /usr/local/lib/wine/ifsmgr.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ifsmgr.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imaadp32.acm'
/usr/bin/install -c   imaadp32.acm.so /usr/local/lib/wine/imaadp32.acm.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imaadp32.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imagehlp'
/usr/bin/install -c   imagehlp.dll.so /usr/local/lib/wine/imagehlp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imagehlp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/imm32'
/usr/bin/install -c   imm32.dll.so /usr/local/lib/wine/imm32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/imm32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inetcomm'
/usr/bin/install -c   inetcomm.dll.so /usr/local/lib/wine/inetcomm.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inetcomm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/infosoft'
/usr/bin/install -c   infosoft.dll.so /usr/local/lib/wine/infosoft.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/infosoft'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/initpki'
/usr/bin/install -c   initpki.dll.so /usr/local/lib/wine/initpki.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/initpki'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inkobj'
/usr/bin/install -c   inkobj.dll.so /usr/local/lib/wine/inkobj.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inkobj'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/inseng'
/usr/bin/install -c   inseng.dll.so /usr/local/lib/wine/inseng.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/inseng'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/iphlpapi'
/usr/bin/install -c   iphlpapi.dll.so /usr/local/lib/wine/iphlpapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/iphlpapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/itircl'
/usr/bin/install -c   itircl.dll.so /usr/local/lib/wine/itircl.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/itircl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/itss'
/usr/bin/install -c   itss.dll.so /usr/local/lib/wine/itss.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/itss'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/jscript'
/usr/bin/install -c   jscript.dll.so /usr/local/lib/wine/jscript.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/jscript'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/kernel32'
/usr/bin/install -c   kernel32.dll.so /usr/local/lib/wine/kernel32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/kernel32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/localspl'
/usr/bin/install -c   localspl.dll.so /usr/local/lib/wine/localspl.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/localspl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/localui'
/usr/bin/install -c   localui.dll.so /usr/local/lib/wine/localui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/localui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/lz32'
/usr/bin/install -c   lz32.dll.so /usr/local/lib/wine/lz32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/lz32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mapi32'
/usr/bin/install -c   mapi32.dll.so /usr/local/lib/wine/mapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciavi32'
/usr/bin/install -c   mciavi32.dll.so /usr/local/lib/wine/mciavi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciavi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mcicda'
/usr/bin/install -c   mcicda.dll.so /usr/local/lib/wine/mcicda.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mcicda'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciseq'
/usr/bin/install -c   mciseq.dll.so /usr/local/lib/wine/mciseq.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciseq'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mciwave'
/usr/bin/install -c   mciwave.dll.so /usr/local/lib/wine/mciwave.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mciwave'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/midimap'
/usr/bin/install -c   midimap.dll.so /usr/local/lib/wine/midimap.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/midimap'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mlang'
/usr/bin/install -c   mlang.dll.so /usr/local/lib/wine/mlang.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mlang'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mmdevldr.vxd'
/usr/bin/install -c   mmdevldr.vxd.so /usr/local/lib/wine/mmdevldr.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mmdevldr.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/monodebg.vxd'
/usr/bin/install -c   monodebg.vxd.so /usr/local/lib/wine/monodebg.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/monodebg.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mountmgr.sys'
/usr/bin/install -c   mountmgr.sys.so /usr/local/lib/wine/mountmgr.sys.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mountmgr.sys'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mpr'
/usr/bin/install -c   mpr.dll.so /usr/local/lib/wine/mpr.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mpr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mprapi'
/usr/bin/install -c   mprapi.dll.so /usr/local/lib/wine/mprapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mprapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32'
/usr/bin/install -c   msacm32.dll.so /usr/local/lib/wine/msacm32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32.drv'
/usr/bin/install -c   msacm32.drv.so /usr/local/lib/wine/msacm32.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msacm32.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msadp32.acm'
/usr/bin/install -c   msadp32.acm.so /usr/local/lib/wine/msadp32.acm.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msadp32.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscat32'
/usr/bin/install -c   mscat32.dll.so /usr/local/lib/wine/mscat32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscat32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscms'
/usr/bin/install -c   mscms.dll.so /usr/local/lib/wine/mscms.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscms'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mscoree'
/usr/bin/install -c   mscoree.dll.so /usr/local/lib/wine/mscoree.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mscoree'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msdmo'
/usr/bin/install -c   msdmo.dll.so /usr/local/lib/wine/msdmo.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msdmo'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msftedit'
/usr/bin/install -c   msftedit.dll.so /usr/local/lib/wine/msftedit.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msftedit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msg711.acm'
/usr/bin/install -c   msg711.acm.so /usr/local/lib/wine/msg711.acm.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msg711.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml'
/usr/bin/install -c   mshtml.dll.so /usr/local/lib/wine/mshtml.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml.tlb'
/usr/bin/install -c   mshtml.tlb.so /usr/local/lib/wine/mshtml.tlb.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mshtml.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msi'
/usr/bin/install -c   msi.dll.so /usr/local/lib/wine/msi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msimg32'
/usr/bin/install -c   msimg32.dll.so /usr/local/lib/wine/msimg32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msimg32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msimtf'
/usr/bin/install -c   msimtf.dll.so /usr/local/lib/wine/msimtf.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msimtf'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msisys.ocx'
/usr/bin/install -c   msisys.ocx.so /usr/local/lib/wine/msisys.ocx.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msisys.ocx'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msnet32'
/usr/bin/install -c   msnet32.dll.so /usr/local/lib/wine/msnet32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msnet32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msrle32'
/usr/bin/install -c   msrle32.dll.so /usr/local/lib/wine/msrle32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msrle32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mssip32'
/usr/bin/install -c   mssip32.dll.so /usr/local/lib/wine/mssip32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mssip32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcirt'
/usr/bin/install -c   msvcirt.dll.so /usr/local/lib/wine/msvcirt.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcirt'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcr71'
/usr/bin/install -c   msvcr71.dll.so /usr/local/lib/wine/msvcr71.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcr71'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt'
/usr/bin/install -c   msvcrt.dll.so /usr/local/lib/wine/msvcrt.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt20'
/usr/bin/install -c   msvcrt20.dll.so /usr/local/lib/wine/msvcrt20.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt20'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt40'
/usr/bin/install -c   msvcrt40.dll.so /usr/local/lib/wine/msvcrt40.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrt40'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrtd'
/usr/bin/install -c   msvcrtd.dll.so /usr/local/lib/wine/msvcrtd.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvcrtd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvfw32'
/usr/bin/install -c   msvfw32.dll.so /usr/local/lib/wine/msvfw32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvfw32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msvidc32'
/usr/bin/install -c   msvidc32.dll.so /usr/local/lib/wine/msvidc32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msvidc32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/mswsock'
/usr/bin/install -c   mswsock.dll.so /usr/local/lib/wine/mswsock.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/mswsock'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/msxml3'
/usr/bin/install -c   msxml3.dll.so /usr/local/lib/wine/msxml3.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/msxml3'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/nddeapi'
/usr/bin/install -c   nddeapi.dll.so /usr/local/lib/wine/nddeapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/nddeapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/netapi32'
/usr/bin/install -c   netapi32.dll.so /usr/local/lib/wine/netapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/netapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/newdev'
/usr/bin/install -c   newdev.dll.so /usr/local/lib/wine/newdev.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/newdev'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdll'
/usr/bin/install -c   ntdll.dll.so /usr/local/lib/wine/ntdll.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdll'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdsapi'
/usr/bin/install -c   ntdsapi.dll.so /usr/local/lib/wine/ntdsapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntdsapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntoskrnl.exe'
/usr/bin/install -c   ntoskrnl.exe.so /usr/local/lib/wine/ntoskrnl.exe.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntoskrnl.exe'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ntprint'
/usr/bin/install -c   ntprint.dll.so /usr/local/lib/wine/ntprint.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ntprint'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/objsel'
/usr/bin/install -c   objsel.dll.so /usr/local/lib/wine/objsel.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/objsel'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/odbc32'
/usr/bin/install -c   odbc32.dll.so /usr/local/lib/wine/odbc32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/odbc32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/odbccp32'
/usr/bin/install -c   odbccp32.dll.so /usr/local/lib/wine/odbccp32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/odbccp32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ole32'
/usr/bin/install -c   ole32.dll.so /usr/local/lib/wine/ole32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ole32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oleacc'
/usr/bin/install -c   oleacc.dll.so /usr/local/lib/wine/oleacc.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oleacc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oleaut32'
/usr/bin/install -c   oleaut32.dll.so /usr/local/lib/wine/oleaut32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oleaut32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olecli32'
/usr/bin/install -c   olecli32.dll.so /usr/local/lib/wine/olecli32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olecli32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/oledlg'
/usr/bin/install -c   oledlg.dll.so /usr/local/lib/wine/oledlg.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/oledlg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olepro32'
/usr/bin/install -c   olepro32.dll.so /usr/local/lib/wine/olepro32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olepro32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olesvr32'
/usr/bin/install -c   olesvr32.dll.so /usr/local/lib/wine/olesvr32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olesvr32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/olethk32'
/usr/bin/install -c   olethk32.dll.so /usr/local/lib/wine/olethk32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/olethk32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/pdh'
/usr/bin/install -c   pdh.dll.so /usr/local/lib/wine/pdh.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/pdh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/powrprof'
/usr/bin/install -c   powrprof.dll.so /usr/local/lib/wine/powrprof.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/powrprof'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/printui'
/usr/bin/install -c   printui.dll.so /usr/local/lib/wine/printui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/printui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/propsys'
/usr/bin/install -c   propsys.dll.so /usr/local/lib/wine/propsys.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/propsys'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/psapi'
/usr/bin/install -c   psapi.dll.so /usr/local/lib/wine/psapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/psapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/pstorec'
/usr/bin/install -c   pstorec.dll.so /usr/local/lib/wine/pstorec.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/pstorec'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qcap'
/usr/bin/install -c   qcap.dll.so /usr/local/lib/wine/qcap.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qcap'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qedit'
/usr/bin/install -c   qedit.dll.so /usr/local/lib/wine/qedit.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qedit'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgr'
/usr/bin/install -c   qmgr.dll.so /usr/local/lib/wine/qmgr.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgr'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgrprxy'
/usr/bin/install -c   qmgrprxy.dll.so /usr/local/lib/wine/qmgrprxy.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/qmgrprxy'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/quartz'
/usr/bin/install -c   quartz.dll.so /usr/local/lib/wine/quartz.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/quartz'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/query'
/usr/bin/install -c   query.dll.so /usr/local/lib/wine/query.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/query'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rasapi32'
/usr/bin/install -c   rasapi32.dll.so /usr/local/lib/wine/rasapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rasapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/resutils'
/usr/bin/install -c   resutils.dll.so /usr/local/lib/wine/resutils.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/resutils'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/riched20'
/usr/bin/install -c   riched20.dll.so /usr/local/lib/wine/riched20.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/riched20'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/riched32'
/usr/bin/install -c   riched32.dll.so /usr/local/lib/wine/riched32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/riched32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rpcrt4'
/usr/bin/install -c   rpcrt4.dll.so /usr/local/lib/wine/rpcrt4.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rpcrt4'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rsabase'
/usr/bin/install -c   rsabase.dll.so /usr/local/lib/wine/rsabase.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rsabase'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/rsaenh'
/usr/bin/install -c   rsaenh.dll.so /usr/local/lib/wine/rsaenh.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/rsaenh'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sane.ds'
/usr/bin/install -c   sane.ds.so /usr/local/lib/wine/sane.ds.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sane.ds'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sccbase'
/usr/bin/install -c   sccbase.dll.so /usr/local/lib/wine/sccbase.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sccbase'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/schannel'
/usr/bin/install -c   schannel.dll.so /usr/local/lib/wine/schannel.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/schannel'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/secur32'
/usr/bin/install -c   secur32.dll.so /usr/local/lib/wine/secur32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/secur32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/security'
/usr/bin/install -c   security.dll.so /usr/local/lib/wine/security.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/security'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sensapi'
/usr/bin/install -c   sensapi.dll.so /usr/local/lib/wine/sensapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sensapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/serialui'
/usr/bin/install -c   serialui.dll.so /usr/local/lib/wine/serialui.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/serialui'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/setupapi'
/usr/bin/install -c   setupapi.dll.so /usr/local/lib/wine/setupapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/setupapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc'
/usr/bin/install -c   sfc.dll.so /usr/local/lib/wine/sfc.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc_os'
/usr/bin/install -c   sfc_os.dll.so /usr/local/lib/wine/sfc_os.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sfc_os'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shdoclc'
/usr/bin/install -c   shdoclc.dll.so /usr/local/lib/wine/shdoclc.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shdoclc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shdocvw'
/usr/bin/install -c   shdocvw.dll.so /usr/local/lib/wine/shdocvw.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shdocvw'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shell32'
/usr/bin/install -c   shell32.dll.so /usr/local/lib/wine/shell32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shell32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shfolder'
/usr/bin/install -c   shfolder.dll.so /usr/local/lib/wine/shfolder.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shfolder'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/shlwapi'
/usr/bin/install -c   shlwapi.dll.so /usr/local/lib/wine/shlwapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/shlwapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/slbcsp'
/usr/bin/install -c   slbcsp.dll.so /usr/local/lib/wine/slbcsp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/slbcsp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/slc'
/usr/bin/install -c   slc.dll.so /usr/local/lib/wine/slc.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/slc'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/snmpapi'
/usr/bin/install -c   snmpapi.dll.so /usr/local/lib/wine/snmpapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/snmpapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/softpub'
/usr/bin/install -c   softpub.dll.so /usr/local/lib/wine/softpub.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/softpub'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/spoolss'
/usr/bin/install -c   spoolss.dll.so /usr/local/lib/wine/spoolss.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/spoolss'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole2.tlb'
/usr/bin/install -c   stdole2.tlb.so /usr/local/lib/wine/stdole2.tlb.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole2.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole32.tlb'
/usr/bin/install -c   stdole32.tlb.so /usr/local/lib/wine/stdole32.tlb.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/stdole32.tlb'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sti'
/usr/bin/install -c   sti.dll.so /usr/local/lib/wine/sti.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sti'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/svrapi'
/usr/bin/install -c   svrapi.dll.so /usr/local/lib/wine/svrapi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/svrapi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/sxs'
/usr/bin/install -c   sxs.dll.so /usr/local/lib/wine/sxs.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/sxs'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/tapi32'
/usr/bin/install -c   tapi32.dll.so /usr/local/lib/wine/tapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/tapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/twain_32'
/usr/bin/install -c   twain_32.dll.so /usr/local/lib/wine/twain_32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/twain_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/unicows'
/usr/bin/install -c   unicows.dll.so /usr/local/lib/wine/unicows.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/unicows'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/url'
/usr/bin/install -c   url.dll.so /usr/local/lib/wine/url.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/url'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/urlmon'
/usr/bin/install -c   urlmon.dll.so /usr/local/lib/wine/urlmon.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/urlmon'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/user32'
/usr/bin/install -c   user32.dll.so /usr/local/lib/wine/user32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/user32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/userenv'
/usr/bin/install -c   userenv.dll.so /usr/local/lib/wine/userenv.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/userenv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/usp10'
/usr/bin/install -c   usp10.dll.so /usr/local/lib/wine/usp10.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/usp10'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/uxtheme'
/usr/bin/install -c   uxtheme.dll.so /usr/local/lib/wine/uxtheme.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/uxtheme'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vdhcp.vxd'
/usr/bin/install -c   vdhcp.vxd.so /usr/local/lib/wine/vdhcp.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vdhcp.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vdmdbg'
/usr/bin/install -c   vdmdbg.dll.so /usr/local/lib/wine/vdmdbg.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vdmdbg'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/version'
/usr/bin/install -c   version.dll.so /usr/local/lib/wine/version.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/version'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vmm.vxd'
/usr/bin/install -c   vmm.vxd.so /usr/local/lib/wine/vmm.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vmm.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vnbt.vxd'
/usr/bin/install -c   vnbt.vxd.so /usr/local/lib/wine/vnbt.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vnbt.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vnetbios.vxd'
/usr/bin/install -c   vnetbios.vxd.so /usr/local/lib/wine/vnetbios.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vnetbios.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vtdapi.vxd'
/usr/bin/install -c   vtdapi.vxd.so /usr/local/lib/wine/vtdapi.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vtdapi.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/vwin32.vxd'
/usr/bin/install -c   vwin32.vxd.so /usr/local/lib/wine/vwin32.vxd.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/vwin32.vxd'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/w32skrnl'
/usr/bin/install -c   w32skrnl.dll.so /usr/local/lib/wine/w32skrnl.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/w32skrnl'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winealsa.drv'
/usr/bin/install -c   winealsa.drv.so /usr/local/lib/wine/winealsa.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winealsa.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineaudioio.drv'
/usr/bin/install -c   wineaudioio.drv.so /usr/local/lib/wine/wineaudioio.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineaudioio.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winecoreaudio.drv'
/usr/bin/install -c   winecoreaudio.drv.so /usr/local/lib/wine/winecoreaudio.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winecoreaudio.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wined3d'
/usr/bin/install -c   wined3d.dll.so /usr/local/lib/wine/wined3d.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wined3d'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winedos'
/usr/bin/install -c   winedos.dll.so /usr/local/lib/wine/winedos.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winedos'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineesd.drv'
/usr/bin/install -c   wineesd.drv.so /usr/local/lib/wine/wineesd.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineesd.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winejack.drv'
/usr/bin/install -c   winejack.drv.so /usr/local/lib/wine/winejack.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winejack.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winejoystick.drv'
/usr/bin/install -c   winejoystick.drv.so /usr/local/lib/wine/winejoystick.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winejoystick.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winemp3.acm'
/usr/bin/install -c   winemp3.acm.so /usr/local/lib/wine/winemp3.acm.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winemp3.acm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winenas.drv'
/usr/bin/install -c   winenas.drv.so /usr/local/lib/wine/winenas.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winenas.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineoss.drv'
/usr/bin/install -c   wineoss.drv.so /usr/local/lib/wine/wineoss.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineoss.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wineps.drv'
/usr/bin/install -c   wineps.drv.so /usr/local/lib/wine/wineps.drv.so
/usr/bin/install -c  -m 644  ./generic.ppd /usr/local/share/wine/generic.ppd
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wineps.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wing32'
/usr/bin/install -c   wing32.dll.so /usr/local/lib/wine/wing32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wing32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winhttp'
/usr/bin/install -c   winhttp.dll.so /usr/local/lib/wine/winhttp.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winhttp'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wininet'
/usr/bin/install -c   wininet.dll.so /usr/local/lib/wine/wininet.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wininet'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winmm'
/usr/bin/install -c   winmm.dll.so /usr/local/lib/wine/winmm.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winmm'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winnls32'
/usr/bin/install -c   winnls32.dll.so /usr/local/lib/wine/winnls32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winnls32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winscard'
/usr/bin/install -c   winscard.dll.so /usr/local/lib/wine/winscard.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winscard'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winspool.drv'
/usr/bin/install -c   winspool.drv.so /usr/local/lib/wine/winspool.drv.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winspool.drv'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wintab32'
/usr/bin/install -c   wintab32.dll.so /usr/local/lib/wine/wintab32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wintab32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wintrust'
/usr/bin/install -c   wintrust.dll.so /usr/local/lib/wine/wintrust.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wintrust'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wldap32'
/usr/bin/install -c   wldap32.dll.so /usr/local/lib/wine/wldap32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wldap32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wmi'
/usr/bin/install -c   wmi.dll.so /usr/local/lib/wine/wmi.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wmi'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wnaspi32'
/usr/bin/install -c   wnaspi32.dll.so /usr/local/lib/wine/wnaspi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wnaspi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wow32'
/usr/bin/install -c   wow32.dll.so /usr/local/lib/wine/wow32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wow32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/ws2_32'
/usr/bin/install -c   ws2_32.dll.so /usr/local/lib/wine/ws2_32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/ws2_32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wsock32'
/usr/bin/install -c   wsock32.dll.so /usr/local/lib/wine/wsock32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wsock32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/wtsapi32'
/usr/bin/install -c   wtsapi32.dll.so /usr/local/lib/wine/wtsapi32.dll.so
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/wtsapi32'
make[2]: Entering directory `/home/doug/Desktop/wine-0.9.61/dlls/winex11.drv'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o ime.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o systray.o text.o window.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so -lcomctl32 -luser32 -lgdi32 -ladvapi32 -limm32 -lkernel32 -lntdll -Wb,-dcomctl32 -L/usr/lib  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls/winex11.drv'
make[1]: *** [winex11.drv/__install-lib__] Error 2
make[1]: Leaving directory `/home/doug/Desktop/wine-0.9.61/dlls'
make: *** [dlls/__install-lib__] Error 2

``` and i need help either to fix all this ro to remove all of wine .61

---

### Post by Patb on 2008-05-04
Amyfan, you are trying to install without being root:
> $ make && make install
Try doing it in two steps:
```
make
```
then 
```
sudo make install
```
In any case, I would install the relevant compiled package directly from the [Wine site]("http://www.winehq.org/site/howto").

If you have not successfuilly installed and want to delete what you have done, just delete the directory you have unpacked into (presuming it has nothing else valuable in it).  If you want to uninstall, check the [Wine guidelines]("http://www.winehq.org/site/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE"). 

Cheers, Pat.

---

