---
title: "Problem with play League of Legends on Ubuntu with metacity"
date: 2017-06-22
forum: Wine
---

### Post by yurilion123 on 2017-06-22
I'm having bug splat in the charge screen using metacity. Using Compiz are all right. Someone have the same problem than me?

---

### Post by QIII on 2017-06-22
Hello!

You will have to explain "bug splat in the charge screen".

---

### Post by yurilion123 on 2017-06-24
Thanks for the help!

Here, the log with the problem:

```
League of Legends caused ACCESS_VIOLATION in module League of Legends

Read from location 8cbb1aeb caused an access violation.


User Information:
    User Name: yuriferreira
    Computer Name: yuriferreira-HP


OS Info:
    Windows XP Service Pack 3 Professional, x86


System Information:
    4 processor(s), type 586.
    71% of memory in use.
    3844M total physical memory.
    1098M free physical memory.
    7827M total paging file.
    4968M free paging file.
    4095M total virtual memory.
    4095M free virtual memory.


Process Memory:
    1233M free.
    2374M reserved.
     488M commited.
    Largest free block is 1177M.


    PageFaultCount: 0
    PeakWorkingSetSize: 0M
    WorkingSetSize: 0M
    QuotaPeakPagedPoolUsage: 0M
    QuotaPagedPoolUsage: 0M
    QuotaPeakNonPagedPoolUsage: 0M
    QuotaNonPagedPoolUsage: 0M
    PagefileUsage: 0M
    PeakPagefileUsage: 0M
    PrivateUsage: 0M


Process Info:
    ThreadCount: 25



```


Here, the complete log of the bugsplat:

```
 

000000.000| ALWAYS| Logging started at 2017-06-22T02:04:39.796000000.001|   OKAY| Riot::RADS::Reader::RadsMain::Initialize: RADS library initializing with specified working directory "C:\Riot Games\League of Legends\RADS\solutions\lol_game_client_sln\releases\0.0.1.179\deploy".
000000.010|   OKAY| Riot::RADS::Reader::RuntimeEnvironment::Create: Creating RADS runtime environment: RADS root directory = "C:/Riot Games/League of Legends/RADS"
000000.017|   OKAY| Riot::RADS::Reader::SolutionManifest::Load: ("C:/Riot Games/League of Legends/RADS/solutions/lol_game_client_sln/releases/0.0.1.179/solutionmanifest")
000000.063|   OKAY| Riot::RADS::Reader::ConfigurationManifest::Load: ("C:/Riot Games/League of Legends/RADS/solutions/lol_game_client_sln/releases/0.0.1.179/configurationmanifest")
000000.070|   OKAY| Riot::RADS::Reader::ReleaseManifest::LoadInternal: ("C:/Riot Games/League of Legends/RADS/projects/lol_game_client_pt_br/releases/0.0.1.13/releasemanifest")
000003.326|   OKAY| Riot::RADS::Reader::ReleaseManifest::LoadInternal: ("C:/Riot Games/League of Legends/RADS/projects/lol_game_client/releases/0.0.1.120/releasemanifest")
000013.966|   OKAY| Unable to process data overlay file ./ToolsConfig.xml, defaulting to overlay now
000013.967| ALWAYS| Data overlay start folder initialized to DATA, Content/Src
000014.044| ALWAYS| Build Version: Version 7.12.190.9002 (Jun 08 2017/18:08:40) [PUBLIC] <Releases/7.12> ChangeList: 1909002
000014.861| ALWAYS| Started System Init
000014.861| ALWAYS| LCURemotingClient: Initializing on port 36736
000015.210| ALWAYS| LCURemotingClient: Connected to app process.
000015.210| ALWAYS| zip manifest, 'ClientZips.txt', not found (expected).
000015.249| ALWAYS| WadFile mount: DATA/FINAL/Global.wad 
000015.332| ALWAYS| WadFile mount: DATA/FINAL/Scripts.wad 
000015.371| ALWAYS| WadFile mount: DATA/FINAL/ShaderCache.wad 
000015.416| ALWAYS| WadFile mount: DATA/FINAL/UI/ui.wad 
000015.418| ALWAYS| WadFile mount: DATA/FINAL/Shaders/Shaders.wad 
000015.446| ALWAYS| WadFile mount: DATA/FINAL/Localized/Global.pt_br.wad 
000015.558| ALWAYS| StartSession called
000015.558| ALWAYS| Started Init event arguments
000015.559| ALWAYS| Waiting until connection...
000015.808| ALWAYS| OS Version String: XP Service Pack 3 Professional, x86
000015.808| ALWAYS| CPU: GenuineIntel, Intel(R) Pentium(R) 4 CPU 2.40GHz, x86 Family 6 Model 42 Stepping 7, 2200 (0 core)
000015.808| ALWAYS| Measured processor speed: 2226
000015.808| ALWAYS| Display info: Intel(R) Sandybridge Mobile 1073741824 1.0
000015.808| ALWAYS| Physical memory: 4030914560
000015.808| ALWAYS| {"messageType":"hardware_information","message_body":"Hardware Info","operating_system":"XP Service Pack 3 Professional, x86","cpu":"GenuineIntel","cpu_processor":"Intel(R) Pentium(R) 4 CPU 2.40GHz","cpu_identifier":"x86 Family 6 Model 42 Stepping 7","cpu_topology":1,"gpu":"Intel(R) Sandybridge Mobile","video_memory":"1073741824","driver_version":"1.0","physical_memory":4030914560,"wine":true}
000015.808| ALWAYS| -----HARDWARE INFORMATION START-----
000015.809| ALWAYS| Operating System: XP Service Pack 3 Professional, x86
000015.809| ALWAYS| GPU Manufacturer: Intel(R) Sandybridge Mobile
000015.809| ALWAYS| GPU Memory: 1073741824
000015.809| ALWAYS| GPU Driver Version: 1.0
000015.809| ALWAYS| CPU Brand: GenuineIntel
000015.809| ALWAYS| CPU Processor Name: Intel(R) Pentium(R) 4 CPU 2.40GHz
000015.809| ALWAYS| CPU Identifier: x86 Family 6 Model 42 Stepping 7
000015.810| ALWAYS| CPU Speed: 2200
000015.810| ALWAYS| CPU Topology: 1 Core
000015.810| ALWAYS| Physical memory: 4030914560
000015.810| ALWAYS| -----HARDWARE INFORMATION END-----
000015.869| ALWAYS| InitRenderer() enter
000015.869| ALWAYS| r3dRenderLayer::Init(0x000100BE) enter
000015.870| ALWAYS| r3dRenderLayer::Init() exit successfully
000016.163|  ERROR| Error: FontConfig(File DATA/Menu/fontconfig_pt_br.txt, Line 5133) - unexpected statement
000016.165|  ERROR| Error: FontConfig(File DATA/Menu/fontconfig_pt_br.txt, Line 5188) - unexpected statement
000016.319| ALWAYS| Loaded locale pt_br via fontconfig
000016.375| ALWAYS| IME file, 'C:/Riot Games/League of Legends/RADS/solutions/lol_game_client_sln/releases/0.0.1.179/deploy/Data/Menu/IMEConfig.xml', is optional. The following error is expected.
000016.391|  ERROR| Missing file on r3dGFile open :C:/Riot Games/League of Legends/RADS/solutions/lol_game_client_sln/releases/0.0.1.179/deploy/Data/Menu/IMEConfig.xml
000016.391|  ERROR| Missing file on r3dGFile open :\Bin\Data\C:/Riot Games/League of Legends/RADS/solutions/lol_game_client_sln/releases/0.0.1.179/deploy/Data/Menu/IMEConfig.xml
000016.453| ALWAYS| SharedConfigPath: ../Air/preferences/
000016.457| ALWAYS| rr3dRenderLayer::InitDevice(XRes = 1280, YRes = 720, BPP = 32) enter
000016.457| ALWAYS| rr3dRenderLayer::InitDevice: Creating X3D device
000016.961| ALWAYS| r3dRenderLayer::RecreateOwnedResources
000017.069| ALWAYS| r3dRenderLayer::InitResources exit successfully
000017.580| ALWAYS| Waiting for client ID
000017.882| ALWAYS| {"messageType":"riot__game_client__connection_info","message_body":"Hard Connect"}
000017.882| ALWAYS| Game Info Start ===========================================
000017.882| ALWAYS| Map: 11, Mode : CLASSIC
000017.882| ALWAYS| FiddleSticks Skin 0 (Order Human)
000017.882| ALWAYS| Game Info End =============================================
000017.882| ALWAYS| Received client ID
000017.887| ALWAYS| Set focus to app
000017.888| ALWAYS| Input started
000017.938| ALWAYS| Query Status Req started
000018.531| ALWAYS| Query Status Req ended
000018.531| ALWAYS| Waiting for server response...
000018.754| ALWAYS| WadFile mount: DATA/FINAL/Maps/Shipping/Map11.wad 
000018.765| ALWAYS| WadFile mount: DATA/FINAL/Maps/Shipping/Map11.pt_br.wad 
000018.824| ALWAYS| Initializing GameModeComponents for mode=CLASSIC.
000018.825| ALWAYS| ... Processing GameMode Mutator = default.
000018.825| ALWAYS| ... Processing GameMode Mutator = LoadingScreenBackground(Data).
000018.825| ALWAYS| ... Processing GameMode Mutator = FOWTexture(FogOfWarOverlay.dds).
000018.825| ALWAYS| ... Processing GameMode Mutator = HudSkin(Default).
000018.825| ALWAYS| ... Processing GameMode Mutator = NavigationMesh(AIPath).
000018.825| ALWAYS| ... Processing GameMode Mutator = MiniMapTexture(2DLevelMinimap.dds).
000018.825| ALWAYS| ... Processing GameMode Mutator = AudioFeature(None).
000018.825| ALWAYS| ... Processing GameMode Mutator = BotSummonerIcon(0).
000018.825| ALWAYS| ... Processing GameMode Mutator = EndOfGameScreenText(Default).
000018.825| ALWAYS| ... Processing GameMode Mutator = HealthTextModifier(default).
000018.825| ALWAYS| ... Processing GameMode Mutator = DamageTextModifier(default).
000018.825| ALWAYS| ... Processing GameMode Mutator = MapObjectESportTeamCustomization(0).
000018.826| ALWAYS| ... Processing GameMode Mutator = LocalizationEncryptKey(none).
000018.826| ALWAYS| ... Processing GameMode Mutator = SuppressMinionSpawn(0).
000018.826| ALWAYS| ... Processing GameMode Mutator = RestrictedItemShopCategories(none).
000018.826| ALWAYS| ... Processing GameMode Mutator = LevelPropsScript(CreateLevelProps.lua).
000018.826| ALWAYS| ... Processing GameMode Mutator = NeutralMinionSpawnScript(NeutralMinionSpawn.lua).
000018.826| ALWAYS| ... Processing GameMode Mutator = MapObjects(MapObjects.mob).
000018.826| ALWAYS| ... Processing GameMode Mutator = SpectatorHudSkin(SpectatorUpdate).
000018.826| ALWAYS| ... Processing GameMode Mutator = SpectatorMiniMapTexture(2DLevelMinimap.dds).
000018.826| ALWAYS| ... Processing GameMode Mutator = WorldGeometry(room).
000018.826| ALWAYS| ... Processing GameMode Mutator = LevelScriptFile(LevelScript.lua).
000018.827| ALWAYS| ... Processing GameMode Mutator = NewSummonerBadgeSystem(0).
000018.827| ALWAYS| ... Processing GameMode Mutator = WorldParticles(Particles.dat).
000018.827| ALWAYS| ... Processing GameMode Mutator = WorldParticlesIni(Particles.ini).
000018.827| ALWAYS| ... Processing GameMode Mutator = ObjectCFG(ObjectCFG.cfg).
000018.827| ALWAYS| ... Processing GameMode Mutator = TerrainINI(terrain.ini).
000018.827| ALWAYS| ... Processing GameMode Mutator = EsportsRecallDecals(0).
000018.827| ALWAYS| ... Processing GameMode Mutator = IconBasedEmotes(0).
000018.827| ALWAYS| ... Processing GameMode Mutator = TowerFirstBloodAnnouncement(1).
000018.828| ALWAYS| ... Processing GameMode Mutator = EnableSRPlants2017Preseason(1).
000018.828| ALWAYS| ... Processing GameMode Mutator = TeamBuilderRosterPositions(1).
000018.828| ALWAYS| ... Processing GameMode Mutator = GodrayLocator(1).
000018.828| ALWAYS| ... Processing GameMode Mutator = CursorLocator(0).
000018.828| ALWAYS| ... Processing GameMode Mutator = SkinNamesInScoreboard(0).
000018.828| ALWAYS| ... Processing GameMode Mutator = NeutralTimers(NeutralTimers.ini).
000018.829| ALWAYS| ... Processing GameMode Mutator = CLASSIC.
000018.829| ALWAYS| ... Processing GameMode Mutator = NewSummonerBadgeSystem(0).
000018.829| ALWAYS| ... Processing GameMode Mutator = Banana.
000018.829| ALWAYS| ... Processing GameMode Mutator = VeryBanana(1).
000018.829| ALWAYS| ... Processing GameMode Mutator = Moments.
000018.829| ALWAYS| ... Processing GameMode Mutator = MomUI(1).
000018.829| ALWAYS| ... Processing GameMode Mutator = TeambuilderRosterPositions(1).
000018.829| ALWAYS| ... Processing GameMode Mutator = Event_Versus.
000018.830| ALWAYS| ... Processing GameMode Mutator = MapID(11)?LoadingScreenBackground(SRVersusBackground).
000018.830| ALWAYS| ... Processing GameMode Mutator = MasteryBadgeOverride(SummonerIconBadge).
000018.830| ALWAYS| ... Processing GameMode Mutator = PracticeTool.
000018.830| ALWAYS| ... Processing GameMode Mutator = PracticeToolOptionsMenuHotkeys(1).
000018.851| ALWAYS| WadFile mount: DATA/FINAL/Champions/PracticeTool_TargetDummy.wad 
000018.887| ALWAYS| WadFile mount: DATA/FINAL/Champions/PracticeTool_TargetDummy.pt_br.wad 
000018.887| ALWAYS| netUID: 0 defaultname
000018.999| ALWAYS| PlayGame Started
000019.000| ALWAYS| r3dRenderLayer::InitDefaultShaders: Initialize shaders for current rendering path
000020.336| ALWAYS| LCUChatClientAsync: Worker thread created.
000020.336| ALWAYS| LCURemotingClient: Initializing on port 36736
000020.336| ALWAYS| LCUChatClientAsync: Worker thread connecting.
000020.352| ALWAYS| LCURemotingClient: Connected to app process.
000020.352| ALWAYS| LCUChatClientAsync: Waiting for active chat session.
000021.362| ALWAYS| LCUChatClientAsync: Chat session is "loaded".
000021.463| ALWAYS| LCUChatClientAsync: Performing post-connect init.
000021.463| ALWAYS| LCUChatClientAsync: Setup the subscriptions.
000021.463| ALWAYS| LCUChatClientAsync: Initiated retrieval of my friends list.
000021.464| ALWAYS| LCUChatClientAsync: Initiated retrieval of my blocked-players list.
000021.466| ALWAYS| LCUChatClientAsync: Post-connect init complete.
000021.745|  ERROR| Can not open file <CCImmunityhealthbar.dds> *********
000021.745|  ERROR| Failed to load CCImmunityhealthbar.dds
000021.746|   WARN| r3dTexture EX: CCImmunityhealthbar.dds - not found. Dummy texture created.
000022.584| ALWAYS| LCUChatClientAsync: Retrieved my friends list.
000023.596| ALWAYS| LCUChatClientAsync: Retrieved my blocked-players list.
000026.664|   WARN| General performance warning: more than 11 texture samplers are being used simultanously.
Please bump this number if this is intentional up to 16 (inclusive)
000026.697| ALWAYS| PlayGame Entered
000026.697| ALWAYS| gRenderPipeline
000026.780| ALWAYS| CreateParticleSystemManager
000027.651| ALWAYS| CreateAudioManager: Create audio manager Wwise.
000028.113| ALWAYS| AudioManager: Wwise Version v2013.2.2 initialized.
000035.713|  ERROR| Can not open file <TurretInitialArmor.dds> *********
000035.713|  ERROR| Failed to load TurretInitialArmor.dds
000035.713|   WARN| r3dTexture EX: TurretInitialArmor.dds - not found. Dummy texture created.
000035.736|  ERROR| Can not open file <LuxCrashingBlitz2.dds> *********
000035.736|  ERROR| Failed to load LuxCrashingBlitz2.dds
000035.736|   WARN| r3dTexture EX: LuxCrashingBlitz2.dds - not found. Dummy texture created.
000038.634|  ERROR| Can not open file <VoidGate_base_TX_CM.DDS> *********
000038.635|  ERROR| Failed to load VoidGate_base_TX_CM.DDS
000038.635|   WARN| r3dTexture EX: VoidGate_base_TX_CM.DDS - not found. Dummy texture created.
000038.772|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000038.772|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000038.772|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000038.772|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000038.773|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000039.768|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000039.768|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000039.768|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000039.768|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000039.769|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000041.528|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <SRU_Plant_Vision_Death_mult.dds>


000041.772|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <SRU_Plant_Vision_Death_mult.dds>


000042.490|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000042.490|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000042.490|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000042.490|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000042.491|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <vladhealtrail.tga>


000043.516|  ERROR| Failed to load spell ini or script: "poisontrailtarget"
000043.517|  ERROR| Failed to load spell ini or script: "poisontrailtarget"
000043.518|  ERROR| Failed to load spell ini or script: "poisontrailtarget"
000043.518|  ERROR| Failed to load spell ini or script: "poisontrailtarget"
000045.260|  ERROR| Can not open file <TemplateFighterPassive.dds> *********
000045.260|  ERROR| Failed to load TemplateFighterPassive.dds
000045.260|   WARN| r3dTexture EX: TemplateFighterPassive.dds - not found. Dummy texture created.
000046.915|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <EH_Baron_Flash.dds>


000047.040|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <EH_Baron_Flash.dds>


000047.486|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <SRU_RiftHerald_Relic_Beacon_Center_Mult.dds>


000047.550|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <SRU_RiftHerald_Relic_Beacon_Center_Mult.dds>


000047.571|  ERROR| Data Error on expression: always
 Data Error message: Missing effect texture <SRU_RiftHerald_Relic_Beacon_Center_Mult.dds>


000049.796|  ERROR| ?:0: attempt to call global 'GetIsGameFeatureEnabled' (a nil value)
000054.517|  ERROR| Crash Occurred
```

---

