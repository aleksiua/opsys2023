# opsys2023
| **Küsimus** | **Linux** | **Windows** | **Linuxis kasutatud käsklus** | **Windowsis kasutatud käsklus** |
|---|---|---|---|---|
| Mitu protsessi kokku arvutis käib? | 226 | 128 | ps -aux \| wc -l | Tegumihaldur, jõudlus |
| Milline on kõige esimesena käivitatud protsess? (lisalugemine: init vs systemd) | /sbin/init/splash | sihost | ps axo pid,cmd,comm,etime | Poweshell, Get-Process \| select Name, StartTime |
| Milliste kasutajate protsesse arvutis käib? (arvesta ka süsteemiprotsesse, mitte ainult sisse logitud kasutajaid) |  | SYSTEM, Annabel, UMFD-1, UMFD-0, LOCAL SERVICE, NETWORK SERVICE |  | Tegumihaldur, üksikasjad |
| Kui kaua on arvuti järjest töötanud (up time)? (Alternatiivselt võib vastata ka, millal (kuupäev ja kellaaeg) arvuti viimati käima pandi.) |  | 22.11.2023 10:34:57 |  | Powershell, Get-CimInstance -ClassName Win32_OperatingSystem \| Select-Object LastBootUpTime |
| Milline protsess käivitati kõige hiljem (viimasena)? (Mitte võtta arvesse programmi, millega seda infot otsida.) |  |  |  |  |
| Milline on kõige rohkem protsessoriaega võttev protsess? |  |  |  |  |
| Milline on kõige rohkem virtuaalmälu (aadressiruumi, commit, Virtual Size) võttev protsess? |  |  |  |  |
| Milline on kõige rohkem füüsilist mälu (working set) võttev protsess? |  |  |  |  |
| Kui palju füüsilisest mälust (Physical Memory) on vaba? |  |  |  |  |
| Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt? |  |  |  |  |
| Milline on kõige suurem kõvakettal olev fail ja kõige suurem alamkaust? |  |  |  |  |
| Võrrelge terminali käskude: sha1sum /dev/zero \| sha1sum /dev/zero ja sha1sum /dev/urandom \| sha1sum /dev/urandom protsessori kasutust. Võrdluseks avage teine terminaliaken ja top samaaegseks käivitamiseks. Uurige, millisele CPU alamtegevusele us, sy, id, wa, st jne kulub enim protsessori aega ja mitu protsenti kulub kummagi käsu korral. (Ainult Linuxis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit. |  |  |  |  |
| Vasta järgnevatele alamküsimustele: (Ainult Windowsis) |  |  |  |  |
| Milline protsess kõige rohkem salvestusseadmele kirjutab? |  |  |  |  |
| Millisesse faili eelmise küsimuse protsess kõige rohkem kirjutab? |  |  |  |  |
| Milline protsess kõige rohkem salvestusseadmelt loeb? |  |  |  |  |
| Millisest failist eelmise küsimuse protsess kõige rohkem loeb? |  |  |  |  |
| Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga? Vali antud protsessi poolt kasutatavatest ühendustest üks ning kirjuta välja järgnev: kohalik IP-aadress, kohalik port, ühenduse teise poole IP-aadress, port, latents ja antud ühenduse poolt kasutatav võrguliikluse kogumaht. (Ainult Windowsis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit. |  |  |  |  |
| Sõber kurdab, et tema arvuti on oluliselt aeglasemaks muutunud. Milliseid konkreetseid programme või käsureakäske kasutad põhjustaja tuvastamiseks. Mõlemal juhul kirjuta, mida konkreetselt jälgid (nt mis aken, veerud, numbrid jne). (Vali Linuxis või Windowsis) |  |  |  |  |
