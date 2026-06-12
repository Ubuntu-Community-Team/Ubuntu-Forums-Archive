---
title: "Eclipse Errors."
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sykil on 2005-10-25
So, I installed Eclipse, and immediately after trying to start it, I get this error:
> An error has occured. See the log file /home/sykil/.eclipse/org.eclipse.platform_3.1.1/configuration/1130296811581.log.

So I check out said log, and it looks like jibberish to me:
> !SESSION 2005-10-25 23:20:11.386 -----------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.update.configurator 2005-10-25 23:20:16.382
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2005-10-25 23:20:16.546
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader16handleClassBeginEiii (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader5parseEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z15_Jv_DefineClassPN4java4lang5ClassEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader11defineClassEPNS0_11ClassLoaderEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader11defineClassEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod16run_synch_objectEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang12LinkageErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang20NoClassDefFoundErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader18transformExceptionEPNS0_5ClassEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class11newInstanceEv (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   ...23 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringEbPNS0_11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier8pop_typeENS_4typeE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier21verify_instructions_0Ev (/usr/lib/libgcj.so.6.0.0)
   at ._Z16_Jv_VerifyMethodP16_Jv_InterpMethod (/usr/lib/libgcj.so.6.0.0)
   at ._ZN21_Jv_InterpreterEngine9do_verifyEPN4java4lang5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN10_Jv_Linker14wait_for_stateEPN4java4lang5ClassEi (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class11newInstanceEv (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader16handleClassBeginEiii (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader5parseEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z15_Jv_DefineClassPN4java4lang5ClassEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader11defineClassEPNS0_11ClassLoaderEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader11defineClassEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
Root exception:
java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang12LinkageErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang20NoClassDefFoundErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader18transformExceptionEPNS0_5ClassEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class11newInstanceEv (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader16handleClassBeginEiii (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader5parseEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z15_Jv_DefineClassPN4java4lang5ClassEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader11defineClassEPNS0_11ClassLoaderEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader11defineClassEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod16run_synch_objectEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringEbPNS0_11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier8pop_typeENS_4typeE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier21verify_instructions_0Ev (/usr/lib/libgcj.so.6.0.0)
   at ._Z16_Jv_VerifyMethodP16_Jv_InterpMethod (/usr/lib/libgcj.so.6.0.0)
   at ._ZN21_Jv_InterpreterEngine9do_verifyEPN4java4lang5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN10_Jv_Linker14wait_for_stateEPN4java4lang5ClassEi (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class11newInstanceEv (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader16handleClassBeginEiii (/usr/lib/libgcj.so.6.0.0)
   at ._ZN15_Jv_ClassReader5parseEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z15_Jv_DefineClassPN4java4lang5ClassEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader11defineClassEPNS0_11ClassLoaderEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader11defineClassEPNS0_6StringEP6JArrayIcEiiPNS_8security16ProtectionDomainE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-25 23:20:17.217
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-25 23:20:17.780
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at ._Z18_Jv_CallAnyMethodAPN4java4lang6ObjectEPNS0_5ClassEP10_Jv_MethodbbP6JArrayIS4_EP6jvalueSB_bS4_ (/usr/lib/libgcj.so.6.0.0)
   at ._Z18_Jv_CallAnyMethodAPN4java4lang6ObjectEPNS0_5ClassEP10_Jv_MethodbP6JArrayIS4_EPS7_IS2_ES4_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang7reflect6Method6invokeEPNS0_6ObjectEP6JArrayIS4_E (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-25 23:20:18.82
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar[/email] [23] was not resolved.

So um... anyone have any idea what my problem is and how I may resolve it?

---

### Post by shadesfox on 2005-10-26
I get similar errors as well.

---

### Post by RAOF on 2005-10-26
You're using the gnu java runtime.  It sort of works, but there are a couple of things which will not run properly under it (Eclipse, as you've found out, and Azureus).

Install the Sun java runtime (howto [here]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=sun+java+package")), then try it.

---

### Post by Sykil on 2005-10-27
Well, I've done that, and I still get the same error, and still with GCJ, despite having Sun's as my default:

```

sykil@astarael:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)

```

```

!SESSION 2005-10-27 00:05:25.830 -----------------------------------------------
eclipse.buildId=
**java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)**
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.update.configurator 2005-10-27 00:05:29.871
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2005-10-27 00:05:30.131
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   ...18 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
Root exception:
java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-27 00:05:30.571
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-27 00:05:30.780
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-27 00:05:30.885
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar [23] was not resolved.

```

---

### Post by RAOF on 2005-10-27
You might want to try starting eclipse with
```
eclipse -vm /usr/java/jre1.5.0_02/bin/java
```
(Or whatever similar path is to your sun JDK).  That should start eclipse with the Sun runtime.

---

### Post by Sykil on 2005-10-27
Gah, I was sure that would work (it just seemed fool-proof), but it doesn't, either. I get an error dialog that says "The custom VM you have chosen is not a valid executable."

So, I checked out the /usr/java/jre1.5.0_02/bin/ folder, and java is there---executable and all. 

(BTW, thanks for helping me out RAOF---I don't want to sound unappreciative)

---

### Post by RAOF on 2005-10-27
Hmm.  I seem to remember people with eclipse errors...  Try searching the forum.  I don't use it (eclipse) myself, so I'm not on top of its tricks, sorry ;)

---

### Post by jvictor on 2005-11-02
I use eclipse 3.1 @ home.. I installed Sun java 1.5 JDK, because I work on J2EE and i will need the java compiler..JRE is not sufficent

Chk out this thread

[http://ubuntuforums.org/showthread.php?t=84700](http://ubuntuforums.org/showthread.php?t=84700)

---

### Post by RAOF on 2005-11-03
Gah!  Of course!  I should have noticed that.

---

### Post by Kareema on 2005-11-03
[QUOTE=jvictor]I use eclipse 3.1 @ home.. I installed Sun java 1.5 JDK, because I work on J2EE and i will need the java compiler..JRE is not sufficent

Chk out this thread

[http://ubuntuforums.org/showthread.php?t=84700](http://ubuntuforums.org/showthread.php?t=84700)[/QUOTE]

OK, I looked into the Eclipse start script (/usr/bin/eclipse) and noticed that you have to call Eclipse with "eclipse -vm /usr/lib/j2sdk1.5-sun" to use the Sun JDK. But no luck: Same error as described above with Gnu Java.

BTW: Eclipse from the Ubuntu repositories works without problems on the i386 architecture with Gnu Java!

---

### Post by jvictor on 2005-11-03
well , can u give the o/p of 
**echo $PATH** 
**echo $JAVA_HOME** 

there is a  symlink in /usr/bin/java which points to gnu java. 
have u changed that to sun java ( i ve the jdk installed I need it coz i do j2ee development)  

also u may need to edit ur .bashrc file and add these line

export JAVA_HOME=<your java home dir>
export PATH=${JAVA_HOME}/bin:${PATH}

My echo $PATH looks  like this

[I]juby@powercube:~$ echo $PATH
/home/juby/java/jdk1.5.0_05/bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games[/I]

---

### Post by Kareema on 2005-11-03
An export of JAVA_HOME and PATH does not solve the problem. After

```

$ export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
$ export PATH=${JAVA_HOME}/bin:${PATH}

```

my path is as expected:

```
$ echo $PATH
/usr/lib/j2sdk1.5-sun//bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
$ echo $JAVA_HOME
/usr/lib/j2sdk1.5-sun/

```

And /usr/bin/java is symlinked to Sun JDK:

```
$ /usr/bin/java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)
```

Starting Eclipse on the command line gives me the message:

```
$ eclipse
using specified vm: /usr/lib/j2sdk1.5-sun/
```

and an error box:

```
An error has occurred. See the log file
/home/mark/.eclipse/org.eclipse.platform_3.1.1/configuration/1131044309184.log.
```

Here's the output of the log file:

```
!SESSION 2005-11-03 19:58:29.89 ------------------------------------------------
eclipse.buildId=
java.version=1.5.0_05
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=de_DE
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.osgi 2005-11-03 19:58:33.109
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2328)
	at java.lang.Class.getConstructor0(Class.java:2640)
	at java.lang.Class.newInstance0(Class.java:321)
	at java.lang.Class.newInstance(Class.java:303)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	... 55 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2328)
	at java.lang.Class.getConstructor0(Class.java:2640)
	at java.lang.Class.newInstance0(Class.java:321)
	at java.lang.Class.newInstance(Class.java:303)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-03 19:58:33.115
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	... 27 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-03 19:58:33.118
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:405)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-03 19:58:33.133
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar [23] was not resolved.
```

So it seems it doesn't matter what JDK I use. As I said: On i386 architecture, there's no such problem!

---

### Post by baRRacuda on 2005-11-03
The best is to download Sun's jre and jdk from [http://java.sun.com](http://java.sun.com) and eclipse from [http://www.eclipse.org](http://www.eclipse.org) (the one in the repos seems to have problems). I just extracted the eclipse archive file, it works fine without any configuration...

---

### Post by Sykil on 2005-11-03
[QUOTE=baRRacuda]The best is to download Sun's jre and jdk from [http://java.sun.com](http://java.sun.com) and eclipse from [http://www.eclipse.org](http://www.eclipse.org) (the one in the repos seems to have problems). I just extracted the eclipse archive file, it works fine without any configuration...[/QUOTE]
Ah, I tried that and it worked awesomely. :) I didn't realize that Eclipse was already compiled for you.

---

### Post by jvictor on 2005-11-03
Kareema from what i can see your path is wrong...

 echo $PATH
/usr/lib/j2sdk1.5-sun**//**bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

I recommend eclipse frm eclipse.org & sun java

---

### Post by estel on 2005-11-04
Also, for some reason I had a permissions problem with both the repo and extracted version - neither chmodded it +x.

---

### Post by Kareema on 2005-11-04
[QUOTE=jvictor]Kareema from what i can see your path is wrong...

 echo $PATH
/usr/lib/j2sdk1.5-sun**//**bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

I recommend eclipse frm eclipse.org & sun java[/QUOTE]

Thanks jvictor, but that doesn't matter. The additional slash is ignored. Using the  correct path doesn't change a thing...

I will use the eclipse package from eclipse.org which works perfectly.

---

### Post by estel on 2005-11-12
I managed to get Eclipse running, and installed CDT successfully but I've hit another stumble... I can't build through it :(.

What options do I need to set eclipse up with in order that it uses make or g++ properly?

---

### Post by edross on 2005-11-12
This is the same error as I'm getting.  If you have java 1.5 installed, you could go the a command window, change to the directory and start eclipse.  Elipse would work ok (Make sure you really have java 1.5 by typing java -version)

My problems is that no matter what I put in bash.bashrc  when I use command window I have java 1.5, when I click from a gnome window it uses java 1.4

Here is how i know

I wrote a script that I execute by clicking 

cd /home/edross/eclipse
java -version >temp.txt

guess what is in temp.txt 

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

This is true even when I went through the synaptic package manager to tell it to completely remove java - didn't happen.


Anyway, lookin for a way to really uninsall the gnu java a really install java 1.5

good luck

---

### Post by UbuntuJohan on 2005-11-13
If you don't run eclipse from commmand line with the option -vm.
Eclipse will search for a java VM according to the file

[B] more /etc/eclipse/java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/sablevm
/usr/lib/fjsdk
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun[/B]

That's why it uses gcj-java even when java-version displays sun-java1.5

To override this simply create the file **~/.eclipse/eclipserc**
with a line for
[B]JAVA_HOME=/usr/lib/j2re1.5-sun
[/B]

Annother problem I've had with eclipse on ubunutu when installed with synaptic is that the directories for plugins etc.. gets rights so that only root is allowed to write to them.

Hope this helps some of you

---

### Post by Sykil on 2005-11-13
Thanks for that, UbuntuJohan!

---

### Post by arpunk on 2005-11-28
Well actually all of those can be resumed into:
```
sudo apt-get remove java-gcj-compat
```
And:
```
sudo update-alternatives --config java
```
And selecting the installed j2sdk by sun. :razz:

---

### Post by estel on 2005-12-01
I would do the first instruction, but it wants me to remove OOo2 as well :P.

Odd also, I have the Sun Java installed, but update-alternatives doesn't offer me it as an alternative. Haven't needed to complain however: Java apps are working :)

---

### Post by arpunk on 2005-12-01
[QUOTE=estel]I would do the first instruction, but it wants me to remove OOo2 as well :P.

Odd also, I have the Sun Java installed, but update-alternatives doesn't offer me it as an alternative. Haven't needed to complain however: Java apps are working :)[/QUOTE]
Hrmmz, weird, it was flawless for me and now eclipse works like charm :/

---

### Post by KevinM on 2006-02-22
I am getting the same errors.

Eclipse works fine if I chose the "Run as different user" option from System tools using root.

---

### Post by davidshere on 2007-02-15
This method worked for me, using the command

admin@raptor:~$ eclipse -vm /usr/bin/java/jdk1.5.0_07/bin/java

but it'd be nice if I didn't have to open and occupy a terminal window while I use eclipse.  Aside from using 

admin@raptor:~$ eclipse -vm /usr/bin/java/jdk1.5.0_07/bin/java &

what can I do to change the "shortcut" in the Applications menu so that is uses the correct VM?

---

### Post by alinuxfan on 2007-02-16
I have tried everything in this thread.  Maybe I messed up one or two, but does anyone have a clue why I am getting this in my log file?
using the ecplise from synaptic and tried both jdk1.5 and 1.6

```
!SESSION 2007-02-16 20:56:30.676 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.6.0_01-ea
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-02-16 20:56:33.638
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-16 20:56:33.639
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-16 20:56:33.639
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-16 20:56:33.639
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-02-16 20:56:33.933
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/adam/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/5/1/.cp/libswt-pi-gtk-3235.so: /home/adam/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/5/1/.cp/libswt-pi-gtk-3235.so: wrong ELF class: ELFCLASS64
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

```

---

### Post by Colonel Kilkenny on 2007-02-16
> **alinuxfan said:**
> I have tried everything in this thread.  Maybe I messed up one or two, but does anyone have a clue why I am getting this in my log file?
using the ecplise from synaptic and tried both jdk1.5 and 1.6

This is a known bug and fixed packages are in proposed-repo.
Insert this line to /etc/apt/sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted
```
Then
```
sudo aptitude update && sudo aptitude upgrade
```
And after the updates are installed start eclipse once with
```
eclipse -clean
```

That should do the trick

---

