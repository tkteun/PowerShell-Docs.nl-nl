---
title: 'Ontwerpen van Help die kan worden bijgewerkt: Stapsgewijze | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849831"
---
# <a name="updatable-help-authoring-step-by-step"></a>Ontwerpen van Help die kan worden bijgewerkt: stap voor stap

Deze documenten worden de stappen van het ontwerpen van bij te werken Help.

## <a name="authoring-updatable-help-step-by-step"></a>Bij te werken Help ontwerpen: stap voor stap

Help bij te werken is ontworpen voor eindgebruikers, maar ook biedt aanzienlijke voordelen voor auteurs en schrijvers van Help-informatie, inclusief de mogelijkheid om toe te voegen inhoud, fouten, leveren in meerdere UI culturen en reageren op aanvragen, en gebruikersopmerkingen lang na de module heeft verzonden. Dit onderwerp wordt uitgelegd hoe u een pakket en help voor uploaden van bestanden, zodat gebruikers kunnen downloaden en te met behulp van installeren de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

De volgende stappen bevatten een overzicht van het proces van ondersteunende bij te werken Help.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Stap 1: Een internetsite vinden voor de help-bestanden

De eerste stap bij het maken van bij te werken Help-informatie is te vinden van een internetlocatie op voor help-bestanden van uw module. Daadwerkelijk, kunt u twee verschillende locaties. U kunt van uw module help-informatiebestand (HelpInfo XML - hieronder beschreven) op één locatie van het Internet en de help-inhoud CAB-bestanden op een andere internetlocatie. Alle help-inhoud CAB-bestanden voor een module moeten zich in dezelfde locatie. U kunt de help-inhoud CAB-bestanden voor andere modules op dezelfde locatie plaatsen.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Stap 2: Een sleutel HelpInfoURI toevoegen aan uw module-manifest

Voeg een **HelpInfoURI** sleutel op uw module-manifest. De waarde van de sleutel is de Uniform Resource Identifier (URI) van de locatie van het bestand met HelpInfo XML voor de module. Voor beveiliging, moet het adres beginnen met 'http' of 'https'. De URI moet een Internet-locatie opgeven, maar niet de naam van het HelpInfo XML-bestand moet bevatten.

Bijvoorbeeld:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Stap 3: Een HelpInfo XML-bestand maken

Het bestand met HelpInfo XML bevat de URI van de Internet-locatie van de help-bestanden en het versienummer van de meest recente help-bestanden voor de module in elke ondersteunde gebruikersinterfacecultuur. Elke Windows PowerShell-module heeft een HelpInfo XML-bestand. Wanneer u de helpbestanden niet bijwerken, u kunt bewerken of vervangen door het HelpInfo XML-bestand. Voeg geen een andere naam. Zie voor meer informatie, [over het maken van een XML-bestand HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Stap 4: Meld u aan uw help-bestanden

Digitale handtekeningen zijn niet vereist, maar ze zijn een best practice-aanbeveling wanneer u bestanden delen.

### <a name="step-5-create-cab-files"></a>Stap 5: CAB-bestanden maken

Gebruik een hulpprogramma waarmee u cab-bestanden, zoals MakeCab.exe maken maakt een. CAB-bestand met de help-bestanden voor de module. Maak een afzonderlijk cabinetbestand voor de help-bestanden in elke ondersteunde gebruikersinterfacecultuur. Zie voor meer informatie, [over het voorbereiden bij te werken Help CAB-bestanden](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Stap 6: Uw bestanden uploaden

Voor het publiceren van nieuwe of bijgewerkte help-bestanden, kunt u de CAB-bestanden uploaden naar de locatie van het Internet die is opgegeven door de **HelpContentUri** -element in het HelpInfo XML-bestand. Vervolgens kunt u het HelpInfo XML-bestand uploaden naar de locatie van het Internet die is opgegeven door de waarde van de **HelpInfoUri** sleutel in de module-manifest.
