```

$hostname = $env:COMPUTERNAME
$psVersion = $PSVersionTable.PSVersion.ToString()
$osVersion = (Get-CimInstance -ClassName Win32_OperatingSystem).Caption


$networkConfig = Get-NetIPConfiguration | Select-Object -Property IPAddress, PrefixLength, DefaultGateway, Dhcp, InterfaceAlias
$macAddress = (Get-NetAdapter | Where-Object { $_.Status -eq 'Up' }).MacAddress


$computerSystem = Get-WmiObject -Class Win32_ComputerSystem
$processor = $computerSystem.Description
$ram = "{0:N2} GB" -f ($computerSystem.TotalPhysicalMemory / 1GB)


$graphicsInfo = Get-CimInstance -ClassName Win32_VideoController | Select-Object -Property Name, DriverVersion, DriverDate, VideoModeDescription


$diskInfo = Get-WmiObject -Class Win32_LogicalDisk | Where-Object { $_.DeviceID -eq 'C:' } | Select-Object -Property VolumeName, Size, FreeSpace


$pciDevices = Get-WmiObject -Class Win32_PnPEntity | Where-Object { $_.ConfigManagerErrorCode -eq 0 } | Select-Object -Property Description, Manufacturer, DriverVersion


$users = Get-WmiObject -Class Win32_UserAccount | Select-Object -Property Name, Description, LocalAccount, Disabled


$processCount = (Get-Process).Count


$recentProcesses = Get-WmiObject Win32_Process | Sort-Object -Property CreationDate -Descending | Select-Object -First 10 -Property Name, ProcessId, CreationDate


$currentDateTime = Get-Date -Format "yyyy-MM-dd HH:mm:ss"

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


```


