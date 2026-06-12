---
title: "OpenMPI and Infiniband on Ubuntu 8.04 Cluster"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by tanner_smash on 2008-08-21
I have a 16-node AMD64 cluster with Mellanox Infiniband cards running Ubuntu 8.04 Server on all nodes. I installed OpenMPI via apt-get on all nodes:

```
apt-get install libopenmpi-dev libopenmpi1 openmpi-bin openmpi-common openmpi-doc
```

Additionally, I installed Infiniband on all nodes via Roland Dreier's repository:

```
deb http://ppa.launchpad.net/roland.dreier/ubuntu/ hardy main
deb-src http://ppa.launchpad.net/roland.dreier/ubuntu/ hardy main
```

```
apt-get install libipathverbs1 libcxgb3-1 librdmacm1 libibverbs1 libmthca1 libmlx4-1
```

Per the OpenMPI documentation, Infiniband is activated by default (which is good). However, OpenMPI can't seem to find the HCA's despite a seemingly successful install of the Infiniband packages. I get the following error for each node upon executing mpirun...

```
--------------------------------------------------------------------------
[0,1,0]: OpenIB on host master was unable to find any HCAs.
Another transport will be used instead, although this may result in 
lower performance.
--------------------------------------------------------------------------
```

Does anyone know if Roland's Infiniband packages work or, alternatively, how to redirect OpenMPI to see the proper Infiniband files? Thanks!

---

### Post by scho on 2009-07-13
By any chance, have you solved the issue yet ? I think I've got same issue now...

---

