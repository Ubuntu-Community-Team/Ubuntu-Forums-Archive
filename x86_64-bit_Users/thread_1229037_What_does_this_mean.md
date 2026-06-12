---
title: "What does this mean?"
date: 2009-08-01
forum: x86 64-bit Users
---

### Post by goldstar1 on 2009-08-01
george@georges-desktop:~$ sudo mkdir /mnt/MintHome
sudo: unable to resolve host georges-desktop
george@georges-desktop:~$

It made the directory...what does "sudo: unable to resolve host georges-desktop" mean?

---

### Post by gila_monster on 2009-08-01
Can you post the output of

```
cat /etc/hosts
```

please? I think there's something up with that file.

---

### Post by oldos2er on 2009-08-01
Can you post the output from the command ```
cat /etc/hosts
```

---

### Post by goldstar1 on 2009-08-01
There are a lot of what looks like junk advertising there. What is all that junk?

I'm writing this because firefox freezes when I attempt to copy and paste to this site.

---

### Post by goldstar1 on 2009-08-01
```
127.0.0.1  ad.media-servers.net
127.0.0.1  ad.mediaprecision.net
127.0.0.1  servedby.morningfalls.com
127.0.0.1  ad.motiveinteractive.com
127.0.0.1  ad.oinadserver.com #[McAfee.Adware-ClickSpring]
127.0.0.1  ad.realcastmedia.com
127.0.0.1  ad.reduxmedia.com
127.0.0.1  optimizedby.rmxads.com
127.0.0.1  ad.scanmedios.com
127.0.0.1  ad.smowtion.com
127.0.0.1  ad.targetingmarketplace.com
127.0.0.1  ad.theadhost.com
127.0.0.1  ad.thewheelof.com
127.0.0.1  ext.tyroo.com
127.0.0.1  ad.valencemedia.com
127.0.0.1  ad.xplusone.com
127.0.0.1  ad.xtendmedia.com
127.0.0.1  cookex.amp.yahoo.com
127.0.0.1  ad.yieldmanager.com #[MVPS.Criteria]
127.0.0.1  ad.yieldx.com
127.0.0.1  ad.z5x.net
# [Yahoo via Right Media - clones via various]
127.0.0.1  content.91s.com
127.0.0.1  content.adconsole.com #[eXact Advertising]
127.0.0.1  content.ad-flow.com
127.0.0.1  content.adnetinteractive.com
127.0.0.1  content.adtegrity.net
127.0.0.1  content.attune.com
127.0.0.1  content.axill.com
127.0.0.1  content.bannerconnect.net
127.0.0.1  content.bigad.com
127.0.0.1  content.contentspecific.com
127.0.0.1  content.cpxinteractive.com
127.0.0.1  content.exigomedia.com
127.0.0.1  content.firstadsolution.com
127.0.0.1  content.globalinteractive.com
127.0.0.1  content.iconadserver.com
127.0.0.1  content.ireit.com
127.0.0.1  content.joetec.net
127.0.0.1  content.joinaxxess.com
127.0.0.1  content.marketingsector.com
127.0.0.1  content.media-servers.net
127.0.0.1  content.mediaprecision.net #[ClickSpring]
127.0.0.1  content.motiveinteractive.com
127.0.0.1  content.realcastmedia.com
127.0.0.1  content.reduxmedia.com
127.0.0.1  content.scanmedios.com
127.0.0.1  adserver.sitesense.com #[Parking Service]
127.0.0.1  content.thewheelof.com
127.0.0.1  content.valencemedia.com
127.0.0.1  content.womensforum.com
127.0.0.1  content.yieldx.com
# [Yaris Industries][AS40824][91.210.56.0 - 91.210.59.255]
127.0.0.1  ultraantivirus2009.com #[Fraudware.Pandora-Software]
127.0.0.1  [www.ultraantivirus2009.com]("http://www.ultraantivirus2009.com")
# [YAWSA LLC][MaxSearch Group][194.90.224.80 - 194.90.224.87]
127.0.0.1  [www.adoptim.com]("http://www.adoptim.com")
127.0.0.1  ariboo.com #[goto.maxifiles.com]
127.0.0.1  de.ariboo.com
127.0.0.1  dk.ariboo.com
127.0.0.1  es.ariboo.com
127.0.0.1  fi.ariboo.com
127.0.0.1  fr.ariboo.com
127.0.0.1  nl.ariboo.com
127.0.0.1  uk.ariboo.com
127.0.0.1  [www.ariboo.com]("http://www.ariboo.com")
127.0.0.1  freeprod.com #[SunBelt.Freeprod/Toolbar888]
127.0.0.1  media.freeprod.com #[Adware/Toolbar888]
127.0.0.1  [www.freeprod.com]("http://www.freeprod.com")
127.0.0.1  jouezgagnant.com
127.0.0.1  goto.maxifiles.com #[TROJ_DLOADER.ACA][Adware.Director]
127.0.0.1  network.maxifiles.com
127.0.0.1  [www.maximpic.com]("http://www.maximpic.com") #[speedtest.dll]
127.0.0.1  referenco.com
127.0.0.1  [www.speedmeter.info]("http://www.speedmeter.info") #[speedtest.dll]
127.0.0.1  admin.teddycash.com
127.0.0.1  [www.teddycash.com]("http://www.teddycash.com")
127.0.0.1  admin.waverevenue.com
127.0.0.1  media.waverevenue.com
127.0.0.1  static.waverevenue.com
# [Yawsa via Yauza][194.90.224.80 - 194.90.224.87]
127.0.0.1  wr.kastora.com
127.0.0.1  wrsavn.kastora.com
127.0.0.1  bugreport.waverevenue.com
# [Yawsa via M5 Computer Security][206.251.244.0 - 206.251.244.255]
127.0.0.1  dl2.bundlext.com
127.0.0.1  [www.fresh-weather.com]("http://www.fresh-weather.com") #[Adware.Fresh]
127.0.0.1  maxifiles.com
127.0.0.1  xml.maxifiles.com
# [Yawsa via M5 Computer Security][206.251.244.0 - 206.251.244.255]
# [Yawsa via M5 Computer Security][206.71.190.0 - 206.71.190.255]
127.0.0.1  b152.bundlext.com
127.0.0.1  b155.bundlext.com
# [Yawsa via M5 Barak I.t.c][62.90.134.0 - 62.90.134.255]
127.0.0.1  mtn6.com-com.ws
127.0.0.1  wrsavn.flutix.com
127.0.0.1  mtn5.goole.ws
# [Yesup Ecommerce Solutions][66.48.78.192 - 66.48.78.255]
127.0.0.1  ads.adonion.com
127.0.0.1  banner.adsrevenue.net
127.0.0.1  popunder.adsrevenue.net #[McAfee.AdClicker-GD]
127.0.0.1  clicksor.com
127.0.0.1  ads.clicksor.com
127.0.0.1  main.clicksor.com
127.0.0.1  mci12.clicksor.com
127.0.0.1  search.clicksor.com
127.0.0.1  serw.clicksor.com
127.0.0.1  track.clicksor.com
127.0.0.1  [www.clicksor.com]("http://www.clicksor.com")
127.0.0.1  mp.clicksor.net
127.0.0.1  [www.e-mailpromotion.com]("http://www.e-mailpromotion.com")
127.0.0.1  goadbar.com
127.0.0.1  gopopup.com
127.0.0.1  [www.gopopup.com]("http://www.gopopup.com")
127.0.0.1  [www.infinityads.com]("http://www.infinityads.com")
127.0.0.1  multipops.com
127.0.0.1  service.multi-pops.com
127.0.0.1  www1.multipops.com
127.0.0.1  www2.multipops.com
127.0.0.1  [www.multipops.com]("http://www.multipops.com")
127.0.0.1  [www.myroitracking.com]("http://www.myroitracking.com")
127.0.0.1  paypopup.com
127.0.0.1  banner.paypopup.com
127.0.0.1  central.paypopup.com
127.0.0.1  central2.paypopup.com
127.0.0.1  creative.paypopup.com
127.0.0.1  popunder.paypopup.com
127.0.0.1  www1.paypopup.com
127.0.0.1  www2.paypopup.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www3.paypopup.com
127.0.0.1  www4.paypopup.com
127.0.0.1  www5.paypopup.com
127.0.0.1  www6.paypopup.com
127.0.0.1  www7.paypopup.com
127.0.0.1  www8.paypopup.com
127.0.0.1  www9.paypopup.com #[toolbar.cab][hotbar.com]
127.0.0.1  www10.paypopup.com
127.0.0.1  www21.paypopup.com #[SunBelt.PayPopup.com]
127.0.0.1  www210.paypopup.com
127.0.0.1  www211.paypopup.com
127.0.0.1  www212.paypopup.com
127.0.0.1  www213.paypopup.com
127.0.0.1  www214.paypopup.com
127.0.0.1  www215.paypopup.com
127.0.0.1  www216.paypopup.com
127.0.0.1  www217.paypopup.com
127.0.0.1  www218.paypopup.com
127.0.0.1  www219.paypopup.com
127.0.0.1  www220.paypopup.com
127.0.0.1  www221.paypopup.com
127.0.0.1  [www.paypopup.com]("http://www.paypopup.com") #[eTrust.Tracking.Cookie]
127.0.0.1  popinads.com
127.0.0.1  [www.popinads.com]("http://www.popinads.com")
127.0.0.1  [www.xxxwebtraffic.com]("http://www.xxxwebtraffic.com")
127.0.0.1  yesadvertising.com
127.0.0.1  test.yesadvertising.com
127.0.0.1  www1.yesadvertising.com
127.0.0.1  www2.yesadvertising.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www3.yesadvertising.com
127.0.0.1  www4.yesadvertising.com
127.0.0.1  www5.yesadvertising.com
127.0.0.1  www6.yesadvertising.com
127.0.0.1  www7.yesadvertising.com
127.0.0.1  www8.yesadvertising.com
127.0.0.1  www9.yesadvertising.com
127.0.0.1  www10.yesadvertising.com
127.0.0.1  www11.yesadvertising.com
127.0.0.1  www12.yesadvertising.com
127.0.0.1  www13.yesadvertising.com
127.0.0.1  www14.yesadvertising.com
127.0.0.1  www15.yesadvertising.com
127.0.0.1  www215.yesadvertising.com
127.0.0.1  www216.yesadvertising.com
127.0.0.1  www217.yesadvertising.com
127.0.0.1  www218.yesadvertising.com
127.0.0.1  www219.yesadvertising.com
127.0.0.1  www220.yesadvertising.com
127.0.0.1  www221.yesadvertising.com
127.0.0.1  yesup.com
127.0.0.1  bt.yesup.com
127.0.0.1  reseller.yesup.com
127.0.0.1  us.yesup.com
127.0.0.1  www2.yesup.com
127.0.0.1  [www.yesup.com]("http://www.yesup.com")
127.0.0.1  forum.yesup.net
127.0.0.1  [www.yesup.net]("http://www.yesup.net")
# [Yesup Ecommerce Solutions][66.48.81.128 - 66.48.81.255]
127.0.0.1  serving.adsrevenue.clicksor.net
127.0.0.1  yourstats.net
127.0.0.1  [www.yourstats.net]("http://www.yourstats.net")
# [Zao National][77.221.148.0 - 77.221.151.255]
# [Zao National][AS30968][92.243.72.0 - 92.243.75.255]
127.0.0.1  wecanall.net
# [Zango / 180Solutions][CDT Inc]
127.0.0.1  180solutions.com
127.0.0.1  ads.180solutions.com
127.0.0.1  ax.180solutions.com
127.0.0.1  bis.180solutions.com #[ADW_SOLU180.F]
127.0.0.1  config.180solutions.com #[eTrust.180SearchAssistant]
127.0.0.1  his.180solutions.com
127.0.0.1  ping.180solutions.com
127.0.0.1  tv.180solutions.com
127.0.0.1  tvf.180solutions.com
127.0.0.1  [www.180solutions.com]("http://www.180solutions.com")
127.0.0.1  [www.180solutions.net]("http://www.180solutions.net")
127.0.0.1  infinity.180searchassistant.com #[ADW_SOLU180.H]
127.0.0.1  msxml.180searchassistant.com #[msxml.infospace.com]
127.0.0.1  powered-by.180searchassistant.com
127.0.0.1  searchresults.180searchassistant.com
127.0.0.1  [www.180searchassistant.com]("http://www.180searchassistant.com") #[Adware.180Search]
127.0.0.1  [www.abcfreedownloads.com]("http://www.abcfreedownloads.com")
127.0.0.1  [www.abcfreegames.com]("http://www.abcfreegames.com")
127.0.0.1  freegamesclub.com
127.0.0.1  [www.fullarmorstudios.com]("http://www.fullarmorstudios.com")
127.0.0.1  [www.games4good.net]("http://www.games4good.net")
127.0.0.1  content.licenseacquisition.org #[Troj/QLowZon-EV]
127.0.0.1  drm.licenseacquisition.org
127.0.0.1  media.licenseacquisition.org #[SiteAdvisor.licenseacquisition.org]
127.0.0.1  origin-cached.licenseacquisition.org
127.0.0.1  preview.licenseacquisition.org
127.0.0.1  metricsdirect.com
127.0.0.1  ads.metricsdirect.com
127.0.0.1  cts.metricsdirect.com
127.0.0.1  reports.metricsdirect.com
127.0.0.1  [www.metricsdirect.com]("http://www.metricsdirect.com")
127.0.0.1  [www.myfreegamedownloads.com]("http://www.myfreegamedownloads.com")
127.0.0.1  n-case.com
127.0.0.1  [www.n-case.com]("http://www.n-case.com") #[Panda.Adware/nCase]
127.0.0.1  games.platrium.com
127.0.0.1  gec.platrium.com
127.0.0.1  installs.platrium.com
127.0.0.1  preview.platrium.com
127.0.0.1  [www.platrium.com]("http://www.platrium.com")
127.0.0.1  search.prositefinder.com #[SunBelt.bho.180Solutions.ProSiteFinder][ValueClick]
127.0.0.1  seekmo.com #[Adware.180Solutions.SearchAssistant]
127.0.0.1  config.seekmo.com
127.0.0.1  cts.seekmo.com
127.0.0.1  downloads.seekmo.com
127.0.0.1  galleries.seekmo.com
127.0.0.1  installs.seekmo.com
127.0.0.1  powered-by.seekmo.com
127.0.0.1  tvf.seekmo.com
127.0.0.1  allofthevideos.powered-by.seekmo.com
127.0.0.1  freeblowjobmovies.powered-by.seekmo.com
127.0.0.1  freeblowjobvideos.powered-by.seekmo.com
127.0.0.1  free-hd-movies.powered-by.seekmo.com
127.0.0.1  funberry.powered-by.seekmo.com
127.0.0.1  keyrastriptease.powered-by.seekmo.com
127.0.0.1  male-celeb-videos.powered-by.seekmo.com
127.0.0.1  pariswallpapers.powered-by.seekmo.com #[WildcardDNS]
127.0.0.1  slutmatrixfree.powered-by.seekmo.com
127.0.0.1  vidshrine.com.powered-by.seekmo.com
127.0.0.1  wallpapernudes.powered-by.seekmo.com
127.0.0.1  te.seekmo.com
127.0.0.1  tv.seekmo.com #[MVPS.Criteria]
127.0.0.1  [www.seekmo.com]("http://www.seekmo.com")
127.0.0.1  tons-of-free-downloads.com
127.0.0.1  tons-of-free-games.com
127.0.0.1  [www.tonsoffreedownloads.com]("http://www.tonsoffreedownloads.com")
127.0.0.1  [www.tonsoffreegames.com]("http://www.tonsoffreegames.com")
127.0.0.1  [www.totallycoolfreedownloads.com]("http://www.totallycoolfreedownloads.com")
127.0.0.1  totallyfunfreegames.com
127.0.0.1  [www.totallyfunfreegames.com]("http://www.totallyfunfreegames.com")
127.0.0.1  white.totallyfunfreestuff.com
127.0.0.1  [www.totallyfunfreestuff.com]("http://www.totallyfunfreestuff.com")
127.0.0.1  zango.com #[SiteAdvisor.zango]
127.0.0.1  adservices.zango.com
127.0.0.1  analytics.zango.com #[zango.com.112.2o7.net]
127.0.0.1  cds.zango.com
127.0.0.1  acces.powered-by.zango.com
127.0.0.1  animeim.powered-by.zango.com
127.0.0.1  annakournikova.powered-by.zango.com
127.0.0.1  cars-screensavers.com.powered-by.zango.com
127.0.0.1  clickpixcursors.powered-by.zango.com
127.0.0.1  coolvuurwerk.powered-by.zango.com
127.0.0.1  dane-cook.powered-by.zango.com
127.0.0.1  davesemu.com.powered-by.zango.com
127.0.0.1  deansplanet.com.powered-by.zango.com #[WildcardDNS]
127.0.0.1  factorygames.powered-by.zango.com
127.0.0.1  fightvideos.powered-by.zango.com
127.0.0.1  fightvids.powered-by.zango.com
127.0.0.1  flashaddictinggames.powered-by.zango.com
127.0.0.1  frazoogames.powered-by.zango.com
127.0.0.1  free.karaoke.songs.powered-by.zango.com
127.0.0.1  freesudokus.powered-by.zango.com
127.0.0.1  freetoplay.ath.cx.powered-by.zango.com
127.0.0.1  games.byethost32.powered-by.zango.com
127.0.0.1  gate1.powered-by.zango.com
127.0.0.1  gate2.powered-by.zango.com
127.0.0.1  gate3.powered-by.zango.com
127.0.0.1  gate4.powered-by.zango.com
127.0.0.1  gate5.powered-by.zango.com
127.0.0.1  gate6.powered-by.zango.com
127.0.0.1  gate7.powered-by.zango.com
127.0.0.1  gate8.powered-by.zango.com
127.0.0.1  gate9.powered-by.zango.com
127.0.0.1  gate10.powered-by.zango.com
127.0.0.1  gate11.powered-by.zango.com
127.0.0.1  gate12.powered-by.zango.com
127.0.0.1  gauntletvideos.powered-by.zango.com
127.0.0.1  getmusicvideocodes.powered-by.zango.com
127.0.0.1  graffitifonts.powered-by.zango.com #[Wildcard DNS]
127.0.0.1  hot-lindsay.powered-by.zango.com
127.0.0.1  iconcave.powered-by.zango.com
127.0.0.1  idrink.powered-by.zango.com
127.0.0.1  lavacards.powered-by.zango.com
127.0.0.1  martinahingis.powered-by.zango.com
127.0.0.1  maratsafin.powered-by.zango.com
127.0.0.1  mediagecko.powered-by.zango.com
127.0.0.1  midis.powered-by.zango.com
127.0.0.1  mmocenter.org.powered-by.zango.com
127.0.0.1  musicvideocodes.powered-by.zango.com
127.0.0.1  mvcodezone.powered-by.zango.com
127.0.0.1  mydisplayimage.powered-by.zango.com
127.0.0.1  myfriendspy.powered-by.zango.com
127.0.0.1  mymoneymakers.powered-by.zango.com
127.0.0.1  myspace.powered-by.zango.com
127.0.0.1  myspace-backgrounds.powered-by.zango.com
127.0.0.1  myspace-codes.powered-by.zango.com
127.0.0.1  myspacegraphics.powered-by.zango.com
127.0.0.1  myspacegraphicsx.powered-by.zango.com
127.0.0.1  myspaceicons.powered-by.zango.com
127.0.0.1  myspaceiconsorg.powered-by.zango.com
127.0.0.1  myspacelayouts.powered-by.zango.com
127.0.0.1  mytop12.com.powered-by.zango.com
127.0.0.1  narutowallpaper.powered-by.zango.com
127.0.0.1  newgrounds.dressup.powered-by.zango.com
127.0.0.1  ophq.powered-by.zango.com
127.0.0.1  pbxanime.powered-by.zango.com
127.0.0.1  phoenixpeople.powered-by.zango.com
127.0.0.1  planet.nana.co.il.powered-by.zango.com
127.0.0.1  pokemonporn.powered-by.zango.com
127.0.0.1  screensaverparadise.powered-by.zango.com
127.0.0.1  sfondigratis.powered-by.zango.com
127.0.0.1  stacy-keibler-pictures.powered-by.zango.com
127.0.0.1  snapshot.powered-by.zango.com
127.0.0.1  theamazingracist.powered-by.zango.com
127.0.0.1  trenchracing.powered-by.zango.com
127.0.0.1  userbars.org.powered-by.zango.com
127.0.0.1  vcc.powered-by.zango.com
127.0.0.1  vimalonline.powered-by.zango.com
127.0.0.1  videocodesworld.powered-by.zango.com
127.0.0.1  whatsthatcode.com.powered-by.zango.com
127.0.0.1  wwedivas.powered-by.zango.com
127.0.0.1  xtreme-cheats.powered-by.zango.com
127.0.0.1  downloads.zango.com #[SunBelt.180Solutions.Zango.TVTimes]
127.0.0.1  games.zango.com #[SunBelt.Adw.Zango.Solitaire]
127.0.0.1  hosted.zango.com
127.0.0.1  lp.zango.com #[McAfee.Adware-ZangoSA]
127.0.0.1  imp.games.zango.com
127.0.0.1  installs.zango.com #[installs.zango.com.edgesuite.net]
127.0.0.1  messenger.zango.com
127.0.0.1  msxml.zango.com #[msxml.infospace.com]
127.0.0.1  partner.zango.com
127.0.0.1  powered-by.zango.com
127.0.0.1  shared.zango.com
127.0.0.1  showtimes.zango.com #[SpySweeper.180search assistant/zango]
127.0.0.1  sitefinder.zango.com #[zangositefinder.simpli.com][ValueClick]
127.0.0.1  te1.zango.com
127.0.0.1  tvf.zango.com
127.0.0.1  tv.zango.com
127.0.0.1  [www.zango.com]("http://www.zango.com") #[Adware.ZangoSearch]
127.0.0.1  zangocash.com #[SiteAdvisor.zangocash.com]
127.0.0.1  partner.zangocash.com
127.0.0.1  prompt.zangocash.com #[eTrust.Win32/Anyhomb.D]
127.0.0.1  public.zangocash.com
127.0.0.1  static.zangocash.com #[CVE-2006-2324][Troj/QLowZon-EV]
127.0.0.1  syndication.zangocash.com
127.0.0.1  [www.zangocash.com]("http://www.zangocash.com")
127.0.0.1  [www.zangogames.com]("http://www.zangogames.com")
127.0.0.1  [www.zangomessenger.com]("http://www.zangomessenger.com")
127.0.0.1  [www.zangopartner.com]("http://www.zangopartner.com")
127.0.0.1  [www.zangopartner.net]("http://www.zangopartner.net")
127.0.0.1  event.zroitracker.com
# [Zango via HotBar]
127.0.0.1  [www.datez.com]("http://www.datez.com")
127.0.0.1  emoticons4us.com
127.0.0.1  [www.emoticons4us.com]("http://www.emoticons4us.com")
127.0.0.1  [www.estationery.com]("http://www.estationery.com")
127.0.0.1  [www.ezaza.com]("http://www.ezaza.com")
127.0.0.1  e-zaza.com
127.0.0.1  [www.e-zaza.com]("http://www.e-zaza.com")
127.0.0.1  fastutilities.com
127.0.0.1  [www.fastutilities.com]("http://www.fastutilities.com")
127.0.0.1  adopt.hbmediapro.com #[SpySweeper.Spy.Cookie]
127.0.0.1  hotbar.com #[SPYW_HOTBAR.P][AdWare.Win32.180Solutions.ay]
127.0.0.1  adopt.hotbar.com #[eTrust.Tracking.Cookie]
127.0.0.1  ads.hotbar.com #[SpySweeper.Spy.Cookie]
127.0.0.1  cs.hotbar.com
127.0.0.1  dynamic.hotbar.com
127.0.0.1  dynmenu.hotbar.com
127.0.0.1  hbmd.hotbar.com
127.0.0.1  installs.hotbar.com #[Win32/Adware.HotBar][McAfee.Adware-HotBar]
127.0.0.1  license.hotbar.com
127.0.0.1  partners.hotbar.com
127.0.0.1  promos.hotbar.com
127.0.0.1  puv.hotbar.com
127.0.0.1  reports.hotbar.com
127.0.0.1  searchdisp.hotbar.com
127.0.0.1  skins.hotbar.com
127.0.0.1  tooltips.hotbar.com
127.0.0.1  updates.hotbar.com
127.0.0.1  vip-farm1.hotbar.com
127.0.0.1  vip-farm2.hotbar.com
127.0.0.1  vip-farm1v.hotbar.com
127.0.0.1  vip-farm2v.hotbar.com
127.0.0.1  vip-farm5v.hotbar.com
127.0.0.1  vip-farm31v.hotbar.com
127.0.0.1  [www.hotbar.com]("http://www.hotbar.com") #[ADW_HOTBAR.O][Edelman.HotBar][Win32.Adware.HotBar]
127.0.0.1  [www.hotbar2.com]("http://www.hotbar2.com")
127.0.0.1  [www.hotbar.net]("http://www.hotbar.net")
127.0.0.1  hotbarmemberdirectory.com
127.0.0.1  net-offers.net
127.0.0.1  [www.pcpolish.com]("http://www.pcpolish.com")
127.0.0.1  cfg.shopperreports.com
127.0.0.1  code.shopperreports.com
127.0.0.1  cs.shopperreports.com #[Trackware.SmartShopper]
127.0.0.1  dynamic.shopperreports.com
127.0.0.1  reports.shopperreports.com #[Adware-HotBar.dr]
127.0.0.1  updates.shopperreports.com
127.0.0.1  upgrades.shopperreports.com #[AdWare.Win32.Shopper.k]
127.0.0.1  [www.shopperreports.com]("http://www.shopperreports.com") #[Adware-ShopprReports]
127.0.0.1  smartshopper.com
127.0.0.1  cs.smartshopper.com #[McAfee.Adware-SmartShopper]
127.0.0.1  installs.smartshopper.com
127.0.0.1  [www.smartshopper.com]("http://www.smartshopper.com")
127.0.0.1  [www.smartshoppernetworks.com]("http://www.smartshoppernetworks.com")
127.0.0.1  software4thenet.com
127.0.0.1  [www.software4thenet.com]("http://www.software4thenet.com")
127.0.0.1  spamblockerutility.com
127.0.0.1  installs.spamblockerutility.com
127.0.0.1  updates.spamblockerutility.com
127.0.0.1  [www.spamblockerutility.com]("http://www.spamblockerutility.com") #[SiteAdvisor.spamblockerutility.com]
127.0.0.1  [www.spamfree.com]("http://www.spamfree.com")
127.0.0.1  page-not-found.net #[McAfee.Adware-HotBar]
127.0.0.1  shopperreports.pricetool.com #[Hotbar.ShoppingReports]
127.0.0.1  resultsmaster.com
127.0.0.1  [www.resultsmaster.com]("http://www.resultsmaster.com") #[Adware.Hotbar]
# [ZapSpot, Inc]
127.0.0.1  [www.p3marketing.com]("http://www.p3marketing.com")
127.0.0.1  download.zapspot.com #[SiteAdvisor.zapspot]
127.0.0.1  [www.zapspot.com]("http://www.zapspot.com") #[eTrust.ZapSpot]
# [ZEDO][AS26914][64.127.125.112 - 64.127.125.127]
127.0.0.1  l7.zedo.com
127.0.0.1  click.zxxds.net
# [ZEDO]
127.0.0.1  zedo.com #[SecuritySpace.WebBug]
127.0.0.1  ads.zedo.com #[McAfee.Cookie-Zedo]
127.0.0.1  c1.zedo.com #[a1979.g.akamai.net]
127.0.0.1  c2.zedo.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c3.zedo.com
127.0.0.1  c4.zedo.com #[zedo.vo.llnwd.net]
127.0.0.1  c5.zedo.com
127.0.0.1  c6.zedo.com
127.0.0.1  c7.zedo.com
127.0.0.1  c8.zedo.com #[zedo.vo.llnwd.net]
127.0.0.1  d2.zedo.com
127.0.0.1  d3.zedo.com
127.0.0.1  d7.zedo.com
127.0.0.1  freeze.zedo.com
127.0.0.1  g.zedo.com #[zedo.live365.com]
127.0.0.1  gw.zedo.com
127.0.0.1  h.zedo.com
127.0.0.1  l1.zedo.com #[a1101.g.akamai.net]
127.0.0.1  l2.zedo.com
127.0.0.1  l3.zedo.com
127.0.0.1  l4.zedo.com #[Panda.Spyware:Cookie/Zedo]
127.0.0.1  l5.zedo.com
127.0.0.1  l6.zedo.com #[a515.g.akamai.net][Tenebril.Tracking.Cookie]
127.0.0.1  l8.zedo.com
127.0.0.1  r1.zedo.com
127.0.0.1  simg.zedo.com #[zedo.vo.llnwd.net][a556.g.akamai.net]
127.0.0.1  ss1.zedo.com
127.0.0.1  ss2.zedo.com
127.0.0.1  ss7.zedo.com
127.0.0.1  xads.zedo.com
127.0.0.1  yads.zedo.com
127.0.0.1  [www.zedo.com]("http://www.zedo.com") #[Adware.RaxSearch]
127.0.0.1  c1.zxxds.net #[g1.panthercdn.com]
127.0.0.1  c7.zxxds.net
# [Zhongbangyatong Telecom][AS17964][124.207.0.0 - 124.207.127.255]
127.0.0.1  agreespeed.com #[ScamFraudAlert.Pharmacy]
127.0.0.1  briefmagic.com
# [Zipservers Inc][74.86.243.176 - 74.86.243.183]
127.0.0.1  tophot-video.com #[Google.Diagnostic]
# [Zlkon / Datoru Express][AS12553][94.247.2.0 - 94.247.3.255]
127.0.0.1  astrumantivirus.com
127.0.0.1  av-plus-support.com
127.0.0.1  avscanonline.com
127.0.0.1  betstarwager.cn
127.0.0.1  filmlifemusicsite.cn
127.0.0.1  gogo2me.net
127.0.0.1  asdasdw.hostindianet.com
127.0.0.1  ghrgt.hostindianet.com
127.0.0.1  sadcwed.hostindianet.com
127.0.0.1  zzzz.hostindianet.com #[Win32/Kryptik.LI]
127.0.0.1  isafeantvirus.com
127.0.0.1  isafeantivirus.com
127.0.0.1  isaferantivirus.com
127.0.0.1  isafe-antivirus.com
127.0.0.1  isafeantivir.com
127.0.0.1  isafeantiviruspro.com
127.0.0.1  litegreatestdirect.cn
127.0.0.1  files.msas2009dl.com
127.0.0.1  rusexportal.com
127.0.0.1  int.sysreport1.com
127.0.0.1  int.sysreport2.com
127.0.0.1  traff.asia
127.0.0.1  truthisoutthere.cn
#end of lines added by WinHelp2002
george@georges-desktop:~$
```

---

### Post by gila_monster on 2009-08-01
Holy cats, that's nasty. I've never seen an /etc/hosts file with that many (apparently bogus) entries.

Suffice it to say, goldstar, that it's very wrong. There should be one entry for 127.0.0.1, mapped to localhost.

Mine looks like this:

```
127.0.0.1	localhost
127.0.1.1	daffodil

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

127.0.0.1 is mapped to localhost. It's the loopback address.

127.0.1.1 is mapped to my hostname. In your case, I think you were aiming for georges-desktop.

The others are IPv6 standard addresses, mapped properly.

That's pretty much everything you need in that file. If you had some serious networking going on, you'd have more in there, but I don't think that's the case in your situation.

Short version is that you need to edit or replace the contents of /etc/hosts to match (but with your hostname) what I included above. Do you know how to use the nano editor?

EDIT: Just noticed it says WinHelp2002. That program (which I thought was Windows only, how did it do this to your Ubuntu hosts file?) will put entries like that in your hosts file as a means of blocking ads and malware and such on websites. Unfortunately, necessary entries were deleted. If you are not an experienced user, I don't recommend trying to accomplish that by modifying the hosts file.

---

### Post by QIII on 2009-08-02
Even if you have several machines on a local home network, you should still only have a few entries...

```
127.0.0.1    localhost
127.0.1.1    ZACK
192.168.1.2     OLDIE
192.168.1.5     NEWBIE

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Suggest you back up your current copy of /etc/hosts just in case and edit to get rid of all the chaff.  Try first with just the two  above the "# The following ..." line as in the post above.

---

### Post by goldstar1 on 2009-08-02
Thank You. Your recommendation worked. I noticed that I didn't have a 127.0.1.1 entry there. All the other junk, well, I have a very slow xp box that i run my business software on and i must have been trying to fix that box somehow and went on some sort of rabbit trail.

Thanks again

by the way...I only use a "Plumbers" software program that is nothing more than a database. If I can somehow learn to use some of the databases on linux, I would create a database for contractors like myself and bring in thousands of folks, like myself, to do away with windows all together.

---

