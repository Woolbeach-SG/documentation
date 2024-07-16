---
title: 2 Registrering via MitID
layout: default
parent: Register MitID
nav_order: 2
has_children: false
---

## 2 Registrering via MitID

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

For at etablere adgang til et MitID-flow skal det sikres at serveren har adgang til [NETS eID Broker](https://netseidbroker.dk)
(port 443). Applikationen kører på Internet Information Services (IIS) under en given servicekonto med
skriverettigheder til AD-attributten ”altSecurityidentities”

### 2.1 Identitetssikring af brugere

Registreringen af CPR/fødselsdato bliver tilføjet i attributten "altSecurityidentities" på brugeren i AD’et, når
brugeren har udført et MitID login.

<img alt="AD-bruger inden registrering" height="65%" src="Billedmateriale\ADbruger.png" width="65%"/>

Bemærk, registreringen skal foretages, mens brugeren er logget ind på en pc på det interne lokale netværk.

I en browser åbnes registreringssiden (eksempel: https://idportal.kundenavn.dk/registermitid), hvor brugeren anmodes
om at logge ind med sin AD-bruger. Løsningen understøtter SSO, så hvis brugeren allerede er
logget ind, vil brugeren komme direkte til RegisterMitID-siden.

![Formbased Login](Billedmateriale\FormbasedLogin.png)

På registreringssiden vælges "Log ind med MitID", som starter et sædvanligt login-forløb med MitID.

![RegisterMitID Frontpage](Billedmateriale\RegisterMitID Frontpage.png)

Efter et fuldført MitID login bliver brugeren mødt af denne side, og har færdiggjort processen.

![RegisterMitIDSucess](Billedmateriale\RegisterMitIDSucess.png)

I AD'et kan man efterfølgende se at brugerens oplysninger er tilføjet til "altSecurityIdentities"-attributten.

Hvis der, på brugeren, kun er oplyst en fødselsdato, vil der stå
```
"DATE-OF-BIRTH: yyyy-MM-dd"
```

Hvis det er et CPR-nummer der er oplyst, vil det fremgå i krypteret på formen:

```
"ENCRYPTED:SSN: xxx"
```

![Værdier i altSecurityIdentities](Billedmateriale\ADaltSecurityIdentitiers.png)

Hvis brugeren efterfølgende bliver i tvivl, så vil der nu vises på RegisterMitID-siden at brugeren allerede har gennemført registreringen.
Hvis registreringen gennemføres igen, bliver den tidligere registrering overskrevet.

![Allerede registreret bruger](Billedmateriale\RegisterMitIDExisting.png)