---
title: 8 FBRS Rettigheder
layout: default
parent: Adgangsstyring
nav_order: 7
has_children: false
---

## 8 FBRS Rettigheder

Modulet ”FBRS” bruges til overblik, udtræk og håndtering af rettigheder fra MitID Erhverv.

![FBRS - Overblik](Billedmateriale\FBRSOverblik.png)

### 8.1 Governance udtræk

Ved at skrive sin mailadresse og trykke på knappen ”Hent governance udtræk” modtages en oversigt over
alle rettigheder, der er sat i MitID Erhverv, i alle cvr-nummer – både rettigheder fra grupper og individuelle.
Dette er en god måde at danne sig et overblik over hvilke rettigheder man gør brug af og hvordan en potentiel
fordeling kunne se ud.

### 8.2 Fjern ALLE direkte rettigheder

Ved at trykke ”Fjern ALLE direkte rettigheder” fjernes samtlige direkte rettigheder, på tværs af forbundne CVR.

### 8.3 Opsætning

I venstre side ses en liste over alle organisationer, som FBRS modulet er i stand til at agere på vegne af. Listen er baseret på de certifikater der er til rådighed i Certifikatstyring.

### 8.4 Rettighedsgrupper i valgt CVR

I højre side er der en oversigt over hvilke rettighedsgrupper, der er i ét specifikt CVR i MitID Erhverv.
Her kan der både oprettes AD-grupper direkte eller tilføjes en allerede eksisterende AD-gruppe.
Under ”Navn” ses hvad brugerrettighedsgrupperne hedder i MitID Erhverv og ”AD-gruppenavn” er det som
AD-gruppen hedder.

#### 8.4.1 Tilføj gruppe
Når der trykkes ”Tilføj gruppe” tilføjes der både en AD-gruppe og en brugerrettighedsgruppe i MitID Erhverv automatisk.

#### 8.4.2 Opret grupper
Når der trykkes ”Opret grupper” oprettes der en AD-gruppe, på baggrund af de brugerrettighedsgrupper i
MitID Erhverv som endnu ikke har tildelt en AD-gruppe. AD-grupperne vil navngives på formen "[CVR] [Navn på gruppe]"

#### 8.4.3 Fjern tilknytninger til slettede AD-grupper
Når der trykkes "Fjern tilknytninger til slettede AD-grupper", fjernes der tilknytninger til AD-grupper der ikke længere kan findes i AD. 

### 8.5 Rettighedsoversigt
Ved en valgt rettighedsgruppe, vises en oversigt over de AD-gruppe tilknytning, Scope og roller.

#### 8.5.1 Ændr Ad-gruppe
Når der trykkes "Ændr Ad-gruppe" kan indtaste full qualified domain name på den ønskede AD-gruppe der skal tilknyttes.

#### 8.5.2 Ændr Scope
Når der trykkes på "Ændr scope" kan man afgrænse rettighedsgruppen til et specifikt PU-nummer, SE-nummer eller CVR. 

#### 8.5.3 Tilføj Roller
Når der trykkes "Tilføj roller" er det muligt at fremsøge og vælge op til flere roller fra MitID Erhvervs rolle-katalog, og tilføje det til gruppen.

#### 8.5.4 Fjern Rolle
Når der trykkes på "Fjern rolle", bliver den enkelte valgte rolle fjernet fra rettighedsgruppen. 

#### 8.5.5 Slet gruppe
Når der trykkes på "Slet gruppe" slettes rettighedsgruppen fra MitID Erhverv. 