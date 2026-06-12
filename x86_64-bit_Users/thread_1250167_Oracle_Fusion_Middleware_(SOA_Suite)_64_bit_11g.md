---
title: "Oracle Fusion Middleware (SOA Suite) 64 bit 11g"
date: 2009-08-26
forum: x86 64-bit Users
---

### Post by LoermansA on 2009-08-26
Hi

Is there anybody here running Oracle's 64 bit Fusion Middleware stack with SOA Suite components on Ubuntu 64 bit Linux?

Installation was straightforward enough, but upon starting the stack I run into a problem which I cannot solve;

I start the SOA domain with:
```
$ startManagedWebLogic.sh soa_server1
```
During startup, it asks for the admin username password which I give. But then it fails to start giving:

```
<Aug 26, 2009 1:09:42 PM CEST> <Critical> <WebLogicServer> <BEA-000386> <Server subsystem failed. Reason: weblogic.security.SecurityInitializationException: Authentication for user weblogic denied
weblogic.security.SecurityInitializationException: Authentication for user weblogic denied
        at weblogic.security.service.CommonSecurityServiceManagerDelegateImpl.doBootAuthorization(CommonSecurityServiceManagerDelegateImpl.java:965)
        at weblogic.security.service.CommonSecurityServiceManagerDelegateImpl.initialize(CommonSecurityServiceManagerDelegateImpl.java:1050)
        at weblogic.security.service.SecurityServiceManager.initialize(SecurityServiceManager.java:875)
        at weblogic.security.SecurityService.start(SecurityService.java:141)
        at weblogic.t3.srvr.SubsystemRequest.run(SubsystemRequest.java:64)
        Truncated. see log file for complete stacktrace
javax.security.auth.login.FailedLoginException: [Security:090303]Authentication Failed: User weblogic weblogic.security.providers.authentication.LDAPAtnDelegateException: [Security:090295]caught unexpected exception
        at weblogic.security.providers.authentication.LDAPAtnLoginModuleImpl.login(LDAPAtnLoginModuleImpl.java:243)
        at com.bea.common.security.internal.service.LoginModuleWrapper$1.run(LoginModuleWrapper.java:110)
        at java.security.AccessController.doPrivileged(Native Method)
        at com.bea.common.security.internal.service.LoginModuleWrapper.login(LoginModuleWrapper.java:106)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        Truncated. see log file for complete stacktrace
>
```

I'm 100% sure I have the correct username and password. Reinstalled everything, no help.

Is there some underlying OS problem with Ubuntu and this SOA Suite release? I know it is an unsupported platform, but I'd like to know why it fails.

I'm running Jaunty, 64 bit.

Regards,

Arjan

---

### Post by LoermansA on 2009-08-30
Even though I've never really figured out what the problem was, I've tried a fresh install and now it's working.

Arjan

---

### Post by woloda on 2009-10-09
were there any issues found by you while installing Oracle SOA 11g on Ubuntu Jaunty...?? I am going to try do the same, 

One question: title of this thread is "Oracle Fusion Middleware (SOA Suite) 64 bit 11g, but at [http://www.oracle.com/technology/software/products/middleware/htdocs/111110_fmw.html](http://www.oracle.com/technology/software/products/middleware/htdocs/111110_fmw.html), where one can download soa suite, only few components are exactly 64 bit, and SOA suite is generic...so did you download your soa suite from other site? or you mean only that you have installed it at 64 bit Ubuntu operating system?

anyway my coulege has already installed soa on CentOS.5.3 and without any issues...

---

