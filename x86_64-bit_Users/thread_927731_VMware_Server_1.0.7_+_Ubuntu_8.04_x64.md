---
title: "VMware Server 1.0.7 + Ubuntu 8.04 x64"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by jasonkeithscott on 2008-09-23
So I still can't get VMware Server 1.0.7 running on Ubuntu 8.04 x64...  I've followed the guide [[https://help.ubuntu.com/community/VMware/Server/AMD64](https://help.ubuntu.com/community/VMware/Server/AMD64) ] and the install seems to work perfect.

However, upon trying to launch the command 'vmware' I always get the following error:

```

/usr/bin/ldd: line 117: 20930 Segmentation fault      LD_TRACE_LOADED_OBJECTS=1 LD_WARN= LD_BIND_NOW= LD_LIBRARY_VERSION=$verify_out LD_VERBOSE= "$@"
Segmentation fault

```

Relevant lines in the wrapper script vmware looks like the following:

```

114  eval 'answers="$'"$dbvar"'_answers"'
115  # There is no double quote around $answers on purpose
116  for i in $answers; do
117    if [ "$i" = "$id" ]; then
118      echo 'remove_answer '"$id" >> "$dbfile"
119      db_answer_remove "$dbvar" "$id"
120      return
121    fi
122  done

```

Sourcing the vmware binary [/usr/lib/vmware/bin/vmware] also produces a SegFault.

Ideas?

---

