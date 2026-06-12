---
title: "Cannot update wine"
date: 2017-03-04
forum: Wine
---

### Post by flyingllama on 2017-03-04
I'm having trouble updating Wine on Ubuntu 16.04 despite trying apt-get update and apt-get upgrade. The repository that I am using is ppa:ubuntu-wine "Ubuntu Wine Team" and it is enabled (it does say however that it was disabled during the upgrade to Xenial from Trusty).

Current Wine version: wine 1.6.2

Thanks

---

### Post by howefield on 2017-03-05
Perhaps not a strictly Wine question but moved to the "*Wine*" anyway.

If the ppa is disabled then of course you won't get any updates. I'd suggest that you remove the existing wine package, add back in the xenial wine repository and install the current version.

From the Winehq site..
> If you have previously installed a Wine package from another repository, please remove it and any packages that depend on it (e.g., wine-mono, wine-gecko, winetricks) before attempting to install the WineHQ packages, as they may cause dependency conflicts.

When installing Wine I use..

```
sudo add-apt-repository ppa:wine/wine-builds
```
```
sudo apt update
```

and then, either..
```
sudo apt-get install --install-recommends winehq-devel
```
or
```
sudo apt-get install --install-recommends winehq-staging
```
depending on which version is required.

---

