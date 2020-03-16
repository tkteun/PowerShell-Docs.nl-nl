---
title: Informatie over een Windows Power shell-module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79406928"
---
# <a name="understanding-a-windows-powershell-module"></a>Inzicht in een Windows PowerShell-module

Een *module* is een set verwante Windows Power shell-functies, gegroepeerd als een handige eenheid (meestal opgeslagen in één map). Als u een reeks gerelateerde script bestanden, verzamelingen en gerelateerde resources als een module definieert, kunt u de code op een andere manier gebruiken, laden, persistent maken en delen.

Het belangrijkste doel van een module is het toestaan van de modularization (IE, hergebruik en abstractie) van Windows Power shell-code. De meest eenvoudige manier om een module te maken, is om eenvoudigweg een Windows Power shell-script op te slaan als een. psm1-bestand. Als u dit doet, kunt u de functies en variabelen in het script beheren (IE, openbaar of privé maken). Als u het script opslaat als een. psm1-bestand, kunt u ook het bereik van bepaalde variabelen beheren. Ten slotte kunt u ook cmdlets zoals [install-module](/powershell/module/PowershellGet/Install-Module) gebruiken om uw script te organiseren, te installeren en te gebruiken als bouw stenen voor grotere oplossingen.

## <a name="module-components-and-types"></a>Module onderdelen en typen

Een module bestaat uit vier basis onderdelen:

1. Een bepaalde soort code bestand: doorgaans een Power shell-script of een beheerde cmdlet-assembly.

2. Alles wat het bovenstaande code bestand mogelijk nodig heeft, zoals extra assembly's, Help-bestanden of scripts.

3. Een manifest bestand waarin de bovenstaande bestanden worden beschreven, evenals de meta gegevens van de auteur en versie van deze gegevens worden opgeslagen.

4. Een map die alle bovenstaande inhoud bevat en die zich bevindt in Power shell die redelijkerwijs kan worden gevonden.

   Houd er rekening mee dat geen van deze onderdelen zelf echt nood zakelijk is. Een module kan bijvoorbeeld technisch alleen een script zijn dat is opgeslagen in een. psm1-bestand. U kunt ook een module hebben die niets maar een manifest bestand is, dat hoofd zakelijk wordt gebruikt voor organisatie doeleinden. U kunt ook een script schrijven dat dynamisch een module maakt en als zodanig geen Directory nodig heeft voor het opslaan van items in. In de volgende secties worden de typen modules beschreven die u kunt verkrijgen door de verschillende mogelijke onderdelen van een module samen te mengen en te vergelijken.

### <a name="script-modules"></a>Script modules

Zoals de naam al aangeeft, is een *script module* een bestand (. psm1) dat een geldige Windows Power shell-code bevat. Ontwikkel aars van scripts en beheerders kunnen dit type module gebruiken om modules te maken waarvan de leden functies, variabelen en meer bevatten. In het hart is een script module gewoon een Windows Power shell-script met een andere extensie, waarmee beheerders import-, export-en beheer functies kunnen gebruiken.

Daarnaast kunt u een manifest bestand gebruiken om andere resources in uw module op te treffen, zoals gegevens bestanden, andere afhankelijke modules of runtime-scripts. Manifest bestanden zijn ook handig voor het volgen van meta gegevens, zoals ontwerpen en versie-informatie.

Ten slotte moet een script module, zoals elke andere module die niet dynamisch wordt gemaakt, worden opgeslagen in een map die in Power shell redelijkerwijs kan worden gedetecteerd. Normaal gesp roken bevindt dit zich op het pad van de Power shell-module. maar als dat nodig is, kunt u expliciet beschrijven waar de module is geïnstalleerd. Zie [een Power shell-script module schrijven](./how-to-write-a-powershell-script-module.md)voor meer informatie.

### <a name="binary-modules"></a>Binaire modules

Een *binaire module* is een .NET Framework-assembly (. dll) die gecompileerde code bevat C#, zoals. Cmdlet-ontwikkel aars kunnen dit type module gebruiken om cmdlets, providers en meer te delen. (Bestaande modules kunnen ook worden gebruikt als binaire modules.) In vergelijking met een script module kunt u met een binaire module cmdlets maken die sneller zijn of gebruikmaken van functies (zoals multi threading) die niet zo gemakkelijk zijn te coderen in Windows Power shell-scripts.

Net als bij script modules kunt u een manifest bestand toevoegen om aanvullende resources te beschrijven die door de module worden gebruikt en om meta gegevens over uw module bij te houden. Op dezelfde manier moet u waarschijnlijk uw binaire module in een map ergens naast het pad van de Power shell-module installeren. Zie How to [Write a Power shell binary module](./how-to-write-a-powershell-binary-module.md)(Engelstalig) voor meer informatie.

### <a name="manifest-modules"></a>Manifest modules

Een *manifest module* is een module die gebruikmaakt van een manifest bestand om alle onderdelen ervan te beschrijven, maar heeft geen sortering van de kern assemblage of het script. (Formeel, een manifest module laat het `ModuleToProcess`-of `RootModule` element van het manifest leeg.) U kunt echter nog steeds gebruikmaken van de andere functies van een module, zoals de mogelijkheid om afhankelijke assembly's te laden of om automatisch bepaalde pre-verwerkings scripts uit te voeren. U kunt ook een manifest module gebruiken als een handige manier om resources te verpakken die andere modules gebruiken, zoals geneste modules, assembly's, typen of indelingen. Zie [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

### <a name="dynamic-modules"></a>Dynamische modules

Een *dynamische module* is een module die niet is geladen vanuit of opgeslagen in een bestand. In plaats daarvan worden ze dynamisch gemaakt door een script met behulp van de cmdlet [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Met dit type module kan een script een module op aanvraag maken die niet hoeft te worden geladen of opgeslagen in permanente opslag. Een dynamische module is door zijn aard bedoeld om kort te worden bewaard en is daarom niet toegankelijk via de cmdlet `Get-Module`. Normaal gesp roken hebben ze doorgaans geen module manifesten nodig en hebben ze waarschijnlijk permanente mappen nodig om hun gerelateerde assembly's op te slaan.

## <a name="module-manifests"></a>Module manifesten

Een *module manifest* is een. psd1-bestand dat een hash-tabel bevat. De sleutels en waarden in de hash-tabel doen het volgende:

- Beschrijf de inhoud en kenmerken van de module.

- Definieer de vereisten.

- Bepaal hoe de onderdelen worden verwerkt.

  Er zijn geen manifesten vereist voor een module. Modules kunnen verwijzen naar script bestanden (. ps1), script module bestanden (. psm1), manifest bestanden (. psd1), opmaak en type bestanden (. ps1xml), cmdlet-en provider-assembly's (. dll), resource bestanden, Help-bestanden, lokalisatie bestanden of andere typen bestanden of bronnen die is gebundeld als onderdeel van de module. Voor een internationaal script bevat de map module ook een set bericht catalogus bestanden. Als u een manifest bestand aan de module map toevoegt, kunt u verwijzen naar de meerdere bestanden als één eenheid door te verwijzen naar het manifest.

  In het manifest zelf worden de volgende categorieën informatie beschreven:

- Meta gegevens over de module, zoals het versie nummer van de module, de auteur en de beschrijving.

- De vereisten die nodig zijn voor het importeren van de module, zoals de Windows Power shell-versie, de versie van de Common Language Runtime (CLR) en de vereiste modules.

- Het verwerken van instructies, zoals de scripts, indelingen en typen die moeten worden verwerkt.

- Beperkingen voor de leden van de module die u wilt exporteren, zoals de aliassen, functies, variabelen en cmdlets die moeten worden geëxporteerd.

  Zie [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

## <a name="storing-and-installing-a-module"></a>Een module opslaan en installeren

Zodra u een script-, binaire of manifest-module hebt gemaakt, kunt u uw werk opslaan op een locatie waar anderen toegang toe hebben. Uw module kan bijvoorbeeld worden opgeslagen in de systeemmap waarin Windows Power shell is geïnstalleerd, maar kan ook worden opgeslagen in een gebruikers map.

Over het algemeen kunt u bepalen waar u uw module moet installeren met behulp van een van de paden die zijn opgeslagen in de variabele `$ENV:PSModulePath`. Als u een van deze paden gebruikt, kan Power shell automatisch uw module vinden en laden wanneer een gebruiker deze in hun code aanroept. Als u uw module ergens anders opslaat, kunt u de Power shell expliciet laten weten door de locatie van uw module als een para meter door te geven wanneer u `Install-Module`aanroept.

Ongeacht het pad van de map wordt de *basis* van de module (erft type) genoemd, en de naam van het script-, binair-of manifest module bestand moet hetzelfde zijn als de naam van de module-map, met de volgende uitzonde ringen:

- Dynamische modules die door de cmdlet `New-Module` worden gemaakt, kunnen worden benoemd met de para meter `Name` van de cmdlet.

- Modules die worden geïmporteerd uit assembly-objecten door de **`Import-Module`-assembly-** opdracht worden benoemd volgens de volgende syntaxis: `"dynamic_code_module_" + assembly.GetName()`.

  Zie [een Power shell-module installeren](./installing-a-powershell-module.md) en het installatiepad voor [PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md)voor meer informatie.

## <a name="module-cmdlets-and-variables"></a>Module-cmdlets en-variabelen

De volgende cmdlets en variabelen worden verzorgd door Windows Power shell voor het maken en beheren van modules.

Cmdlet [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) met deze cmdlet wordt een nieuwe dynamische module gemaakt die alleen in het geheugen bestaat. De module wordt gemaakt op basis van een script blok en de geëxporteerde leden, zoals de functies en variabelen, zijn onmiddellijk beschikbaar in de sessie en blijven beschikbaar totdat de sessie wordt gesloten.

Cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) deze cmdlet maakt een nieuw module manifest bestand (. psd1), vult de waarden in en slaat het manifest bestand op in het opgegeven pad. Deze cmdlet kan ook worden gebruikt voor het maken van een module manifest sjabloon die hand matig kan worden ingevuld.

[Import-module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet deze cmdlet voegt een of meer modules toe aan de huidige sessie.

[Get-module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet deze cmdlet haalt informatie op over de modules die zijn of die in de huidige sessie kunnen worden geïmporteerd.

De cmdlet [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) met deze cmdlet worden de module leden (zoals cmdlets, functies, variabelen en aliassen) opgegeven die worden geëxporteerd uit een script module bestand (. psm1) of van een dynamische module die is gemaakt met behulp van de cmdlet `New-Module`.

Cmdlet [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) met deze cmdlet worden modules uit de huidige sessie verwijderd.

Cmdlet [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) met deze cmdlet wordt gecontroleerd of een module manifest de onderdelen van een module nauw keurig beschrijft door te controleren of de bestanden die worden vermeld in het manifest bestand van de module (. psd1) werkelijk aanwezig zijn in de opgegeven paden.

$PSScriptRoot deze variabele bevat de map van waaruit de script module wordt uitgevoerd. Hiermee kunnen scripts het pad naar de module gebruiken om toegang te krijgen tot andere resources.

$env:P SModulePath deze omgevings variabele bevat een lijst met de directory's waarin Windows Power shell-modules zijn opgeslagen. Windows Power shell gebruikt de waarde van deze variabele bij het automatisch importeren van modules en het bijwerken van Help-onderwerpen voor modules.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-module.md)
