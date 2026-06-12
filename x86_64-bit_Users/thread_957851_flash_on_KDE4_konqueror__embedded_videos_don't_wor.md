---
title: "flash on KDE4 konqueror : embedded videos don't work"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by brazzmonkey on 2008-10-24
hello there,
flash videos do work when i'm browsing websites like youtube, dailymotion, etc.
but they do not work when they're embedded in 3rd-party websites, i.e. when there's a youtube video in a news website, or when there's a specific flash animation for instance.

any idea about what's wrong ??

---

### Post by SunnyRabbiera on 2008-10-24
The answer is simple: flash doesnt really work for any browser in linux other then firefox.
It works paritially in opera.

---

### Post by brazzmonkey on 2008-10-24
well, anyhow it does work properly on konqueror 4 in my 32-bit installations. it does work properly in opera in 64-bit too.

update : it sometimes happens on youtube as well.

here's the output when it fails
```
(npviewer.bin:32290): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
konqueror(32266) NSPluginInstance::~NSPluginInstance: release
konqueror(32266) NSPluginLoader::release: NSPluginLoader::release ->  2
konqueror(32266) NSPluginInstance::~NSPluginInstance: <- NSPluginInstance::~NSPluginInstance
konqueror(32266) NSPluginLoader::release: NSPluginLoader::release ->  1
konqueror(32266) KConfigGroup::readXdgListEntry: List entry mime in "/usr/share/kde4/apps/kjava/pluginsinfo" is not compliant with XDG standard (missing trailing semicolon).
konqueror(32266) NSPluginLoader::instance: NSPluginLoader::instance ->  2
konqueror(32266) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x30b5be0 , url= "http://s.ytimg.com/yt/swf/watch-vfl59966.swf" , mime= "application/x-shockwave-flash" , ...)
konqueror(32266) NSPluginLoader::newInstance: -> ownID ":1.339"  viewer ID: "org.kde.nspluginviewer-32266"
konqueror(32266) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/firefox/plugins/flashplugin-alternative.so"
nspluginviewer(32278) NSPluginInstance::NPGetValue: results in  0
konqueror(32266) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x22f0c20
konqueror(32266) NSPluginInstance::resizeEvent: 100 30 false false false
konqueror(32266) NSPluginInstance::showEvent: 100 30 true false false
konqueror(32266) NSPluginInstance::pluginResized: 480 385
konqueror(32266) NSPluginLoader::instance: NSPluginLoader::instance ->  3
nspluginviewer(32278) PluginHostXEmbed::setupWindow: 33621706 480 385
nspluginviewer(32278) NSPluginInstance::NPSetWindow: results in  0
konqueror(32266) NSPluginInstance::resizeEvent: 480 385 true true true
nspluginviewer(32278) NSPluginInstance::resizePlugin: 480 480 385 385 true
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://s.ytimg.com/yt/swf/watch-vfl59966.swf"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://s.ytimg.com/yt/swf/watch-vfl59966.swf"
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
```

and here's the output when it works
```
(npviewer.bin:32290): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
konqueror(32266) NSPluginInstance::~NSPluginInstance: release                                      
konqueror(32266) NSPluginLoader::release: NSPluginLoader::release ->  2                            
konqueror(32266) NSPluginInstance::~NSPluginInstance: <- NSPluginInstance::~NSPluginInstance       
konqueror(32266) NSPluginLoader::release: NSPluginLoader::release ->  1                            
konqueror(32266) KConfigGroup::readXdgListEntry: List entry mime in "/usr/share/kde4/apps/kjava/pluginsinfo" is not compliant with XDG standard (missing trailing semicolon). 
konqueror(32266) NSPluginLoader::instance: NSPluginLoader::instance ->  2                                                                                                     
konqueror(32266) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x2c1a8e0 , url= "http://s.ytimg.com/yt/swf/watch-vfl59966.swf" , mime= "application/x-shockwave-flash" , ...)                                                                                                                                                                    
konqueror(32266) NSPluginLoader::newInstance: -> ownID ":1.339"  viewer ID: "org.kde.nspluginviewer-32266"                                                                          
konqueror(32266) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/firefox/plugins/flashplugin-alternative.so"                   
nspluginviewer(32278) NSPluginInstance::NPGetValue: results in  0                                                                                                                   
konqueror(32266) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x29a4020                                                                                           
konqueror(32266) NSPluginInstance::resizeEvent: 100 30 false false false                                                                                                            
konqueror(32266) NSPluginInstance::showEvent: 100 30 true false false
konqueror(32266) NSPluginInstance::pluginResized: 480 385
konqueror(32266) NSPluginLoader::instance: NSPluginLoader::instance ->  3
nspluginviewer(32278) PluginHostXEmbed::setupWindow: 33627165 480 385
nspluginviewer(32278) NSPluginInstance::NPSetWindow: results in  0
konqueror(32266) NSPluginInstance::resizeEvent: 480 385 true true true
nspluginviewer(32278) NSPluginInstance::resizePlugin: 480 480 385 385 true
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://s.ytimg.com/yt/swf/watch-vfl59966.swf"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://s.ytimg.com/yt/swf/watch-vfl59966.swf"
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://s.ytimg.com/yt/swf/lpbf-vfl54521.swf"
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://s.ytimg.com/yt/swf/lpbb-vfl54521.swf"
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://i2.ytimg.com/crossdomain.xml"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://s.ytimg.com/yt/swf/lpbf-vfl54521.swf"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://s.ytimg.com/yt/swf/lpbb-vfl54521.swf"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://i2.ytimg.com/crossdomain.xml"
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(32278) NSPluginInstance::timer: getting  "http://i2.ytimg.com/vi/IGzdzRFftBc/default.jpg"
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://i2.ytimg.com/vi/IGzdzRFftBc/default.jpg"
nspluginviewer(32278) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(32278) NSPluginInstance::NPDestroyStream: results in  0
konqueror(32266) PluginPart::statusMessage: PluginPart::statusMessage  ""
```

---

