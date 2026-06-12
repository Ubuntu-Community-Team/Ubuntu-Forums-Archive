---
title: "Leap 15.3:  docker0: port 1(veth7f4b2c0) entered blocking state"
date: 2022-04-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2022-04-04
Web application running on nginx in docker container does not work in Leap 15.3.

```
$ Proxy error: Could not proxy request /some/path from 172.19.0.2:3000 to http://172.18.0.1:8080.
See https://nodejs.org/api/errors.html#errors_common_system_errors for more information (ETIMEDOUT).

Proxy error: Could not proxy request /some/path2 from 172.19.0.2:3000 to http://172.18.0.1:8080.
See https://nodejs.org/api/errors.html#errors_common_system_errors for more information (ETIMEDOUT).
```

```
# dmesg
[30899.259583] nvidia-modeset: WARNING: GPU:0: Correcting number of heads for current head configuration (0x00)
[33493.211393] docker0: port 1(veth7f4b2c0) entered blocking state
[33493.211395] docker0: port 1(veth7f4b2c0) entered disabled state
[33493.211464] device veth7f4b2c0 entered promiscuous mode
[33493.215730] br-6205584aa04f: port 1(veth5bf75fd) entered blocking state
[33493.215732] br-6205584aa04f: port 1(veth5bf75fd) entered disabled state
[33493.215795] device veth5bf75fd entered promiscuous mode
[33493.216721] br-6205584aa04f: port 1(veth5bf75fd) entered blocking state
[33493.216722] br-6205584aa04f: port 1(veth5bf75fd) entered forwarding state
[33493.219102] br-6205584aa04f: port 1(veth5bf75fd) entered disabled state
[33494.171233] br-6205584aa04f: port 2(veth2e8c2d7) entered blocking state
[33494.171235] br-6205584aa04f: port 2(veth2e8c2d7) entered disabled state
[33494.171285] device veth2e8c2d7 entered promiscuous mode
[33494.171344] br-6205584aa04f: port 2(veth2e8c2d7) entered blocking state
[33494.171345] br-6205584aa04f: port 2(veth2e8c2d7) entered forwarding state
[33494.174559] IPv6: ADDRCONF(NETDEV_CHANGE): br-6205584aa04f: link becomes ready
[33494.175708] br-6205584aa04f: port 2(veth2e8c2d7) entered disabled state
[33495.755080] br-6205584aa04f: port 3(veth0409411) entered blocking state
[33495.755082] br-6205584aa04f: port 3(veth0409411) entered disabled state
[33495.755126] device veth0409411 entered promiscuous mode
[33497.414895] cgroup: cgroup: disabling cgroup2 socket matching due to net_prio or net_cls activation
[33497.728473] eth0: renamed from veth059641e
[33497.771551] IPv6: ADDRCONF(NETDEV_CHANGE): veth7f4b2c0: link becomes ready
[33497.771596] docker0: port 1(veth7f4b2c0) entered blocking state
[33497.771598] docker0: port 1(veth7f4b2c0) entered forwarding state
[33497.771642] IPv6: ADDRCONF(NETDEV_CHANGE): docker0: link becomes ready
[33498.167576] eth0: renamed from vethc3b4953
[33498.219866] eth0: renamed from vethc23f22a
[33498.235461] IPv6: ADDRCONF(NETDEV_CHANGE): veth2e8c2d7: link becomes ready
[33498.235508] br-6205584aa04f: port 2(veth2e8c2d7) entered blocking state
[33498.235510] br-6205584aa04f: port 2(veth2e8c2d7) entered forwarding state
[33498.237314] IPv6: ADDRCONF(NETDEV_CHANGE): veth5bf75fd: link becomes ready
[33498.237353] br-6205584aa04f: port 1(veth5bf75fd) entered blocking state
[33498.237364] br-6205584aa04f: port 1(veth5bf75fd) entered forwarding state
[33498.263753] eth1: renamed from vethfe9de02
[33498.283593] IPv6: ADDRCONF(NETDEV_CHANGE): veth0409411: link becomes ready
[33498.283640] br-6205584aa04f: port 3(veth0409411) entered blocking state
[33498.283642] br-6205584aa04f: port 3(veth0409411) entered forwarding state
#
```

It is working in other linux distributions - are please some configuration changes needed in Leap 15.3 ?

---

