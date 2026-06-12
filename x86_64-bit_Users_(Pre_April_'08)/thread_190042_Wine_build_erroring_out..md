---
title: "Wine build erroring out."
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hickeroar on 2006-06-05
Well, i'm about to pull my hair out.  Hopefull yall can provide a little more insight into my problem here.

I've uploaded my config.log here: [http://misc.rwven.com/config.log]("http://misc.rwven.com/config.log")
If you scroll to the bottom, it looks a little weird to me down there.

My process of Install:  

First i ran **sudo apt-get build-dep wine**
When that was done, i ran **sudo apt-get --build source wine**

At this point is goes through all sorts of stuff and eventually gets to the stuff i've pasted below.  You can see the error it gives me at the very bottom of this post.  I'm clueless at this point.  I don't really know what this error means or what i need to do to fix it (It filled up the terminal buffer, so i'm only showing you what was left...):

---------------------------------------------------
../../include/winbase.h:1845: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1846: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1847: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1848: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1849: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1850: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1852: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1853: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1854: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1855: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1856: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1858: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1859: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1860: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1861: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1862: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1863: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1864: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1866: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1867: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1868: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1869: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1870: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1871: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1873: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1874: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1875: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1876: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1877: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1878: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1879: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1880: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1882: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1883: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1885: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1886: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1887: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1889: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1890: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1891: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1892: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1893: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1895: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1896: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1897: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1898: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1899: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1900: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1901: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1902: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1904: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1905: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1907: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1908: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1909: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1911: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1912: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1914: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1915: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1917: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1918: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1919: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1921: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1922: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1923: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1924: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1925: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1926: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1928: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1929: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1930: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1931: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1933: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1934: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1935: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1936: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1937: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1938: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1939: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1940: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1942: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1943: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1944: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1945: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1946: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1948: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1949: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1950: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1951: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1952: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1953: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1955: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1956: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1957: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1958: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1959: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1960: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1961: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1962: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1963: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1964: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1965: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1966: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1967: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1968: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1969: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1970: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1972: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1973: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1975: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1976: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1977: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1978: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1979: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1980: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1981: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1982: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1983: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1984: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1985: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1986: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1987: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1988: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1989: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1990: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1991: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1992: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1993: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1994: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1995: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1996: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1997: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:1999: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2000: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2001: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2002: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2003: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2005: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2006: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2008: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2009: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2010: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2011: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2012: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2013: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2014: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2015: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2016: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2017: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2018: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2019: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2020: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2021: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2022: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2023: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2024: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2025: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2027: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2028: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2029: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2030: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2031: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2033: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2034: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2036: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2037: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2039: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2040: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2041: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2043: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2044: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2046: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2048: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2050: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2051: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2052: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2053: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2054: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2055: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2056: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2057: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2064: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2079: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2094: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2101: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2106: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2113: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2118: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2126: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2141: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2142: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2143: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2144: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2145: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2146: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2147: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2148: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2149: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2150: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2152: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2153: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2187: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2188: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2189: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2190: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2191: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2192: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2193: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2194: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2195: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2196: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2197: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2198: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2199: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2200: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2201: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2214: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2216: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2223: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2225: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2232: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2234: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2241: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2243: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2247: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2249: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2253: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2255: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2261: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2263: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2269: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2271: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2277: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2279: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2283: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2285: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2307: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2319: warning: ‘__stdcall__’ attribute ignored
../../include/winbase.h:2337: warning: ‘__stdcall__’ attribute ignored
In file included from ../../include/wine/unicode.h:28,
                 from casemap.c:4:
../../include/winnls.h:579: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:580: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:581: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:582: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:583: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:584: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:585: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:586: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:587: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:588: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:589: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:590: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:591: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:592: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:593: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:594: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:595: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:596: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:597: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:598: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:599: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:663: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:664: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:666: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:667: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:668: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:670: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:671: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:673: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:674: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:676: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:677: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:679: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:680: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:682: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:683: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:684: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:686: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:687: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:689: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:690: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:692: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:693: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:695: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:696: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:698: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:699: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:701: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:702: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:703: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:704: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:706: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:707: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:709: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:710: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:712: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:713: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:715: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:716: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:718: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:719: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:721: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:722: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:724: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:725: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:726: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:727: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:728: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:730: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:731: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:732: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:733: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:734: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:735: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:737: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:738: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:739: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:740: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:741: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:742: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:743: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:744: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:745: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:746: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:747: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:749: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:750: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:751: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:753: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:754: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:756: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:757: warning: ‘__stdcall__’ attribute ignored
../../include/winnls.h:758: warning: ‘__stdcall__’ attribute ignored
make[3]: *** [casemap.o] Error 1
make[3]: Leaving directory `/home/ryan/install/wine-0.9.14~winehq1~ubuntu~6.06/libs/unicode'
make[2]: *** [unicode] Error 2
make[2]: Leaving directory `/home/ryan/install/wine-0.9.14~winehq1~ubuntu~6.06/libs'
make[1]: *** [libs] Error 2
make[1]: Leaving directory `/home/ryan/install/wine-0.9.14~winehq1~ubuntu~6.06'
make: *** [build-stamp] Error 2
Build command 'cd wine-0.9.14~winehq1~ubuntu~6.06 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

---

### Post by Hickeroar on 2006-06-05
<subscribing to thread>

---

### Post by Kilz on 2006-06-05
[QUOTE=Hickeroar]<subscribing to thread>[/QUOTE]

[Take a look here for an easy solution.]("http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64+bit") I dont know if its possible to compile a 64 bit version of a 32 bit emulator.

---

### Post by Hickeroar on 2006-06-05
OK, i get it.  Thanks a lot for the help.  :-P

---

