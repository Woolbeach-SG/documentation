---
title: Adgangsstyring
layout: home
nav_order: 2 
---

## Adgangsstyring

### Administrer brugeres identifikationsmidler og adgange til systemerne i den fælleskommunale (FK) rammearkitektur og MitID Erhverv

Juli 2024

## Indholdsfortegnelse
- 1 Indledning Indholdsfortegnelse
- 2 Roller og rettigheder
    - 2.1 Konfiguration
- 3 Identifikationsmidler
    - 3.1 Administrér identifikationsmidler
    - 3.2 Udtræk, revision & validering
    - 3.3 Tilføj / fjern token-registreringer
- 4 FK Administration
    - 4.1 Opret jobfunktionsrolle
    - 4.2 Se / redigér jobfunktionsroller
    - 4.3 Se / redigér AD-opmærkninger
- 5 FK Organisation
    - 5.1 Opret funktion
    - 5.2 Administration
    - 5.3 Synkronisering
    - 5.4 Udbetalende enheder
    - 5.5 Henvendelsessteder
- 6 ADFS Log
    - 6.1 Fremsøg hændelser
    - 6.2 Se diagrammer
    - 6.3 Udtræk og validering
    - 6.4 Oprydning
    - 6.5 Se loginfejl
    - 6.6 Fremsøg konfigurationsændringer
- 7 Certifikatstyring
    - 7.1 Administrér certifikater
    - 7.2 Tilføj features
- 8 Indstillinger
    - 8.1 Aktivitetslog
    - 8.2 Opsætning
    - 8.3 Konfigurer adgang
    - 8.4 Konfigurer tilknytningsmuligheder
    - 8.5 Licenser
    - 8.6 Skift FK-miljø
- 9 Tekniske konfigurationsdetaljer Navitas ▪ Inge Lehmanns Gade 10 ▪ 8000 Aarhus C info@signaturgruppen.dk
    - 9.1 Systemadministrator
    - 9.2 Rolleadministrator
    - 9.3 Brugeradministrator
    - 9.4 Lokal administration
    - 9.5 Begrænset administration
    - 9.6 Databasebeskrivelse


### Indledning Indholdsfortegnelse

Adgangsstyring fra Signaturgruppen er et modulopbygget system, der gør det muligt for organisationen at
administrere brugeres identifikationsmidler, certifikater og adgange til systemerne i den fælleskommunale
(FK) rammearkitektur.

Adgangsstyring indeholder følgende moduler:

```
▪ Identifikationsmidler
Administration af brugeres identifikationsmidler til brug i føderative systemer, hvor tjenester kræ-
ver to-faktor adgang.
▪ FK Administration
Administration af brugere og deres jobfunktionsroller og tilhørende opmærkninger til brug for ad-
gang til fagsystemer i FK rammearkitekturen.
▪ FK Organisation
Administration af organisatoriske funktioner og tilhørende opmærkninger til brug i støttesystemet
Organisation i FK rammearkitekturen.
```
```
▪ ADFS Log
Inspektion af data opsamlet i forbindelse med brugeres føderative logins via ADFS.
▪ Certifikatstyring
Administration af certifikater
▪ FBRS
Oversigt, udtræk og håndtering af rettigheder fra MitID Erhverv.
▪ Indstillinger
Her findes aktivitetslog til udtræk, detaljer om opsætning, konfiguration af adgangsgivende AD-
grupper både for identifikationsmidler og for adgangen til Adgangsstyring-portalen, samt liste over
hvilke licenserede tredjepartsprodukter Adgangsstyring anvender.
```
Modulerne er beskrevet i separate afsnit i denne vejledning.

Ikke alle moduler er relevante for alle organisationer, og hvert modul kan derfor aktiveres eller deaktiveres
efter behov i samarbejde med Signaturgruppen. Hvis alle moduler er aktiveret, så ser hovedmenuen ud
som vist herunder.

## 2 Roller og rettigheder

Adgangsstyring anvendes af _brugeradministratorer_ til at administrere brugernes identifikationsmidler, ad-
gang til logs samt rettigheder i FK rammearkitekturen. Brugeradministratorernes egne rettigheder til at be-
nytte moduler og funktioner i Adgangsstyring administreres af en _rettighedsadministrator_.

Oversigt:

```
▪ Rettighedsadministrator (rettighedskonfiguration)
Melder brugeradministratorer ind og ud af brugeradministratorgrupper i AD og tilknytter brugerad-
ministratorgrupper til roller inde i Adgangsstyring (under Indstillinger).
```
```
▪ Brugeradministrator (brugerkonfiguration)
Betjener en eller flere funktioner i modulerne i Adgangsstyring.
```
### 2.1 Konfiguration

Grundlaget for tildeling af rettigheder i Adgangsstyring er AD-grupper.
Afsnit 9.3 viser, hvilke roller der kan knyttes AD-grupper til.

Konfiguration af Adgangsstyring foregår på følgende måde:

1. AD-administratoren opretter AD-grupper til brug for rolletildeling i Adgangsstyring
2. AD-administratoren opretter en AD-gruppe til rettighedsadministratorer ("R-gruppen")
3. AD-administratoren melder en rettighedsadministrator ind i R-gruppen
4. Rettighedsadministratoren melder brugeradministratorerne ind i de relevante AD-grupper
5. En domæneadministrator logger ind i Adgangsstyring, og udpeger R-gruppen via Indstillinger > Kon-
   figurer adgang > Rettighedsadministration
6. Rettighedsadministratoren logger ind i Adgangsstyring, og knytter AD-grupperne til de respektive
   roller (se afsnit 9.3)

Herefter kan brugeradministratorerne logge ind i Adgangsstyring og udføre deres opgaver.

## 3 Identifikationsmidler

Modulet Identifikationsmidler bruges til administration af brugere og deres identifikationsmidler til brug i
føderative systemer, hvor tjenester kræver to-faktor adgang.

Modulet indeholder tre overordnede funktioner:

```
▪ Administrér identifikationsmidler
▪ Udtræk lister til revision
▪ Tilføj / fjern token-registreringer
```
### 3.1 Administrér identifikationsmidler

Fremsøg en bruger ved at indtaste mindst de to første bogstaver i brugernavnet og klik på Søg.
Det eller de brugernavne, der matcher søgningen vises i en liste under søgefeltet.
Klik på det brugernavn hvis detaljerede oplysninger ønskes vist.

I billedet med detaljerede brugeroplysninger er der fire faneblade:

```
▪ Administration viser oplysninger om brugerens AD-konto
▪ Historik viser brugerens fulde historik over identifikationsmidler
▪ Administrationshistorik viser administrative hændelser og integritetssikringen her af
```
- fx tilknytning og spærring af identifikationsmidler
  ▪ Trafik viderestiller til modulet ADFS Log, hvor login-trafik kan
  fremsøges – tilføjer automatisk brugernavnet


Signaturgruppen A/S [http://www.signaturgruppen.dk](http://www.signaturgruppen.dk)
Navitas ▪ Inge Lehmanns Gade 10 ▪ 8000 Aarhus C info@signaturgruppen.dk

Afhængigt af tildelte roller, så er det under Administration muligt for en administrator at

```
▪ tilknytte SoloID app til brugerens AD-konto
▪ tilknytte Yubikey til brugerens AD-konto
▪ udstede engangskoder til brugeren (kan bruges som alternativ til login med privat MitID)
▪ fjerne identifikationsmidler fra brugerens konto
▪ udstede NSIS registreringskoder til brugeren (kan bruges som alternativ til personverifikation med
privat MitID – kun hvis man har tilkøbt manuel registrering og er RA-administrator)
```

Hvis der er registreret et eller flere identifikationsmidler på brugerens konto, så ses de i bunden af Admini-
strationsfanebladet.

I modsat fald er listen tom.

Klik på det røde kryds ud for et identifikationsmiddel for at fjerne det fra brugerens konto.

Bekræft handlingen for at gennemføre sletningen.

Hvis, der er registreret en mail på brugerens AD-konto, så modtager brugeren en e-mail fra systemet inde-
holdende en spærringskvittering.

### 3.2 Udtræk, revision & validering

Denne funktion tilbyder diverse former for udtræk af data til brug for statistik og revision. Udtrækkene le-
veres i CSV-filformat.
Herunder er der tre faneblade:

```
▪ Udtræk hent lister over alle registrerede ID-midler og kodevisere
▪ Revision hent lister til revision inkl. tidsperiode filtrering
▪ Validering her kan sendes en e-mail med validering af integritetsbeskyttelsen
```

Under revisionsfanebladet er det muligt at angive et tidsinterval og hente lister med NSIS-relevante hæn-
delser og registreringer.

**Her er et eksempel for Identitetssikringer:**

Først vælges hvilken tidsperiode man ønsker dokumenteret:

Ved at trykke ”Hent Identitetssikringer” begynder download af .csv filen der er navngivet med Revision -
den valgte liste (her: identitetssikring) samt tidsperioden.

Listen indeholder de identitetssikringer, der er gjort i den angivet periode, User Principle Name (UPN) for
brugerne, den anvendte loginmetode og evt. hvilken administratorer der foretog identitetssikringen, hvis
man har tilkøbt det manuelle registreringsmodul.

Under Valideringsfanen kan der ligeledes filtreres efter en specifik tidsperiode. Indtast mailadressen som
integritetsbeskyttelsen skal sendes til og tryk ”Test integritetsbeskyttelse”.

Et eksempel på hvordan e-mailen kan se ud:

### 3.3 Tilføj / fjern token-registreringer

Administratorer med rettighed til at udføre denne funktion kan lægge Kodeviser-registreringer ind i syste-
mets database, eller fjerne registreringer fra databasen.

En bruger kan kun tilknytte en forud-registreret kodeviser til sin AD-konto som et to-faktoridentifikations-
middel.

## 4 FK Administration

Modulet FK Administration bruges til administration af brugere og deres jobfunktionsroller og tilhørende
opmærkninger til brug for adgang til fagsystemer i den fælleskommunale (FK) rammearkitektur.

Modulet indeholder tre overordnede funktioner:

```
▪ Opret jobfunktionsrolle
▪ Se / redigér jobfunktionsroller
▪ Se / redigér AD-opmærkninger
```
### 4.1 Opret jobfunktionsrolle

Denne funktion bruges til at oprette jobfunktionsroller i FK Administration og (optionelt) tilhørende AD-
gruppe i det lokale AD. En jobfunktionsrolle er i AD repræsenteret ved en gruppe som de brugere, der skal
have rollen skal være medlem af. Man kan enten udpege en eksisterende gruppe, eller angive, at der skal
oprettes en ny gruppe. Hvis der skal oprettes en ny gruppe, så skal man angive, hvilken OU-knude gruppen
skal placeres under. Hvis man ønsker at placere gruppen under en ny OU-knude (som ikke findes i forvejen),
så er man nødt til at oprette den nye OU-knude inden man vælger at oprette jobfunktionsrollen.

Klik på Opret jobfunktionsrolle og følg guiden.

### 4.2 Se / redigér jobfunktionsroller

Denne funktion bruges til at se, ændre og slette jobfunktionsroller i FK Administration og (optionelt) tilhø-
rende AD-grupper i det lokale AD.

Funktionen kan bruges til at

```
▪ Se oplysninger om jobfunktionsroller (navn, brugersystemrolle, brugersystem, ad-gruppe)
▪ Slette jobfunktionsroller i FK Administration
▪ Opmærke AD-grupper med jobfunktionsroller
▪ Tilføje brugersystemroller til jobfunktionsroller
▪ Slette brugersystemroller fra jobfunktionsroller
```
Klik på Se/redigér jobfunktionsroller og følg guiden.

### 4.3 Se / redigér AD-opmærkninger

Denne funktion bruges til at administrere opmærkninger i det lokale AD.

Funktionen indeholder tre underordnede indgange svarende til de AD-elementer, der kan opmærkes:

```
▪ Brugere (AD user-objekter)
▪ Grupper (AD security groups)
```

```
▪ Organisatoriske enheder (AD organizational units)
```
Eksempel på opmærkninger:
På brugere og grupper gemmes opmærkningen i attributten altSecurityIdentities.
På organisatoriske enheder gemmes opmærkningen i attributten businessCategory.

Begge attributter er multivalued og kan indeholde flere opmærkninger.

**4.3.1 Brugere**

Funktionen kan bruges til at

▪ Fremsøge brugere ud fra brugernavn og/eller jobfunktionsrolle
▪ Se oplysninger om en brugers opmærkning
▪ Oprette en brugers opmærkning (jfr, kle, osv.)
▪ Slette en brugers opmærkning (jfr, kle, osv.)
▪ Melde en bruger ind/ud af en opmærket gruppe
**4.3.2 Grupper**

Funktionen kan bruges til at

```
▪ Fremsøge AD-grupper ud fra gruppenavn
▪ Se oplysninger om en AD-gruppes opmærkning
▪ Oprette en AD-gruppes opmærkning (jfr, kle, osv.)
▪ Slette en AD-gruppes opmærkning (jfr, kle, osv.)
▪ Melde brugere ind/ud af en AD-gruppe
```

**4.3.3 Organisatoriske enheder**

Funktionen kan bruges til at

```
▪ Fremsøge organisatoriske enheder (OU) ud fra OU-navn
▪ Se oplysninger om en OU's opmærkning
▪ Oprette en OU's opmærkning (jfr, kle, osv.)
▪ Slette en OU's opmærkning (jfr, kle, osv.)
▪ Oprette en AD-gruppe under OU'en
```

## 5 FK Organisation

Modulet FK Organisation bruges til administration af organisatoriske funktioner og tilhørende opmærknin-
ger til brug i støttesystemet Organisation i den fælleskommunale (FK) rammearkitektur.

Modulet indeholder tre overordnede funktioner:

```
▪ Opret funktion
▪ Administration
▪ Synkronisering
```
### 5.1 Opret funktion

Denne funktion bruges til at oprette organisatoriske funktioner (fx udbetalende enheder og henvendelses-
steder). De organisatoriske funktioner gemmes som opmærkninger i det lokale AD, og oprettes efterføl-
gende i FK Organisation via synkroniseringsservicen FK Organisationssynkronisering fra Signaturgruppen.

Klik på Opret funktion og følg guiden.

Læs mere om oprettelse af udbetalende enheder og henvendelsessteder i afsnittene herunder.

### 5.2 Administration

Denne funktion bruges til at oprette, se, ændre og slette opmærkninger på AD-grupper og organisatoriske
funktioner, der skal synkroniseres til FK Organisation. Eksempler på opmærkninger er fx team/afdeling, KLE,
eller ”udelad gruppe fra synkronisering”. De organisatoriske funktioner gemmes som opmærkninger i det
lokale AD, og oprettes efterfølgende i FK Organisation via synkroniseringsservicen FK Organisationssynkro-
nisering fra Signaturgruppen.

Klik på Administration og følg guiden.

### 5.3 Synkronisering

FK Organisationssynkronisering fra Signaturgruppen synkroniserer normalt data fra AD til FK Organisation
en gang i døgnet – typisk om natten. Denne funktion (Synkronisering) kan bruges til at

- Straks-synkronisere en specifik AD-konto til FK Organisation
- Starte en fuld synkronisering

Klik på Synkronisering og følg guiden.

### 5.4 Udbetalende enheder

Registreringsmønsteret ”Udbetalende Enheder” er beskrevet i afsnit 6.3 i KOMBIT’s dokument ”Anvisninger
til anvendelse af Organisation”, og er illustreret på følgende måde:

Læg mærke til, at den udbetalende enhed skal relateres til en LOS-adresse. Den underliggende synkronise-
ring af LOS-information til FK Organisation sættes op i synkroniseringsservicen i samarbejde med Signatur-
gruppen.

Fremgangsmåde ved oprettelse af udbetalende enhed:

1. Klik på Opret og vælg ”Udbetalende Enhed” under type.
2. Giv den udbetalende enhed et navn og udpeg den organisatoriske enhed, der står for udbetalin-
   gerne.
3. Tilføj eventuelt opgaver til den udbetalende enhed (fx niveau og/eller KLE).
4. Tilknyt de organisatoriske enheder, der skal anvende den udbetalende enhed. Det kan være enhe-
   den selv og/eller andre enheder.

Den udbetalende enhed bliver i første omgang oprettet i det lokale AD, og i forbindelse med den natlige
synkronisering oprettes enheden også i FK Organisation. Hvis der er behov for en straks-oprettelse, så kan
en synkronisering igangsættes med det samme under menupunktet Synkronisering.

### 5.5 Henvendelsessteder

Registreringsmønsteret ”Henvendelsessteder” er beskrevet i afsnit 6.4 i KOMBIT’s dokument ”Anvisninger
til anvendelse af Organisation”, og er illustreret på følgende måde:

Fremgangsmåde ved oprettelse af henvendelsessted:

1. Klik på Opret og vælg ”Henvendelsessted” under type.
2. Giv henvendelsesstedet et navn og udpeg den organisatoriske enhed, der står for kontakten med
   borgerne.
3. Tilføj eventuelt opgaver til henvendelsesstedet (fx niveau og/eller KLE).
4. Tilknyt de organisatoriske enheder, hvis egne adresseoplysninger skal erstattes af henvendelsesste-
   dets kontaktoplysninger i kommunikation med borgerne. Det kan være enheden selv og/eller andre
   enheder.

Henvendelsesstedet bliver i første omgang oprettet i det lokale AD, og i forbindelse med den natlige syn-
kronisering oprettes enheden også i FK Organisation. Hvis der er behov for en straks-oprettelse, så kan en
synkronisering igangsættes med det samme under menupunktet Synkronisering.

## 6 ADFS Log

Modulet ADFS Log bruges til inspektion af data opsamlet i forbindelse med brugeres fødererede logins via
ADFS.

Modulet indeholder tre overordnede funktioner:

```
▪ Fremsøg hændelser
▪ Se diagrammer
▪ Udtræk og validering
▪ Oprydning
▪ Se loginfejl
▪ Fremsøg konfigurationsændringer
```
### 6.1 Fremsøg hændelser

Denne funktion bruges til at inspicere indholdet af logninger.

Angiv et mere eller mindre specifikt søgekriterie for at inspicere større eller mindre dele af loggen.

Mulige søgekriterier:

```
▪ Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
▪ Specifik relying party
▪ Datointerval
▪ kombinationer af ovennævnte
```
For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’.
De fremfundne logninger vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søge-
kriteriet, så vises de på flere sider.

Klik på en logning for at folde den ud og se detaljerne i den pågældende logning.

### 6.2 Se diagrammer

Denne funktion bruges til at danne et grafisk overblik over logningerne.

Start med at vælge det faneblad, der svarer til den ønskede oversigt:

```
▪ Dagsoversigt fordeling af logins hen over timerne i et døgn
▪ Månedsoversigt fordeling af logins hen over dagene i en måned
▪ Fordeling af relying party fordeling af logins på tjenester i en periode
```
Angiv det ønskede tidsinterval og klik på Opdater.

De fremfundne logninger vises i en graf under søgefeltet.

### 6.3 Udtræk og validering

Denne funktion giver et udtræk af alle brugernes seneste registrerede 2 - faktor login. Listen indeholder hvem
der har brugt hvad og hvornår.
Validering af ADFS-logs.

### 6.4 Oprydning

Denne funktion bruges til at slette ældre ADFS-logfiler. Der slettes permanent filer der er ældre end det an-
givne antal måneder. Dvs. hvis man angiver ”6” så slettes ADFS-logfiler der er ældre end 6 måneder.
Kan kun gøres hvis man har redigeringsadgang.

### 6.5 Se loginfejl

Denne funktion tilbyder også Log og Grafer svarende til de ovenfor beskrevne funktioner, men viser mislyk-
kede logins i stedet for succesfulde logins.

**6.5.1 Fremsøg hændelser**

Angiv et mere eller mindre specifikt søgekriterie for at inspicere større eller mindre dele af loggen.

Mulige søgekriterier:

```
▪ Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
▪ Specifik relying party
▪ Datointerval
▪ kombinationer af ovennævnte
```
For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’. De fremfundne logninger
vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søgekriteriet, så vises de på flere
sider.

**6.5.2 Se diagrammer**

Denne funktion bruges til at danne et grafisk overblik over logningerne.

Start med at vælge det faneblad, der svarer til den ønskede oversigt:

```
▪ Dagsoversigt fordeling af fejlede logins hen over timerne i et døgn
▪ Månedsoversigt fordeling af fejlede logins hen over dagene i en måned
▪ Fordeling af brugernavne fordeling af fejlede logins for specifikke brugere i en periode
```
Angiv det ønskede tidsinterval og klik på Opdater.
De fremfundne logninger vises i en graf under søgefeltet.

### 6.6 Fremsøg konfigurationsændringer

Denne funktion bruges til at få vist ændringer på ADFS-konfigurationen, det kan fx være et certifikatskifte.

Angiv et mere eller mindre specifikt søgekriterie for at inspicere større eller mindre dele af loggen.

Mulige søgekriterier:

```
▪ Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
▪ Datointerval
```
For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’.
De fremfundne logninger vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søge-
kriteriet, så vises de på flere sider.
Klik på en logning for at folde den ud og se detaljerne i den pågældende logning.

## 7 Certifikatstyring

Modulet Certifikatstyring bruges til administration af certifikater.

Modulet indeholder en overordnet funktion:
▪ Administrér certifikater

### 7.1 Administrér certifikater

Tilføj et nyt certifikat ved enten at importere et eksisterende certifikat eller ved at udstede et certifikat ud
fra et referencenummer og en pinkode.

**7.1.1 Importér certifikat**

**7.1.2 Opret administrationscertifikat**

### 7.2 Tilføj features

Efterfølgende vil certifikatet fremgå på certifikatoversigten og ved at trykke på det pågældende certifikat kan
der tilføjes forskellige features.

**7.2.1 IdMSync feature**

Denne feature bruges til at administrere det systemcertifikat der skal oprettes til en IdM-sync løsning.
Under Gruppe DN skal synkroniseringsgruppenavnets Distinguished Name stå. Et eksempel kunne være:
▪ CN=MitIDErhverv,OU=gruppe,OU=organisation,OU=securitygroup,DC=domæne,DC=dk

De forskellige bokse der kan afkrydses, betyder følgende;
▪ Bestil ID-midler:
o Skal afkrydses hvis I ønsker at IdM-sync løsningen skal bestille ID-midler (kodeviser, chip,
kodeoplæser) til brugere, der har valgt en af disse ID-midler.
o Har I oplyst et EAN-nummer i MitID Erhverv, og ønsker at IdM-sync skal bestille ID-midler,
skal I notere det oplyste EAN-nummer i boksen nederst på siden.

```
▪ Opsæt adresse på gruppe (standard er læst fra AD-bruger):
o Skal afkrydses hvis I ønsker, at de ID-midler, der bestilles gennem IdM-sync løsningen, skal
sendes til fx hovedkontoret, hvor I derefter selv står for distribueringen.
o (Som standard aflæses adressen direkte på den pågældende AD-bruger og ID-midlet sendes
til den adresse, der er oplyst i AD’et.)
```
**7.2.2 CERTADMIN feature**

Når certifikatet er oprettet i MitID Erhverv kan der krydses af om certifikatet skal have ’Adgang til håndtering
af certifikater’. Hvis denne er afkrydset på certifikatet, så vil denne feature fremgå på certifikatet der er uplo-
adet i Adgangsstyring.

**7.2.3 IDMADMIN feature**

Når certifikatet er oprettet i MitID Erhverv kan der krydses af om certifikatet må få ’Adgang til IdM services i
MitID Erhverv’. Hvis dette er afkrydset, vil denne feature fremgå på certifikatet.

**7.2.4 STSADMIN feature**

Denne feature anvendes til at uploade systemcertifikat til FK rammearkitekturen.

**7.2.5 SC feature**

Denne feature er kun relevant for Signaturcentraler med OCES3 funktionalitet.

## 8 FBRS Rettigheder

Modulet ”FBRS” bruges til overblik, udtræk og håndtering af rettigheder fra MitID Erhverv.

### 8.1 Governance udtræk

Ved at skrive sin mailadresse og trykke på knappen ”Hent governance udtræk” modtages en oversigt over
alle rettigheder, der er sat i MitID Erhverv, i alle cvr-nummer – både rettigheder fra grupper og individuelle.
Dette er en god måde at danne sig et overblik over hvilke rettigheder man gør brug af og hvordan en potentiel
fordeling kunne se ud.

### 8.2 Opsætning

I venstre side ses en liste over alle organisationer, som der er

### 8.3 Rettighedsgrupper i valgt CVR

I højre side er der en oversigt over hvilke rettighedsgrupper, der er i ét specifikt CVR i MitID Erhverv.
Her kan der både oprettes AD-grupper direkte eller tilføjes en allerede eksisterende AD-gruppe.
Under ”Navn” ses hvad brugerrettighedsgrupperne hedder i MitID Erhverv og ”AD-gruppenavn” er det som
AD-gruppen hedder.

Når der trykkes ”Tilføj gruppe” tilføjes der både en AD-gruppe og en brugerrettighedsgruppe i MitID Erhverv.

Når der trykkes ”Opret grupper” oprettes der en AD-gruppe, på baggrund af de brugerrettighedsgrupper i
MitID Erhverv.

### 8.4 Fjern rettigheder

Ved at trykke ”Fjern ALLE direkte rettigheder” fjernes

### 8.5 Fjern tilknytninger til slettede AD-grupper

## 8 Indstillinger

Menuen ’Indstillinger’ bruges til at se og ændre Adgangsstyrings virkemåde.

Menuen indeholder fem funktioner:

```
▪ Aktivitetslog
▪ Opsætning
▪ Konfigurer adgang
▪ Konfigurer tilknytningsmuligheder
▪ Licenser
```
### 8.1 Aktivitetslog

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

### 8.3 Konfigurer adgang

Denne funktion bruges af rettighedsadministratorer til at styre brugeradministratorernes adgang til funktio-
nerne i Adgangsstyring. Styringen er baseret på AD-grupper, der knyttes til en eller flere roller i Adgangssty-
ring. Hver af de fire moduler har et faneblad med et sæt roller, der kan knyttes til AD-grupper. Se eksem-
pler på billederne herunder.

En AD-gruppe fremsøges ved at klikke på Redigér-ikonet ud for feltet, hvorefter rettigheds-administratoren
enten kan se og udpege den ønskede gruppe i dropdown-listen, eller begynde at skrive de første bogstaver
i gruppens navn, hvorved listens elementer tilpasses.

**9.3.1 FK Administration**

Under FK Administration er der tre roller:
▪ AD læseadgang (Read Only)
▪ AD redigeringsadgang (Administrator)
▪ FK jobfunktionsrolle redigeringsadgang (STS Administrator)

Bemærk, at STS Administrator indeholder Administrator, og Administrator indeholder Read Only.

**9.3.2 FK Organisation**

Under FK Organisation er der tre roller:
▪ AD læseadgang (Read Only)
▪ AD redigeringsadgang (Administrator)
▪ Synkroniseringsadgang (Extended)

Bemærk, at Extended indeholder Administrator, og Administrator indeholder Read Only.

**9.3.3 ADFS logs**

Under ADFS logs er der tre roller:
▪ Logdata læseadgang (Read Only)
▪ Auditøradgang (Auditør)
▪ Logdata sletteadgang (Administrator)

Bemærk, at Administrator indeholder Read Only, men ikke Auditør.

**9.3.4 Identifikationsmidler**

Under Identifikationsmidler er der op til fem roller:
▪ Læseadgang (Read Only)
▪ Auditør adgang (Auditør)
▪ Redigeringsadgang (Administrator)
▪ Kodeviser registreringsadgang (TOTP-administrator)
▪ Adgang til manuel verifikation (NSIS-RA Administrator)

Bemærk, at Adgang til manuel verifikation (NSIS-RA Administrator) er et tilkøbsmodul.

**9.3.5 Certifikatstyring**

Under Certifikatstyring er der kun én rolle.
▪ Administration af certifikater (Administrator)

**9.3.6 Rettighedsadministration**

Under Rettighedsadministration er der kun én rolle – men til gengæld er det rollen, som giver adgang til alle
de andre roller i Adgangsstyring.
▪ Rettighedsadministration (Administrator)

I forbindelse med opsættelsen af Adgangsstyring modulet, vil det kun være en domæneadministrator, som
kan tilgå ”Rettighedsadministration”- fanen og ingen af de andre faner vil være synlige. Domæneadministra-
toren sætter en AD-gruppe op, som skal være for dem, som må få adgang til at se og konfigurere adgangen
til de moduler, der er tilgængelige i den pågældende løsning. Dette er en sikkerhedsforanstaltning, der sikrer
fuld kontrol over hvem der har adgang til hvad. Se en mere detaljeret og teknisk uddybning i afsnittet: Sy-
stemadministrator.

Det er også muligt at angive hvilke AD-grupper, det skal være muligt at vælge for administratorbrugerne
under de forskellige faner.

### 8.4 Konfigurer tilknytningsmuligheder

Administratorer med rettighed til at udføre denne funktion kan konfigurere AD-gruppebaseret adgang for
brugere til at tilknytte ID-midler.

### 8.5 Licenser

Denne funktion viser hvilke licenserede tredjepartsprodukter Adgangsstyring anvender samt i hvilken ver-
sion.

### 8.6 Skift FK-miljø

I øverste højre side findes oplysninger om brugeren man er logget ind med og her er også mulighed for at
skrifte FK-miljø. Denne funktion bruges til at skifte mellem de to fælleskommunale serviceplatforme TEST
og PROD. Det er således muligt at oprette fx jobfunktionsroller på begge serviceplatforme i samme session
og med samme Adgangsstyringsværktøj.

Bemærk, at denne funktion kun er til rådighed med en udvidet licens.

## 10 Tekniske konfigurationsdetaljer

Adgangsstyring anvendes af _brugeradministratorer_ til at administrere brugernes identifikationsmidler samt
rettigheder i FK rammearkitekturen. Brugeradministratorernes egne rettigheder til moduler og funktioner i
Adgangsstyring administreres af _rolleadministratorer_. _Systemadministratorer_ hjælper rolleadministrato-
rerne med at ændre systemets underliggende konfiguration, når det er nødvendigt.

Oversigt:

```
▪ Systemadministrator (systemkonfiguration)
Opretter brugeradministratorgrupper og rolleadministratorgrupper i AD og melder rolleadministra-
torer ind og ud af rollegrupperne.
▪ Rolleadministrator (rettighedskonfiguration)
Melder brugeradministratorer ind og ud af brugeradministratorgrupper i AD og tilknytter brugerad-
ministratorgrupper til roller i Adgangsstyring.
```
```
▪ Brugeradministrator (brugerkonfiguration)
Betjener en eller flere funktioner i modulerne i Adgangsstyring.
```
### 9.1 Systemadministrator

Adgangsstyring er en føderativ web-tjeneste, hvilket betyder, at brugeradministratorernes login til værktø-
jet foregår via en ADFS i organisationen. I ADFS’en er der en relying party trust, der hører til Adgangsstyring,
og i de tilhørende claim rules kan systemadministratoren knytte roller og AD-rollegrupper sammen. Signa-
turgruppen leverer et sæt af opstartsregler som organisationen kan tilpasse.

Den nemmeste måde at knytte roller og AD-grupper sammen på, er via Adgangsstyringsmenuen ’Indstillin-
ger’ – se afsnittet: Konfigurer adgang. Resten af dette afsnit indeholder en mere detaljeret og teknisk for-
klaring af rettighedsstyringen.

En typisk rolletildelingsregel er baseret på en claim rule template der hedder ”Send Group Membership as a
Claim”. I claim rule language ser en typisk regel ud som vist herunder, hvor c’s Value er en AD-gruppes
objectGUID, og issue-value er den Adgangsstyringsrolle som reglen udløser.

c:[
Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid",
Value == "S- 1 - 5 - 21 - 119678056 - 279223570 - 496954922 - 31554",
Issuer == "AD AUTHORITY"]
=> issue(
Type = "http://schemas.microsoft.com/ws/2008/06/identity/claims/role",
Value = "IDM_ADMIN",
Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, ValueType = c.ValueType);

Systemadministratoren og rolleadministratoren fastlægger relationen mellem AD-rollegrupper og roller – fx
om en given AD-rollegruppe skal repræsentere en enkelt eller flere roller. Herefter opretter systemadmini-
stratoren rollegrupperne i AD, hvis de ikke allerede findes, og afspejler relationen til rollerne via claim rules
i ADFS’en.

I det helt simple tilfælde knyttes alle roller til en enkelt rollegruppe med den konsekvens, at alle der er
medlem af rollegruppen får adgang til alle funktioner i Adgangsstyring. Et mere detaljeret eksempel følger
herunder.

**10.1.1 Eksempel**

Antag at organisationen har følgende brugeradministratorer:

```
▪ Anders
Superadministrator som skal have adgang til alt i Adgangsstyring.
▪ Bent
FK-administrator som skal have adgang til alt under FK Administration.
▪ Carsten
Lokal administrator for SAPA og skal have adgang til at give brugere rettigheder i SAPA.
▪ Dennis
Lokal administrator for KSD og skal have adgang til at give brugere rettigheder i KSD.
▪ Erik
Auditør som skal have adgang til at se logs.
```
Systemadministratoren og rolleadministratoren har fastlagt nedenstående relation mellem roller, rettighe-
der og AD-rollegrupper. Under hver AD-rollegruppe er der angivet, hvilke brugeradministratorer, der er
meldt ind for at de kan opnå de nødvendige rettigheder i Adgangsstyring.

Relationer:

```
▪ AD-gruppe: Adgangsstyring (autorisationsgruppe)
Repræsenterer de brugere, der har grundliggende adgang til Adgangsstyring.
Medlemmer: Anders, Bent, Carsten, Dennis, Erik
```
```
▪ AD-gruppe: FK-Admin
Udløser rollen ACCESS_CONTROL.
Medlemmer: Anders, Bent, Carsten, Dennis
▪ AD-gruppe: JFR-Admin
Udløser rollen ACCESS_CONTROL_STS.
Medlemmer: Anders, Bent
▪ AD-gruppe: Lokal-Admin
Udløser rollen ACCESS_CONTROL_LOCAL.
Medlemmer: Carsten, Dennis
```
```
▪ AD-gruppe: SAPA-Admin
Repræsenterer en SAPA-restriktion (fx et undertræ i AD).
Udløser rollen ACCESS_CONTROL_LOCAL + en restriktion
Medlemmer: Carsten
▪ AD-gruppe: KSD-Admin
Repræsenterer en KSD-restriktion (fx et undertræ i AD).
Udløser rollen ACCESS_CONTROL_LOCAL + en restriktion
Medlemmer: Dennis
```

```
▪ AD-gruppe: Auditør
Udløser rollerne AUDITOR, ADFS, IDM, IDM_AUDITOR
Medlemmer: Erik
```
### 10.2 Rolleadministrator

Organisationens rolleadministratorer tildeler rettigheder til de brugeradministratorer, der skal have adgang
til de forskellige moduler og funktioner i Adgangsstyring. Rettighedsstyringen er baseret på AD-gruppemed-
lemskaber som rolleadministratoren administrerer. Rolleadministratoren tildeler således rettigheder til bru-
geradministratorerne ved at indmelde dem i de AD-rollegrupper, der matcher de roller de skal have i Ad-
gangsstyring.

Den grundliggende rettighed til at komme ind i Adgangsstyring styres med en AD-gruppe (”autorisations-
gruppe”), hvis eneste formål er at indeholde de brugeradministratorer, der må få adgang til at bruge Ad-
gangsstyring. Et medlemskab af denne autorisationsgruppe giver i sig selv ingen rettigheder til modulerne
inde i Adgangsstyring – kun til at komme ind i Adgangsstyring.

Rettigheder til at anvende de forskellige moduler og funktioner inde i Adgangsstyring styres via medlemska-
ber af rollegrupper i AD. Adgang til administrationsfunktionerne inde i et enkelt modul kan være fordelt ud
på mere end en enkelt rollegruppe, hvilket gør det muligt at give nogle brugeradministratorer begrænset
adgang til funktionerne i et modul, mens andre brugeradministratorer kan få fuld adgang til alle funktio-
nerne.

Organisationen kan som tidligere nævnt selv vælge, om en given AD-rollegruppe skal repræsentere en en-
kelt eller flere roller.

### 9.3 Brugeradministrator

Brugeradministratoren betjener en eller flere funktioner i modulerne i Adgangsstyring. Disse er beskrevet i
de tidligere kapitler.

### 9.4 Lokal administration

En brugeradministrator kan i udgangspunktet administrere adgange for alle brugere i hele AD. Hvis en bru-
geradministrator kun skal kunne administrere en del af brugerne eller grupperne i AD, så skal det sættes op
i systemet som beskrevet herunder.

Modulerne FK Administration og Identifikationsmidler understøtter lokal administration, og de tilhørende
roller er:

```
▪ ACCESS_CONTROL_LOCAL FK Administration
▪ IDM_LOCAL Identifikationsmidler
```
Rollerne tildeles som ekstra roller, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Administration og Identifikationsmidler.

**10.4.1 OU-restriktion**

En brugeradministrator med rollen som lokal administrator kan begrænses til kun at fremsøge og admini-
strere brugere og grupper under en bestemt OU i AD.

Restriktionen angives i et claim:
▪ Claim: https://federation.signaturgruppen.dk/ac/local/base
▪ Value: {OU distinguishedName}

En lokal administrator kan højest have én OU som base.

**10.4.2 Grupperestriktion**

En brugeradministrator med rollen som lokal administrator begrænses til kun at fremsøge og administrere
grupper der er opmærket med lokaladministratorens objectGUID.

Restriktionen angives i et claim:
▪ Claim: https://federation.signaturgruppen.dk/objectguid
▪ Value: {objectGUID}

En gruppe opmærkes ved at indsætte værdien {objectGUID} i gruppens altSecurityIdentities-attribut, hvor
{objectGUID} angiver lokaladministratorens objectGUID.

I Adgangsstyring kan en brugeradministrator opmærke grupper til lokal administration under FK Admini-
stration > Grupper ved at fremsøge gruppen, der ønskes opmærket, vælge Tilføj/Fjern opmærkninger >
Type > LOKAL_ADMINISTRATOR, fremsøge bruger eller gruppe og klikke Tilføj.

**10.4.3 Brugerrestriktion**

En brugeradministrator med rollen som lokal administrator kan begrænses til kun at fremsøge og admini-
strere brugere med en specifik værdi i en specifik attribut.

Restriktionen angives i et claim:
▪ Claim: https://federation.signaturgruppen.dk/ac/local/user/attribute
▪ Value: {attributNavn}={attributVærdi}

En lokal administrator kan have flere brugerrestriktioner baseret på en eller flere attributter.

### 9.5 Begrænset administration

Hvis en brugeradministrator kun skal have læseadgang i FK Administration, så skal vedkommende tildeles
denne rolle:
▪ ACCESS_CONTROL_RO

Rollen tildeles som en ekstra rolle, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Administration.

Hvis en brugeradministrator kun skal have læseadgang i FK Organisation, så skal vedkommende tildeles
denne rolle:

#### ▪ ORG_SYNC_RO

Rollen tildeles som en ekstra rolle, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Organisation.

### 9.6 Databasebeskrivelse

Adgangsstyring anvender en database til opbevaring af konfiguration og logninger. I dette afsnit findes en
beskrivelse af tabellerne i databasen.

**10.6.1 Adgangsstyringstabeller**

Adgangsstyring omfatter følgende tabeller:

```
Tabel Beskrivelse
AdfsAuditLog ADFS log sletningshændelser udført af administratorer
CertificateEntity Kobling af EIA systemcertifikater og AD-grupper (IdM-synkronisering)
CustomerConfiguration Indstillinger i Adgangsstyring
GroupAccessMapping Gruppebaseret rettighed for administratorer til at fremsøge brugere
KLEGroup KLE-definitioner
KLEMainGroup KLE-definitioner
KLESubject KLE-definitioner
KombitAuditLog Administrative ændringer i FK Administration
MfaMappings Gruppebaseret rettighed for brugere til at se ID-midler i ID-portalen
NsisRegistrationCodeAudit Log over manuelle identitetssikringer
OathTotp Registrerede kodevisere
OrgSyncAuditLog Administrative ændringer i FK Organisation
RoleMapping Gruppebaseret rettighed for administratorer til funktioner i Adgangsstyring
```
```
AdfsAuditLog
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
AdditionalInformation
AuditUser Information om administrator
LogEventType
```
```
CertificateEntity
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
Apikey
CvrNumber CVR-nummer
ExpirationDate Tidsstempel for certifikatudløb
FeatureInfo Anvendes ikke
Features Liste med aktiverede certifikatanvendelser
Name Certifikatnavn
OrganizationName CVR-navn
P 12 MitID Erhverv systemcertifikat inkl. privat nøgle
```

```
Type
Uuid MitID Erhverv systemcertifikat UUID
ValidFrom Startdato for MitID Erhverv systemcertifikats gyldighed
FeatureInfoExtended
```
```
CustomerConfiguration
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
Activated true/false
AdditionalInformation
Type Fx ADFS_NIGHTLY_LOG_CLEANER_NSIS
```
```
GroupAccessMapping
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
AccessToGroupDn AD gruppe distinguished name
AccessToGroupName AD gruppenavn
GroupDn AD gruppe distinguished name
GroupName AD gruppenavn
```
```
KLEGroup
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
GroupId Fx 00.01
MainGroupId Fx 00
Tooltip Fx Kommunens styrelse
```
```
KLEMainGroup
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
MainGroupId Fx 00
Tooltip Fx Kommunens styrelse
```

```
KLESubject
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
Updated Tidsstempel for opdatering
UpdatedBy Information om administrator
GroupId Fx 00.01
SubjectId Fx 00.01.00
Tooltip Fx Kommunens styrelse
```
```
KombitAuditLog
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
AdditionalInformation
AuditUser Information om administrator
LogEventType
```
```
MfaMappings
Kolonne Beskrivelse
GroupName AD gruppenavn
Mfa Identifikationsmiddel
Domain Netværksdomæne
```
```
NsisRegistrationCodeAudit
Kolonne Beskrivelse
Applicant Bruger-ID
CheckedBy RA-medarbejder
Created Tidsstempel for hændelsen
CreatedBy RA-medarbejder
Hash
PrimaryId Fx dansk kørekort
RunIdNumber Fx 1234567890
SecondaryId Fx dåbsattest
Upload Billed-ID
```
```
OathTotp
Kolonne Beskrivelse
EncryptedSharedSe-
cret
```
```
Kodeviser shared secret
```
```
Serial Kodeviser serienummer
```

```
OrgSyncAuditLog
Kolonne Beskrivelse
Created Tidsstempel for hændelsen
CreatedBy Information om administrator
AdditionalInformation
AuditUser
DistinguishedName
LogEventType
```
```
RoleMapping
Kolonne Beskrivelse
GroupName AD gruppenavn
Name Anvendes ikke
Role Adgangsstyringsrolle (fx IDM_ADMIN)
```
**10.6.2 ADFS-log-tabeller**

Signaturgruppens ADFS logservice indsamler relevante hændelser fra andre Signaturgruppemoduler og gem-
mer hændelserne som log-entries i tabeller, hvor hvert log-entry bliver gemt i sin egen række i den relevante
tabel. ADFS-log omfatter følgende tabeller:

```
Tabel Beskrivelse
LogEvent Autentifikationshændelser
InputClaim Autentifikationsoplysninger i forespørgsler
OutputClaim Autentifikationsoplysninger i svar
WindowsEvent ADFS-hændelser uden tilhørende autentifikationsoplysninger
DeviceLog Registreringshændelser (loginmidler, betingelsesaccepter, identitetssikringer)
ClaimType Claimtypes
RelyingParty Relying Parties
```
Autentifikationshændelser hentes fra ADFS-serveres Security-log:
Event Viewer (Local) > Windows Logs > Security.
Udover selve token issue event'et (Event ID 299) hentes også tilhørende input claim events (Event ID 501) og
output claim events (Event ID 500). Disse informationer gemmes i de tre tabeller LogEvent, InputClaim og
OutputClaim med hændelsens InstanceID som relationsnøgle.

```
Tabel: LogEvent
```
```
···
```
```
UserId EventId
741852
```
```
Ins tanceId
```
```
123456
369258
```
```
Tabel: InputClaim
```
```
···
```
```
Ty pe Value
987654
```
```
InstanceId
```
```
123456
```
```
456789
```
```
123456
```
```
Tabel: OutputClaim
```
```
···
```
```
Ty pe Value
987654
```
```
Ins tanceId
```
```
123456
```
```
456789
```
```
123456
```
Figuren herover illustrerer, at en enkelt autentifikation indeholder flere input claims og output claims – typisk
10 - 20 claims af hver slags pr. autentifikation.

LogEvent-tabellen indeholder følgende informationer om en autentifikationshændelse:

```
LogEvent
Kolonne Beskrivelse
Id Entydigt identifikationsnummer hørende til dette log-entry
TimeCreated Tidsstempel for autentifikationshændelsen
EventId Windows LogEventID (299 og 324)
MachineName ADFS servernavn
RelyingParty Relying Party Trust identifier
InstanceId Entydigt hændelsesID (relationsnøgle)
ClaimUserName Information om den autentificerede bruger
TimeUpdated Tidsstempel for beregning af HMAC-værdi
Mac BCV-værdi hørende til denne række i tabellen
```
InputClaim- og OutputClaim-tabellerne indeholder følgende informationer om claims hørende til autentifi-
kationshændelser:

```
InputClaim og OutputClaim
Kolonne Beskrivelse
Id Entydigt identifikationsnummer hørende til dette log-entry
InstanceId Entydigt hændelsesID (relationsnøgle)
Value Claim-værdi
ClaimType Claim-type
```
Rækker med EventID 299 repræsenterer brugere, der både er autentificerede og autoriserede.
(A token was successfully issued for the relying party X)

Rækker med EventId 324 repræsenterer brugere, der er autentificerede, men ikke er autoriserede.
(The Federation Service could not authorize token issuance for caller A to relying party X).

For at spare plads i databasen er navnene på claim types og relying parties lagt ud i tabellerne ClaimType og
RelyingParty, og disse navne refereres via id (foreign key) fra tabellerne InputClaim og OutputClaim.

ClaimType- og RelyingParty-tabellerne indeholder følgende informationer:

```
ClaimType og RelyingParty
Kolonne Beskrivelse
Id Entydigt identifikationsnummer hørende til navnet
Name Navn på claim type / relying party
```
ADFS-hændelser uden tilhørende autentifikationsoplysninger gemmes i WindowsEvent-tabellen, der inde-
holder følgende informationer om hver hændelse:

```
WindowsEvent
Kolonne Beskrivelse
Id Entydigt identifikationsnummer hørende til dette log-entry
TimeCreated Tidsstempel for ADFS-hændelsen
EventId Windows LogEventID (411 og 1007)
MachineName ADFS servernavn
ActivityId Entydigt hændelsesID
UserName Information om den bruger, der forårsagede hændelsen
Message Beskrivelse af hændelsen
TimeUpdated Tidsstempel for beregning af HMAC-værdi
Mac BCV-værdi hørende til denne række i tabellen
```
Nedenstående hændelser gemmes i WindowsEvent-tabellen.

Rækker med EventId 411 repræsenterer bruger-autentifikationsfejl.
(The username or password is incorrect)

Rækker med EventId 1007 repræsenterer eksport af ADFS’ens signeringscertifikat.
(A certificate has been exported)

Registreringshændelser hentes fra ID-portal-serveres Security-log:
Event Viewer (Local) > Application and Services Logs > SIB.
Registreringshændelser hentes fra administrationsportal-serveres Security-log:
Event Viewer (Local) > Application and Services Logs > Federation.
Hændelserne omfatter identitetssikring, accept af betingelser samt tilknytning og spærring af NSIS identifi-
kations-midler.
Disse hændelser gemmes i DeviceLog-tabellen, der indeholder følgende informationer om en hændelse:

```
DeviceLog
```

```
Kolonne Beskrivelse
Id Entydigt identifikationsnummer hørende til dette log-entry
Created Tidsstempel for registreringshændelsen
MachineName Den anvendte portals servernavn
Upn Information om den autentificerede bruger
Browser Information om den browser der blev anvendt til registrering
ApprovedBy Information om udførende administrator (hvis relevant)
Registration Registreringens data
Type Registreringens type (REGISTRATION eller DELETION)
AdditionalInfo Information om identitetssikringsmetoden (login context)
ActivityId Entydigt hændelsesID
OperatingSystem Information om brugerens operativsystem
LogName Den anvendte portals lognavn (SIB eller Federation)
TimeUpdated Tidsstempel for beregning af HMAC-værdi
Mac HMAC-værdi hørende til denne række i tabellen
```
