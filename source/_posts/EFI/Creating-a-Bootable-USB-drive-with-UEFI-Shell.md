---
title: Creating a Bootable USB drive with UEFI Shell
toc: true
date: 2019-08-28 09:28:47
tags: [EFI,UEFI,Shell,Boot]
categories: [EFI]
---



<!--more-->

1. Format your media as FAT32
2. Create the following directory structure in the root of the new media
   - /efi/boot
3. Download the UEFI Shell (Shell.efi) from the following link
   - For 64bit BIOS: https://github.com/tianocore/edk2/blob/UDK2018/ShellBinPkg/UefiShell/X64/Shell.efi
   - Others BIOS: https://github.com/tianocore/edk2/tree/UDK2018/ShellBinPkg/UefiShell
4. Rename the UEFI shell file to Bootx64.efi
   - 32bit : Bootia32.efi
5. Copy the UEFI shell (now Bootx64.efi) to the /efi/boot directory

## 参考资料

> - [Creating a Bootable USB drive with UEFI Shell](https://github.com/chipsec/chipsec/wiki/Creating-a-Bootable-USB-drive-with-UEFI-Shell)

