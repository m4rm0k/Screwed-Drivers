ScrewedDrivers
======

### General information
We have created this repository as a centralized source of knowledge which contains a list of drivers determined to be vulnerable as well as example code for how to use this kind of functionality.

***
### Known files.xlsx 
This file contains a list of drivers, hashes, and who they are signed by.  In some cases, links to advisories and other research we found discussing these drivers will be included as well.

# Code samples:
### C#
#### LoadDriverAsService: 
This is an example of an application to automate the loading of a driver as a service in Windows, if run as user it will prompt a UAC. We used this to help us load various drivers for experimentation.
#### exampleApplication: 
An example of how to use an ASrock driver to read an MSR, including all the relevant imports from Windows.

### Powershell
#### ASRock_readmsr.ps1:
Based on FuzzySec's excellent writeup and example, this code does the same as the C# "exampleApplication", except written in PowerShell.

#### ASRock_readcr.ps1:
Example of reading Control Registers from PowerShell

#### ASRock_writecr.ps1:
Example of writing Control Registers from PowerShell

#### ASRock_kaslr.ps1:
Example of reading LSTAR MSR and CR3 to find Windows kernel syscall entry point and kernel page table base, defeating KASLR

#### ASRock_check_smep.ps1:
Checks if SMEP is enabled on each CPU from PowerShell

#### ASRock_disable_smep.ps1:
Disables SMEP temporarily from PowerShell

#### ASRock_disable_kern_wp.ps1:
Disables CR0 Write Protect bit temporarily from PowerShell 

# Detection
## wormhole.py
This is a script written using the angr dynamic analysis framework to detect this kind of vulnerability in drivers.

## x86_spotter.py
This file contains gymrat spotter functions to address limitations in the pyvex framework angr depends on.



| sha256                                                           | filename           | Signer information, Name:                          | Co-Signer                                          | where to find the drivers or more info                                                                                                |
|------------------------------------------------------------------|--------------------|----------------------------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| b4d47ea790920a4531e3df5a4b4b0721b7fea6b49a35679f0652f1e590422602 | AsUpIO64.sys       | ASUSTeK Computer Inc.                              |                                                    | https://codeinsecurity.wordpress.com/2016/06/12/asus-uefi-update-driver-physical-memory-readwrite/                                    |
| ece0a900ea089e730741499614c0917432246ceb5e11599ee3a1bb679e24fd2c | AsrDrv10.sys       | ASROCK Incorporation                               |                                                    | https://www.exploit-db.com/exploits/45716                                                                                             |
| f40435488389b4fb3b945ca21a8325a51e1b5f80f045ab019748d0ec66056a8b | AsrDrv101.sys      | ASROCK Incorporation                               |                                                    | https://www.exploit-db.com/exploits/45716                                                                                             |
| a7c2e7910942dd5e43e2f4eb159bcd2b4e71366e34a68109548b9fb12ac0f7cc | AsrDrv102.sys      | ASROCK Incorporation                               |                                                    | https://www.exploit-db.com/exploits/45716                                                                                             |
| 2003b478b9fd1b3d76ec5bf4172c2e8915babbbee7ad1783794acbf8d4c2519d | AsrDrv103.sys      | ASROCK Incorporation                               |                                                    | https://www.exploit-db.com/exploits/45716                                                                                             |
| f929bead59e9424ab90427b379dcdd63fbfe0c4fb5e1792e3a1685541cd5ec65 | BSMEMx64.sys       | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 59626cac380d8fe0b80a6d4c4406d62ba0683a2f0f68d50ad506ca1b1cf25347 | BSMIXP64.sys       | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 552f70374715e70c4ade591d65177be2539ec60f751223680dfaccb9e0be0ed9 | BSMIx64.sys        | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 86a8e0aa29a5b52c84921188cc1f0eca9a7904dcfe09544602933d8377720219 | BS_Flash64.sys     | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 1d0397c263d51e9fc95bcc8baf98d1a853e1c0401cd0e27c7bf5da3fba1c93a8 | BS_HWMIO64_W10.sys | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 60c6f4f34c7319cb3f9ca682e59d92711a05a2688badbae4891b1303cd384813 | BS_HWMIo64.sys     | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 55fee54c0d0d873724864dc0b2a10b38b7f40300ee9cae4d9baaf8a202c4049a | BS_I2c64.sys       | BIOSTAR MICROTECH INT'L CORP                       |                                                    | https://download.biostar.com.tw/upload/Driver/S_Software_Intel_300/TemperatureMonitor_NEW.zip                                         |
| 61a1bdddd3c512e681818debb5bee94db701768fc25e674fcad46592a3259bd0 | GLCKIO2.sys        | ASUSTeK Computer Inc.                              |                                                    | https://codeinsecurity.wordpress.com/2016/06/12/asus-uefi-update-driver-physical-memory-readwrite/                                    |
| 42f0b036687cbd7717c9efed6991c00d4e3e7b032dc965a2556c02177dfdad0f | GVCIDrv64.sys      | GIGA-BYTE TECHNOLOGY CO., LTD.                     |                                                    | https://www.secureauth.com/labs/advisories/gigabyte-drivers-elevation-privilege-vulnerabilities                                       |
| bb1135b51acca8348d285dc5461d10e8f57260e7d0c8cc4a092734d53fc40cbc | HwOs2Ec10x64.sys   | Huawei Technologies Co.,Ltd.                       | Microsoft Windows Hardware Compatibility Publisher | https://web.archive.org/web/20190317184311/https://consumer.huawei.com/us/support/pc/matebook-x-pro/                                  |
| b179e1ab6dc0b1aee783adbcad4ad6bb75a8a64cb798f30c0dd2ee8aaf43e6de | HwOs2Ec7x64.sys    | Huawei Technologies Co.,Ltd.                       | Microsoft Windows Hardware Compatibility Publisher | https://web.archive.org/web/20190317184311/https://consumer.huawei.com/us/support/pc/matebook-x-pro/                                  |
| 525d9b51a80ca0cd4c5889a96f857e73f3a80da1ffbae59851e0f51bdfb0b6cd | MsIo64.sys         | MICSYS Technology Co., Ltd.                        | Microsoft Windows Hardware Compatibility Publisher | https://github.com/rwfpl/rewolf-msi-exploit                                                                                           |
| 3f2fda9a7a9c57b7138687bbce49a2e156d6095dddabb3454ea09737e02c3fa5 | NBIOLib_X64.sys    | MICRO-STAR INTERNATIONAL CO., LTD.                 |                                                    | https://github.com/rwfpl/rewolf-msi-exploit                                                                                           |
| 314384b40626800b1cde6fbc51ebc7d13e91398be2688c2a58354aa08d00b073 | NCHGBIOS2x64.SYS   | TOSHIBA CORPORATION                                |                                                    | https://support.dynabook.com/support/viewContentDetail?contentId=4016085                                                              |
| d8b58f6a89a7618558e37afc360cd772b6731e3ba367f8d58734ecee2244a530 | NTIOLib_X64.sys    | Micro-Star Int'l Co. Ltd.                          |                                                    | https://github.com/rwfpl/rewolf-msi-exploit                                                                                           |
| 65db1b259e305a52042e07e111f4fa4af16542c8bacd33655f753ef642228890 | PhlashNT.sys       | Phoenix Technology Ltd.                            |                                                    | Bios Update tool                                                                                                                      |
| 19a212e6fc324f4cb9ee5eba60f5c1fc0191799a4432265cbeaa3307c76a7fc0 | Phymemx64.sys      | Huawei Technologies Co.,Ltd.                       | Microsoft Windows Hardware Compatibility Publisher | http://download-c1.huawei.com/download/downloadCenter?downloadId=98665&version=416103&siteCode=jp                                     |
| a7c8f4faf3cbb088cac7753d81f8ec4c38ccb97cd9da817741f49272e8d01200 | UCOREW64.SYS       | American Megatrends, Inc.                          |                                                    | BIOS Flash Tool                                                                                                                       |
| 677c0b1add3990fad51f492553d3533115c50a242a919437ccb145943011d2bf | WinFlash64.sys     | Phoenix Technology Ltd.                            |                                                    | BIOS Flash Tool                                                                                                                       |
| 11bd2c9f9e2397c9a16e0990e4ed2cf0679498fe0fd418a3dfdac60b5c160ee5 | WinRing0x64.sys    | Noriyuki MIYAZAKI                                  |                                                    | Wormhole driver by design                                                                                                             |
| fc22977ff721b3d718b71c42440ee2d8a144f3fbc7755e4331ddd5bcc65158d2 | amifldrv64.sys     | American Megatrends, Inc.                          |                                                    | BIOS Flash tool                                                                                                                       |
| ad40e6d0f77c0e579fb87c5106bf6de3d1a9f30ee2fbf8c9c011f377fa05f173 | atillk64.sys       | ATI Technologies, Inc                              |                                                    | ATI GPU flash update tool                                                                                                             |
| 18e1707b319c279c7e0204074088cc39286007a1cf6cb6e269d5067d8d0628c6 | dbk64.sys          | Cheat Engine                                       | Microsoft Windows Hardware Compatibility Publisher | Wormhole by Design                                                                                                                    |
| c9cf1d627078f63a36bbde364cd0d5f2be1714124d186c06db5bcdf549a109f8 | mtcBSv64.sys       | Getac Technology Corp.                             | Microsoft Windows Hardware Compatibility Publisher | Search for "getac bios" or  windows update catalog  0859190d-fb2d-41bf-98a0-a736b3502d85_77ee5a4539da45d47826338c3e4ee56462d702db.cab |
| afdd66562dea51001c3a9de300f91fc3eb965d6848dfce92ccb9b75853e02508 | nvflash.sys        | NVIDIA Corporation                                 | Microsoft Windows Hardware Compatibility Publisher | Nvidia GPU flash update tool                                                                                                          |
| a899b659b08fbae30b182443be8ffb6a6471c1d0497b52293061754886a937a3 | nvflsh64.sys       | NVIDIA Corporation                                 |                                                    | https://us.msi.com/Laptop/support/gt72-dominator-pro-gtx-980m#down-firmware                                                           |
| 1963d5a0e512b72353953aadbe694f73a9a576f0241a988378fa40bf574eda52 | phymem64.sys       | Super Micro Computer, Inc.                         |                                                    | Supermicro update tools                                                                                                               |
| 7133a461aeb03b4d69d43f3d26cd1a9e3ee01694e97a0645a3d8aa1a44c39129 | rtkio64.sys        | Realtek Semiconductor Corp.                        |                                                    | https://ftp.hp.com/pub/softpaq/sp87501-88000/sp87568.exe                                                                              |
| 32e1a8513eee746d17eb5402fb9d8ff9507fb6e1238e7ff06f7a5c50ff3df993 | rtkiow10x64.sys    | Realtek Semiconductor Corp.                        |                                                    | https://ftp.hp.com/pub/softpaq/sp87501-88000/sp87568.exe                                                                              |
| 082c39fe2e3217004206535e271ebd45c11eb072efde4cc9885b25ba5c39f91d | rtkiow8x64.sys     | Realtek Semiconductor Corp.                        | Microsoft Windows Hardware Compatibility Publisher | https://ftp.hp.com/pub/softpaq/sp87501-88000/sp87568.exe                                                                              |
| 65329dad28e92f4bcc64de15c552b6ef424494028b18875b7dba840053bc0cdd | segwindrvx64.sys   | Insyde Software Corp.                              |                                                    | Insyde firmware update tools H2OFFT                                                                                                   |
| f8430bdc6fd01f42217d66d87a3ef6f66cb2700ebb39c4f25c8b851858cc4b35 | superbmc.sys       | Super Micro Computer, Inc.                         |                                                    | Supermicro update tools                                                                                                               |
| 9f1229cd8dd9092c27a01f5d56e3c0d59c2bb9f0139abf042e56f343637fda33 | semav6msr.sys      | Intel (R) Code Signing External                    |                                                    | Intel® Computing Improvement Program                                                                                                  |
| b03f26009de2e8eabfcf6152f49b02a55c5e5d0f73e01d48f5a745f93ce93a29 | piddrv64.sys       | Microsoft Windows Hardware Compatibility Publisher |                                                    | Intel® Processor Identification Utility for Windows                                                                                   |


| filename     | Signer information, Name: | Location                                                                                                                |
|--------------|---------------------------|-------------------------------------------------------------------------------------------------------------------------|
| devcon.exe   | Ralink                    | included as part of the installer in https://d86o2zu8ugzlg.cloudfront.net/mediatek-craft/drivers/RT2770_2870_RT307x.zip |
| devcon64.exe | Ralink                    | included as part of the installer in https://d86o2zu8ugzlg.cloudfront.net/mediatek-craft/drivers/RT2770_2870_RT307x.zip |
