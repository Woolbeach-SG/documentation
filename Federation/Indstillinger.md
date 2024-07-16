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

![Indstillinger - Aktivitetslog](Billedmateriale\IndstillingerAktivitetslog.png)

### 9.2 Rolleadministrator

Denne funktion bruges til at se og ændre dele af Adgangsstyrings virkemåde.

”NSIS log: Automatisk oprydning” aktiveres ved at afkrydse funktionen, angive antal måneder for ældste
logning, der skal gemmes. Klik på knappen ’Gem’ for at gemme den valgte opsætning.
”NSIS log: Automatisk validering” aktiveres ved at afkrydse funktionen, angive e-mailadressen og trykke
’Gem’.

![Indstillinger - Opsætning](Billedmateriale\IndstillingerOpsætning.png)

### 9.3 Konfigurer adgang

Denne funktion bruges af rettighedsadministratorer til at styre brugeradministratorernes adgang til funktio-
nerne i Adgangsstyring. Styringen er baseret på AD-grupper, der knyttes til en eller flere roller i Adgangssty-
ring. Hver af de fire moduler har et faneblad med et sæt roller, der kan knyttes til AD-grupper. Se eksem-
pler på billederne herunder.

En AD-gruppe fremsøges ved at klikke på Redigér-ikonet ud for feltet, hvorefter rettigheds-administratoren
enten kan se og udpege den ønskede gruppe i dropdown-listen, eller begynde at skrive de første bogstaver
i gruppens navn, hvorved listens elementer tilpasses.

**9.3.1 FK Administration**
Under FK Administration er der tre roller:
* AD læseadgang (Read only)
* AD redigeringsadgang (Administrator)
* FK Jobfunktionsrolle redigeringsadgang (STS Administrator)

Bemærk, at STS Administrator indeholder Redigeringsadgang, og Redigeringsadgang indeholder Læseadgang.

![Indstillinger - FK Administration](Billedmateriale\KonfigurerAdgangFKadministration.png)

**9.3.2 FK Organisation**

Under FK Organisation er der tre roller:
* AD læseadgang (Read only)
* AD redigeringsadgang (Administrator)
* Synkroniseringsadgang (Extended)

Bemærk, at Synkroniseringsadgang indeholder Redigeringsadgang, og Redigeringsadgang indeholder Læseadgang.

![Indstillinger - FK Organisation](Billedmateriale\KonfigurerAdgangFKOrganisation.png)

**9.3.3 ADFS Logs**
Under ADFS Logs er der tre roller:
* Logdata læseadgang (Read only)
* Auditøradgang (Auditør)
* Logdata sletteadgang (Administrator)

Bemærk, at Logdata sletteadgang indeholder logdata læseadgang, men _ikke_ Auditør

![Indstillinger - ADFS Logs](Billedmateriale\KonfigurerAdgangADFSLogs.png)

**9.3.4 Identifikationsmidler**
Under identifikationsmidler er der op til fem roller:
* Læseadgang (Read only)
* Auditøradgang (Auditør)
* Redigeringsadgang (Administrator)
* Kodeviseradministration (TOTP-administrator)
* ADgang til manuel verifikation (NSIS-RA Administrator)

Bemærk, at manuel verifikation er et tilkøbsmodul. 

![Indstillinger - Identifikationsmidler](Billedmateriale\KonfigurerAdgangIdentifikationsmidler.png)

**9.3.5 Certifikatstyring**
Under certifikatstyring er der kun én rolle:
* Certifikatstyring (Administrator)

![Indstillinger - Certifikatstyring](Billedmateriale\KonfigurerAdgangCertifikatstyring.png)

**9.3.6 Rettighedsadministration**
Under Rettighedsadministration er der kun én rolle - men til gengæld er det rollen, som giver adgang til at\
administrere alle de andre roller i Adgangsstyring.
* Rettighedsadministration  (Administrator)

I forbindelse med opsætningen af Adgangsstyring-modulet, vil det kun vær en domæneadministrator, der kan tilgå "Rettighedsadministration"-fanen\
og ingen af de andre faner vil være synlige. Domæneadministratoren sætter en AD-gruppe op, som skal være for dem, som må få adgang til at se og konfigurere\
adgangen til de moduler, der er tilgængelige i løsningen.\
Dette er en sikkerhedsforanstaltning, der sikrer fuld kontrol over hvem der har adgang til de enkelte moduler.\
For en mere detaljeret og teknisk uddybning, se da afsnittet 10.1 "Systemadministrator".

![Indstillinger - Rettighedsadministration](Billedmateriale\KonfigurerAdgangRettighedsadministration.png)

### 9.4 Konfigurer tilknytningsmuligheder
Administratorer med rettighed til at udføre denne funktion, kan konfigurere AD-gruppebaseret adgang for brugere til at tilknyutte ID-midler.

### 9.5 Licenser
Denne funktion viser hvilke licenserede tredjepartsprodukter Signaturgruppens Adgangsstyring anvender, herunder versionsnummer.

### 9.6 Skift FK-miljø
I øverste højre side findes oplysninger om brugeren man er logget ind med, og her er også mulighed for at skifte FK-miljø - antaget at FK-Administration/Organisation er tændt.
Denne funktion bruges til at skifte mellem de to fælleskommunale serviceplatforme; TEST og PROD. Det er således muligt at oprette eksempelvis Jobfunktionsroller\
på begge serviceplatforme i samme session. 

Bemærk, at denne funktion kun er til rådighed med en udvidet licens. 

![Indstillinger - Skift Miljø](Billedmateriale\IndstillingerSkiftmiljø.png)