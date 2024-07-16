---
title: 3 Registrering via pas
layout: default
parent: Register MitID
nav_order: 3
has_children: false
---

## 3 Registrering via pas

For en bruger, der ikke kan eller vil identitetssikre sig med et personligt MitID, kan alternativet være at
identitetssikre sig med et pas (pas-registrering).\
Det forudsættes, at brugeren, der ønsker at benytte pasregistrering, er i besiddelse af et gyldigt maskinlæsbart pas samt en smartphone.

Pasregistrering indeholder en implementering af kravene i NSIS-afsnit 3.1.2 Verifikation af Identitet (fysiske personer) på sikringsniveau Betydelig, 
og består blandt andet af en verifikationsproces og et teknisk
modul, der understøtter processen, og som brugeren skal benytte.

Pasregistrering i den lokale IdP består af følgende trin:
1. Brugerens registrering af sit pas på sin AD-konto
2. Brugerens identitetssikring med sit pas i den lokale IdP

Registrering af pas skal foretages, mens brugeren er logget ind på en pc på det interne lokale netværk.

I en browser åbnes registreringssiden.

![Pasregistrering Frontpage](Billedmateriale\RegisterPassFrontpage.jpg)

På registreringssiden vælges "Log ind med pas", som starter et pasverifikationsforløb, der skal udføres med
brug af et gyldigt maskinlæsbart pas samt en smartphone med kamera.

De næste tre billeder er dem brugeren ser i sin browser, og de efterfølgende billeder er dem brugeren ser i
Nets paslæser app undervejs i verifikationsforløbet.

En beskrivelse af Nets paslæser app kan ses via dette link:
[NETS ID Verifier](https://www.nets.eu/developer/e-ident/eids/Pages/netspassportreader.aspx)

1. I browseren beder brugeren om at installere Nets paslæser app.

![NETS ID Verifier Install](NEIDV1.jpg)

2. I browseren viser brugeren en aktiveringskode og beder brugeren om at verificere sig i app'en. Resten af forløbet finder sted i app'en.

![NETS ID Verifier Kode](NEIDV2.jpg)

3. I browseren viser brugeren en kvitteringsside efter gennemført pasregistrering.

![NETS ID Verifier Kvittering](NEIDV3.jpg)

### 3.1 Identitetssikring med pas

Efter endt pasregistreirng har brugeren mulighed for at gennemføre NSIS identitetssikring i den lokale IdP med brug af sit pas.

I en browser åbnes ID-Portalen.

![ID-Portalen](IDPortalen.png)

Klik på "Passport" for at starte NETS paslæser. Første billede kan bruges til at hente app'en, hvis den ikke allerede er installeret på brugerens smartphone.

![NETS ID Verifier Download](NetsPaslæserDownload.jpg)

Næste billede viser aktiveringskoden smo en talkode og som en QR-kode. Aktiveringskoden skal anvendes i app'en til at starte verifikationsforløbet.

![NETS ID Verifier Godkend](NEIDV4.jpg)

Næste billede vises, mens brugeren verificerer sig i app'en.

![NETS ID Verifier Afventer](NEIDV5.jpg)

Efter gennemført verifikation i Nets paslæser-app kommer brugeren ind i den lokale IDP's ID-Portal, og kan fuldføre sin registrering i systemet på samme måde som brugere,
der har autentificeret sig med personligt MitID.

![NETS ID Verifier Afventer](IdPortalLogin.png)