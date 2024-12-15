# Praktikum 12 aruanne



Ülesanne 3 Skript:
1. !#/bin/sh
2. echo "Sisesta oma nimi:"
3. read nimi
4. echo "Sisesta oma eriala:"
5. read eriala
6. echo "Sisesta oma matriklinumber:"
7. read matriklinumber
8. 
9. echo "Sisestatud andmed:"
10. echo "Nimi: $nimi"
11. echo "Eriala: $eriala"
12. echo "Matriklinumber: $matriklinumber" 

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
