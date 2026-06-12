---
title: "Leap 15.5: Signature verification failed for file 'repomd.xml' from repository 'Updat"
date: 2024-05-29
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-05-29
```
# zypper patch -g security 
Signature verification failed for file 'repomd.xml' from repository 'Update repository with updates from SUSE Linux Enterprise 15'.

    Note: Signing data enables the recipient to verify that no modifications occurred after the data
    were signed. Accepting data with no, wrong or unknown signature can lead to a corrupted system
    and in extreme cases even to a system compromise.

    Note: File 'repomd.xml' is the repositories master index file. It ensures the integrity of the
    whole repo.

    Warning: This file was modified after it has been signed. This may have been a malicious change,
    so it might not be trustworthy anymore! You should not continue unless you know it's safe.

    Note: This might be a transient issue if the server is in the midst of receiving new data. The
    data file and its signature are two files which must fit together. In case the request hit the
    server in the midst of updating them, the signature verification might fail. After a few
    minutes, when the server has updated its data, it should work again.

Signature verification failed for file 'repomd.xml' from repository 'Update repository with updates from SUSE Linux Enterprise 15'. Continue? [yes/no] (no):
```

Is it please safe to accept it ?

---

### Post by maketopsite on 2024-06-09
It's solved now - no question anymore.

---

