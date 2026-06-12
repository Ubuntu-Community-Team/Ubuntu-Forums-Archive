---
title: "synaptic not working under proxy"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by srinivas45 on 2009-04-30
i have just installed jaunty.i have to access net through a proxy so i changed the settings in network proxy, clicked apply system wide.i hav also changed the settings in spm preferences , added it /etc/apt/apt.conf

but when i try to update u[pdate manager tells that it cannot resolve the proxy.
so i cant download any plugins and ubuntu is useless.please help me.

---

### Post by sahabcse on 2009-04-30
Hi

Add the following lines to /etc/apt/apt.conf (might be empty) 

ACQUIRE {
http::proxy &#8220;[http://172.16.1.71:8080/&#8221;](http://172.16.1.71:8080/&#8221;)
}

If you need to authenticate use

ACQUIRE {
http::proxy &#8220;[http://DOMAIN\username:Password@FQDN.or.IP:8080/&#8221;](http://DOMAIN\username:Password@FQDN.or.IP:8080/&#8221;)
}

For more infor pls click [here]("http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html")

---

### Post by srinivas45 on 2009-04-30
i am getting this error even after following what was explained in that blog
     ** 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill    the request. Access to the Web Proxy filter is denied.  )**
i hav '@' in my password does that have to do anthing with this problem

---

### Post by dcstar on 2009-05-01
> **srinivas45 said:**
> i am getting this error even after following what was explained in that blog
     ** 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill    the request. Access to the Web Proxy filter is denied.  )**
i hav '@' in my password does that have to do anthing with this problem

**You** have to put in whatever **your** proxy requires.

---

### Post by srinivas45 on 2009-05-01
update manager shows that there are some updates available but when i click on update it gives me 407 error for everything.i have modified apt.conf as told.even pidgin doesnot not work under proxy(gives the same error).pls help me out

---

### Post by srinivas45 on 2009-05-02
this what i wrote in apt.conf file.
Acquire {
http:proxy "http://mucampus\080905014:block6@mit@10.49.0.13:8080/";
}
is this correct?
it is still not working .plz guys help me out

---

### Post by sahabcse on 2009-05-02
check you entry It seems to be some error there, follow this url this may be help

[http://www.go2linux.org/debian-ubuntu-package-proxy-server](http://www.go2linux.org/debian-ubuntu-package-proxy-server)

---

