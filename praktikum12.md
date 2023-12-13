3.
```
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

``` 
3.  ![image](https://github.com/aleksiua/opsys2023/assets/145049882/dec895ea-152a-4d5c-b292-0ee19fb67adc)
4.  
```
#!/bin/bash

vana_fail=$1
uus_fail=$2

for file in *.$vana_fail; do
    if [ -f "$file" ]; then
        uus_fail="${file%.$vana_fail}.$uus_fail"
        mv "$file" "$uus_fail"
        echo "Fail $file nimetati ümber failiks $uus_fail" 
    fi
done

```
4. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/1d4c1443-2454-477f-b341-c71d757a35cb)
5. 

```
#!/bin/bash

otsitav=$1
pids=$(pgrep "$otsitav")

if [ -n "$pids" ]; then
    for pid in $pids; do
        process=$(ps -p "$pid" -o comm=)
        echo "Protsessi nimi: $process, PID: $pid"
    done
else
    echo "Protsessi nimega '$otsitav' ei leitud."
fi
```
5. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/a20bcde4-c7c4-43b8-ac75-2abf9de209f2)  

