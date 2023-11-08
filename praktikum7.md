# opsys2023
Uurisin, kuidas lokaalseid ja võrgukettaid Windowsi ja Linuxi keskkonnas kasutada. Õppisin paremini tundma mount-käske ning USB-ga töötamist.  
  
1. Andmekandjad vajavad lähtestamist, et tagada andmete turvalisus ja privaatsus. Ilma lähtestamata võivad teie andmed sattuda halbadesse kätesse.
2. GPT kasutamise eelised võrreldes MBRiga on järgmised: GTP kõvaketta maht on suurem. GTP pakub suuremat kaitset andmete kadumise vastu, kuna ta suudab parandada rikutud partitisioone. GTP toetab rohkem partitisioone, MBR toetab kuni nelja, GTP tuhandeid. Suurte andmekandjate puhul tuleb see kasuks, kui on vaja mitmeid partitsioone haldada.8  
3.  https://kodu.ut.ee/~aleksiua/hdd.png  
4. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/d6625ef1-e7e6-4273-a2a9-cd911f5b5364)
5. '-o ro' käsuga määrataksse partitsioon ainult lugemiseks, ehk andmeid ei saa juurde kirjutada ega muuta.
'-t auto' käsuga saab tuvastada failisüsteemi tüübi automaatselt. Kui ei ole teada, millist failisüsteemi kasutatakse, siis proovib see käsk automaatselt juba erinevaid variante läbi ja hoitakse aega kokku.
auto-parameeter asendati exfat'iga.
6. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/7daf8353-6a9f-4c36-8696-f6ef8f4ace63)
   


 
