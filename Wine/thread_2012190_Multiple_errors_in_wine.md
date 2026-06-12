---
title: "Multiple errors in wine"
date: 2012-06-28
forum: Wine
---

### Post by pajser on 2012-06-28
Wine only lunches apps trough console, everything worked fine before I updated ubuntu. I uninstalled and installed wine tryd different versions, and I somehow broke wine tricks (witch is second problem) when i lunch it trough command line i get "wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ...". 
These are really low priority. One thing that was caused by trying to fix above was that i somehow deleted all my settings and now I got a bug that somehow disapeerd 5 months ago (probably by me but i dont know how). And this is really a weird bug I googled and lookd at apphq wine database and could not found anyone with same problem. 
It goes lunch starcraft and i get ubuntu dash board on really low resolution ( you cant view map its impossible) so solution to this is that i uncheck in wine config "allow window maneger to control windows" (in graphics tab) but by doing that i get extreme lags that are caused by clicing the mouse (im not sure of this but it lags).  Please help me

winetricks -v
[QUOTE+ return 0
[SIZE=1]+ shift
+ winetricks_handle_option
+ return 1
+ winetricks_init
+ test marin
+ WINETRICKS_WORKDIR=/tmp/w.marin.15843
+ test  = 1
+ rm -rf /tmp/w.marin.15843
+ WINETRICKS_METADATA=/tmp/w.marin.15843/metadata
+ WINETRICKS_CATEGORIES=apps benchmarks dlls fonts games settings
+ mkdir -p /tmp/w.marin.15843/metadata/apps
+ mkdir -p /tmp/w.marin.15843/metadata/benchmarks
+ mkdir -p /tmp/w.marin.15843/metadata/dlls
+ mkdir -p /tmp/w.marin.15843/metadata/fonts
+ mkdir -p /tmp/w.marin.15843/metadata/games
+ mkdir -p /tmp/w.marin.15843/metadata/settings
+ WINETRICKS_CURMENU=prefix
+ trap winetricks_cleanup EXIT HUP INT QUIT ABRT
+ WINETRICKS_OPT_KEEPISOS=0
+ WINETRICKS_OPT_DD=dd
+ WINETRICKS_OPT_SHAREDPREFIX=0
+ which sha1sum
+ [ -x /usr/bin/sha1sum ]
+ WINETRICKS_SHA1SUM=sha1sum
+ date +%S
+ WINETRICKS_SOURCEFORGE=http://downloads.sourceforge.net
+ test -d /home/marin/Library/Caches
+ XDG_CACHE_HOME=/home/marin/.cache
+ test 
+ W_CACHE=/home/marin/.cache/winetricks
+ WINETRICKS_POST=/home/marin/.local/share/winetricks/postinstall
+ test -d /home/marin/.cache/winetricks
+ WINETRICKS_AUTH=/home/marin/.local/share/winetricks/auth
+ WINE=wine
+ test -x wineserver
+ dirname wine
+ test -x ./server/wineserver
+ which wineserver
+ test -x /usr/bin/wineserver
+ which wineserver
+ WINESERVER=/usr/bin/wineserver
+ test 
+ WINETRICKS_ORIGINAL_WINEPREFIX=/home/marin/.wine
+ which wine
+ _abswine=/usr/bin/wine
+ test -x /usr/bin/wine
+ test -f /usr/bin/wine
+ echo -n Wine is 'wine'; Wine version is 
Wine is 'wine'; Wine version is + wine --version
wine-1.4
+ unset _abswine
+ winetricks_set_wineprefix
+ test 
+ WINEPREFIX=/home/marin/.wine
+ export WINEPREFIX
+ dirname /home/marin/.wine
+ mkdir -p /home/marin
+ w_expand_env ProgramFiles
+ winetricks_early_wine cmd.exe /c echo %ProgramFiles%
+ WINEDEBUG=-all wine cmd.exe /c echo %ProgramFiles%
+ tr -d+  \r
grep+  -v Module not found
sed s/.*1h.=//
+ W_PROGRAMS_WIN=%ProgramFiles%
+ w_die wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ... can be caused a corrupt wineprefix, an old wine, or by not owning /home/marin/.wine
+ w_warn wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ... can be caused a corrupt wineprefix, an old wine, or by not owning /home/marin/.wine
+ echo ------------------------------------------------------
------------------------------------------------------
+ echo wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ... can be caused a corrupt wineprefix, an old wine, or by not owning /home/marin/.wine
wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ... can be caused a corrupt wineprefix, an old wine, or by not owning /home/marin/.wine
+ echo ------------------------------------------------------
------------------------------------------------------
+ test
+ unset _W_timeout
+ exit 1
+ winetricks_cleanup
+ set +e
+ test -f /tmp/w.marin.15843/dd-pid
+ test 
+ test  = 1
+ rm -rf /tmp/w.marin.15843[/SIZE]
][/QUOTE]

for starcraft bug i messed with regedit, tryd most of recomended things for playing games on wine like setting variables for graphics to use opengl etc.

---

