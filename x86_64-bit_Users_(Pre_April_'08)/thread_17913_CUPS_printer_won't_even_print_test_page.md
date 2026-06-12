---
title: "CUPS printer won't even print test page"
date: 2005-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by downtime on 2005-03-03
I'm not sure if this is the correct forum for this, but I am using Ubuntu AMB64.

I have a HP PSC 2355 printer/scanner. I'm using CUPS + hpoj + hpijs and the ptal backend in CUPS. I'm able to scan just fine with xsane, but I can't even get a test page to print. This is the first trouble I've ever had with this printer. When I try to print a test page, it shows in the queue, sits there for a few seconds (like it's being spooled) then disappears. Through all of this, the printer never even wakes up. To make sure it wasn't the printer, I hooked it up to my laptop running FC3, set it up, and it worked perfectly.

I can provide other information as necessary. I really need to get this to work. Any help is appreciated.

---

### Post by kleeman on 2005-03-03
Do you have this file: /var/log/cups/error_log

If so show the last 20 lines or so...

---

### Post by Kamco on 2005-03-04
I'm having a similar problem. I'm trying to print a test page to a Canon BJC-240 on the parallel port but nothing happens. The print icon will just stay there forever but the printer never seems to get a page to print.

Ken

---

### Post by downtime on 2005-03-05
[QUOTE=kleeman]Do you have this file: /var/log/cups/error_log

If so show the last 20 lines or so...[/QUOTE]

here's the whole thing.

# cat /var/log/cups/error_log
I [05/Mar/2005:02:02:00 -0600] Listening to 7f000001:631
I [05/Mar/2005:02:02:00 -0600] Loaded configuration file "/etc/cups/cupsd.conf"
I [05/Mar/2005:02:02:00 -0600] Configured for up to 100 clients.
I [05/Mar/2005:02:02:00 -0600] Allowing up to 100 client connections per host.
I [05/Mar/2005:02:02:00 -0600] Full reload is required.
I [05/Mar/2005:02:02:00 -0600] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [05/Mar/2005:02:02:00 -0600] LoadPPDs: No new or changed PPDs...
I [05/Mar/2005:02:02:00 -0600] Full reload complete.
I [05/Mar/2005:11:28:42 -0600] Adding start banner page "none" to job 31.
I [05/Mar/2005:11:28:42 -0600] Adding end banner page "none" to job 31.
I [05/Mar/2005:11:28:42 -0600] Job 31 queued on 'PSC-2350' by 'downtime'.
I [05/Mar/2005:11:28:42 -0600] Started filter /usr/lib/cups/filter/pstops (PID 18104) for job 31.
I [05/Mar/2005:11:28:42 -0600] Started filter /usr/lib/cups/filter/foomatic-rip (PID 18105) for job 31.
I [05/Mar/2005:11:28:42 -0600] Started backend /usr/lib/cups/backend/ptal (PID 18106) for job 31.
E [05/Mar/2005:11:28:42 -0600] PID 18105 stopped with status 3!
I [05/Mar/2005:11:28:42 -0600] Hint: Try setting the LogLevel to "debug" to find out more.

---

### Post by downtime on 2005-03-05
and so now it works.

installed foomatic-db-hpijs and apparently hpijs *wasn't* installed.

thanks for you help.

---

### Post by kleeman on 2005-03-05
Good one. BTW to increase the loglevel so you can get more informative messages in the logfile mentioned follow this guide; (see troubleshooting section)
[http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch05s05.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch05s05.html)

---

### Post by miketyson on 2005-03-10
Hi!

I'm having the same troubles with my newly-upgraded Hoary.. I hit print, it goes into the queue, reports it's printing, then disappears without anything happening..

Anyone know where to go from here?

Here's my cups log:

D [11/Mar/2005:10:34:27 +1100] ReadClient: 4 POST / HTTP/1.1
D [11/Mar/2005:10:34:27 +1100] ProcessIPPRequest: 4 status_code=0
D [11/Mar/2005:10:34:28 +1100] AcceptClient: 6 from localhost:631.
D [11/Mar/2005:10:34:28 +1100] ReadClient: 6 POST /printers/DeskJet-656C HTTP/1.1
D [11/Mar/2005:10:34:28 +1100] print_job: auto-typing file...
D [11/Mar/2005:10:34:28 +1100] print_job: request file type is application/postscript.
D [11/Mar/2005:10:34:28 +1100] check_quotas: requesting-user-name = 'kat'
D [11/Mar/2005:10:34:28 +1100] print_job: requesting-user-name = 'kat'
D [11/Mar/2005:10:34:28 +1100] Adding default job-sheets values "none,none"...
I [11/Mar/2005:10:34:28 +1100] Adding start banner page "none" to job 123.
I [11/Mar/2005:10:34:28 +1100] Adding end banner page "none" to job 123.
I [11/Mar/2005:10:34:28 +1100] Job 123 queued on 'DeskJet-656C' by 'kat'.
D [11/Mar/2005:10:34:28 +1100] Job 123 hold_until = 0
D [11/Mar/2005:10:34:28 +1100] StartJob(123, 0x80969d0)
D [11/Mar/2005:10:34:28 +1100] StartJob() id = 123, file = 0/1
D [11/Mar/2005:10:34:28 +1100] job-sheets=none,none
D [11/Mar/2005:10:34:28 +1100] banner_page = 0
D [11/Mar/2005:10:34:28 +1100] StartJob: argv = "DeskJet-656C","123","kat","Test Page","1","","/var/spool/cups/d00123-001"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[2]="USER=root"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[3]="CHARSET=iso-8859-15"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[4]="LANG=en"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[5]="TZ=Australia/Melbourne"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-656C.ppd"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[11]="DEVICE_URI=usb://3745?serial=TH48K120F9040Q"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[12]="PRINTER=DeskJet-656C"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"D [11/Mar/2005:10:34:28 +1100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [11/Mar/2005:10:34:28 +1100] StartJob: envp[16]="IPP_PORT=631"
D [11/Mar/2005:10:34:28 +1100] StartJob: statusfds = [ 7 8 ]
D [11/Mar/2005:10:34:28 +1100] StartJob: filterfds[1] = [ 9 -1 ]
D [11/Mar/2005:10:34:28 +1100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [11/Mar/2005:10:34:28 +1100] StartJob: filterfds[0] = [ 10 11 ]
D [11/Mar/2005:10:34:28 +1100] start_process("/usr/lib/cups/filter/pstops", 0xbffefe00, 0xbffef170, 9, 11, 8)
I [11/Mar/2005:10:34:28 +1100] Started filter /usr/lib/cups/filter/pstops (PID 4977) for job 123.
D [11/Mar/2005:10:34:28 +1100] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [11/Mar/2005:10:34:28 +1100] StartJob: filterfds[1] = [ 9 12 ]
D [11/Mar/2005:10:34:28 +1100] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbffefe00, 0xbffef170, 10, 12, 8)
I [11/Mar/2005:10:34:28 +1100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4978) for job 123.
D [11/Mar/2005:10:34:28 +1100] StartJob: backend = "/usr/lib/cups/backend/usb"
D [11/Mar/2005:10:34:28 +1100] StartJob: filterfds[0] = [ -1 10 ]
D [11/Mar/2005:10:34:28 +1100] start_process("/usr/lib/cups/backend/usb", 0xbffefe00, 0xbffef170, 9, 10, 8)
I [11/Mar/2005:10:34:28 +1100] Started backend /usr/lib/cups/backend/usb (PID 4979) for job 123.
D [11/Mar/2005:10:34:28 +1100] ProcessIPPRequest: 6 status_code=0
D [11/Mar/2005:10:34:28 +1100] [Job 123] Page = 595x842; 10,48 to 585,833
D [11/Mar/2005:10:34:28 +1100] [Job 123] slowcollate=0, slowduplex=0, sloworder=0
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%Title: PPR Test Page
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%Pages: 1
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%DocumentNeededResources: font Helvetica
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%EndComments
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%BeginProlog
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%EndProlog
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%BeginSetup
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%IncludeResource: font Helvetica
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%IncludeFeature: *PageSize A4
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%EndSetup
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%Page: 1 1
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%Page: 1 1
D [11/Mar/2005:10:34:28 +1100] [Job 123] pw = 575.6, pl = 784.8
D [11/Mar/2005:10:34:28 +1100] [Job 123] PageLeft = 9.7, PageRight = 585.3
D [11/Mar/2005:10:34:28 +1100] [Job 123] PageTop = 833.0, PageBottom = 48.2
D [11/Mar/2005:10:34:28 +1100] [Job 123] PageWidth = 595.0, PageLength = 842.0
D [11/Mar/2005:10:34:28 +1100] [Job 123] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%Title: Ubuntu final logo
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%Creator: FreeHand 10.0
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%CreationDate: 15/9/04 11:16 am
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%BoundingBox: 0 0 350 81
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%FHPageNum:1
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%ColorUsage: Color
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%DocumentProcessColors: Black
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (PANTONE 151 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (PANTONE 1235 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (PANTONE 179 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (0r 43g 61b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (244r 72g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (251r 139g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ (212r 0g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%EndComments
D [11/Mar/2005:10:34:28 +1100] [Job 123] 1 %%BeginFont: Times-Roman
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Setting locale failed.
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Please check that your locale settings:
D [11/Mar/2005:10:34:28 +1100] [Job 123] LANGUAGE = (unset),
D [11/Mar/2005:10:34:28 +1100] [Job 123] LC_ALL = (unset),
D [11/Mar/2005:10:34:28 +1100] [Job 123] LANG = "en"
D [11/Mar/2005:10:34:28 +1100] [Job 123] are supported and installed on your system.
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Falling back to the standard locale ("C").
D [11/Mar/2005:10:34:28 +1100] [Job 123] Printer using device file "/dev/usb/lp0"...
D [11/Mar/2005:10:34:28 +1100] [Job 123] LPGETSTATUS returned a port status of 18...
D [11/Mar/2005:10:34:28 +1100] [Job 123] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [11/Mar/2005:10:34:28 +1100] [Job 123] Parsing PPD file ...
D [11/Mar/2005:10:34:28 +1100] [Job 123] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option ColorSpace
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option Resolution
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option PageSize
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option PageRegion
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option Model
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option PrintoutMode
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option ImageableArea
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option PaperDimension
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option Quality
D [11/Mar/2005:10:34:28 +1100] [Job 123] Added option Font
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] Parameter Summary
D [11/Mar/2005:10:34:28 +1100] [Job 123] -----------------
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] Spooler: cups
D [11/Mar/2005:10:34:28 +1100] [Job 123] Printer: DeskJet-656C
D [11/Mar/2005:10:34:28 +1100] [Job 123] PPD file: /etc/cups/ppd/DeskJet-656C.ppd
D [11/Mar/2005:10:34:28 +1100] [Job 123] Printer model: HP DeskJet 656C Foomatic/hpijs (recommended)
D [11/Mar/2005:10:34:28 +1100] [Job 123] Job title: Test Page
D [11/Mar/2005:10:34:28 +1100] [Job 123] File(s) to be printed:
D [11/Mar/2005:10:34:28 +1100] [Job 123] <STDIN>
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] ================================================
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] File: <STDIN>
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] ================================================
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] Reading PostScript input ...
D [11/Mar/2005:10:34:28 +1100] [Job 123] --> This document is DSC-conforming!
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] -----------
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%BeginProlog
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%EndProlog
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] -----------
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%BeginSetup
D [11/Mar/2005:10:34:28 +1100] [Job 123] Inserting PostScript code for CUPS' page accounting
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%BeginFeature: *PrintoutMode Normal
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: PrintoutMode=Normal --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: PrintoutMode=Normal --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%BeginFeature: *Quality FromPrintoutMode
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: Quality=FromPrintoutMode --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: Quality=FromPrintoutMode --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%BeginFeature: *PageSize A4
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: PageSize=A4 --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [11/Mar/2005:10:34:28 +1100] [Job 123] Option: PageSize=A4 --> Setting option
D [11/Mar/2005:10:34:28 +1100] [Job 123] Found: %%EndSetup
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] -----------
D [11/Mar/2005:10:34:28 +1100] [Job 123] New page:  1 1
D [11/Mar/2005:10:34:28 +1100] [Job 123] Inserting option code into "PageSetup" section.
D [11/Mar/2005:10:34:28 +1100] [Job 123] No page header or page header not DSC-conforming
D [11/Mar/2005:10:34:28 +1100] [Job 123] Stopping search for page header optionsD [11/Mar/2005:10:34:28 +1100] [Job 123] Found:
D [11/Mar/2005:10:34:28 +1100] [Job 123] 66BA0F2FBD4C92D25121A2647E8081BF05241DF408C9CE4EED2A630C3018869E51E7F90C030031A6E8FEE178DF9A598A4F1D8CA4C7741AA2C40081C0D48C29A8B4B60A0FE5D7BA4DD1F7CC51282CEF697AC70713546B0933B65246AAAC6A881DFB16
D [11/Mar/2005:10:34:28 +1100] [Job 123] --> Output goes directly to the renderer now.
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] Starting renderer
D [11/Mar/2005:10:34:28 +1100] [Job 123] JCL: <job data>
D [11/Mar/2005:10:34:28 +1100] [Job 123]
D [11/Mar/2005:10:34:28 +1100] [Job 123] renderer PID kid4=4981
D [11/Mar/2005:10:34:28 +1100] [Job 123] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="DESKJET 656" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1 -dIjsUseOutputFD -sOutputFile=- -
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Setting locale failed.
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Please check that your locale settings:
D [11/Mar/2005:10:34:28 +1100] [Job 123] LANGUAGE = (unset),
D [11/Mar/2005:10:34:28 +1100] [Job 123] LC_ALL = (unset),
D [11/Mar/2005:10:34:28 +1100] [Job 123] LANG = "en"
D [11/Mar/2005:10:34:28 +1100] [Job 123] are supported and installed on your system.
D [11/Mar/2005:10:34:28 +1100] [Job 123] perl: warning: Falling back to the standard locale ("C").
D [11/Mar/2005:10:34:28 +1100] [Job 123] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=DESKJET 656' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=1' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%EndFont
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%BeginResource: procset Altsys_header 4 0
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%EndResource
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%EndProlog
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%BeginSetup
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%IncludeResource: font Times-Roman
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%EndSetup
D [11/Mar/2005:10:34:29 +1100] [Job 123] Found: %%EndProlog
D [11/Mar/2005:10:34:29 +1100] [Job 123]
D [11/Mar/2005:10:34:29 +1100] [Job 123] -----------
D [11/Mar/2005:10:34:29 +1100] [Job 123] Found: %%BeginSetup
D [11/Mar/2005:10:34:29 +1100] [Job 123] "%%BeginSetup" in page header
D [11/Mar/2005:10:34:29 +1100] [Job 123] Found: %%EndSetup
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%Trailer
D [11/Mar/2005:10:34:29 +1100] [Job 123] 1 %%EndDocument
D [11/Mar/2005:10:34:29 +1100] [Job 123] 0 %%Trailer
D [11/Mar/2005:10:34:29 +1100] [Job 123] Saw Trailer!
D [11/Mar/2005:10:34:29 +1100] [Job 123] Saw EOF!
D [11/Mar/2005:10:34:29 +1100] [Job 123]
D [11/Mar/2005:10:34:29 +1100] [Job 123] Closing renderer
D [11/Mar/2005:10:34:30 +1100] ReadClient: 4 POST / HTTP/1.1
D [11/Mar/2005:10:34:30 +1100] ProcessIPPRequest: 4 status_code=0
D [11/Mar/2005:10:34:30 +1100] ReadClient: 4 POST / HTTP/1.1
D [11/Mar/2005:10:34:30 +1100] ProcessIPPRequest: 4 status_code=1
D [11/Mar/2005:10:34:31 +1100] ReadClient: 5 POST / HTTP/1.1
D [11/Mar/2005:10:34:31 +1100] ProcessIPPRequest: 5 status_code=0
D [11/Mar/2005:10:34:31 +1100] ReadClient: 5 POST / HTTP/1.1
D [11/Mar/2005:10:34:31 +1100] ProcessIPPRequest: 5 status_code=1
D [11/Mar/2005:10:34:32 +1100] [Job 123] KID3 exited with status 0
D [11/Mar/2005:10:34:32 +1100] [Job 123] tail process done writing data to STDOUT
D [11/Mar/2005:10:34:32 +1100] [Job 123] KID4 finished
D [11/Mar/2005:10:34:32 +1100] [Job 123] KID4 exited with status 0
D [11/Mar/2005:10:34:32 +1100] [Job 123] Renderer exit stat: 0
D [11/Mar/2005:10:34:32 +1100] [Job 123] KID3 finished
D [11/Mar/2005:10:34:32 +1100] [Job 123] Renderer process finished
D [11/Mar/2005:10:34:32 +1100] [Job 123]
D [11/Mar/2005:10:34:32 +1100] [Job 123] Closing foomatic-rip.
D [11/Mar/2005:10:34:32 +1100] UpdateJob: job 123, file 0 is complete.
D [11/Mar/2005:10:34:32 +1100] CancelJob: id = 123
D [11/Mar/2005:10:34:32 +1100] StopJob: id = 123, force = 0
D [11/Mar/2005:10:34:32 +1100] StopJob: printer state is 3

---

### Post by downtime on 2005-03-11
this may not be much help, but be sure you have foomatic-db-hpijs installed. just do 'sudo dpkg -l|grep foo' and you should see it listed.

installing that and hpijs (which i thought was already installed) got mine working.

---

### Post by bihe on 2005-03-15
there you go, it exactly looks like my log-file - same behaviour  :-? 
i've filed a bug at bugzilla.ubuntu.com
[bugzilla bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7579) 

[QUOTE=miketyson]Hi!

I'm having the same troubles with my newly-upgraded Hoary.. I hit print, it goes into the queue, reports it's printing, then disappears without anything happening..

Anyone know where to go from here?

Here's my cups log:

....
D [11/Mar/2005:10:34:27 +1100] ReadClient: 4 POST / HTTP/1.1
D [11/Mar/2005:10:34:27 +1100] ProcessIPPRequest: 4 status_code=0
....
[/QUOTE]

---

