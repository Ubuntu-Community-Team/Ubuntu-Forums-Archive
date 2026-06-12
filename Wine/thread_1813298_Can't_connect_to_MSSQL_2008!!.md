---
title: "Can't connect to MSSQL 2008!!"
date: 2011-07-27
forum: Wine
---

### Post by Romulo Carlos on 2011-07-27
Hi everyone.

I'm trying to use a windows third part software, and it uses a MSSQL database stored in a Windows 2008 Server. For this, I have Ubuntu 11, Wine 1.2.2 and WineTricks.

So, I installed Wine, and with Winetricks I install MDAC 2.8 SP1. Following some instructions around this forum, I have run CLICONFIG.EXE, enabled the protocol I want (TCP/IP), and configure it.

Second step is run ODBCAD32.EXE, and configure SYSTEM DSN source. I click "Add", the fill the information needed (it finds the server), and click Next. In this window, I must use SQL Server Authentication. So, I check it, leave "Connect to SQL Server..." checked and fill the username/password.

When I click Next, it freeze for a while and returns a error:
Connection Failed:
SQLState: '01000'
SQL Server Error: 19
[Microsoft][ODBC SQL Server Driver][TCP/IP Sockets]ConnectionOpen
(PreloginHandshake())
Connection Failed:
SQLState: '08001'
SQL Server Error: 19
[Microsoft][ODBC SQL Server Driver][TCP/IP Sockets]SQLServer
Requires Encryption On

So, I go back to CLICONFIG.EXE, and check the encryption option, but the error persists.

As far I read, is a hard task, Linux don't "talk" with MSSQL very well. I know. But, any way to connect to my server?

Thanks in advice.

---

### Post by Romulo Carlos on 2011-08-01
I made a progress, I think.

With Winetricks, I installed SECUR32, and the error is gone. But I still can't connect. Another error comes up: "SSL Security Error".

Running ODBCAD32 from terminal, I get 2 messages when I select my server on the field "Wich SQL Server you want to connect to?":

"fixme:netbios:NetServerEnum Stub ((null) 100 0x32bad0 -1 0x32bac8 0x32bacc 4 (null) (nil))" 

and

"fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180..." and 

Maybe these errors are affecting my SQL setup, but I don't know well about this.

Any suggestions?? Thanks.

---

### Post by Romulo Carlos on 2011-08-03
I copied a fresh new windows installation to wine virtual drive, and still don't connecting... 

Any suggestions?

---

