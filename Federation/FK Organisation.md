---
title: 5 FK Organisation
layout: default
parent: Adgangsstyring
nav_order: 4
has_children: false
---

## 5 FK Organisation

Modulet FK Organisation bruges til administration af organisatoriske funktioner og tilhørende opmærknin-
ger til brug i støttesystemet Organisation i den fælleskommunale (FK) rammearkitektur.

Modulet indeholder tre overordnede funktioner:

* Opret funktion
* Administration
* Synkronisering

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

* Straks-synkronisere en specifik AD-konto til FK Organisation
* Starte en fuld synkronisering

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



