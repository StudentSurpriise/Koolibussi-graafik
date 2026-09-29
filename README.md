# Koolibussi graafik

Süsteem, mille abil õpilased saavad vaadata väljumisi ja peatusi ning juhid või dispetšerid saavad märkida hilinemisi ja hallata liine.

**Tegijad:** Danil Razskazov, Ivan Petrash NPTV24

## Kasutajad ja nõuded
Kaks rolli: õpilane/lapsevanem ja bussijuht/dispetšer. Kuus kasutajalugu on Issues all, tähtsamad on märgitud `must`.

## Arendusmudel
Koolibussi-graafiku projekti jaoks valiksin inkrementaalse mudeli, sest süsteemi saab arendada väikeste osadena. Esmalt saab luua põhilise bussigraafiku ning seejärel lisada näiteks peatuste, õpilaste ja busside haldamise. Iga valminud osa saab eraldi testida ja vajadusel parandada. Kosemudel ei oleks sama sobiv, sest seal on hilisemate muudatuste tegemine keerulisem. Inkrementaalne mudel võimaldab projekti jooksul paindlikult uusi vajadusi arvesse võtta.

## Diagrammid
![Kasutusjuhud](diagrams/UML.drawio.png)
![Klassid](diagrams/class.drawio.png)

## Makett
Tegime iteratiivselt, sest soovisime kasutajaliidest samm-sammult testida ja tagasiside põhjal täiustada.
![Ekraan 1](protsess/Screenshot.png)

## Kuidas me töötasime
Tahvel alguses ja lõpus: `protsess/`. 
Retrospektiiv: Projekti algus sujus hästi tänu selgele tööjaotusele ja heale tiimitööle. Raskusi valmistas reaalajas andmete sünkroniseerimise loogika ja seoste paika panemine klassidiagrammil. Järgmine kord kaasaksime kasutajaid testimisse veelgi varem.
