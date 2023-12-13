3.  
#!/bin/sh  
chmod 700 esimene.sh  
echo "sisesta oma nimi:"  
read nimi  
echo "Sisesta oma eriala:"  
read eriala  
echo "Sisesta oma matriklinumber:"  
read matriklinumber  
echo "$nimi"  
echo "$eriala"  
echo "matriklinumber"  
3.  ![image](https://github.com/aleksiua/opsys2023/assets/145049882/dec895ea-152a-4d5c-b292-0ee19fb67adc)
4.  4. if [ "$#" -ne 2 ]; then
    echo "Kasutamine: $0 <vana_laiend> <uus_laiend>"
    exit 1
fi

vana_laiend=$1
uus_laiend=$2

for i in *.$vana_laiend; do
    if [ "${i##*.}" = "$vana_laiend" ]; then
        uus_nimi="${i%.$vana_laiend}.$uus_laiend"
        mv "$i" "$uus_nimi"
        echo "Fail ümbernimetatud: $i -> $uus_nimi"
    fi
done  
4. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/381e4ead-d572-4928-95fb-d0ad9a7fcd78)  
