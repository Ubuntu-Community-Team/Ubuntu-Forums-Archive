---
title: "dmidecode showing wrong memory size?"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by matemargo on 2009-04-26
I have a MSI K8N Neo2 Platinum motherboard which supports 4 GB of RAM.

I've recently installed 4 modules of 1 GB @ 400MHz, and Ubuntu shows me that I have 3.5 GB.

I run the dmidecode command and this is what I got in the memory device section:

```

Handle 0x001C, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x001D, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None

Handle 0x001E, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None

Handle 0x001F, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: Unknown
	Type Detail: None

Handle 0x0020, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: A3
	Bank Locator: Bank6/7
	Type: Unknown
	Type Detail: None

Handle 0x0021, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x007FFFFFFFF
	Range Size: 32 GB
	Physical Array Handle: 0x001C
	Partition Width: 0

Handle 0x0022, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x001FFFFFFFF
	Range Size: 8 GB
	Physical Device Handle: 0x001D
	Memory Array Mapped Address Handle: 0x0021
	Partition Row Position: 1

Handle 0x0023, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00200000000
	Ending Address: 0x003FFFFFFFF
	Range Size: 8 GB
	Physical Device Handle: 0x001E
	Memory Array Mapped Address Handle: 0x0021
	Partition Row Position: 1

Handle 0x0024, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00400000000
	Ending Address: 0x005FFFFFFFF
	Range Size: 8 GB
	Physical Device Handle: 0x001F
	Memory Array Mapped Address Handle: 0x0021
	Partition Row Position: 1

Handle 0x0025, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00600000000
	Ending Address: 0x007FFFFFFFF
	Range Size: 8 GB
	Physical Device Handle: 0x0020
	Memory Array Mapped Address Handle: 0x0021
	Partition Row Position: 1

```

Why it says *Size: 8192 MB*? shouldn't say 1024 MB?

I was trying to figure out if one of those modules has 512 MB instead of 1 GB avoiding to remove one by one.

---

