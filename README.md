## Galaxy Buds FOTA Analysis

An analysis of the FOTA files for Samsung Galaxy Buds/Buds+ (e.g. FOTA_R175XXU0ATH7.bin).

## General

No data inside the file, as far as known, encrypted or somehow else unreadable.

All data inside the FOTA file is little-endian, so the least significant byte comes first (e.g. 0xCAFECAFE is stored as 0xFA 0xCE 0xFA 0xCE).

### Range `0x0 to 0x3` (4 bytes): 0xCAFECAFE

Every FOTA file begins with the magic number `0xCAFECAFE` (`0xFE 0xCA 0xFE 0xCA`) which also appears multiple times inside the binary file.

### Range `0x4 to 0x7` (4 bytes): File size

A 32-bit integer that contains the update file size.

### Range `0x8 to 0xF` (8 bytes): Constant

In every file, this is filled with `0x07 0x00 0x00 0x00  0x01 0x00 0x00 0x00 `

### Range `0x10 to 0x81` (114 bytes): Unknown yet

To be further analyzed. However, there are clearly noticable patterns. Probably checksums and/or offset ranges.

### Range `0x82 to 0x8B`: Constant

In every file, this is filled with `0x02 0x00  0x00 0x04 0x20 0x00  0x00 0x00 0x00 0x00`.

### Range `0x8C to (end-0x5)`:

Contains program data, mp3 file data as well as strings.

### Range `(end-0x4) to end` (4 bytes):

Different every time. Probably a checksum. To be further analyzed.
