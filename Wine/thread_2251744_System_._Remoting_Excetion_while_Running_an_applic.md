---
title: "System . Remoting Excetion while Running an application using Wine"
date: 2014-11-06
forum: Wine
---

### Post by suryamohan2 on 2014-11-06
System.Runtime.Remoting.RemotingException: Configuration file 'C:\Program Files\Kareo\Client\Kareo.Superbill.Windows.KareoBase.exe.config' could not be loaded: An exception was thrown by the type initializer for Belikov.GenuineChannels.DotNetRemotingLayer.GenuineUniversalServerTransportSink ---> System.TypeInitializationException: An exception was thrown by the type initializer for Belikov.GenuineChannels.DotNetRemotingLayer.GenuineUniversalServerTransportSink ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Belikov.GenuineChannels.DotNetRemotingLayer.GenuineUniversalServerTransportSink..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Belikov.GenuineChannels.DotNetRemotingLayer.BasicChannelWithSecurity.InitializeInstance (IDictionary properties) [0x00000] in <filename unknown>:0 
  at Belikov.GenuineChannels.GenuineTcp.GenuineTcpChannel..ctor (IDictionary properties, IClientChannelSinkProvider iClientChannelSinkProvider, IServerChannelSinkProvider iServerChannelSinkProvider) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Runtime.Remoting.RemotingConfiguration.ReadConfigFile (System.String filename) [0x00000] in <filename unknown>:0 
  at System.Runtime.Remoting.RemotingConfiguration.Configure (System.String filename, Boolean ensureSecurity) [0x00000] in <filename unknown>:0 
  at System.Runtime.Remoting.RemotingConfiguration.Configure (System.String filename) [0x00000] in <filename unknown>:0 
  at Kareo.Superbill.BrokerServer.Facade.RemoteBrokerFactory..ctor (System.String host, System.String configurationFileName) [0x00000] in <filename unknown>:0 
  at Kareo.Superbill.Windows.KareoBase.KareoAppController.Main () [0x00000] in <filename unknown>:0

---

