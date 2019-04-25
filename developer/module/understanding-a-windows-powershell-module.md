---
title: Inzicht krijgen in een Windows PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082099"
---
# <a name="understanding-a-windows-powershell-module"></a>Inzicht in een Windows PowerShell-module

Een *module* is een set van gerelateerde Windows PowerShell-functies, gegroepeerd als een handige eenheid (meestal opgeslagen in één map). Bevat een reeks van verwante scriptbestanden, assembly's en gerelateerde resources als een module, kunt u verwijzen naar, laden, behouden en deel uw code veel eenvoudiger dan u anders zouden doen.

Het belangrijkste doel van een module is om toe te staan de modulevorming (ie, opnieuw gebruiken en abstractie) van Windows PowerShell-code. Bijvoorbeeld, is de eenvoudigste manier voor het maken van een module gewoon een Windows PowerShell-script opslaan als een psm1-bestand. Als dit dus kunt u bepalen (ie, zorg openbaar of privé) de functies en variabelen die zijn opgenomen in het script. Het script op te slaan als een psm1-bestand kunt u voor het beheren van het bereik van bepaalde variabelen. Ten slotte, u kunt ook gebruik cmdlets zoals [Install-Module](/powershell/module/PowershellGet/Install-Module) om te organiseren, installeren en gebruiken van uw script als bouwstenen voor grotere oplossingen.

## <a name="module-components-and-types"></a>Module-onderdelen en typen

Een module bestaat uit vier algemene onderdelen:

1. Sommige sorteren van codebestand - meestal een PowerShell-script of een beheerde cmdlet-assembly.

2. Zaken die het bovenstaande codebestand mogelijk nodig, zoals extra assembly's, hulp-bestanden of scripts.

3. Een manifestbestand waarin de bovenstaande bestanden worden beschreven, evenals metadada, zoals informatie over de auteur en versiebeheer worden opgeslagen...

4. Een map bevat alle van de bovenstaande inhoud en bevindt zich waar PowerShell redelijkerwijs deze kan vinden.

   Houd er rekening mee dat geen van deze onderdelen op zichzelf, daadwerkelijk nodig zijn. Een module mag bijvoorbeeld technisch alleen scripts die zijn opgeslagen in een psm1-bestand. U kunt ook een module die is niets, maar een manifestbestand hoofdzakelijk voor organisatie-toepassing gebruikt wordt hebben. U kunt ook een script dat dynamisch maakt een module en daarom niet daadwerkelijk moet een map voor het opslaan van alles in schrijven. De volgende secties wordt beschreven welke typen modules die u krijgen kunt door een combinatie van en die overeenkomt met de verschillende mogelijk onderdelen van een module samen.

### <a name="script-modules"></a>Scriptmodules

Als de naam al aangeeft, een *scriptmodule* is een bestand (.psm1) met een geldige Windows PowerShell-code. Script ontwikkelaars en beheerders kunnen dit type module gebruiken om te maken van modules waarvan de leden functies, variabelen en meer bevatten. Kern is een scriptmodule gewoon een Windows PowerShell-script met een andere extensie, waarmee beheerders import, export, en beheerfuncties op het gebruik.

U kunt bovendien een manifestbestand gebruiken om op te nemen van andere bronnen in uw module, zoals bestanden, andere afhankelijke modules of runtime-scripts. Manifest-bestanden zijn ook nuttig voor het bijhouden van metagegevens, zoals informatie over ontwerpen en versiebeheer.

Ten slotte moet een scriptmodule, net als elke andere module dat dynamisch wordt niet gemaakt, worden opgeslagen in een map die PowerShell redelijkerwijs kan detecteren. Meestal is dit op het pad van de PowerShell-module; maar indien nodig kunt u expliciet aangeven waar uw module is geïnstalleerd. Zie voor meer informatie, [over het schrijven van een PowerShell-Script-Module](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Binaire Modules

Een *binaire module* is een .NET Framework-assembly (dll) waarin gecompileerde code, zoals C#. Cmdlet-ontwikkelaars kunnen dit type module gebruiken voor het delen van cmdlets en providers. (Bestaande-modules kan ook worden gebruikt als binaire modules.) Een binaire module vergeleken met een scriptmodule, kunt u cmdlets die zijn sneller of functies maken (zoals multithreading) die niet zijn net zo gemakkelijk om te coderen in Windows PowerShell-scripts.

Als met scriptmodules, kunt u een manifestbestand om te beschrijven aanvullende bronnen die gebruikmaakt van de module en om bij te houden van metagegevens over uw module opnemen. Op dezelfde manier moet waarschijnlijk u uw binaire module in een map ergens op het pad van de module PowerShell. Zie voor meer informatie over het [over het schrijven van een PowerShell-Module voor binaire](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Manifest Modules

Een *manifest module* is een module die gebruikmaakt van een manifestbestand voor het beschrijven van alle onderdelen, maar beschikt niet over een of andere vorm van core assembly of het script. (Voorheen, een manifest module verlaat de `ModuleToProcess` of `RootModule` element van het manifest leeg zijn.) U kunt echter nog steeds andere functies van een module, zoals de mogelijkheid om te laden van afhankelijke assembly's of automatisch uitvoeren van bepaalde vooraf verwerken scripts gebruiken. U kunt ook een manifest module gebruiken als een handige manier om de resources die andere modules, zoals geneste modules, assembly's, typen en indelingen gebruiken wilt verpakken. Zie voor meer informatie, [over het schrijven van een PowerShell-Module-Manifest](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dynamische Modules

Een *dynamische module* is een module is niet geladen vanuit of naar een bestand opgeslagen. In plaats daarvan worden dynamisch gemaakt door een script met behulp van de [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Dit type module kunt een script voor het maken van een module op aanvraag die niet worden geladen of opgeslagen in een permanente opslag nodig heeft. Door de aard, een dynamische module is bedoeld als tijdelijke en daarom kan niet worden geopend door de `Get-Module` cmdlet. Op dezelfde manier, meestal hoeven ze niet modulemanifesten en waarschijnlijk moeten ze permanente mappen voor het opslaan van de bijbehorende assembly's.

## <a name="module-manifests"></a>Modulemanifesten

Een *module-manifest* is een .psd1-bestand met een hash-tabel. De sleutels en waarden in de hash-tabel kunt u het volgende doen:

- Beschrijf de inhoud en de kenmerken van de module.

- De vereisten definiëren.

- Bepalen hoe de onderdelen worden verwerkt.

  Manifesten zijn niet vereist voor een module. Modules kunnen verwijzen naar scriptbestanden (.ps1), module-bestanden (.psm1), manifestbestand (.psd1), opmaak script en typt u bestanden (.ps1xml), -cmdlet en provider assembly's (.dll), bestanden, Help-bestanden, lokalisatie bestanden of een ander type bestand of de resource die wordt geleverd als onderdeel van de module. De modulemap bevat ook een set catalogusbestanden voor een geïnternationaliseerde script. Als u een manifestbestand aan de modulemap toevoegt, u kunt verwijzen naar meerdere bestanden als één eenheid door te verwijzen naar het manifest.

  Het manifest zelf beschrijft de volgende categorieën van informatie:

- De metagegevens van de module, zoals het versienummer van de module, de auteur en de beschrijving.

- Vereiste onderdelen die nodig zijn om de module, zoals de Windows PowerShell-versie, de common language runtime (CLR)-versie en de vereiste modules te importeren.

- Verwerking richtlijnen, zoals scripts, indelingen en typen om te verwerken.

- Beperkingen voor de leden van de module te exporteren, zoals de aliassen, functies, variabelen en cmdlets voor het exporteren.

  Zie voor meer informatie, [over het schrijven van een PowerShell-Module-Manifest](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Opslaan en installeren van een Module

Als u een script, binair of manifest module hebt gemaakt, kunt u uw werk opslaan op een locatie die anderen hiertoe toegang hebben is. De module kan bijvoorbeeld worden opgeslagen in de map waar Windows PowerShell is geïnstalleerd, of deze kan worden opgeslagen in de map van een gebruiker.

In het algemeen kunt u bepalen waar u de module moet installeren met behulp van een van de paden die zijn opgeslagen in de `$ENV:PSModulePath` variabele. Met behulp van een van deze paden betekent dat PowerShell automatisch kunt vinden en uw module geladen wanneer een gebruiker Hiermee wordt een aanroep toe in de code. Als u uw module ergens anders opslaan, kunt u expliciet laten weten door te geven op de locatie van uw module als een parameter bij het aanroepen van PowerShell `Install-Module`.

Ongeacht het pad van de map wordt aangeduid als de *basis* van de module (ModuleBase) en de naam van het script, binair of manifest module-bestand moet hetzelfde zijn als de naam van de module map met de volgende uitzonderingen:

- Dynamische modules die zijn gemaakt door de `New-Module` cmdlet kan worden met de naam met behulp van de `Name` parameter van de cmdlet.

- Modules die zijn geïmporteerd uit assembly objecten op basis van de  **`Import-Module` -Assembly** opdracht zijn met de naam op basis van de volgende syntaxis: `"dynamic_code_module_" + assembly.GetName()`.

  Zie voor meer informatie, [een PowerShell-Module installeren](./installing-a-powershell-module.md) en [wijzigen van het installatiepad PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Module-Cmdlets en -variabelen

De volgende cmdlets en -variabelen worden geleverd door Windows PowerShell voor het maken en beheren van de modules.

[Nieuwe Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet met deze cmdlet maakt een nieuwe dynamische module die bestaat alleen in het geheugen. De module vanuit een scriptblok wordt gemaakt en de geëxporteerde leden, zoals de functies en variabelen, zijn onmiddellijk beschikbaar in de sessie en beschikbaar blijven totdat de sessie wordt gesloten.

[Nieuwe ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet met deze cmdlet maakt een nieuw bestand van de module-manifest (.psd1), vult u de waarden ervan en slaat u de manifest-bestand voor het opgegeven pad. Deze cmdlet kan ook worden gebruikt om te maken van een module-manifest sjabloon die handmatig kan worden ingevuld.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet met deze cmdlet wordt een of meer modules toegevoegd aan de huidige sessie.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet met deze cmdlet wordt informatie opgehaald over de modules die zijn of die kunnen worden geïmporteerd in de huidige sessie.

[Exporteren-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet met deze cmdlet Hiermee geeft u de module leden (zoals cmdlets, functies, variabelen en aliassen) die zijn geëxporteerd uit een scriptbestand voor module (.psm1) of van een dynamische module gemaakt met behulp van de `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet deze cmdlet wordt modules verwijderd uit de huidige sessie.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet met deze cmdlet wordt gecontroleerd of een module-manifest nauwkeurig de onderdelen van een module beschrijft door te controleren dat de bestanden die worden vermeld in de module manifestbestand (.psd1) werkelijk bestaan in de opgegeven paden.

$PSScriptRoot deze variabele bevat de map van waaruit de scriptmodule wordt uitgevoerd. Hiermee kunt scripts gebruikmaken van het modulepad voor toegang tot andere resources.

$env: PSModulePath deze omgevingsvariabele bevat een overzicht van de mappen in welke Windows PowerShell modules worden opgeslagen. Windows PowerShell maakt gebruik van de waarde van deze variabele bij het automatisch importeren van modules en Help-onderwerpen voor modules bijwerken.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
