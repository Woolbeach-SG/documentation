---
title: 3 Identifikationsmidler
layout: default
parent: Adgangsstyring
nav_order: 3
has_children: false
---

## 3 Identifikationsmidler

Modulet Identifikationsmidler bruges til administration af brugere og deres identifikationsmidler til brug i
føderative systemer, hvor tjenester kræver to-faktor adgang.

Modulet indeholder tre overordnede funktioner:


* Administrér identifikationsmidler
* Udtræk lister til revision
* Tilføj / fjern token-registreringer

### 3.1 Administrér identifikationsmidler

Fremsøg en bruger ved at indtaste mindst de to første bogstaver i brugernavnet og klik på Søg.
Det eller de brugernavne, der matcher søgningen vises i en liste under søgefeltet.
Klik på det brugernavn hvis detaljerede oplysninger ønskes vist.

I billedet med detaljerede brugeroplysninger er der fire faneblade:

* Administration
   * Viser oplysninger om brugerens AD-konto
* Historik
   * Viser brugerens fulde historik over identifikationsmidler
* Administrationshistorik
   * Viser administrative hændelser og integritetssikringen heraf - eksempelvis tilknytning og spærring af identifikationsmidler
* Trafik
   * Viderestiller til modulet ADFS Log, hvor login-trafik kan
     fremsøges – tilføjer automatisk brugernavnet

![Federation Menu](Billedmateriale\Identifikationsmiddeladministration.png)

Afhængigt af tildelte roller, så er det under Administration muligt for en administrator at

* Tilknytte SoloID app til brugerens AD-konto
* Tilknytte Yubikey til brugerens AD-konto
* Udstede engangskoder til brugeren (kan bruges som alternativ til login med privat MitID)
* Fjerne identifikationsmidler fra brugerens konto
* Udstede NSIS registreringskoder til brugeren (kan bruges som alternativ til personverifikation med privat MitID – kun hvis man har tilkøbt manuel registrering og er RA-administrator)

Hvis der er registreret et eller flere identifikationsmidler på brugerens konto, så ses de i bunden af Admini-
strationsfanebladet.

![Identifikationsmidler Overblik](Billedmateriale\IdentifikationsmidlerOverblik.png)

I modsat fald er listen tom.

![Identifikationsmidler Overblik Tom](Billedmateriale\IdentifikationsmidlerOverblikTom.png)

Klik på det røde kryds ud for et identifikationsmiddel for at fjerne det fra brugerens konto.

![Identifikationsmidler Slet](Billedmateriale\IdentifikationsmidlerOverblikSlet.png)

Bekræft handlingen for at gennemføre sletningen.

![Identifikationsmidler Slet bekræft](Billedmateriale\IdentifikationsmidlerOverblikSlet2.png)

Hvis, der er registreret en mail på brugerens AD-konto, så modtager brugeren en e-mail fra systemet inde-
holdende en spærringskvittering.

### 3.2 Udtræk, revision & validering

Denne funktion tilbyder diverse former for udtræk af data til brug for statistik og revision. Udtrækkene leveres i CSV-filformat.

Herunder er der tre faneblade:

* Udtræk hent lister over alle registrerede ID-midler og kodevisere
* Revision hent lister til revision inkl. tidsperiode filtrering
* Validering her kan sendes en e-mail med validering af integritetsbeskyttelsen

![Udtræk, revision & validering](Billedmateriale\UdtrækRevisionValidering.png)

Under revisionsfanebladet er det muligt at angive et tidsinterval og hente lister med NSIS-relevante hæn-
delser og registreringer.

![Revision](Billedmateriale\Revision.png)

**Her er et eksempel for Identitetssikringer:**

Først vælges hvilken tidsperiode man ønsker dokumenteret:

![Revision Eksempel](Billedmateriale\RevisionEksempel.png)

Ved at trykke ”Hent Identitetssikringer” begynder download af .csv filen der er navngivet med Revision -
den valgte liste (her: identitetssikring) samt tidsperioden.

![Revision Eksempel Fil](Billedmateriale\RevisionEksempelFil.png)

Listen indeholder de identitetssikringer, der er gjort i den angivet periode, User Principle Name (UPN) for
brugerne, den anvendte loginmetode og evt. hvilken administratorer der foretog identitetssikringen, hvis
man har tilkøbt det manuelle registreringsmodul.

![Revision Eksempel Fil](Billedmateriale\RevisionEksempelFilIndhold.png)

Under Valideringsfanen kan der ligeledes filtreres efter en specifik tidsperiode. Indtast mailadressen som
integritetsbeskyttelsen skal sendes til og tryk ”Test integritetsbeskyttelse”.

Et eksempel på hvordan e-mailen kan se ud:

![Revision Eksempel Fil](Billedmateriale\RevisionEksempelMail.png)

### 3.3 Tilføj / fjern token-registreringer

Administratorer med rettighed til at udføre denne funktion kan lægge Kodeviser-registreringer ind i syste-
mets database, eller fjerne registreringer fra databasen.

En bruger kan kun tilknytte en forud-registreret kodeviser til sin AD-konto som et to-faktoridentifikations-
middel.

![Revision Eksempel Fil](Billedmateriale\KodeviserRegistrering.png)


