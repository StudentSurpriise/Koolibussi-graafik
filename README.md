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

## Tools
![Tools](protsess/tools/comprasion.png)
