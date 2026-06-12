---
title: "[error] Repository 'openSUSE:Leap:15.5:Update' is invalid"
date: 2024-04-01
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-04-01
```

# zypper ref
...

Building repository 'brave-browser' cache ......................................................................................[done]
Forcing raw metadata refresh
Retrieving repository 'openSUSE:Leap:15.5:Update' metadata ....................................................................[error]
Repository 'openSUSE:Leap:15.5:Update' is invalid.
[http-download.opensuse.org-ff8e5a28|http://download.opensuse.org/repositories/openSUSE:/Leap:/15.5:/Update/standard/] Valid metadata not found at specified URL
History:
 - [http-download.opensuse.org-ff8e5a28|http://download.opensuse.org/repositories/openSUSE:/Leap:/15.5:/Update/standard/] Repository type can't be determined.

Please check if the URIs defined for this repository are pointing to a valid repository.
Skipping repository 'openSUSE:Leap:15.5:Update' because of the above error.
Forcing raw metadata refresh
Retrieving repository 'libdvdcss repository' metadata ..........................................................................[done]
...

```

Does anyone other have same problem please ?

---

### Post by maketopsite on 2024-04-02
It works now, I don't know what caused that.

---

