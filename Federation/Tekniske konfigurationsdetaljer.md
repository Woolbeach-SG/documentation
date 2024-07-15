---
title: 10 Tekniske konfigurationsdetaljer
layout: default
parent: Adgangsstyring
nav_order: 9
has_children: false
---

## 10 Tekniske konfigurationsdetaljer

Adgangsstyring anvendes af _brugeradministratorer_ til at administrere brugernes identifikationsmidler samt
rettigheder i FK rammearkitekturen. Brugeradministratorernes egne rettigheder til moduler og funktioner i
Adgangsstyring administreres af _rolleadministratorer_. _Systemadministratorer_ hjælper rolleadministrato-
rerne med at ændre systemets underliggende konfiguration, når det er nødvendigt.

Oversigt:

* Systemadministrator (systemkonfiguration)\
Opretter brugeradministratorgrupper og rolleadministratorgrupper i AD og melder rolleadministra-
torer ind og ud af rollegrupperne.
* Rolleadministrator (rettighedskonfiguration)\
Melder brugeradministratorer ind og ud af brugeradministratorgrupper i AD og tilknytter brugerad-
ministratorgrupper til roller i Adgangsstyring.

* Brugeradministrator (brugerkonfiguration)\
Betjener en eller flere funktioner i modulerne i Adgangsstyring.

### 10.1 Systemadministrator

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

```
c:[
Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid",
Value == "S- 1 - 5 - 21 - 119678056 - 279223570 - 496954922 - 31554",
Issuer == "AD AUTHORITY"]
=> issue(
Type = "http://schemas.microsoft.com/ws/2008/06/identity/claims/role",
Value = "IDM_ADMIN",
Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, ValueType = c.ValueType);
```

Systemadministratoren og rolleadministratoren fastlægger relationen mellem AD-rollegrupper og roller – fx
om en given AD-rollegruppe skal repræsentere en enkelt eller flere roller. Herefter opretter systemadmini-
stratoren rollegrupperne i AD, hvis de ikke allerede findes, og afspejler relationen til rollerne via claim rules
i ADFS’en.

I det helt simple tilfælde knyttes alle roller til en enkelt rollegruppe med den konsekvens, at alle der er
medlem af rollegruppen får adgang til alle funktioner i Adgangsstyring. Et mere detaljeret eksempel følger
herunder.

**10.1.1 Eksempel**

Antag at organisationen har følgende brugeradministratorer:


* Anders\
Superadministrator som skal have adgang til alt i Adgangsstyring.


* Bent\
FK-administrator som skal have adgang til alt under FK Administration.


* Carsten\
Lokal administrator for SAPA og skal have adgang til at give brugere rettigheder i SAPA.


* Dennis\
Lokal administrator for KSD og skal have adgang til at give brugere rettigheder i KSD.


* Erik\
Auditør som skal have adgang til at se logs.

Systemadministratoren og rolleadministratoren har fastlagt nedenstående relation mellem roller, rettighe-
der og AD-rollegrupper. Under hver AD-rollegruppe er der angivet, hvilke brugeradministratorer, der er
meldt ind for at de kan opnå de nødvendige rettigheder i Adgangsstyring.

Relationer:


* AD-gruppe: Adgangsstyring (autorisationsgruppe)\
Repræsenterer de brugere, der har grundliggende adgang til Adgangsstyring.\
Medlemmer: Anders, Bent, Carsten, Dennis, Erik


* AD-gruppe: FK-Admin\
Udløser rollen ACCESS_CONTROL.\
Medlemmer: Anders, Bent, Carsten, Dennis


* AD-gruppe: JFR-Admin\
Udløser rollen ACCESS_CONTROL_STS.\
Medlemmer: Anders, Bent


* AD-gruppe: Lokal-Admin\
Udløser rollen ACCESS_CONTROL_LOCAL.\
Medlemmer: Carsten, Dennis


* AD-gruppe: SAPA-Admin\
Repræsenterer en SAPA-restriktion (fx et undertræ i AD).\
Udløser rollen ACCESS_CONTROL_LOCAL + en restriktion\
Medlemmer: Carsten


* AD-gruppe: KSD-Admin\
Repræsenterer en KSD-restriktion (fx et undertræ i AD).\
Udløser rollen ACCESS_CONTROL_LOCAL + en restriktion\
Medlemmer: Dennis


* AD-gruppe: Auditør\
Udløser rollerne AUDITOR, ADFS, IDM, IDM_AUDITOR\
Medlemmer: Erik

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

### 10.3 Brugeradministrator

Brugeradministratoren betjener en eller flere funktioner i modulerne i Adgangsstyring. Disse er beskrevet i
de tidligere kapitler.

### 10.4 Lokal administration

En brugeradministrator kan i udgangspunktet administrere adgange for alle brugere i hele AD. Hvis en bru-
geradministrator kun skal kunne administrere en del af brugerne eller grupperne i AD, så skal det sættes op
i systemet som beskrevet herunder.

Modulerne FK Administration og Identifikationsmidler understøtter lokal administration, og de tilhørende
roller er:

```
▪ ACCESS_CONTROL_LOCAL              FK Administration
▪ IDM_LOCAL                         Identifikationsmidler
```

Rollerne tildeles som ekstra roller, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Administration og Identifikationsmidler.

**10.4.1 OU-restriktion**

En brugeradministrator med rollen som lokal administrator kan begrænses til kun at fremsøge og admini-
strere brugere og grupper under en bestemt OU i AD.

Restriktionen angives i et claim:
```
▪ Claim: https://federation.signaturgruppen.dk/ac/local/base
▪ Value: {OU distinguishedName}
```

En lokal administrator kan højest have én OU som base.

**10.4.2 Grupperestriktion**

En brugeradministrator med rollen som lokal administrator begrænses til kun at fremsøge og administrere
grupper der er opmærket med lokaladministratorens objectGUID.

Restriktionen angives i et claim:
```
▪ Claim: https://federation.signaturgruppen.dk/objectguid
▪ Value: {objectGUID}
```

En gruppe opmærkes ved at indsætte værdien {objectGUID} i gruppens altSecurityIdentities-attribut, hvor
{objectGUID} angiver lokaladministratorens objectGUID.

I Adgangsstyring kan en brugeradministrator opmærke grupper til lokal administration under FK Admini-
stration > Grupper ved at fremsøge gruppen, der ønskes opmærket, vælge Tilføj/Fjern opmærkninger >
Type > LOKAL_ADMINISTRATOR, fremsøge bruger eller gruppe og klikke Tilføj.

**10.4.3 Brugerrestriktion**

En brugeradministrator med rollen som lokal administrator kan begrænses til kun at fremsøge og admini-
strere brugere med en specifik værdi i en specifik attribut.

Restriktionen angives i et claim:
```
▪ Claim: https://federation.signaturgruppen.dk/ac/local/user/attribute
▪ Value: {attributNavn}={attributVærdi}
```

En lokal administrator kan have flere brugerrestriktioner baseret på en eller flere attributter.

### 10.5 Begrænset administration

Hvis en brugeradministrator kun skal have læseadgang i FK Administration, så skal vedkommende tildeles
denne rolle:
* ACCESS_CONTROL_RO

Rollen tildeles som en ekstra rolle, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Administration.

Hvis en brugeradministrator kun skal have læseadgang i FK Organisation, så skal vedkommende tildeles
denne rolle:

* ORG_SYNC_RO

Rollen tildeles som en ekstra rolle, udover de funktionsspecifikke roller, der giver brugeradministratoren
rettigheder til funktionerne i FK Organisation.

### 10.6 Databasebeskrivelse

Adgangsstyring anvender en database til opbevaring af konfiguration og logninger. I dette afsnit findes en
beskrivelse af tabellerne i databasen.

**10.6.1 Adgangsstyringstabeller**

Adgangsstyring omfatter følgende tabeller:

| **Tabel**                 | **Beskrivelse**                                                             |
| ------------------------- | --------------------------------------------------------------------------- |
| AdfsAuditLog              | ADFS log sletningshændelser udført af administratorer                       |
| CertificateEntity         | Kobling af EIA systemcertifikater og AD-grupper (IdM-synkronisering)        |
| CustomerConfiguration     | Indstillinger i Adgangsstyring                                              |
| GroupAccessMapping        | Gruppebaseret rettighed for administratorer til at fremsøge brugere         |
| KLEGroup                  | KLE-definitioner                                                            |
| KLEMainGroup              | KLE-definitioner                                                            |
| KLESubject                | KLE-definitioner                                                            |
| KombitAuditLog            | Administrative ændringer i FK Administration                                |
| MfaMappings               | Gruppebaseret rettighed for brugere til at se ID-midler i ID-portalen       |
| NsisRegistrationCodeAudit | Log over manuelle identitetssikringer                                       |
| OathTotp                  | Registrerede kodevisere                                                     |
| OrgSyncAuditLog           | Administrative ændringer i FK Organisation                                  |
| RoleMapping               | Gruppebaseret rettighed for administratorer til funktioner i Adgangsstyring |

| **Adfs Audit Log**    |                              |
|-----------------------|------------------------------|
| **Kolonne**           | **Beskrivelse**              |
| Created               | Tidsstempel for hændelsen    |
| CreatedBy             | Information om administrator |
| AdditionalInformation |                              |
| AuditUser             | Information om administrator |
| LogEventType          |                              |

| **CertificateEntity** |                                                         |
| --------------------- |---------------------------------------------------------|
| **Kolonne**           | **Beskrivelse**                                         |
| Created               | Tidsstempel for hændelsen                               |
| CreatedBy             | Information om administrator                            |
| Updated               | Tidsstempel for opdatering                              |
| UpdatedBy             | Information om administrator                            |
| Apikey                |                                                         |
| CvrNumber             | CVR-nummer                                              |
| ExpirationDate        | Tidsstempel for certifikatudløb                         |
| FeatureInfo           | Anvendes ikke                                           |
| Features              | Liste med aktiverede certifikatanvendelser              |
| Name                  | Certifikatnavn                                          |
| OrganizationName      | CVR-navn                                                |
| P12                   | MitID Erhverv systemcertifikat inkl. privat nøgle       |
| Type                  |                                                         |
| Uuid                  | MitID Erhverv systemcertifikat UUID                     |
| ValidFrom             | Startdato for MitID Erhverv systemcertifikats gyldighed |
| FeatureInfoExtended   |                                                         |

| **CustomerConfiguration** |                                  |
| ------------------------- |----------------------------------|
| **Kolonne**               | **Beskrivelse**                  |
| Created                   | Tidsstempel for hændelsen        |
| CreatedBy                 | Information om administrator     |
| Updated                   | Tidsstempel for opdatering       |
| UpdatedBy                 | Information om administrator     |
| Activated                 | true/false                       |
| AdditionalInformation     |                                  |
| Type                      | Fx ADFS_NIGHTLY_LOG_CLEANER_NSIS |

| **GroupAccessMapping** |                              |
| ---------------------- |------------------------------|
| **Kolonne**            | **Beskrivelse**              |
| Created                | Tidsstempel for hændelsen    |
| CreatedBy              | Information om administrator |
| Updated                | Tidsstempel for opdatering   |
| UpdatedBy              | Information om administrator |
| AccessToGroupDn        | AD gruppe distinguished name |
| AccessToGroupName      | AD gruppenavn                |
| GroupDn                | AD gruppe distinguished name |
| GroupName              | AD gruppenavn                |

| **KLEGroup** |                               |
| ------------ |-------------------------------|
| **Kolonne**  | **Beskrivelse**               |
| Created      | Tidsstempel for hændelsen     |
| CreatedBy    | Information om administrator  |
| Updated      | Tidsstempel for opdatering    |
| UpdatedBy    | Information om administrator  |
| GroupId      | Fx 00.01                      |
| MainGroupId  | Fx 00                         |
| Tooltip      | Fx Kommunens styrelse         |

| **KLEMainGroup** |                              |
| ---------------- |------------------------------|
| **Kolonne**      | **Beskrivelse**              |
| Created          | Tidsstempel for hændelsen    |
| CreatedBy        | Information om administrator |
| Updated          | Tidsstempel for opdatering   |
| UpdatedBy        | Information om administrator |
| MainGroupId      | Fx 00                        |
| Tooltip          | Fx Kommunens styrelse        |


| **KLESubject** |                              |
| -------------- |------------------------------|
| **Kolonne**    | **Beskrivelse**              |
| Created        | Tidsstempel for hændelsen    |
| CreatedBy      | Information om administrator |
| Updated        | Tidsstempel for opdatering   |
| UpdatedBy      | Information om administrator |
| GroupId        | Fx 00.01                     |
| SubjectId      | Fx 00.01.00                  |
| Tooltip        | Fx Kommunens styrelse        |

| **KombitAuditLog**    |                               |
| --------------------- |-------------------------------|
| **Kolonne**           | **Beskrivelse**               |
| Created               | Tidsstempel for hændelsen     |
| CreatedBy             | Information om administrator  |
| AdditionalInformation |                               |
| AuditUser             | Information om administrator  |
| LogEventType          |                               |

| **MfaMappings** |                       |
| --------------- |-----------------------|
| **Kolonne**     | **Beskrivelse**       |
| GroupName       | AD gruppenavn         |
| Mfa             | Identifikationsmiddel |
| Domain          | Netværksdomæne        |

| **NsisRegistrationCodeAudit** |                           |
| ----------------------------- |---------------------------|
| **Kolonne**                   | **Beskrivelse**           |
| Applicant                     | Bruger-ID                 |
| CheckedBy                     | RA-medarbejder            |
| Created                       | Tidsstempel for hændelsen |
| CreatedBy                     | RA-medarbejder            |
| Hash                          |                           |
| PrimaryId                     | Fx dansk kørekort         |
| RunIdNumber                   | Fx 1234567890             |
| SecondaryId                   | Fx dåbsattest             |
| Upload                        | Billed-ID                 |

| **OathTotp**          |                         |
| --------------------- |-------------------------|
| **Kolonne**           | **Beskrivelse**         |
| EncryptedSharedSecret | Kodeviser shared secret |
| Serial                | Kodeviser serienummer   |

| **OrgSyncAuditLog**   |                              |
| --------------------- |------------------------------|
| **Kolonne**           | **Beskrivelse**              |
| Created               | Tidsstempel for hændelsen    |
| CreatedBy             | Information om administrator |
| AdditionalInformation |                              |
| AuditUser             |                              |
| DistinguishedName     |                              |
| LogEventType          |                              |

| **RoleMapping** |                                     |
| --------------- |-------------------------------------|
| **Kolonne**     | **Beskrivelse**                     |
| GroupName       | AD gruppenavn                       |
| Name            | Anvendes ikke                       |
| Role            | Adgangsstyringsrolle (fx IDM_ADMIN) |

**10.6.2 ADFS-log-tabeller**

Signaturgruppens ADFS logservice indsamler relevante hændelser fra andre Signaturgruppemoduler og gem-
mer hændelserne som log-entries i tabeller, hvor hvert log-entry bliver gemt i sin egen række i den relevante
tabel. ADFS-log omfatter følgende tabeller:

| **Tabel**    | **Beskrivelse**                                                                |
| ------------ | ------------------------------------------------------------------------------ |
| LogEvent     | Autentifikationshændelser                                                      |
| InputClaim   | Autentifikationsoplysninger i forespørgsler                                    |
| OutputClaim  | Autentifikationsoplysninger i svar                                             |
| WindowsEvent | ADFS-hændelser uden tilhørende autentifikationsoplysninger                     |
| DeviceLog    | Registreringshændelser (loginmidler, betingelsesaccepter, identitetssikringer) |
| ClaimType    | Claimtypes                                                                     |
| RelyingParty | Relying Parties                                                                |

Autentifikationshændelser hentes fra ADFS-serveres Security-log:
Event Viewer (Local) > Windows Logs > Security.
Udover selve token issue event'et (Event ID 299) hentes også tilhørende input claim events (Event ID 501) og
output claim events (Event ID 500). Disse informationer gemmes i de tre tabeller LogEvent, InputClaim og
OutputClaim med hændelsens InstanceID som relationsnøgle.

![Tekniske Konfigurationsdetaljer](Billedmateriale\TekniskeDetaljerClaims.png)

Figuren herover illustrerer, at en enkelt autentifikation indeholder flere input claims og output claims – typisk
10 - 20 claims af hver slags pr. autentifikation.

LogEvent-tabellen indeholder følgende informationer om en autentifikationshændelse:

| **LogEvent**  |                                                            |
| ------------- |------------------------------------------------------------|
| **Kolonne**   | **Beskrivelse**                                            |
| Id            | Entydigt identifikationsnummer hørende til dette log-entry |
| TimeCreated   | Tidsstempel for autentifikationshændelsen                  |
| EventId       | Windows LogEventID (299 og 324)                            |
| MachineName   | ADFS servernavn                                            |
| RelyingParty  | Relying Party Trust identifier                             |
| InstanceId    | Entydigt hændelsesID (relationsnøgle)                      |
| ClaimUserName | Information om den autentificerede bruger                  |
| TimeUpdated   | Tidsstempel for beregning af HMAC-værdi                    |
| Mac           | BCV-værdi hørende til denne række i tabellen               |

InputClaim- og OutputClaim-tabellerne indeholder følgende informationer om claims hørende til autentifi-
kationshændelser:

| **InputClaim og OutputClaim** |                                                            |
| ----------------------------- |------------------------------------------------------------|
| **Kolonne**                   | **Beskrivelse**                                            |
| Id                            | Entydigt identifikationsnummer hørende til dette log-entry |
| InstanceId                    | Entydigt hændelsesID (relationsnøgle)                      |
| Value                         | Claim-værdi                                                |
| ClaimType                     | Claim-type                                                 |

Rækker med EventID 299 repræsenterer brugere, der både er autentificerede og autoriserede.
(A token was successfully issued for the relying party X)

Rækker med EventId 324 repræsenterer brugere, der er autentificerede, men ikke er autoriserede.
(The Federation Service could not authorize token issuance for caller A to relying party X).

For at spare plads i databasen er navnene på claim types og relying parties lagt ud i tabellerne ClaimType og
RelyingParty, og disse navne refereres via id (foreign key) fra tabellerne InputClaim og OutputClaim.

ClaimType- og RelyingParty-tabellerne indeholder følgende informationer:

| **ClaimType og RelyingParty** |                                                   |
| ----------------------------- |---------------------------------------------------|
| **Kolonne**                   | **Beskrivelse**                                   |
| Id                            | Entydigt identifikationsnummer hørende til navnet |
| Name                          | Navn på claim type / relying party                |

ADFS-hændelser uden tilhørende autentifikationsoplysninger gemmes i WindowsEvent-tabellen, der inde-
holder følgende informationer om hver hændelse:

| **WindowsEvent** |                                                            |
| ---------------- |------------------------------------------------------------|
| **Kolonne**      | **Beskrivelse**                                            |
| Id               | Entydigt identifikationsnummer hørende til dette log-entry |
| TimeCreated      | Tidsstempel for ADFS-hændelsen                             |
| EventId          | Windows LogEventID (411 og 1007)                           |
| MachineName      | ADFS servernavn                                            |
| ActivityId       | Entydigt hændelsesID                                       |
| UserName         | Information om den bruger, der forårsagede hændelsen       |
| Message          | Beskrivelse af hændelsen                                   |
| TimeUpdated      | Tidsstempel for beregning af HMAC-værdi                    |
| Mac              | BCV-værdi hørende til denne række i tabellen               |

Nedenstående hændelser gemmes i WindowsEvent-tabellen.

Rækker med EventId 411 repræsenterer bruger-autentifikationsfejl.\
(The username or password is incorrect)

Rækker med EventId 1007 repræsenterer eksport af ADFS’ens signeringscertifikat.\
(A certificate has been exported)

Registreringshændelser hentes fra ID-portal-serveres Security-log:
Event Viewer (Local) > Application and Services Logs > SIB.
Registreringshændelser hentes fra administrationsportal-serveres Security-log:
Event Viewer (Local) > Application and Services Logs > Federation.
Hændelserne omfatter identitetssikring, accept af betingelser samt tilknytning og spærring af NSIS identifi-
kations-midler.\
Disse hændelser gemmes i DeviceLog-tabellen, der indeholder følgende informationer om en hændelse:

| **DeviceLog**   |                                                              |
| --------------- |--------------------------------------------------------------|
| **Kolonne**     | **Beskrivelse**                                              |
| Id              | Entydigt identifikationsnummer hørende til dette log-entry   |
| Created         | Tidsstempel for registreringshændelsen                       |
| MachineName     | Den anvendte portals servernavn                              |
| Upn             | Information om den autentificerede bruger                    |
| Browser         | Information om den browser der blev anvendt til registrering |
| ApprovedBy      | Information om udførende administrator (hvis relevant)       |
| Registration    | Registreringens data                                         |
| Type            | Registreringens type (REGISTRATION eller DELETION)           |
| AdditionalInfo  | Information om identitetssikringsmetoden (login context)     |
| ActivityId      | Entydigt hændelsesID                                         |
| OperatingSystem | Information om brugerens operativsystem                      |
| LogName         | Den anvendte portals lognavn (SIB eller Federation)          |
| TimeUpdated     | Tidsstempel for beregning af HMAC-værdi                      |
| Mac             | HMAC-værdi hørende til denne række i tabellen                |