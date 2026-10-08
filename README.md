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
![Ekraan 1](mockup/Screenshot.png)

## Kuidas me töötasime
Tahvel alguses ja lõpus: `protsess/`. 
Retrospektiiv: Projekti algus sujus hästi tänu selgele tööjaotusele ja heale tiimitööle. Raskusi valmistas reaalajas andmete sünkroniseerimise loogika ja seoste paika panemine klassidiagrammil. Järgmine kord kaasaksime kasutajaid testimisse veelgi varem.

## Tools
![Vahendite võrdlus](protsess/tools/comprasion.png)

## Diagrammid
```mermaid
classDiagram
  class Route {
    -int distance
    -int time
    +getMenu(date)
    +getRouteDetails()
    +calculateTotalTime()
  }

  class Driver {
    +String name
    -int id
    -String phone
    -String licenseCategory
    +findAllergy()
    +getDetails()
    +updateLocation()
    +reportDelay(minutes)
  }

  class Buss {
    -String mark
    -int tankCapacity
    -float fuelInMoment
    -float averageConsumption
    -String color
    -String regNumber
    -int seatsCount
    +toString()
    +checkRoute()
    +refuel(amount)
    +isAvailableForRoute()
  }

  class Student {
    -String name
    -String IK
    -String group
    -int age
    -String address
    -String parentPhone
    +toString()
    +getAssignedBus()
    +updateAttendance(status)
  }
  Route "1" --> "*" Buss : teenindab
  Driver "*" --> "*" Buss : juhib
  Buss "1" --> "*" Student : veab

 	## Projekti kaart

  **Tellija:** Kooli juhtkond / koolibussiteenuse korraldaja, kes vastutab õpilaste transpordi ja bussiliinide toimimise eest.
  **Probleem:** Praegu on õpilastel ja lapsevanematel keeruline saada kiiresti ja kindlalt infot koolibussi väljumiste, peatuste ning hilinemiste kohta. Bussijuht või dispetšer peab muudatusi ja hilinemisi edastama käsitsi, mistõttu võib info jõuda kasutajateni hilinemisega või üldse mitte.
  **Eesmärk:** 1. detsembriks 2026 saavad õpilased ja lapsevanemad veebis vaadata bussiliinide väljumisaegu ja peatusi ning bussijuhid/dispetšerid saavad hilinemisi süsteemis märkida. Vähemalt 90% testkasutajatest leiab soovitud bussiliini ja selle väljumisaja kuni 1 minuti jooksul.
  **Tulemus:**
töötav koolibussi graafiku süsteem;
õpilase/lapsevanema vaade väljumiste ja peatuste vaatamiseks;
bussijuhi/dispetšeri vaade hilinemiste märkimiseks;
bussiliinide ja bussidega seotud andmete haldamine;
süsteemi kasutamist kirjeldav dokumentatsioon.


**Ulatus SEES:**
bussiliinide ja peatuste kuvamine;
busside väljumisaegade kuvamine;
hilinemiste märkimine bussijuhi/dispetšeri poolt;
õpilaste ja busside seostamine liinidega;
bussiliinide, busside ja juhtide põhiandmete haldamine.
**Ulatus VÄLJAS:**
mobiilirakendus — projektis tehakse veebipõhine lahendus;
bussipiletite või sõitude eest maksmine;
GPS-põhine bussi reaalajas jälgimine kaardil.

**Kolmnurk:** aeg: fikseeritud; raha/inimesed: olemasolev 2-liikmeline meeskond ja õppetööks ettenähtud ressursid; ulatus: paindlik. Fikseeritud on: projekti lõpptähtaeg ja põhifunktsioonid ehk graafiku vaatamine ning hilinemiste märkimine.
**Rollid:** tellija — kooli juhtkond; projektijuht — meeskonna liige, kes koordineerib ülesandeid; meeskond — Danil Razskazov ja Ivan Petrash; huvipooled — õpilased, lapsevanemad, bussijuhid.

| Risk | Tõenäosus 1–3 | Mõju 1–3 | Mida teeme enne |
|---|---|---|---|
| Graafiku ja hilinemiste andmete sünkroniseerimine ei tööta korrektselt |2 |3 |Lepime andmete struktuuri ja uuendamise loogika varakult kokku ning testime seda eraldi |
| Põhifunktsioonide arendus ei valmi tähtajaks |2 |3 |Seame prioriteediks „must“ nõuded ja jätame vähem olulised funktsioonid lõppu |
| Kasutajaliides ei ole õpilastele või juhtidele piisavalt arusaadav |2 |2 |Testime maketti ja prototüüpi varakult vähemalt mõne võimaliku kasutajaga ning parandame probleemsed kohad enne lõplikku versiooni |

**Edukriteerium:** Tellija kontrollib lõpus, kas õpilane/lapsevanem saab süsteemis vaadata õige bussiliini väljumisaega ja peatusi ning kas bussijuht/dispetšer saab süsteemis hilinemise märkida. Kui mõlemad tegevused töötavad ilma arendaja abita, on projekt edukalt lõpetatud — jah.
