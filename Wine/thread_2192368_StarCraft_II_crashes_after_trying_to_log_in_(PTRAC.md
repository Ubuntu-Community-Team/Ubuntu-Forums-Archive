---
title: "StarCraft II crashes after trying to log in (PTRACE trick does NOT work)"
date: 2013-12-07
forum: Wine
---

### Post by mueldeponi on 2013-12-07
Hello Ubuntu pr0s!

I'm really into StarCraft right now and for obvious reasons I don't want to boot Windows for that. So I installed it via PoL, but it didn't work (It crashed with an unexpected fatal error). I was able to solve that problem by copying the Windows' installation to the exact same directory in the virtual drive (If it was in "Program Files (x86)" you had to copy it to "Program Files (x86)").

But now, I can't log in. I searched for solutions and it was recommended to disable "ptrace_scope", but it didn't work. It just crashes when I want to click the login button:

```
[12/07/13 18:47:26] - Running wine-1.7.7 StarCraft II.exe (Working directory : /home/marcel/.PlayOnLinux/wineprefix/SC2_WoL/drive_c/Program Files (x86)/StarCraft II)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
[12/07/13 18:48:35] - Running wine-1.7.7 StarCraft II.exe (Working directory : /home/marcel/.PlayOnLinux/wineprefix/SC2_WoL/drive_c/Program Files (x86)/StarCraft II)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:wininet:open_http_connection create_netconn failed: 12029
err:wininet:open_http_connection create_netconn failed: 12029
fixme:hnetcfg:fw_profile_get_NotificationsDisabled 0x13f6a0, 0x33f940
Argument[0]: 'C:/users/Public/Application Data/Battle.net/Agent/Agent.2380/Agent.exe' 
Argument[1]: '--locale=deDE' 
Agent is running as Administrator. 
Database Insert: /option 
Database Insert: /agent 
Database Insert: / 
Database Insert: /version 
Database Insert: /repair 
Database Insert: /update 
Database Insert: /game/s2_dede 
Database Insert: /uninstall 
Database Insert: /install 
Database Insert: /gamesession 
Database Insert: /agent/download 
Database Insert: /backfill 
Database Insert: /game 
Database Insert: /createshortcut 
Database Insert: /game/client 
Database Insert: /spawned 
Database Insert: /agent/download 
Database Insert: /register 
Session Hash created: '18297578199215540033' 
Initialize HttpProtocol Server Called. 
Agent started on port #1120 
Executing operation: disable_firewall applicationPath="C:\users\Public\Application Data\Battle.net\Agent\Agent.2380\Agent.exe" applicationName="Battle.net Update Agent" 
AgentAsAdmin failed to add a firewall exception for 'C:\users\Public\Application Data\Battle.net\Agent\Agent.2380\Agent.exe'. 
Registered Periodic Event: "auth validation event" with a resolution of 10000 and a start delay of 10000 
Registered Event: "shutdown event" 
Registered Event: "database flush event" 
Registered Periodic Event: "network connection event" with a resolution of 60000 and a start delay of 0 
Handle Event: "network connection event" 
PostTo succeeded status: 0 for url: http://deDE.patch.battle.net:1119/patch 
Post Data: 
<version program="Agnt"><record program="Agnt" component="cdn" version="1" /><record program="Agnt" component="cfg" version="1" /><record program="Agnt" component="Win" version="2380" /><record prograPost Response: 
<patch> 
<record program="Agnt" component="cdn"> 
dist.blizzard.com.edgesuite.net|llnw.blizzard.com 
</record> 
<record program="Agnt" component="Win"> 
;;2380;0;2380 
</record> 
</patch> 
Firing Event: "database flush event" 
Request Issued: GET /agent 
 
Handle Event: "database flush event" 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "87FE0032A62061FCC494DB54AD4AA95A" 
} 
Request Issued: GET /game 
 
Response: 200 
{ 
    "client" : { 
        "link" : "/game/client" 
    }, 
    "s2_dede" : { 
        "link" : "/game/s2_dede" 
    } 
} 
Request Issued: GET /agent 
 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "87FE0032A62061FCC494DB54AD4AA95A" 
} 
Request Issued: GET /game/client 
 
Response: 200 
{ 
    "uid_override" : "battle.net", 
    "install_dir" : "C:/users/Public/Application Data/Battle.net/Client", 
    "binary_launch_path" : "Blizzard Launcher.exe", 
    "binary_launch_path64" : "", 
    "expansion_level" : 0.000000, 
    "current_version" : 2005.000000, 
    "local_version" : "0.5.4.2005", 
    "opaque_product_specific" : { 
        "ui" : "hots" 
    }, 
    "supports_multibox" : true, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 0.000000, 
    "needs_rebase" : false, 
    "product" : "Clnt", 
    "update_method" : "client update", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "", 
    "mfil_hash" : "00000000000000000000000000000000", 
    "torrent_hash" : "00000000000000000000000000000000", 
    "alternate" : false, 
    "supports_offline" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "" 
} 
Request Issued:fixme:heap:HeapSetInformation (nil) 1 (nil) 0
 GET /game/s2_dede 
 
Response: 200 
{ 
    "uid_override" : "", 
    "install_dir" : "C:/Program Files (x86)/StarCraft II", 
    "binary_launch_path" : "Support/SC2Switcher.exe", 
    "binary_launch_path64" : "", 
    "selected_locale" : "deDE", 
    "selected_asset_locale" : "deDE", 
    "expansion_level" : 2.000000, 
    "current_version" : 26825.000000, 
    "local_version" : "2.0.11.26825", 
    "opaque_product_specific" : {}, 
    "supports_multibox" : false, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 1.000000, 
    "needs_rebase" : false, 
    "product" : "S2", 
    "update_method" : "patch on demand", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "http://dist.blizzard.com.edgesuite.net/sc2-pod-retail/AF11CD00/EU/s2-24621-164D664E6A79442FD8488D79C79C752B.xml", 
    "mfil_hash" : "DF9F3EF639EA57159B1008693AE35270", 
    "torrent_hash" : "93C99E692239DDCAB7D6F1CEDC7F84CD", 
    "alternate" : false, 
    "supports_offline" : true, 
    "installed_locales" : [ 
        "deDE" 
    ], 
    "display_locales" : [ 
        "enUS", 
        "esMX", 
        "ptBR", 
        "deDE", 
        "enGB", 
        "esES", 
        "frFR", 
        "itIT", 
        "plPL", 
        "ruRU", 
        "koKR", 
        "zhTW" 
    ], 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "sc2-pod-retail/rebase/24621-swarm/s2-24621-eu-win-C8791078DDE8E2258274B16EC7F83F4E.torrent" 
} 
Request Issued: POST /version 
{"uid":"s2_dede"} 
Database Insert: /version/s2_dede 
Response: 200 
{ 
    "response_uri" : "/version/s2_dede" 
} 
Request Issued: POST /version 
{"uid":"client"} 
Database Insert: /version/client 
Response: 200 
{ 
    "response_uri" : "/version/client" 
} 
Request Issued: GET /version/client 
 
Response: 200 
{ 
    "state" : 1007.000000, 
    "local_version" : "0.5.4.2005", 
    "playable" : true, 
    "needs_rebase" : false, 
    "current_version" : 2005.000000, 
    "build" : 2005.000000, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false 
} 
Request Issued: POST /gamesession 
{ 
    "uid" : "client", 
    "launch_arguments" : [ 
        "--gamepath=C:\\Program Files (x86)\\StarCraft II", 
        "--game=s2_dede" 
    ] 
} 
Agent::Product::StartSession() - Begin Waiting 
Agent::Product::StartSession() - End Waiting 
Launched C:/users/Public/Application Data/Battle.net/Client/Blizzard Launcher.exe as PID: 47 w/ --gamepath=C:\Program Files (x86)\StarCraft II 
--game=s2_dede 
********************************************** 
GameSession BringToFrontFunc: hasChild: true, pid 47, childPid 0. 
Database Insert: /gamesession/client 
Database Insert: /gamesession/client/1 
Response: 200 
{ 
    "response_uri" : "/gamesession/client" 
} 
Response: 200 
(null) 
PostTo succeeded status: 0 for url: http://eu.patch.battle.net:1119/patch 
Post Data: 
<version program="Clnt"><record program="Agnt" component="cdn" version="1" /><record program="Agnt" component="cfg" version="1" /><record program="Clnt" component="Win" version="2005" /><record prograPost Response: 
<patch> 
<record program="Agnt" component="cdn"> 
dist.blizzard.com.edgesuite.net|llnw.blizzard.com 
</record> 
<record program="Clnt" component="Win"> 
;;2005;0;2005 
</record> 
<record program="Clnt" component="blob"> 
http://dist.blizzard.com.edgesuite.net/tools-pod/Blob.1949.Client05HotS;00000000000000000000000000000000;21194985089F993F9C0F641B198FEADC;0 
</record> 
</patch> 
Firing Event: "database flush event" 
Handle Event: "database flush event" 
PostTo succeeded status: 0 for url: http://eu.patch.battle.net:1119/patch 
Post Data: 
<version program="S2"><record program="Agnt" component="cdn" version="1" /><record program="S2" component="deDE" version="1" /><record program="S2" component="blob" version="1" /></version> 
Post Response: 
<patch> 
<record program="Agnt" component="cdn"> 
dist.blizzard.com.edgesuite.net|llnw.blizzard.com 
</record> 
<record program=err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks.
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\users\\Public\\Application Data\\Battle.net\\Client\\Blizzard Launcher.2005\\imageformats\\qsvg4.dll") not found
fixme:shell:SetCurrentProcessExplicitAppUserModelID L"BlizzardEntertainment.StarCraftII.retail": stub
fixme:msg:pack_message msg 80 (WM_SETICON) not supported yet
fixme:msg:pack_message msg 80 (WM_SETICON) not supported yet
"S2" component="deDE"> 
http://dist.blizzard.com.edgesuite.net/sc2-pod-retail/AF11CD00/EU/s2-24621-164D664E6A79442FD8488D79C79C752B.xml;93C99E692239DDCAB7D6F1CEDC7F84CD;DF9F3EF639EA57159B1008693AE35270;26825 
</record> 
<record program="S2" component="blob"> 
http://dist.blizzard.com.edgesuite.net/sc2-pod/Blob.24621.Swarm20Rebase;849EA78C1BDEB96AEE852C96E6A7C86E;50927548A616FF852AE14426E3C42D38;0 
</record> 
</patch> 
Firing Event: "database flush event" 
Handle Event: "database flush event" 
CheckChildPid: found child pid: 13 using path C:/users/Public/Application Data/Battle.net/Client/Blizzard Launcher.2005/Blizzard Launcher.exe. 
Firing Event: "database flush event" 
Request Issued: GET /agent 
 
Handle Event: "database flush event" 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "B6D8D3EDECB7F397131791C4B9E045BA" 
} 
Firing Event: "database flush event" 
Request Issued: GET /agent 
 
Handle Event: "database flush event" 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "02D015658C8055F62900172E4692E286" 
} 
Request Issued: GET /game/client 
 
Response: 200 
{ 
    "uid_override" : "battle.net", 
    "install_dir" : "C:/users/Public/Application Data/Battle.net/Client", 
    "binary_launch_path" : "Blizzard Launcher.exe", 
    "binary_launch_path64" : "", 
    "expansion_level" : 0.000000, 
    "current_version" : 2005.000000, 
    "local_version" : "0.5.4.2005", 
    "opaque_product_specific" : { 
        "ui" : "hots" 
    }, 
    "supports_multibox" : true, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [ 
        { 
            "gamesession" : "/gamesession/client" 
        } 
    ], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 0.000000, 
    "needs_rebase" : false, 
    "product" : "Clnt", 
    "update_method" : "client update", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "", 
    "mfil_hash" : "00000000000000000000000000000000", 
    "torrent_hash" : "00000000000000000000000000000000", 
    "alternate" : false, 
    "supports_offline" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "" 
} 
Request Issued to non-existent Uri: GET - /game/s2_ptr_dede 
Request Issued: GET /game/s2_dede 
 
Response: 200 
{ 
    "uid_override" : "", 
    "install_dir" : "C:/Program Files (x86)/StarCraft II", 
    "binary_launch_path" : "Support/SC2Switcher.exe", 
    "binary_launch_path64" : "", 
    "selected_locale" : "deDE", 
    "selected_asset_locale" : "deDE", 
    "expansion_level" : 2.000000, 
    "current_version" : 26825.000000, 
    "local_version" : "2.0.11.26825", 
    "opaque_product_specific" : {}, 
    "supports_multibox" : false, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 1.000000, 
    "needs_rebase" : false, 
    "product" : "S2", 
    "update_method" : "patch on demand", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "http://dist.blizzard.com.edgesuite.net/sc2-pod-retail/AF11CD00/EU/s2-24621-164D664E6A79442FD8488D79C79C752B.xml", 
    "mfil_hash" : "DF9F3EF639EA57159B1008693AE35270", 
    "torrent_hash" : "93C99E692239DDCAB7D6F1CEDC7F84CD", 
    "alternate" : false, 
    "supports_offline" : true, 
    "installed_locales" : [ 
        "deDE" 
    ], 
    "display_locales" : [ 
        "enUS", 
        "esMX", 
        "ptBR", 
        "deDE", 
        "enGB", 
        "esES", 
        "fixme:win:FlashWindowEx 0x33cfb4
frFR", 
        "itIT", 
        "plPL", 
        "ruRU", 
        "koKR", 
        "zhTW" 
    ], 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "sc2-pod-retail/rebase/24621-swarm/s2-24621-eu-win-C8791078DDE8E2258274B16EC7F83F4E.torrent" 
} 
Request Issued to non-existent Uri: GET - /install/s2_dede 
Request Issued to non-existent Uri: GET - /update/s2_dede 
Request Issued to non-existent Uri: GET - /gamesession/s2_dede 
Request Issued to non-existent Uri: DELETE - /backfill/s2_dede 
Request Issued: GET /agent 
 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "02D015658C8055F62900172E4692E286" 
} 
Request Issued: POST /update 
{"uid":"client"} 
Database Insert: /update/client 
Queuing /update/client 
Insert to Queue at HEAD 
Firing Event: "database flush event" 
Handle Event: "database flush event" 
Response: 200 
{ 
    "response_uri" : "/update/client", 
    "result_uri" : "/game/client" 
} 
Start Queued Task 'Update Clnt' 
Request Issued: GET /update/client 
 
Response: 200 
{ 
    "state" : 1007.000000 
} 
Request Issued: GET /update/client 
 
Response: 200 
{ 
    "state" : 1007.000000 
} 
PostTo succeeded status: 0 for url: http://eu.patch.battle.net:1119/patch 
Post Data: 
<version program="Clnt"><record program="Agnt" component="cdn" version="1" /><record program="Agnt" component="cfg" version="1" /><record program="Clnt" component="Win" version="2005" /><record prograPost Response: 
<patch> 
<record program="Agnt" component="cdn"> 
dist.blizzard.com.edgesuite.net|llnw.blizzard.com 
</record> 
<record program="Clnt" component="Win"> 
;;2005;0;2005 
</record> 
<record program="Clnt" component="blob"> 
http://dist.blizzard.com.edgesuite.net/tools-pod/Blob.1949.Client05HotS;00000000000000000000000000000000;21194985089F993F9C0F641B198FEADC;0 
</record> 
</patch> 
Pause Task Update Clnt 
Removed HEAD item from Queue 
Firing Event: "database flush event" 
Handle Event: "database flush event" 
Request Issued: GET /update/client 
 
Response: 200 
{ 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true 
} 
Request Issued: GET /game/client 
 
Response: 200 
{ 
    "uid_override" : "battle.net", 
    "install_dir" : "C:/users/Public/Application Data/Battle.net/Client", 
    "binary_launch_path" : "Blizzard Launcher.exe", 
    "binary_launch_path64" : "", 
    "expansion_level" : 0.000000, 
    "current_version" : 2005.000000, 
    "local_version" : "0.5.4.2005", 
    "opaque_product_specific" : { 
        "ui" : "hots" 
    }, 
    "supports_multibox" : true, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [ 
        { 
            "gamesession" : "/gamesession/client" 
        } 
    ], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 0.000000, 
    "needs_rebase" : false, 
    "product" : "Clnt", 
    "update_method" : "client update", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "", 
    "mfil_hash" : "00000000000000000000000000000000", 
    "torrent_hash" : "00000000000000000000000000000000", 
    "alternate" : false, 
    "supports_offline" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "" 
} 
Request Issued: POST /version 
{  
    "uid":"s2_dede" 
} 
 
Response: 200 
{ 
    "response_uri" : "/version/s2_dede" 
} 
Request Issued: GET /version/s2_dede 
 
Response: 200 
{ 
    "state" : 1007.000000, 
    "local_version" : "2.0.11.26825", 
    "playable" : true, 
    "needs_rebase" : false, 
    "current_version" : 26825.000000, 
    "build" : 26825.000000, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "bacfixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:shell:SetCurrentProcessExplicitAppUserModelID L"BlizzardEntertainment.StarCraftII.StarCraftII": stub
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x1512e8, 0x69af034
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x69ae174,0x69ae178): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
kground_download_available" : false, 
    "background_download_complete" : false 
} 
Request Issued: GET /version/s2_dede 
 
Response: 200 
{ 
    "state" : 1007.000000, 
    "local_version" : "2.0.11.26825", 
    "playable" : true, 
    "needs_rebase" : false, 
    "current_version" : 26825.000000, 
    "build" : 26825.000000, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false 
} 
Request Issued: GET /version/s2_dede 
 
Response: 200 
{ 
    "state" : 1007.000000, 
    "local_version" : "2.0.11.26825", 
    "playable" : true, 
    "needs_rebase" : false, 
    "current_version" : 26825.000000, 
    "build" : 26825.000000, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false 
} 
Firing Event: "database flush event" 
Handle Event: "database flush event" 
Request Issued: GET /version/s2_dede 
 
Response: 200 
{ 
    "state" : 1004.000000, 
    "local_version" : "2.0.11.26825", 
    "playable" : true, 
    "needs_rebase" : false, 
    "current_version" : 26825.000000, 
    "build" : 26825.000000, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false 
} 
Request Issued: POST /gamesession 
{"uid":"s2_dede","launch_arguments":[],"run64bit":false} 
Agent::Product::StartSession() - Begin Waiting 
Agent::Product::StartSession() - End Waiting 
Launched C:/Program Files (x86)/StarCraft II/Support/SC2Switcher.exe as PID: 41 w/ -launch 
-uid 
s2_dede 
********************************************** 
GameSession BringToFrontFunc: hasChild: true, pid 41, childPid 0. 
Database Insert: /gamesession/s2_dede 
Database Insert: /gamesession/s2_dede/1 
Response: 200 
{ 
    "response_uri" : "/gamesession/s2_dede" 
} 
Request Issued: DELETE /update/client 
Remove - invalid operation - from Queue 
Database Remove: /update/client 
Response: 200 
{} 
Remove - invalid operation - from Queue 
Queue 'async_task' Resource for delete 
Deferred delete of 'async_task' Resource 
Deferred delete of 'async_task' Resource completed 
Request Issued: GET /gamesession/s2_dede 
 
Response: 200 
{ 
    "1" : { 
        "pid" : 41.000000, 
        "launch_path" : "C:/Program Files (x86)/StarCraft II/Support/SC2Switcher.exe", 
        "launch_arguments" : "-launch\n-uid\ns2_dede" 
    } 
} 
CheckChildPid: found child pid: 75 using path C:/Program Files (x86)/StarCraft II/Versions/Base26490/SC2.exe. 
Firing Event: "database flush event" 
Request Issued: GET /agent 
 
Handle Event: "database flush event" 
Response: 200 
{ 
    "update" : {}, 
    "install" : {}, 
    "backfill" : {}, 
    "pid" : 48.000000, 
    "state" : 1004.000000, 
    "playable" : true, 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "version" : "1.9.2.2380", 
    "type" : "retail", 
    "opt_in_feedback" : false, 
    "session" : "18297578199215540033", 
    "authorization" : "5CA458493D3B1D90E02D00046C0C1201" 
} 
Request Issued: GET /game/s2_dede 
 
Response: 200 
{ 
    "uid_override" : "", 
    "install_dir" : "C:/Program Files (x86)/StarCraft II", 
    "binary_launch_path" : "Support/SC2Switcher.exe", 
    "binary_launch_path64" : "", 
    "selected_locale" : "deDE", 
    "selected_asset_locale" : "deDE", 
    "expansion_level" : 2.000000, 
    "current_version" : 26825.000000, 
    "local_version" : "2.0.11.26825", 
    "opaque_product_specific" : {}, 
    "supports_multibox" : false, 
    "switcher" : true, 
    "use_sparse" : false, 
    "operations" : [ 
        { 
            "gamesession" : "/gamesession/s2_dede" 
        } 
    ], 
    "playable" : true, 
    "ever_playable" : true, 
    "last_played" : 0.000000, 
    "update_progress" : 1.000000, 
    "needs_rebase" : false, 
    "product" : "S2", 
    "update_method" : "patch on demand", 
    "region" : "eu", 
    "patch_url" : "http://eu.patch.battle.net:1119/patch", 
    "patch_url_beta" : "http://public-test.patch.battle.net:1119/patch", 
    "config_url" : "http://dist.blizzard.com.edgesuite.net/sc2-pod-retail/AF11CD00/EU/s2-24621-164D664E6A79442FD8488D79C79C752B.xml", 
    "mfil_hash" : "DF9F3EF639EA57159B1008693AE35270", 
    "torrent_hash" : "93C99E692239DDCAB7D6F1CEDC7F84CD", 
    "alternate" : false, 
    "supports_offline" : true, 
    "installed_locales" : [ 
        "deDE"fixme:win:EnumDisplayDevicesW ((null),0,0x69aef38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x69ae898,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x69ae4d8,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x69ae4b8,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x69ae4a8,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0082: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout 0x4090409 is not supported
fixme:msctf:ThreadMgrSource_AdviseSink (0x9c46a60) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xbf0e9a4): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:msvcrt:__clean_type_info_names_internal (0x1c54f20) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1c06450) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1bc0450) stub
fixme:msvcrt:__clean_type_info_names_internal (0x3d8480) stub
fixme:msvcrt:__clean_type_info_names_internal (0x3c7468) stub
fixme:msvcrt:__clean_type_info_names_internal (0x6104e830) stub
fixme:msvcrt:__clean_type_info_names_internal (0x109b7c90) stub
fixme:msvcrt:__clean_type_info_names_internal (0x640dfa58) stub
fixme:msvcrt:__clean_type_info_names_internal (0x37ee68) stub
fixme:msvcrt:__clean_type_info_names_internal (0x65761a20) stub
fixme:msvcrt:__clean_type_info_names_internal (0x67221b20) stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x697e848,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697eb78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697eb78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697e8f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697e8f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697ea38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x697ea38,0x00000000), stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x2416e9a4): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:imm:ImmReleaseContext (0x30088, 0x178ac0): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
 
    ], 
    "display_locales" : [ 
        "enUS", 
        "esMX", 
        "ptBR", 
        "deDE", 
        "enGB", 
        "esES", 
        "frFR", 
        "itIT", 
        "plPL", 
        "ruRU", 
        "koKR", 
        "zhTW" 
    ], 
    "patch_application_complete" : true, 
    "download_complete" : true, 
    "background_download_available" : false, 
    "background_download_complete" : false, 
    "perform_ogg_to_wav" : false, 
    "baseline" : "sc2-pod-retail/rebase/24621-swarm/s2-24621-eu-win-C8791078DDE8E2258274B16EC7F83F4E.torrent" 
} 
Handle Event: "auth validation event" 
Handle Event: "auth validation event" 
Registered Periodic Event: "shutdown event" with a resolution of 10000 and a start delay of 10000 
Handle Event: "shutdown event" 
Handle Event: "auth validation event" 
Agent is shutting down 
Firing Event: "database flush event" 
Database Remove: /option 
Database Remove: /gamesession/client 
Database Remove: /gamesession/client/1 
Queue 'default' Resource for delete 
Database Remove: /gamesession/s2_dede 
Database Remove: /gamesession/s2_dede/1 
Deferred delete of 'default' Resource 
Queue 'default' Resource for delete 
Database Remove: /agent 
Deferred delete of 'default' Resource completed 
Queue 'download' Resource for delete 
Deferred delete of 'default' Resource 
Database Remove: /version/client 
Deferred delete of 'default' Resource completed 
Database Remove: / 
Database Remove: /register 
Deferred delete of 'download' Resource 
Deferred delete of 'download' Resource completed 
Queue 'registerroot' Resource for delete 
Deferred delete of 'registerroot' Resource 
Database Remove: /game 
Deferred delete of 'registerroot' Resource completed 
Database Remove: /game/client 
Queue 'game' Resource for delete 
Database Remove: /game/s2_dede 
Deferred delete of 'game' Resource 
Deferred delete of 'game' Resource completed 
Deferred delete of 'game' Resource 
Queue 'game' Resource for delete 
Deferred delete of 'game' Resource completed 
Queue 'gameroot' Resource for delete 
Database Remove: /repair 
Deferred delete of 'gameroot' Resource 
Deferred delete of 'gameroot' Resource completed 
Queue 'repairroot' Resource for delete 
Deferred delete of 'repairroot' Resource 
Queue 'agentroot' Resource for delete 
Deferred delete of 'repairroot' Resource completed 
Database Remove: /gamesession 
Deferred delete of 'agentroot' Resource 
Queue 'composite' Resource for delete 
Queue 'composite' Resource for delete 
Queue 'gamesessionroot' Resource for delete 
Database Remove: /backfill 
Queue 'backfillroot' Resource for delete 
Deferred delete of 'agentroot' Resource completed 
Deferred delete of 'composite' Resource 
Database Remove: /spawned 
Deferred delete of 'composite' Resource completed 
Queue 'spawnedroot' Resource for delete 
Deferred delete of 'composite' Resource 
Deferred delete of 'composite' Resource completed 
Queue 'optionroot' Resource for delete 
Deferred delete of 'gamesessionroot' Resource 
Database Remove: /version 
Deferred delete of 'gamesessionroot' Resource completed 
Queue 'async_task' Resource for delete 
Deferred delete of 'backfillroot' Resource 
Database Remove: /version/s2_dede 
Deferred delete of 'backfillroot' Resource completed 
Queue 'async_task' Resource for delete 
Deferred delete of 'spawnedroot' Resource 
Deferred delete of 'spawnedroot' Resource completed 
Queue 'versionroot' Resource for delete 
Deferred delete of 'optionroot' Resource 
Database Remove: /update 
Deferred delete of 'optionroot' Resource completed 
Queue 'updateroot' Resource for delete 
Deferred delete of 'async_task' Resource 
Database Remove: /createshortcut 
Queue 'createshortcut' Resource for delete 
Deferred delete of 'async_task' Resource completed 
Deferred delete of 'async_task' Resource 
Database Remove: /uninstall 
Queue 'uninstallroot' Resource for delete 
Database Remove: /install 
Queue 'installroot' Resource for delete 
Queue 'root' Resource for delete 
Database Remove: /agent/download 
Queue 'download' Resource for delete 
Deferred delete of 'async_task' Resource completed 
Deferred delete of 'versionroot' Resource 
Deferred delete of 'versionroot' Resource completed 
Deferred delete of 'updateroot' Resource 
Deferred delete of 'updateroot' Resource completed 
Deferred delete of 'createshortcut' Resource 
Deferred delete of 'createshortcut' Resource completed 
Deferred delete of 'uninstallroot' Resource 
Deferred delete of 'uninstallroot' Resource completed 
Deferred delete of 'installroot' Resource 
Deferred delete of 'installroot' Resource completed 
Deferred delete of 'root' Resource 
Deferred delete of 'root' Resource completed 
Deferred delete of 'download' Resource 
Deferred delete of 'download' Resource completed 
Deleting remaining resources 
Connection statistics (times in milliseconds) 
    latency = 17.808 ms 
    bandwidth = 1.715 MB/sec 
    downloadUrlCount: 9 
    downloadUrlCallTime: 227.133 (25.236989) 
    downloadUrlElapsedTime: 402.293 (44.699278) 
 
    connectionsCreated: 6 
    connectionsClosed: 6 
    requestsCreated: 9 
    requestsClosed: 9 
 
    parseUrlTime: 0.069 (0.007711) 
    createRequestTime: 0.802 (0.089122) 
    createHeadersTime: 0.026 (0.002944) 
    sendRequestTime: 0.284 (0.031578) 
    httpSendRequestTime: 0.251 (0.027878) 
    httpResponseTime: 160.272 (17.807978) 
 
    readissued: 102 
    readsync: 102 
    readasync: 0 
    readfail: 0 
    readzero: 8 
    readnonzero: 94 
    readfileTime: 103.128 (1.011058) 
    readfileWaitTime: 0.000 (0.000000) 
    readfileResponseTime: 1.013 (0.010771) 
    readCallbackTime: 0.060 (0.000635) 
 
    readBytes: 178638 

```
Please, ubuntu pr0s, help me with my problem! If you need more information, tell me!

[HR][/HR]
Some additional information:

My PC: i5-3550 + GTX650@331
Glxinfo:
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_SGI_video_sync
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_copy_image, GLX_NV_float_buffer, GLX_NV_multisample_coverage, 
    GLX_NV_present_video, GLX_NV_swap_group, GLX_NV_video_capture, 
    GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_SGIX_fbconfig,                                            
    GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_SGI_video_sync                                                      
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 650/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 331.20
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_bindless_texture, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_compute_shader, GL_ARB_compute_variable_group_size, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_indirect_parameters, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_draw_parameters, 
    GL_ARB_shader_group_vote, GL_ARB_shader_image_load_store, 
    GL_ARB_shader_image_size, GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sparse_texture, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_Cg_shader, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_NVX_nvenc_interop, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_bindless_texture, GL_NV_blend_equation_advanced, GL_NV_blend_square, 
    GL_NV_compute_program5, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_draw_texture, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_OES_compressed_ETC1_RGB8_texture, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

OpenGL version string: 4.4.0 NVIDIA 331.20
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_bindless_texture, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_compute_shader, 
    GL_ARB_compute_variable_group_size, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_indirect_parameters, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_draw_parameters, 
    GL_ARB_shader_group_vote, GL_ARB_shader_image_load_store, 
    GL_ARB_shader_image_size, GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sparse_texture, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_Cg_shader, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_NVX_nvenc_interop, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_bindless_texture, GL_NV_blend_equation_advanced, GL_NV_blend_square, 
    GL_NV_compute_program5, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_draw_texture, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_OES_compressed_ETC1_RGB8_texture, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

228 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x040 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x041 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x042 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x043 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x045 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x047 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x048 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x049 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x04b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x04c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x04d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x04f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x050 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x051 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x052 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x053 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x054 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x055 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x056 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x057 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x058 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x059 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x05a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x05b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x05c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x05d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x05e 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x05f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x060 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x061 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x063 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x064 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x066 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x067 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x068 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x069 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x06b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x06d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x06e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x071 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x072 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x073 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x074 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x075 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x077 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x079 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x07b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x07c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x07d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x07e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x07f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x080 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x081 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x082 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x084 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x086 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x088 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x089 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x08a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x08b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x08c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x08e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x08f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x090 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x097 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x099 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x09a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x09c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09d 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0a0 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0a1 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0a2 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0a3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0a6 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0a7 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0a8 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0ad 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0ae 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0af 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0b0 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0b1 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0b2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0b3 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0b4 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0b5 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0b6 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b8 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0bb 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0bc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0bd 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0be 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0c3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0c4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0c5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c9 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ca 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0cb 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0cc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0cd 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0ce 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0cf 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0d0 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0d1 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0d2 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0d3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0d4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0d5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0d6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0d7 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d8 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d9 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0da 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0db 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0dc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0dd 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0de 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0df 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0e0 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0e1 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0e2 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0e3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0e4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0e5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0e6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0e7 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e8 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e9 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0ea 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0eb 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0ec 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0ed 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0ee 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0ef 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0f0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0f1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f4 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f5 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f9 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0fa 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0fb 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0fc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0fd 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0fe 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0ff 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x100 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x101 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x102 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x103 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x104 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon

311 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x105 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x106 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x108 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x109 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x10a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x10b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x10d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x10e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x110 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x111 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x112 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x113 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x114 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x115 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x116 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x117 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x118 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x119 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x11a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x11b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x11c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x11d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x11e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x11f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x120 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x121 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x122 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x123 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x124 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x125 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x126 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x127 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x128 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x129 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x12a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x12b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x12c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x12d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x12e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x12f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x131 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x132 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x133 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x135 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x136 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x137 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x138 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x139 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x13a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x13b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x13c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x13d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x13e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x13f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x141 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x142 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x143 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x144 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x145 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x146 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x147 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x148 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x149 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x14a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x14b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x14c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x14d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x14e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x14f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x150 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x151 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x152 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x153 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x155 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x156 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x157 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x158 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x159 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x15a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x15b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x15c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x15d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x15e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x15f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x160 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x161 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x162 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x163 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x164 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x165 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x166 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x167 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x168 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x169 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x16a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x16b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x16c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x16d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x16e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x16f 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x170 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x171 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x172 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x173 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x174 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x175 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x176 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x177 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x178 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x179 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17e 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x17f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x180 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x181 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x182 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x183 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x184 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x185 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x186 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x187 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x188 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x189 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x18a 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x18b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x18c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x18d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x18e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x18f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x190 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x191 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x192 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x193 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x194 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x195 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x196 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x197 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x198 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x199 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x19a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x19b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x19c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x19d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x19e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x19f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x1a0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x1a1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x1a2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x1a3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x1a4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x1a5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x1a6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x1a7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x1a8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x1a9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1aa 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1ab 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1ac 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1ad 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1ae 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1b3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1b4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1b5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1b6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1ca 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1cb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1cc 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1cd 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1ce 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1cf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1d0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1d1 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1d2 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1d3 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1d4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1d5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1d6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1d7 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1d8 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1d9 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1da 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1db 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1dc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1dd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1de 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1df 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1e0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1e1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1e2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1e3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1e4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1e5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1e6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1e7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1e8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1e9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1ea  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1eb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1ec  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1ed  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1ee  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1ef  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1f0  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1f1  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1f2  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1f3  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1f4  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1f5  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1f6  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1f7  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1f8  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1f9  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1fa  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1fb  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1fc  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1fd  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1fe  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1ff  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x200  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x201  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x202  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x203  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x204  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x205  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x206  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x207  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x208  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x209  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x20a  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x20b  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x20c  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x20d  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x20e  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x20f  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x210  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x211  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x212  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x213  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x214  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x215  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x216  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x217  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x218  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x219  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x21a  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x21b  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x21c  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x21d  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x21e  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x21f  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x220  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x221  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x222  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x223  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x224  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x225  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x226  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x227  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x228  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x229  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x22a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x22b  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x22c  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x22d  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x22e  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x22f  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x230  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x231  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x232  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x233  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x234  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x235  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x236  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x237  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x238  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x239  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x23a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x23b  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None


```
Kernel: 3.11-2-amd64

---

### Post by cyanophyteae on 2013-12-07
Yo, Im no pro but have you installed Internet explorer as addon in wine? Maybe try a different wine version, although the version you`re running is working perfect with sc2 on my comp.

---

### Post by mueldeponi on 2013-12-07
I just installed ie6 and I don't even come to the login screen - while loading, it immediately crashes with an unexpected fatal error :(

#EDIT: Okay, I fixed it. For some reason, win version was set to 2000. I changed it to XP and installed IE8. Now I get to the login screen - but it still "crashes" when i click the button.

---

### Post by cyanophyteae on 2013-12-07
I see..In Wine config you chose not to show a virtual desktop right? All my display settings are on default, except from video memory size.

---

### Post by cyanophyteae on 2013-12-07
Did you try installing the game through PlayonLinux?

---

### Post by mueldeponi on 2013-12-07
No virtual desktop, no special settings. If i tweak (like it is described on the winehq page) it doesn't change.

Yep, it runs through PoL

---

### Post by mueldeponi on 2013-12-09
Please help me, ubuntu pr0s!

I'm sure some of you play Starcraft II too, and you also use Linux so you should know how to install it. Please help, I don't know what to do. I tried everything I found on the Interwebz, but nothing worked :-|

#EDIT: Wow. I just fixed it. I don't know why it didn't work before. I just deleted everything sc2 related and "installed" it again in PoL, stopped the installation, copied the wind0ws files, made a shortcut, and now... it works.

---

