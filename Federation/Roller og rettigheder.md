---
title: Roller og Rettigheder
layout: default
parent: Adgangsstyring
nav_order: 1
has_children: false
---

## 2 Roller og Rettigheder

Adgangsstyring anvendes af _brugeradministratorer_ til at administrere brugernes identifikationsmidler, ad-
gang til logs samt rettigheder i FK rammearkitekturen. Brugeradministratorernes egne rettigheder til at be-
nytte moduler og funktioner i Adgangsstyring administreres af en _rettighedsadministrator_.

Oversigt:

* Rettighedsadministrator (rettighedskonfiguration)\
Melder brugeradministratorer ind og ud af brugeradministratorgrupper i AD og tilknytter brugerad-
ministratorgrupper til roller inde i Adgangsstyring (under Indstillinger).

* Brugeradministrator (brugerkonfiguration)\
Betjener en eller flere funktioner i modulerne i Adgangsstyring.

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

