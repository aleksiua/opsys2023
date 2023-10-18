
Linuxi failiõigused  
Praktikumis harjutasin Linuxi käsurea kirjutamist ja erinevate kasutajate õiguste haldamist.  
5.1 a) Faili lugemiseks on kasutajal vaja +r õigusi.  
b) Faili kustutamiseks ei vaja kasutaja ühtegi õigust.  
5.2 Sellest õigusest ei piisa, kuna skripti on vaja ka lugeda ja selle käsuga ei ole 
antud kasutajale õigust skripti lugeda. Selleks on vaja anda käsk chmod a+r Kaust3/skript.sh.  
5.3 See aitab tagada failidele suurema turvalisuse, kuna siis ei pääse igaüks ligi teiste failidele. Omanikul on õigused rw ja teistel on ainult r õigus.  
5.4 Selleks, et tavakasutaja saaks kuvada sisu, tuleb grupile lisada lugemisõigus r. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/a5807eb5-f47b-4b4c-8cbe-8c7ac953890f)  
5.5 Setuid laseb käivitada faili või skripti omaniku õigustega.
<img width="296" alt="image" src="https://github.com/aleksiua/opsys2023/assets/145049882/46701477-beb9-4c02-9455-b0d17d720daa">  
5.6 Jah, setuid vähendab süsteemi turvalisust, kuna see annab kõikidele kasutajatele õiguse kasutada faili ning nii võib pääseda keegi arvutile ligi omanikuõigustega.  
5.7 Sticky bit-õigustega yhiskaust-kataloogist saavad peeter-kasutaja loodud faile kustutada: opetaja, peeter ja jukuisa.  
5.8 peeter@aleksius-U23:/home/opetaja/klass$ getfacl hinded.txt  
-# file: hinded.txt    
-# owner: opetaja    
-# group: opetaja  
user::rw-  
group::---  
group:direktor:rw-  
mask::rw-  
other::---   
5.9 root kasutaja saab chattr +i-parameetriga faili sisu modifitseerida. kustutada saab sudo chattr -i testfail-2 käsuga ja seejärel rm testfail-2.
