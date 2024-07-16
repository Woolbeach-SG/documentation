---
title: 7 Certifikatstyring
layout: default
parent: Adgangsstyring
nav_order: 7
has_children: false
---

## 7 Certifikatstyring

Modulet Certifikatstyring bruges til administration af certifikater.

Modulet indeholder en overordnet funktion:
▪ Administrér certifikater

### 7.1 Administrér certifikater

Tilføj et nyt certifikat ved enten at importere et eksisterende certifikat eller ved at udstede et certifikat ud
fra et referencenummer og en pinkode.

**7.1.1 Importér certifikat**

![Certifikatstyring - Importer Certifikat](Billedmateriale\CertifikatStyringImporter.png)

**7.1.2 Opret administrationscertifikat**

![Certifikatstyring - Opret administrationscertifikat](Billedmateriale\CertifikatstyringOpretAdministrationscertifikat.png)

### 7.2 Tilføj features

Efterfølgende vil certifikatet fremgå på certifikatoversigten og ved at trykke på det pågældende certifikat kan
der tilføjes forskellige features.

![Certifikatstyring - Tilføj Features](Billedmateriale\CertifikatStyringFeatures.png)

**7.2.1 IdMSync feature**

Denne feature bruges til at administrere det systemcertifikat der skal oprettes til en IdM-sync løsning.
Under Gruppe DN skal synkroniseringsgruppenavnets Distinguished Name stå. Et eksempel kunne være:
▪ CN=MitIDErhverv,OU=gruppe,OU=organisation,OU=securitygroup,DC=domæne,DC=dk

De forskellige bokse der kan afkrydses, betyder følgende;
* **Bestil ID-midler:**
  * Skal afkrydses hvis I ønsker at IdM-sync løsningen skal bestille ID-midler (kodeviser, chip,
  kodeoplæser) til brugere, der har valgt en af disse ID-midler.
  * Har I oplyst et EAN-nummer i MitID Erhverv, og ønsker at IdM-sync skal bestille ID-midler,
  skal I notere det oplyste EAN-nummer i boksen nederst på siden.

* **Opsæt adresse på gruppe (standard er læst fra AD-bruger):**
  * Skal afkrydses hvis I ønsker, at de ID-midler, der bestilles gennem IdM-sync løsningen, skal
  sendes til fx hovedkontoret, hvor I derefter selv står for distribueringen.
  * (Som standard aflæses adressen direkte på den pågældende AD-bruger og ID-midlet sendes
  til den adresse, der er oplyst i AD’et.)

![Certifikatstyring - Opsætning](Billedmateriale\CertifikatStyringOpsætning.png)

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



