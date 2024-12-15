# Praktikum 12 aruanne



Ülesanne 3 Skript:
1.     !#/bin/sh
echo "Sisesta oma nimi:"
read nimi
echo "Sisesta oma eriala:"
read eriala
echo "Sisesta oma matriklinumber:"
read matriklinumber

echo "Sisestatud andmed:"
echo "Nimi: $nimi"
echo "Eriala: $eriala"
echo "Matriklinumber: $matriklinumber" 

Ülesanne 4 Skript:
1. #!/bin/bash
2. laiend1=$1
3. laiend2=$2
4. 
5. for fail in *.$laiend1
6. do
7.     mv "$fail" "${fail%.$laiend1}.$laiend2"
8.     echo "$fail nimetati ümber laiendiks $laiend2"
9.     done
