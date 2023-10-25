# opsys2023  
Protsessid ja signaalid  
Praktikumis 6 õppisin kasutama Ubuntu terminali uusi käske, millega oskan leida soovitud teksti andmestest  
ning seda salvestada faili. Õppisin ka käivitama ja sulgema programme erinevatel viisidel gedit käsuga.  
1. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/a7ba4a9c-4520-4cc1-aecd-d6e4b7c67f32)  
2. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/022c6cbb-59a9-4500-bd2a-eee1bca746da)  
3. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/a225a372-dcea-4874-b29b-5c3b418b2747)  
ps -axu | grep daemon | tr -s " " | cut -d" " -f11-  
4. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/2a644571-d85a-4856-8087-19eea3b16f53) 
ip a | grep inet" " | tail -n+2 | tr -s " " | cut -d" " -f3- | cut -c-9 > ipaddress.txt  

