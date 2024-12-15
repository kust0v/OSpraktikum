# Praktikum 12 aruanne

Selles praktikumis tegelesin Linuxis skriptimisega. Praktikum ei olnud väga suure mahuga ja pigem võttis vähem aega kui teised. Õppisin selles praktikumis Linuxis skriptimist ja arvan, et see tuleb tulevikus mulle kasuks.


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

Ülesanne 3 väljund:
<img width="983" alt="ylesanne12.3" src="https://github.com/user-attachments/assets/d30fd078-08f9-4255-9b9d-35794e379538">

Ülesanne 4 väljund:
<img width="983" alt="ylesanne12.4" src="https://github.com/user-attachments/assets/622fa8b0-8e91-4da1-8f66-88f1c8dc6c71">

Ülesanne 5 väljund:
<img width="983" alt="ylesanne12.5" src="https://github.com/user-attachments/assets/b5e193db-9a74-45f0-b448-6c9bcac4e84c">

Ülesanne 6 väljund:
<img width="983" alt="ylesanne12.6" src="https://github.com/user-attachments/assets/8dfd1492-bba2-4bb1-a70c-14c185ee0574">

Ülesanne 7
<img width="983" alt="ylesanne12.7.1" src="https://github.com/user-attachments/assets/f6e0b622-ae23-4f9c-8557-27dd4bff83ae">
<img width="983" alt="ylesanne12.7.2" src="https://github.com/user-attachments/assets/8d69fe78-32b0-4d26-ab33-a26a737a0aae">
<img width="983" alt="ylesanne12.7.3" src="https://github.com/user-attachments/assets/af3b5d5d-50ab-4405-8f46-7b95a3f25452">
