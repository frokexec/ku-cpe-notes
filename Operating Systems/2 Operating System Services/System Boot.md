## System Boot

- Small pieces of code - bootstrap loader, BIOS, stored in ROM or EEPROM locates the kernel, loads it into memory, and start it
- Sometimes two-step process where boot block at fixed location loaded by ROM coded, which loads bootstrap loader from disk
- Modern systems use UEFI instead of BIOS