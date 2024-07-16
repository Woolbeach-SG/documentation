---
title: 2 Registrering via MitID
layout: default
parent: Register MitID
nav_order: 2
has_children: false
---

## 2 Registrering af CPR/fødselsdato via MitID

For at oprette en MitID Erhverv-bruger kræves det at MitID Erhverv kan verificere at brugeren er, hvem den
siger den er. Dette gøres gennem CPR-nummer eller fødselsdato + aktiveringskode. For at Signaturgruppens
IdM-synkroniseringsmodul kan oprette MitID Erhverv-brugere på vegne af en organisation, er servicen nødt
til at kende disse oplysninger. Register MitID er en måde hvorpå oplysningerne kan indhentes, ved at anmode
brugeren om at logge ind med sit MitID og få CPR eller fødselsdato derigennem.\
Register MitID indeholder en implementering af kravene i NSIS-afsnit 3.1.2 Verifikation af Identitet (fysiske
personer) på sikringsniveau Betydelig, og består blandt andet af en verifikationsproces og et teknisk modul, 
der understøtter processen, og som brugeren skal benytte.

Modulet kan også benyttes til verifikation af brugere til login på Signaturgruppens ID-portal eller via Password Reset-klienten, 
hvor fx passwords kan opdateres.

For at etablere adgang til et MitID-flow skal det sikres at serveren har adgang til https://netseidbroker.dk
(port 443). Applikationen kører på Internet Information Services (IIS) under en given servicekonto med
skriverettigheder til AD-attributten ”altSecurityidentities”

### 2.1 Identitetssikring af brugere

Registreringen af CPR/fødselsdato bliver tilføjet i attributten altSecurityidentities på brugeren i AD’et, når
brugeren har udført et MitID login.

