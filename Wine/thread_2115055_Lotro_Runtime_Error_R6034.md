---
title: "Lotro Runtime Error R6034"
date: 2013-02-11
forum: Wine
---

### Post by Nelsonomicon on 2013-02-11
Hey all. Trying to get lotro to run under Wine 1.3.28 with launcher version 0.1.15. The launcher says that Visual C++ is installed. I'm also noob so maybe this belongs in beginners forum (also, first thread here)? Just looking for some quick terminal lines or a link to a how-to to fix the issues below. I really have searched a lot and found many similar posts, here and elsewhere, but none have done the trick for me.

This is what I get from the Wine output after hitting login on the launcher:

err:module:find_forwarded_export module not found for forward 'msvcr90._encode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._encoded_null' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._decode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90.__clean_type_info_names_internal' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._encode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._decode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._encoded_null' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90.__clean_type_info_names_internal' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._invalid_parameter_noinfo' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._invalid_parameter_noinfo' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._decode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._encode_pointer' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90.__sys_nerr' used by L"C:\\windows\\system32\\msvcr80.dll"

err:module:find_forwarded_export module not found for forward 'msvcr90._stat64i32' used by L"C:\\windows\\system32\\msvcr80.dll"
wine: Call from 0x7bc49e20 to unimplemented function MSVCR80.dll._encode_pointer, aborting
err:module:attach_process_dlls "lua51.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Turbine\\The Lord of the Rings Online\\lotroclient.exe" failed, status 80000100

*** Finished ***

Any help would be greatly appreciated.

---

