---
title: "Leap 15.5: New repository or package signing key received:"
date: 2024-07-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-07-21
```

# zypper patch -g security
...
New repository or package signing key received:

  Repository:       nVidia Graphics Drivers
  Key Fingerprint:  2FB0 3195 DECD 4949 2BD1 C17A B1D0 D788 DB27 FD5A
  Key Name:         NVIDIA Linux Driver Team <linux-bugs@nvidia.com>
  Key Algorithm:    RSA 4096
  Key Created:      Fri Apr 15 00:04:01 2022
  Key Expires:      (does not expire)
  Rpm Name:         gpg-pubkey-db27fd5a-62589a51



    Note: Signing data enables the recipient to verify that no modifications occurred after the data
    were signed. Accepting data with no, wrong or unknown signature can lead to a corrupted system
    and in extreme cases even to a system compromise.

    Note: A GPG pubkey is clearly identified by its fingerprint. Do not rely on the key's name. If
    you are not sure whether the presented key is authentic, ask the repository provider or check
    their web site. Many providers maintain a web page showing the fingerprints of the GPG keys they
    are using.

Do you want to reject the key, trust temporarily, or trust always? [r/t/a/?] (r):
```

Is it please safe to accept it ?

---

### Post by currentshaft on 2024-07-21
Seems safe based on a 5 second web search: [https://news.opensuse.org/2024/06/12/new-NVIDIA-signing-key/](https://news.opensuse.org/2024/06/12/new-NVIDIA-signing-key/)

---

### Post by maketopsite on 2024-07-22
> **currentshaft said:**
> Seems safe based on a 5 second web search: [https://news.opensuse.org/2024/06/12/new-NVIDIA-signing-key/](https://news.opensuse.org/2024/06/12/new-NVIDIA-signing-key/)

Thank you.

---

