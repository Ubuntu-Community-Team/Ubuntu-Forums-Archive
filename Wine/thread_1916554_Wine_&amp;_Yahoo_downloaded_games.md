---
title: "Wine &amp; Yahoo downloaded games"
date: 2012-01-28
forum: Wine
---

### Post by sunfromhere on 2012-01-28
The issue here are Yahoo downloaded games - you download a free trial (from Yahoo games), which opens in a small window which says: Buy/register or play demo. As it happens, a couple of years ago, still running a Windows machine, I bought several of those games. 

So - I run the installer, the game installs. But, when starting the game I just get a white window with this:

```
<html>
<head>
<title>Yahoo! Games</title>
<script language="JavaScript" src="am_include.js" type="text/javascript"></script>
<script language="JavaScript" src="author.js" type="text/javascript"></script>
<script language="JavaScript" src="author531.js" type="text/javascript"></script>
<script language="JavaScript" src="language.js" type="text/javascript"></script>
<script language=javascript>
function CheckConnection(typeSubmittion) {
var url = "http://get.games.yahoo.com/download/handlerTryMedia?lproc=conncheck";
if (typeof(window.external.activemark_checkconnection) != "undefined" )
    {
      
     if( window.external.activemark_checkconnection(url) == true )
     {
        if ( typeSubmittion == "buy" ) document.buyform.submit();
        if ( typeSubmittion == "relicense" ) document.relicenseform.submit();
     }
     else
     {
    if ( typeSubmittion == "buy" ) document.buyform.action=AM_Compose_URL('naverror.html');
    if ( typeSubmittion == "relicense" ) document.relicenseform.action=AM_Compose_URL('naverror.html');
     }
   }
   return true;
}                                 
</script>
<STYLE type="text/css">
 <!--
 .submitbutton { border: 0; background-color: #F4F7FC; text-decoration : underline; font-size:-1; font-weight: bold; cursor
: hand; color : #06407B; face : arial; width : 150;}
 //-->
</STYLE>

</head>
<body marginheight=0 marginwidth=0 topmargin=0 leftmargin=0 bgcolor="4E74B3">
<center>
  <table width="663" border="0" cellspacing="0" cellpadding="0">
    <tr> 
      <td colspan="3"><img src="topbar1.gif" width="663" height="63"></td>
    </tr>
    <tr> 
      <td valign="top" width="24" background="left1.gif"><img src="left1.gif" width="24" height="275"></td>
      <td bgcolor="F4F7FC" width="620" valign="top"> 
        <table width="98%" border="0" cellspacing="0" cellpadding="8" align="center">
          <tr> 
            <td width="150" valign="top" align=center>
        <img height=150 src="chickeninvaders2_logo.jpg" width=150 border=0><br>
              <br>
              <table width="100%" border="0" cellspacing="0" cellpadding="6" align="center">
                <tr align="center"> 
          <form action="#" method="post" name="relicenseform" onSubmit="return CheckConnection('relicense')">
                            <script language=javascript>
                             AM_Init_Relicense(document.relicenseform);
                            </script>
                            <td width=150>
                <font face="arial" size="-1" color="06407B">Already Bought 
                            <br>
                            the Game?<b><br></b></font>
                            <input type="submit"name="relicense" value="Renew your License" class="submitbutton" id="heresub">
                            </td>
                        </form>
                </tr>
              </table>
              
            </td>
            <td width="83%"> 
              <table width="100%" border="0" cellspacing="0" cellpadding="3">
                <
```
This should be the window which gives me the options to enter my information so the game can be registered.
"Locate java" gives a long list of java named things, so I'm guessing it's installed.

Googling gives results only on Yahoo games that you play in a browser, and mostly it's about installing java.

I'd appreciate any help here.

---

### Post by sunfromhere on 2012-01-29
These are the errors displayed when trying to run gamelauncher.exe from terminal:

```

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:ieframe:PersistStreamInit_InitNew (0x1707a0)
fixme:ieframe:OleObject_Advise (0x1707a0)->(0xc46030, 0xc4607c)
fixme:ieframe:ViewObject_SetAdvise (0x1707a0)->(1 00000000 0xc46030)
fixme:ieframe:ViewObject_Draw (0x1707a0)->(1 -1 (nil) (nil) (nil) 0x61c 0xc46094 0xc46094 (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:iphlpapi:NotifyAddrChange (Handle 0x360e91c, overlapped 0x360e900): stub
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x170850)->((null) 1 0x33ba54 (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ieframe:ClientSite_GetContainer (0x170850)->(0x33ba64)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClientSite_GetContainer (0x170850)->(0x33c8d4)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:navigate_url Unsupported args (Flags 0x33e7e8:22; TargetFrameName 0x33e7f8:0)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x170850)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:win:EnumDisplayDevicesW ((null),0,0x33db50,0x00000000), stub!
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:ieframe:DocObjectService_FireDocumentComplete 0x37abf48 0x37ab4e0 0
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x43067b0)->()
fixme:ieframe:ClientSite_GetContainer (0x170850)->(0x33e0cc)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsChannel_IsNoCacheResponse (0x43067b0)->(0x33c960)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x170850)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:DocObjectService_FireDocumentComplete 0x37abf48 0x37ab4e0 0
fixme:mshtml:nsChannel_IsNoCacheResponse (0x43067b0)->(0x33df24)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x175920)->(0x33f45c)
fixme:ieframe:ViewObject_SetAdvise (0x1707a0)->(1 00000000 (nil))
fixme:ieframe:OleObject_Unadvise (0x1707a0)->(0)
fixme:ieframe:ControlSite_OnFocus (0x170850)->(0)
fixme:ieframe:InPlaceSite_OnInPlaceDeactivateEx fNoRedraw (1) ignored
fixme:mshtml:HlinkTarget_SetBrowseContext (0x175920)->((nil))
fixme:ras:RasEnumConnectionsA (0x630607a8,0x33fcd0,0x6305f610),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!


```

---

### Post by sunfromhere on 2012-02-23
Some time has passed, perhaps anyone has any ideas?

---

