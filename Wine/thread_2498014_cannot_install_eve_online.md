---
title: "cannot install eve online"
date: 2024-05-26
forum: Wine
---

### Post by filiprybar on 2024-05-26
I tried to nstall eve online with wine: $ wine start eve-setup
I get:
$ 0120:err:winediag:ntlm_check_version ntlm_auth was not found. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
0120:err:ntlm:ntlm_LsaApInitializePackage no NTLM support, expect problems
0144:err:winediag:ntlm_check_version ntlm_auth was not found. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
0144:err:ntlm:ntlm_LsaApInitializePackage no NTLM support, expect problems
015c:err:ole:marshal_object Failed to create an IRpcStubBuffer from IPSFactory for {659cdeac-489e-11d9-a9cd-000d56965251} with error 0x80004002
01b0:err:winediag:ntlm_check_version ntlm_auth was not found. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
01b0:err:ntlm:ntlm_LsaApInitializePackage no NTLM support, expect problems
0210:err:wusa:install_files_copy Required file L"C:\\users\\filip\\Temp\\msu2.tmp\\amd64_netfx4-servicemodel_mof_files_b03f5f7f11d50a3a_4.0.9600.17187_none_7f79f6c9b36ef700\\ServiceModel.mof.uninstall" not found
0210:err:wusa:install_assembly Failed to install all files for L"NetFx4-ServiceModel_mof_files"
0210:err:wusa:install_updates Failed to install update L"Package_for_KB2934520"
0210:err:wusa:install_msu Dry run failed, aborting installation

---

### Post by nicolasdentremont on 2024-05-26
Have you tried Lutris? In my experience, running Windows games with Lutris works much better than with regular WINE. Lutris still uses WINE to run Windows programs but comes with extra tweaks that make it much more likely to successfully run games.

If you check the Lutris database [https://lutris.net/games/eve-online/](https://lutris.net/games/eve-online/) you'll find that there's an install script for EVE Online. Once you have Lutris installed you can just run the script from the Lutris website and it will help with installing the game.

At first I tried installing games just with WINE and nothing was working properly but with Lutris, most of my Windows games work fine, some even better than on Windows.

---

### Post by currentshaft on 2024-05-26
> **nicolasdentremont said:**
> Have you tried Lutris? In my experience, running Windows games with Lutris works much better than with regular WINE. Lutris still uses WINE to run Windows programs but comes with extra tweaks that make it much more likely to successfully run games.

If you check the Lutris database [https://lutris.net/games/eve-online/](https://lutris.net/games/eve-online/) you'll find that there's an install script for EVE Online. Once you have Lutris installed you can just run the script from the Lutris website and it will help with installing the game.

At first I tried installing games just with WINE and nothing was working properly but with Lutris, most of my Windows games work fine, some even better than on Windows.

+1 on Lutris, especially as a Flatpak. Runs great, manages dependencies well and can play all the old school games.

---

### Post by filiprybar on 2024-06-07
lutris showing:
RuntimeError('No path can be generated for DXVK because no version information is available.')

---

### Post by QIII on 2024-06-07
Moved to **Wine**

---

### Post by nicolasdentremont on 2024-06-08
> **filiprybar said:**
> lutris showing:
RuntimeError('No path can be generated for DXVK because no version information is available.')

Did you run the install script for the game before launching Lutris for the first time by any chance? Lutris installs some extra stuff when you start it for the first time.

---

