---
title: 6 ADFS Log
layout: default
parent: Adgangsstyring
nav_order: 5
has_children: false
---

## 6 ADFS Log

Modulet ADFS Log bruges til inspektion af data opsamlet i forbindelse med brugeres fødererede logins via
ADFS.

Modulet indeholder tre overordnede funktioner:


* Fremsøg hændelser
* Se diagrammer
* Udtræk og validering
* Oprydning
* Se loginfejl
* Fremsøg konfigurationsændringer

### 6.1 Fremsøg hændelser

Denne funktion bruges til at inspicere indholdet af logninger.

Angiv et mere eller mindre specifikt søgekriterie for at inspicere større eller mindre dele af loggen.

Mulige søgekriterier:


* Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
* Specifik relying party
* Datointerval
* kombinationer af ovennævnte

For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’.
De fremfundne logninger vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søge-
kriteriet, så vises de på flere sider.

Klik på en logning for at folde den ud og se detaljerne i den pågældende logning.

### 6.2 Se diagrammer

Denne funktion bruges til at danne et grafisk overblik over logningerne.

Start med at vælge det faneblad, der svarer til den ønskede oversigt:


* Dagsoversigt fordeling af logins hen over timerne i et døgn
* Månedsoversigt fordeling af logins hen over dagene i en måned
* Fordeling af relying party fordeling af logins på tjenester i en periode

Angiv det ønskede tidsinterval og klik på Opdater.

De fremfundne logninger vises i en graf under søgefeltet.

### 6.3 Udtræk og validering

Denne funktion giver et udtræk af alle brugernes seneste registrerede 2 - faktor login. Listen indeholder hvem
der har brugt hvad og hvornår.
Validering af ADFS-logs.

![ADFS Log - Udtræk og validering](Billedmateriale\ELPUdtræk.png)

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


* Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
* Specifik relying party
* Datointerval
* kombinationer af ovennævnte

For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’. De fremfundne logninger
vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søgekriteriet, så vises de på flere
sider.

**6.5.2 Se diagrammer**

Denne funktion bruges til at danne et grafisk overblik over logningerne.

Start med at vælge det faneblad, der svarer til den ønskede oversigt:


* Dagsoversigt fordeling af fejlede logins hen over timerne i et døgn
* Månedsoversigt fordeling af fejlede logins hen over dagene i en måned
* Fordeling af brugernavne fordeling af fejlede logins for specifikke brugere i en periode

Angiv det ønskede tidsinterval og klik på Opdater.
De fremfundne logninger vises i en graf under søgefeltet.

### 6.6 Fremsøg konfigurationsændringer

Denne funktion bruges til at få vist ændringer på ADFS-konfigurationen, det kan fx være et certifikatskifte.

Angiv et mere eller mindre specifikt søgekriterie for at inspicere større eller mindre dele af loggen.

Mulige søgekriterier:


* Specifikt brugernavn eller dele af et brugernavn (mindst de to første bogstaver)
* Datointerval
* InstanceID

For at se hvilken server logningerne kommer fra, afkrydser der i feltet ’Server’.
De fremfundne logninger vises i en liste under søgefeltet. Hvis der er mange logninger, der matcher søge-
kriteriet, så vises de på flere sider.
Klik på en logning for at folde den ud og se detaljerne i den pågældende logning.



