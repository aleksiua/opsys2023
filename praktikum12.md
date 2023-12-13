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

6.
```
#!/bin/bash

astenda() {
  base=$1
  exponent=$2
  result=1

  while [ $exponent -gt 0 ]; do
    result=$(($result * $base))
    exponent=$(($exponent - 1))
  done

  echo $result
}

tulemus=$(astenda 9 5)
echo "9^5 = $tulemus"
```
6. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/5675360e-8f9c-4794-a638-62502106f42f)
7. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/03776194-4269-49d5-a447-669ab63cc5e1)
7. ![image](https://github.com/aleksiua/opsys2023/assets/145049882/30a49d22-7d19-44e3-bfb0-8d2b89082a80)
8.  7. ```
       #!/bin/bash

# Defineerime funktsiooni astenda, mis võtab vastu kaks argumenti: alus ja astendaja
function astenda {
    if (( $2 == 0 )); then
        echo 1
    else
        echo $(($1 * $(astenda $1 $(($2 - 1)))))
    fi
}

# Väljastame 9^5 väärtuse, kasutades loodud funktsiooni
tulemus=$(astenda 9 5)
echo "9^5 = $tulemus"
```
