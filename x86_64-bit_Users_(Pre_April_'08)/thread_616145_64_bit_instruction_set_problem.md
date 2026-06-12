---
title: "64 bit instruction set problem"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-11-17
Does anyone know how to enable 64 bit in make.conf?  I get errors.  The sdl and xml errors were fixed after this post.

djr@popeyes-laptop:~/cvs/elc$ make -f Makefile.linux
make: sdl-config: Command not found
make: xml2-config: Command not found
make: sdl-config: Command not found
make: xml2-config: Command not found
gcc -march=i686 -Wall -Wdeclaration-after-statement -O0 -ggdb -pipe -DLINUX -DELC  -DAFK_FIX  -DALPHA_ACTORS  -DATI_9200_FIX  -DAUTO_UPDATE  -DCOUNTERS  -DCUSTOM_LOOK  -DCUSTOM_UPDATE  -DCXX_MISC  -DEYE_CANDY  -DFONTS_FIX  -DFUZZY_PATHS  -DIDLE_FIX  -DMASKING  -DNEW_ACTOR_ANIMATION  -DNEW_TEX  -DOGG_VORBIS  -DOPTIONS_I18N  -DPNG_SCREENSHOT  -DPOPUP  -DSFX  -DSIMPLE_LOD  -DUSE_INLINE  -DUSE_SEND_VIDEO_INFO  -DZLIB  -DPNG_SCREENSHOT   -fno-strict-aliasing  -MM  2d_objects.c  3d_objects.c  actor_scripts.c  actors.c  alphamap.c  asc.c  astrology.c  bbox_tree.c  books.c  buddy.c  bags.c  cache.c  cal.c  chat.c  cluster.c  colors.c  console.c  consolewin.c  counters.c  cursors.c  dialogues.c  draw_scene.c  elconfig.c  elwindows.c  encyclopedia.c  errors.c  events.c  filter.c  font.c  framebuffer.c  frustum.c  gamewin.c  gl_init.c  hud.c  help.c  highlight.c  ignore.c  init.c  interface.c  items.c  io/e3d_io.c  io/elc_io.c  io/map_io.c  keys.c  knowledge.c  langselwin.c  lights.c  list.c  load_gl_extensions.c  loginwin.c  loading_win.c  main.c  manufacture.c  map.c  mapwin.c  md5.c  mines.c  misc.c  multiplayer.c  new_actors.c  new_character.c  openingwin.c  particles.c  paste.c  pathfinder.c  pm_log.c  questlog.c  queue.c  reflection.c  rules.c  skills.c  serverpopup.c  servers.c  session.c  shadows.c  sound.c  spells.c  stats.c  storage.c  tabs.c  text.c  textures.c  tile_map.c  timers.c  translate.c  trade.c  update.c  url.c  weather.c  widgets.c  popup.c  special_effects.c >.depend
2d_objects.c:0: error: CPU you selected does not support x86-64 instruction set
3d_objects.c:0: error: CPU you selected does not support x86-64 instruction set
actor_scripts.c:0: error: CPU you selected does not support x86-64 instruction set
actors.c:0: error: CPU you selected does not support x86-64 instruction set
alphamap.c:0: error: CPU you selected does not support x86-64 instruction set
asc.c:0: error: CPU you selected does not support x86-64 instruction set
astrology.c:0: error: CPU you selected does not support x86-64 instruction set
bbox_tree.c:0: error: CPU you selected does not support x86-64 instruction set
books.c:0: error: CPU you selected does not support x86-64 instruction set
buddy.c:0: error: CPU you selected does not support x86-64 instruction set
bags.c:0: error: CPU you selected does not support x86-64 instruction set
cache.c:0: error: CPU you selected does not support x86-64 instruction set
cal.c:0: error: CPU you selected does not support x86-64 instruction set
chat.c:0: error: CPU you selected does not support x86-64 instruction set
cluster.c:0: error: CPU you selected does not support x86-64 instruction set
colors.c:0: error: CPU you selected does not support x86-64 instruction set
console.c:0: error: CPU you selected does not support x86-64 instruction set
consolewin.c:0: error: CPU you selected does not support x86-64 instruction set
counters.c:0: error: CPU you selected does not support x86-64 instruction set
cursors.c:0: error: CPU you selected does not support x86-64 instruction set
dialogues.c:0: error: CPU you selected does not support x86-64 instruction set
draw_scene.c:0: error: CPU you selected does not support x86-64 instruction set
elconfig.c:0: error: CPU you selected does not support x86-64 instruction set
elwindows.c:0: error: CPU you selected does not support x86-64 instruction set
encyclopedia.c:0: error: CPU you selected does not support x86-64 instruction set
errors.c:0: error: CPU you selected does not support x86-64 instruction set
events.c:0: error: CPU you selected does not support x86-64 instruction set
filter.c:0: error: CPU you selected does not support x86-64 instruction set
font.c:0: error: CPU you selected does not support x86-64 instruction set
framebuffer.c:0: error: CPU you selected does not support x86-64 instruction set
frustum.c:0: error: CPU you selected does not support x86-64 instruction set
gamewin.c:0: error: CPU you selected does not support x86-64 instruction set
gl_init.c:0: error: CPU you selected does not support x86-64 instruction set
hud.c:0: error: CPU you selected does not support x86-64 instruction set
I am installing sdl and xml1, xml2 as I type this.  I know my cpu is 64 bit.  
Intel T7200 core 2 duo.
Do I have the wrong Gutsy installed? How can I check. Or am I missing a module?
I did the auto-update installation of Gutsy via update manager.
help.c:0: error: CPU you selected does not support x86-64 instruction set
highlight.c:0: error: CPU you selected does not support x86-64 instruction set
ignore.c:0: error: CPU you selected does not support x86-64 instruction set
init.c:0: error: CPU you selected does not support x86-64 instruction set
interface.c:0: error: CPU you selected does not support x86-64 instruction set
items.c:0: error: CPU you selected does not support x86-64 instruction set
io/e3d_io.c:0: error: CPU you selected does not support x86-64 instruction set
io/elc_io.c:0: error: CPU you selected does not support x86-64 instruction set
io/map_io.c:0: error: CPU you selected does not support x86-64 instruction set
keys.c:0: error: CPU you selected does not support x86-64 instruction set
knowledge.c:0: error: CPU you selected does not support x86-64 instruction set
langselwin.c:0: error: CPU you selected does not support x86-64 instruction set
lights.c:0: error: CPU you selected does not support x86-64 instruction set
list.c:0: error: CPU you selected does not support x86-64 instruction set
load_gl_extensions.c:0: error: CPU you selected does not support x86-64 instruction set
loginwin.c:0: error: CPU you selected does not support x86-64 instruction set
loading_win.c:0: error: CPU you selected does not support x86-64 instruction set
main.c:0: error: CPU you selected does not support x86-64 instruction set
manufacture.c:0: error: CPU you selected does not support x86-64 instruction set
map.c:0: error: CPU you selected does not support x86-64 instruction set
mapwin.c:0: error: CPU you selected does not support x86-64 instruction set
I am installing sdl and xml1, xml2 as I type this.  I know my cpu is 64 bit.  
Intel T7200 core 2 duo.
Do I have the wrong Gutsy installed? How can I check. Or am I missing a module?
I did the auto-update installation of Gutsy via update manager.
md5.c:0: error: CPU you selected does not support x86-64 instruction set
mines.c:0: error: CPU you selected does not support x86-64 instruction set
misc.c:0: error: CPU you selected does not support x86-64 instruction set
multiplayer.c:0: error: CPU you selected does not support x86-64 instruction set
new_actors.c:0: error: CPU you selected does not support x86-64 instruction set
new_character.c:0: error: CPU you selected does not support x86-64 instruction set
openingwin.c:0: error: CPU you selected does not support x86-64 instruction set
particles.c:0: error: CPU you selected does not support x86-64 instruction set
paste.c:0: error: CPU you selected does not support x86-64 instruction set
pathfinder.c:0: error: CPU you selected does not support x86-64 instruction set
pm_log.c:0: error: CPU you selected does not support x86-64 instruction set
questlog.c:0: error: CPU you selected does not support x86-64 instruction set
I am installing sdl and xml1, xml2 as I type this.  I know my cpu is 64 bit.  
Intel T7200 core 2 duo.
Do I have the wrong Gutsy installed? How can I check. Or am I missing a module?
I did the auto-update installation of Gutsy via update manager.
queue.c:0: error: CPU you selected does not support x86-64 instruction set
reflection.c:0: error: CPU you selected does not support x86-64 instruction set
rules.c:0: error: CPU you selected does not support x86-64 instruction set
skills.c:0: error: CPU you selected does not support x86-64 instruction set
serverpopup.c:0: error: CPU you selected does not support x86-64 instruction set
servers.c:0: error: CPU you selected does not support x86-64 instruction set
session.c:0: error: CPU you selected does not support x86-64 instruction set
shadows.c:0: error: CPU you selected does not support x86-64 instruction set
sound.c:0: error: CPU you selected does not support x86-64 instruction set
spells.c:0: error: CPU you selected does not support x86-64 instruction set
stats.c:0: error: CPU you selected does not support x86-64 instruction set
storage.c:0: error: CPU you selected does not support x86-64 instruction set
I am installing sdl and xml1, xml2 as I type this.  I know my cpu is 64 bit.  
Intel T7200 core 2 duo.
Do I have the wrong Gutsy installed? How can I check. Or am I missing a module?
I did the auto-update installation of Gutsy via update manager.
tabs.c:0: error: CPU you selected does not support x86-64 instruction set
text.c:0: error: CPU you selected does not support x86-64 instruction set
textures.c:0: error: CPU you selected does not support x86-64 instruction set
tile_map.c:0: error: CPU you selected does not support x86-64 instruction set
timers.c:0: error: CPU you selected does not support x86-64 instruction set
translate.c:0: error: CPU you selected does not support x86-64 instruction set
trade.c:0: error: CPU you selected does not support x86-64 instruction set
update.c:0: error: CPU you selected does not support x86-64 instruction set
url.c:0: error: CPU you selected does not support x86-64 instruction set
weather.c:0: error: CPU you selected does not support x86-64 instruction set
widgets.c:0: error: CPU you selected does not support x86-64 instruction set
popup.c:0: error: CPU you selected does not support x86-64 instruction set
special_effects.c:0: error: CPU you selected does not support x86-64 instruction set
make: sdl-config: Command not found
make: xml2-config: Command not found
gcc -march=i686 -Wall -Wdeclaration-after-statement -O0 -ggdb -pipe -DLINUX -DELC  -DAFK_FIX  -DALPHA_ACTORS  -DATI_9200_FIX  -DAUTO_UPDATE  -DCOUNTERS  -DCUSTOM_LOOK  -DCUSTOM_UPDATE  -DCXX_MISC  -DEYE_CANDY  -DFONTS_FIX  -DFUZZY_PATHS  -DIDLE_FIX  -DMASKING  -DNEW_ACTOR_ANIMATION  -DNEW_TEX  -DOGG_VORBIS  -DOPTIONS_I18N  -DPNG_SCREENSHOT  -DPOPUP  -DSFX  -DSIMPLE_LOD  -DUSE_INLINE  -DUSE_SEND_VIDEO_INFO  -DZLIB  -DPNG_SCREENSHOT   -fno-strict-aliasing  -c -o 2d_objects.o 2d_objects.c
2d_objects.c:1: error: CPU you selected does not support x86-64 instruction set
make: *** [2d_objects.o] Error 1

---

### Post by jaakan on 2007-11-18
" gcc -march=i686 "
that should be x64_86 or something

---

