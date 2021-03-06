---
ms.date: 09/13/2016
ms.topic: reference
title: Bij te werken hulp bij het ontwerpen-stap voor stap
description: Bij te werken hulp bij het ontwerpen-stap voor stap
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658814"
---
# <a name="updatable-help-authoring-step-by-step"></a>Ontwerpen van Help die kan worden bijgewerkt: stap voor stap

Dit document bevat een lijst met de stappen in het proces van het maken van een Beschrijf bare Help.

## <a name="authoring-updatable-help-step-by-step"></a>Beschrijf bare Help voor ontwerpen: stapsgewijs

De Help die kan worden bijgewerkt, is ontworpen voor eind gebruikers, maar biedt ook aanzienlijke voor delen van module auteurs en Help-schrijvers, met inbegrip van de mogelijkheid om inhoud toe te voegen, fouten op te lossen, te leveren in meerdere GEBRUIKERSINTERFACE culturen en te reageren op opmerkingen en aanvragen van gebruikers, lang nadat de module is verzonden. In dit onderwerp wordt uitgelegd hoe u Help-bestanden inpakt en uploadt, zodat gebruikers deze kunnen downloaden en installeren met behulp van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en cmdlets voor [opslaan-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

De volgende stappen bieden een overzicht van het proces van het ondersteunen van de Help-informatie die kan worden bijgewerkt.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Stap 1: een Internet site voor uw Help-bestanden zoeken

De eerste stap bij het maken van een Help-informatie is het vinden van een Internet locatie voor de Help-bestanden van uw module. U kunt ook twee verschillende locaties gebruiken. U kunt het bestand met Help-informatie voor de module (HelpInfo XML-hieronder) op één Internet locatie en de CAB-bestanden van de Help-inhoud op een andere Internet locatie houden. Alle CAB-bestanden van de Help-inhoud voor een module moeten zich op dezelfde locatie bezoeken. U kunt CAB-bestanden voor Help-inhoud voor verschillende modules op dezelfde locatie plaatsen.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Stap 2: een HelpInfoURI-sleutel toevoegen aan het module manifest

Voeg een **HelpInfoURI** -sleutel toe aan het module manifest. De waarde van de sleutel is de Uniform Resource Identifier (URI) van de locatie van het HelpInfo XML-gegevens bestand voor uw module. Voor beveiliging moet het adres beginnen met http of https. De URI moet een Internet locatie opgeven, maar mag de HelpInfo XML-bestands naam niet bevatten.

Bijvoorbeeld:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Stap 3: een HelpInfo XML-bestand maken

Het HelpInfo XML-informatie bestand bevat de URI van de Internet locatie van uw Help-bestanden en de versie nummers van de nieuwste Help-bestanden voor uw module in elke ondersteunde UI-cultuur. Elke Windows Power shell-module heeft één HelpInfo XML-bestand. Wanneer u de Help-bestanden bijwerkt, moet u het HelpInfo XML-bestand bewerken of vervangen. u kunt geen andere toevoegen. Zie [How to Create a HELPINFO XML file](./how-to-create-a-helpinfo-xml-file.md)(Engelstalig) voor meer informatie.

### <a name="step-4-create-cab-files"></a>Stap 4: CAB-bestanden maken

Gebruik een hulp programma waarmee u Cabinet ( `.cab` )-bestanden maakt, zoals `MakeCab.exe` , om een CAB-bestand te maken dat de Help-bestanden voor uw module bevat. Maak een afzonderlijk CAB-bestand voor de Help-bestanden in elke ondersteunde UI-cultuur. Zie voor meer informatie voor [bereiding voor het voorbereiden van bijwerk bare Help cab-bestanden](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-5-upload-your-files"></a>Stap 5: uw bestanden uploaden

Als u nieuwe of bijgewerkte Help-bestanden wilt publiceren, uploadt u de CAB-bestanden naar de Internet locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand HelpInfo. Upload vervolgens het HelpInfo XML-bestand naar de Internet locatie die is opgegeven door de waarde van de sleutel **HelpInfoUri** in het module manifest.
