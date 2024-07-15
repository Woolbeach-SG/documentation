---
title: FK Administration
layout: default
parent: Adgangsstyring
nav_order: 4
has_children: false
---

## 4 FK Administration

Modulet FK Administration bruges til administration af brugere og deres jobfunktionsroller og tilhørende
opmærkninger til brug for adgang til fagsystemer i den fælleskommunale (FK) rammearkitektur.

Modulet indeholder tre overordnede funktioner:


* Opret jobfunktionsrolle
* Se / redigér jobfunktionsroller
* Se / redigér AD-opmærkninger

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


* Se oplysninger om jobfunktionsroller (navn, brugersystemrolle, brugersystem, ad-gruppe)
* Slette jobfunktionsroller i FK Administration
* Opmærke AD-grupper med jobfunktionsroller
* Tilføje brugersystemroller til jobfunktionsroller
* Slette brugersystemroller fra jobfunktionsroller

Klik på Se/redigér jobfunktionsroller og følg guiden.

### 4.3 Se / redigér AD-opmærkninger

Denne funktion bruges til at administrere opmærkninger i det lokale AD.

Funktionen indeholder tre underordnede indgange svarende til de AD-elementer, der kan opmærkes:


* Brugere (AD user-objekter)
* Grupper (AD security groups)
* Organisatoriske enheder (AD organizational units)

![FK Administration](Billedmateriale\FKAdministration.png)

Eksempel på opmærkninger:
På brugere og grupper gemmes opmærkningen i attributten altSecurityIdentities.
På organisatoriske enheder gemmes opmærkningen i attributten businessCategory.

Begge attributter er multivalued og kan indeholde flere opmærkninger.

**4.3.1 Brugere**

Funktionen kan bruges til at

* Fremsøge brugere ud fra brugernavn og/eller jobfunktionsrolle
* Se oplysninger om en brugers opmærkning
* Oprette en brugers opmærkning (jfr, kle, osv.)
* Slette en brugers opmærkning (jfr, kle, osv.)
* Melde en bruger ind/ud af en opmærket gruppe

**4.3.2 Grupper**

Funktionen kan bruges til at

* Fremsøge AD-grupper ud fra gruppenavn
* Se oplysninger om en AD-gruppes opmærkning
* Oprette en AD-gruppes opmærkning (jfr, kle, osv.)
* Slette en AD-gruppes opmærkning (jfr, kle, osv.)
* Melde brugere ind/ud af en AD-gruppe

**4.3.3 Organisatoriske enheder**

Funktionen kan bruges til at

* Fremsøge organisatoriske enheder (OU) ud fra OU-navn
* Se oplysninger om en OU's opmærkning
* Oprette en OU's opmærkning (jfr, kle, osv.)
* Slette en OU's opmærkning (jfr, kle, osv.)
* Oprette en AD-gruppe under OU'en



