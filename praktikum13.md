```

# Masina nimi, PowerShelli versioon ja Windowsi versioon
$hostname = $env:COMPUTERNAME
$psVersion = $PSVersionTable.PSVersion.ToString()
$osVersion = (Get-CimInstance -ClassName Win32_OperatingSystem).Caption

# Võrgu konfiguratsioon
$networkConfig = Get-NetIPConfiguration | Select-Object -Property IPAddress, PrefixLength, DefaultGateway, Dhcp, InterfaceAlias
$macAddress = (Get-NetAdapter | Where-Object { $_.Status -eq 'Up' }).MacAddress

# Arvuti protsessori ja RAM info
$computerSystem = Get-WmiObject -Class Win32_ComputerSystem
$processor = $computerSystem.Description
$ram = "{0:N2} GB" -f ($computerSystem.TotalPhysicalMemory / 1GB)

# Graafikakaardi info
$graphicsInfo = Get-CimInstance -ClassName Win32_VideoController | Select-Object -Property Name, DriverVersion, DriverDate, VideoModeDescription

# Arvuti kõvaketaste informatsioon (ainult C-ketas)
$diskInfo = Get-WmiObject -Class Win32_LogicalDisk | Where-Object { $_.DeviceID -eq 'C:' } | Select-Object -Property VolumeName, Size, FreeSpace

# PCI-seadmete draiverite info
$pciDevices = Get-WmiObject -Class Win32_PnPEntity | Where-Object { $_.ConfigManagerErrorCode -eq 0 } | Select-Object -Property Description, Manufacturer, DriverVersion

# Arvutis olevad kasutajad
$users = Get-WmiObject -Class Win32_UserAccount | Select-Object -Property Name, Description, LocalAccount, Disabled

# Käimasolevate protsesside arv
$processCount = (Get-Process).Count

# 10 viimast käivitatud protsessi
$recentProcesses = Get-WmiObject Win32_Process | Sort-Object -Property CreationDate -Descending | Select-Object -First 10 -Property Name, ProcessId, CreationDate


# Arvuti kuupäev ja kellaaeg
$currentDateTime = Get-Date -Format "yyyy-MM-dd HH:mm:ss"

# Faili loomine ja info salvestamine
$outputPath = "C:\Users\Annabel\praktikum.txt"
Set-Content -Path $outputPath -Value @"
Arvuti info:
---------------------
Masina nimi: $hostname
PowerShelli versioon: $psVersion
Windowsi versioon: $osVersion

Võrgu konfiguratsioon:
IP-aadress: $($networkConfig.IPAddress)
Võrgumask: $($networkConfig.PrefixLength)
Gateway: $($networkConfig.DefaultGateway)
DHCP lubatud: $($networkConfig.Dhcp)
MAC-aadress: $macAddress

Protsessor: $processor
Põhimälu RAM kogus: $ram

Graafikakaart:
Nimi: $($graphicsInfo.Name)
Draiveri versioon: $($graphicsInfo.DriverVersion)
Draiveri kuupäev: $($graphicsInfo.DriverDate)
Ekraani lahutus: $($graphicsInfo.VideoModeDescription)

Kõvaketta info:
Partitsioon: $($diskInfo.VolumeName)
Mahutavus: $($diskInfo.Size / 1GB) GB
Vaba ruum C:-kettal: $($diskInfo.FreeSpace / 1GB) GB

PCI-seadmete draiverite info:
$($pciDevices | Format-Table | Out-String)

Arvutis olevad kasutajad:
$($users | Format-Table | Out-String)

Käimasolevate protsesside arv: $processCount

10 viimast protsessi:
$($recentProcesses | Format-Table | Out-String)

Arvuti kuupäev ja kellaaeg: $currentDateTime
"@

Arvuti info:
---------------------
Masina nimi: ALEKSIUS-W11
PowerShelli versioon: 5.1.22621.2506
Windowsi versioon: Microsoft Windows 11 Pro Education

Võrgu konfiguratsioon:
IP-aadress: 10.0.2.15
Võrgumask: 255.255.255.0
Gateway: 10.0.2.2
DHCP lubatud: 
MAC-aadress: 08-00-27-95-BE-2B

Protsessor: AT/AT COMPATIBLE
Põhimälu RAM kogus: 3,98 GB

Graafikakaart:
Nimi: VirtualBox Graphics Adapter (WDDM)
Draiveri versioon: 7.0.10.8379
Draiveri kuupäev: 07/12/2023 03:00:00
Ekraani lahutus: 1148 x 1000 x 4294967296 colors

Kõvaketta info:
Partitsioon: 
Mahutavus: 63.2246055603027 GB
Vaba ruum C:-kettal: 33.2716636657715 GB

PCI-seadmete draiverite info:

Description                                            Manufacturer                     DriverVersion
-----------                                            ------------                     -------------
Microsoft AC Adapter                                   Microsoft                                     
Direct memory access controller                        (Standard system devices)                     
Volume                                                 Microsoft                                     
Microsoft ACPI-Compliant Control Method Battery        Microsoft                                     
Kohalik prindij rjekord                                Microsoft                                     
Volume Manager                                         Microsoft                                     
VirtualBox Graphics Adapter (WDDM)                     Oracle Corporation                            
Trusted Platform Module 2.0                            (Standard)                                    
Computer Device                                        Microsoft                                     
WAN Miniport (PPPOE)                                   Microsoft                                     
High Definition Audio Device                           Microsoft                                     
Microsoft Basic Display Driver                         (Standard display types)                      
HID-compliant mouse                                    Microsoft                                     
 ldine tarkvaralitsents                                Microsoft                                     
Volume                                                 Microsoft                                     
WAN Miniport (PPTP)                                    Microsoft                                     
Microsoft Hyper-V Virtualization Infrastructure Driver Microsoft                                     
PCI to ISA Bridge                                      Intel                                         
WAN Miniport (IKEv2)                                   Microsoft                                     
Composite Bus Enumerator                               Microsoft                                     
Microsoft Virtual Drive Enumerator                     Microsoft                                     
Microsoft Storage Spaces Controller                    Microsoft                                     
Intel Processor                                        Intel                                         
Intel Processor                                        Intel                                         
Microsoft Kernel Debug Network Adapter                 Microsoft                                     
Microsoft PS/2 Mouse                                   Microsoft                                     
UMBus Root Bus Enumerator                              Microsoft                                     
USB Input Device                                       (Standard system devices)                     
Charge Arbitration Driver                              (Standard system devices)                     
 ldine tarkvaralitsents                                Microsoft                                     
System timer                                           (Standard system devices)                     
ACPI x64-based PC                                      (Standard computers)                          
PCI Bus                                                (Standard system devices)                     
VirtualBox Guest Device                                Oracle Corporation                            
WAN Miniport (Network Monitor)                         Microsoft                                     
WAN Miniport (IP)                                      Microsoft                                     
Standard SATA AHCI Controller                          Standard SATA AHCI Controller                 
Microsoft ACPI-Compliant System                        Microsoft                                     
                                                                                                     
Microsoft Basic Render Driver                          Microsoft                                     
WAN Miniport (SSTP)                                    Microsoft                                     
ACPI Fixed Feature Button                              (Standard system devices)                     
USB Root Hub (USB 3.0)                                 (Standard USB HUBs)                           
Disk drive                                             (Standard disk drives)                        
Volume                                                 Microsoft                                     
CPU to PCI Bridge                                      Intel                                         
 ldine tarkvaralitsents                                Microsoft                                     
Kohalik prindij rjekord                                Microsoft                                     
NDIS Virtual Network Adapter Enumerator                Microsoft                                     
Heli l pp-punkt                                        Microsoft                                     
USB xHCI Compliant Host Controller                     Generic USB xHCI Host Controller              
High Definition Audio Controller                       Microsoft                                     
Volume                                                 Microsoft                                     
Microsoft System Management BIOS Driver                (Standard system devices)                     
Intel(R) PRO/1000 MT Desktop Adapter                   Intel                                         
Programmable interrupt controller                      (Standard system devices)                     
Standard PS/2 Keyboard                                 (Standard keyboards)                          
Plug and Play Software Device Enumerator               (Standard system devices)                     
Heli l pp-punkt                                        Microsoft                                     
CD-ROM Drive                                           (Standard CD-ROM drives)                      
Remote Desktop Device Redirector Bus                   Microsoft                                     
Generic Non-PnP Monitor                                (Standard monitor types)                      
WAN Miniport (IPv6)                                    Microsoft                                     
WAN Miniport (L2TP)                                    Microsoft                                     




Arvutis olevad kasutajad:

Name               Description                                                                                     Loca
                                                                                                                   lAcc
                                                                                                                   ount
----               -----------                                                                                     ----
Administrator      Built-in account for administering the computer/domain                                          True
Annabel                                                                                                            True
Annabel-tava                                                                                                       True
DefaultAccount     A user account managed by the system.                                                           True
Guest              Built-in account for guest access to the computer/domain                                        True
tootaja1                                                                                                           True
tootaja2                                                                                                           True
WDAGUtilityAccount A user account managed and used by the system for Windows Defender Application Guard scenarios. True
ylemus                                                                                                             True




Käimasolevate protsesside arv: 139

10 viimast protsessi:

Name                   ProcessId CreationDate             
----                   --------- ------------             
WmiPrvSE.exe                7132 20231220115445.598246+120
WmiPrvSE.exe                 604 20231220115445.386748+120
SearchProtocolHost.exe      4200 20231220115443.898035+120
svchost.exe                 9816 20231220115249.929974+120
Notepad.exe                 9308 20231220115022.031208+120
svchost.exe                 7964 20231220114938.151894+120
smartscreen.exe             9004 20231220113953.459443+120
MoNotificationUx.exe        5608 20231220112603.588163+120
msedge.exe                  9728 20231220112238.911449+120
msedge.exe                  3008 20231220112238.827351+120




Arvuti kuupäev ja kellaaeg: 2023-12-20 11:54:45


```


