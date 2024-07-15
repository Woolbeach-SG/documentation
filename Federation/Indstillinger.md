---
title: 9 Indstillinger
layout: default
parent: Adgangsstyring
nav_order: 8
has_children: false
---

## 9 Indstillinger

Menuen ’Indstillinger’ bruges til at se og ændre Adgangsstyrings virkemåde.

![Indstillinger - Aktivitetslog](Billedmateriale\IndstillingerOversigt.png)

Menuen indeholder fem funktioner:

* Aktivitetslog
* Opsætning
* Konfigurer adgang
* Konfigurer tilknytningsmuligheder
* Licenser

### 9.1 Aktivitetslog
Denne funktion bruges til at inspicere administratorernes handlinger i forskellige systemer. For at kunne se
denne skal man være min. være Auditor.

Her kan der i eventfilteret og dato-intervallet angives et mere eller mindre specifikt søgekriterie for at inspi-
cere større eller mindre dele af de forskellige logs.

De fremfundne logninger vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søge-
kriteriet, så vises de på flere sider.

### 9.2 Rolleadministrator

Denne funktion bruges til at se og ændre dele af Adgangsstyrings virkemåde.

”NSIS log: Automatisk oprydning” aktiveres ved at afkrydse funktionen, angive antal måneder for ældste
logning, der skal gemmes. Klik på knappen ’Gem’ for at gemme den valgte opsætning.
”NSIS log: Automatisk validering” aktiveres ved at afkrydse funktionen, angive e-mailadressen og trykke
’Gem’.

### 9.3 Konfigurer adgang

Denne funktion bruges af rettighedsadministratorer til at styre brugeradministratorernes adgang til funktio-
nerne i Adgangsstyring. Styringen er baseret på AD-grupper, der knyttes til en eller flere roller i Adgangssty-
ring. Hver af de fire moduler har et faneblad med et sæt roller, der kan knyttes til AD-grupper. Se eksem-
pler på billederne herunder.

En AD-gruppe fremsøges ved at klikke på Redigér-ikonet ud for feltet, hvorefter rettigheds-administratoren
enten kan se og udpege den ønskede gruppe i dropdown-listen, eller begynde at skrive de første bogstaver
i gruppens navn, hvorved listens elementer tilpasses.