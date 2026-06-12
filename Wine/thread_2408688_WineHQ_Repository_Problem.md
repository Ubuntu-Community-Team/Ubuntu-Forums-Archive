---
title: "WineHQ Repository Problem"
date: 2018-12-21
forum: Wine
---

### Post by MSGone on 2018-12-21
I've had the problem for the last couple of days. I try to check for updates, and this is what I get:

An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672FFailed to fetch [https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/InRelease](https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672FSome index files failed to download. They have been ignored, or old ones used instead.

I don't have a clue what to do. Could someone please help me? Thanks in advance.

---

### Post by Holger_Gehrke on 2018-12-22
A quick look at the [Ubuntu installation page at winehq]("https://wiki.winehq.org/Ubuntu") would have told you what is wrong. The repository key was changed recently and you need to download the new key and add it to the list of keys apt trusts.

Holger

---

### Post by MSGone on 2018-12-22
> **Holger_Gehrke said:**
> A quick look at the [Ubuntu installation page at winehq]("https://wiki.winehq.org/Ubuntu") would have told you what is wrong. The repository key was changed recently and you need to download the new key and add it to the list of keys apt trusts.

Holger

Thank you sincerely. I Googled the problem and did wind up on the page you suggested. It solved my problem. Thank you again.

---

