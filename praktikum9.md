# opsys2023
| **Küsimus** | **Linux** | **Windows** | **Linuxis kasutatud käsklus** | **Windowsis kasutatud käsklus** |
|---|---|---|---|---|
| Mitu protsessi kokku arvutis käib? | 226 | 128 | ps -aux \| wc -l | Tegumihaldur, jõudlus |
| Milline on kõige esimesena käivitatud protsess? (lisalugemine: init vs systemd) | /sbin/init/splash | sihost | ps axo pid,cmd,comm,etime | Poweshell, Get-Process \| select Name, StartTime |
| Milliste kasutajate protsesse arvutis käib? (arvesta ka süsteemiprotsesse, mitte ainult sisse logitud kasutajaid) | annabel, root, kernoops, syslog, message+, avahi, systemd+ | SYSTEM, Annabel, UMFD-1, UMFD-0, LOCAL SERVICE, NETWORK SERVICE | ps aux | Tegumihaldur, üksikasjad |
| Kui kaua on arvuti järjest töötanud (up time)? (Alternatiivselt võib vastata ka, millal (kuupäev ja kellaaeg) arvuti viimati käima pandi.) | 5min | 53:15 | uptime | Tegumihaldur, jõudlus |
| Milline protsess käivitati kõige hiljem (viimasena)? (Mitte võtta arvesse programmi, millega seda infot otsida.) | ps aux --sort=-start_time | Powershell | ps aux --sort=-start_time | Get-Process \| Sort-Object StartTime -Descending \| Format-Table -Property Id, ProcessName, StartTime -AutoSize |
| Milline on kõige rohkem protsessoriaega võttev protsess? | /usr/bin/gnome-shell | SearchHost | ps aux --sort=-%cpu \| awk 'NR==2' | Get-Process \| Sort-Object CPU -Descending \| Select-Object -First 1 \| Format-Table -Property Id, ProcessName, CPU -AutoSize |
| Milline on kõige rohkem virtuaalmälu (aadressiruumi, commit, Virtual Size) võttev protsess? | /usr/bin/gnome-shell | SearchHost | ps aux --sort=-vsz \| awk 'NR==2' | Get-Process \| Sort-Object VirtualMemorySize -Descending \| Select-Object -First 1 \| Format-Table -Property Id, ProcessName, VirtualMemorySize -AutoSize |
| Milline on kõige rohkem füüsilist mälu (working set) võttev protsess? | /usr/bin/gnome-shell | explorer | ps aux --sort=-rss \| awk 'NR==2' | Get-Process \| Sort-Object WorkingSet -Descending \| Select-Object -First 1 \| Format-Table -Property Id, ProcessName, WorkingSet -AutoSize |
| Kui palju füüsilisest mälust (Physical Memory) on vaba? | 1,6 GB | 1473 MB | free -h | cmd, systeminfo \| find "Physical Memory" |
| Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt? | 11GB, 47% | 35 GB, 55% | df -h / | file explorer, see arvuti |
| Milline on kõige suurem kõvakettal olev fail ja kõige suurem alamkaust? | /mnt/share/Opsysteemid kaust/Operatsioonisüsteemid 2023/Win11_22H2_Estonian_x64v2.iso | Windows, pagefile.sys | sudo find / -type f -exec du -h {} + \| sort -rh \| head -n 1 | WinDirStat, minu kompuuter, C:, Vaatasin kaste. |
| Võrrelge terminali käskude: sha1sum /dev/zero \| sha1sum /dev/zero ja sha1sum /dev/urandom \| sha1sum /dev/urandom protsessori kasutust. Võrdluseks avage teine terminaliaken ja top samaaegseks käivitamiseks. Uurige, millisele CPU alamtegevusele us, sy, id, wa, st jne kulub enim protsessori aega ja mitu protsenti kulub kummagi käsu korral. (Ainult Linuxis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit. | Mõlemad käsud kasutavad palju CPU-d. Esimese käsu korral kasutab user palju CPU-d, system vähe ja muud üldse mitte. Teise käsu korral kasutab user vähem cpud ja system  rohkem cpud. |  |  |  |
| Vasta järgnevatele alamküsimustele: (Ainult Windowsis) |  |  |  |  |
| Milline protsess kõige rohkem salvestusseadmele kirjutab? |  | system |  | Tegumihaldur, ketas |
| Millisesse faili eelmise küsimuse protsess kõige rohkem kirjutab? |  | C:\$Logfile (NTFS Volume Vlog) |  | Resource Monitor, Disk, Disk Activity |
| Milline protsess kõige rohkem salvestusseadmelt loeb? |  | msedgewebview2.exe |  | Resource Monitor, Disk, Disk Activity |
| Millisest failist eelmise küsimuse protsess kõige rohkem loeb? |  | C:\USers\Annabel\AppData\Local\Packages\MicrosoftWindows.Client.WebExperience_cw5n1h2txyewy\LocalState\EBWebView\Default\DIPS |  | Resource Monitor, Disk, Disk Activity |
| Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga? Vali antud protsessi poolt kasutatavatest ühendustest üks ning kirjuta välja järgnev: kohalik IP-aadress, kohalik port, ühenduse teise poole IP-aadress, port, latents ja antud ühenduse poolt kasutatav võrguliikluse kogumaht. (Ainult Windowsis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit. |  | Firefox.exe, 10.0.2.15, 65142, 62.65.193.8, 80, 7, 38887. |  |  |
| Sõber kurdab, et tema arvuti on oluliselt aeglasemaks muutunud. Milliseid konkreetseid programme või käsureakäske kasutad põhjustaja tuvastamiseks. Mõlemal juhul kirjuta, mida konkreetselt jälgid (nt mis aken, veerud, numbrid jne). (Vali Linuxis või Windowsis) |  | Avan Resource Monitori ja vaatan, millised protsessid kasutavad kõige rohkem ressursse. Kontrollin ka võrguliiklust pahavara pärast. Avan käsuviiba ja teen ketta puhastuse, et eemaldada ajutised failid ja muu, kassutades käsku cleanmgr. Vaatan EventVieweris, et poleks süsteemi- ja rakenduselogides vigu. Kontrollin sätetes, kas süsteemis on viirusetõrje tarkvara. |  |  |
|  |  |  |  |  |  

![image](https://github.com/aleksiua/opsys2023/assets/145049882/06f76fdd-1cff-464b-9100-e76603815fd7)

