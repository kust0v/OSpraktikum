# Praktikum 5 aruanne

Selles praktikumis tegelesin failiõigustega Linuxis. Sain Unixi failiõigustest ülevaate, tegelesin setuid- ja setgid-failidega. Sain teada mis on Sticky Bit ja ACL, samuti käsitlesin failisüsteemi täiendavaid attribuute.

5.1 Faili lugemiseks on vaja r-x ja faili kustutamiseks rwx.

5.2 Sellepärast, et tal ei ole võimalik seda lugeda. Selleks, et skriptifail saaks käivitada, on lisaks käivitamisõigusele vaja ka lugemisõigust.

5.3 See on kasulik näiteks failide ja kataloogide turvaliseks haldamiseks. Tagab turvalisuse ja privaatsuse.

5.4 Minimaalsed õigused on rw-r-----, et kuvada uusfail.txt sisu.
<img width="983" alt="ylesanne5.4" src="https://github.com/user-attachments/assets/50111683-1224-407d-a069-23de03121141">

5.5 <img width="983" alt="ylesanne5.2" src="https://github.com/user-attachments/assets/1b582936-bde5-4cfc-b762-d7712a4d4b41">

5.6 Jah vähendab süsteemi turvalisust, näiteks valesti seadistamine võib tekitada turvaauke.

5.7 Kasutajad Peeter, Root ja Opetaja saavad Sticky Bit-õigustega yhiskaust-kataloogist nüüd peeter-kasutaja loodud faile kustutada.

5.8 
"# file: hinded.txt"
"# owner: opetaja"
"# group: opetaja"
user::rw-
group::r--
group:direktor:rw-
mask::rw-
other::r–

5.9 Faili sisu ei saa keegi modifitseerida, isegi mitte root, seni kui chattr +i atribuut on määratud.  Faili kustutamiseks peab eemaldada chattr +i atribuut käsuga sudo chattr -i testfail-2, siis saab faili kustutada käsuga rm testfail-2.
