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
1.     #!/bin/bash
       laiend1=$1
       laiend2=$2

       for fail in *.$laiend1
       do
          mv "$fail" "${fail%.$laiend1}.$laiend2"
          echo "$fail nimetati ümber laiendiks $laiend2"
       done

Ülesanne 5 Skript:
1.     #!/bin/bash
       protsess=$1

       ps -A | grep "$protsess" | while read line
       do
         pid=$(echo "$line" | tr -s ' ' | cut -d ' ' -f1)
         process_name=$(echo "$line" | tr -s ' ' | cut -d ' ' -f2)
         echo "Protsess: $process_name, PID: $pid"
       done

Ülesanne 6 Skript:
1.     #!/bin/bash
       astenda () {
         tulemus=1
         baasi=$1
         aste=$2

         while [ $aste -gt 0 ]
         do
           tulemus=$(($tulemus * $baasi))
           aste=$(($aste - 1))
         done

         echo $tulemus
        }

        echo "9 astmel 5 on: $(astenda 9 5)"

