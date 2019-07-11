---
title: Overzicht van Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734859"
---
# <a name="windows-powershell-provider-overview"></a>Overzicht van Windows PowerShell-providers

Een Windows PowerShell-provider kan een gegevensarchief worden weergegeven als een bestandssysteem alsof het een gekoppeld station. De ingebouwde registerprovider kunt u navigeren naar het register, zoals u navigeert bijvoorbeeld de `c` station van de computer. Een provider kan ook overschrijven de `Item` cmdlets (bijvoorbeeld `Get-Item`, `Set-Item`, enzovoort) die de gegevens in uw data store kunnen worden behandeld als bestanden en mappen worden behandeld als een bestandssysteem te navigeren. Zie voor meer informatie over providers en -stations en de ingebouwde providers in Windows PowerShell, [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Providers en -stations

Een Provider definieert de logica die wordt gebruikt om te openen, te navigeren en bewerken van een gegevensarchief, terwijl een station Hiermee geeft u een specifiek toegangspunt naar een gegevensarchief (of een gedeelte van een gegevensarchief) die is van het type dat is gedefinieerd door de provider. Bijvoorbeeld, de Register-provider hebt u toegang tot componenten en sleutels in een register en de stations HKLM en HKCU de bijbehorende onderdelen in het register opgeven. Beide met de stations HKLM en HKCU gebruiken de Register-provider.

Wanneer u een provider schrijft, kunt u standaard stations-stations die automatisch worden gemaakt wanneer de provider beschikbaar is. U ook definiëren een methode voor het maken van nieuwe schijven die gebruikmaken van die provider.

## <a name="type-of-providers"></a>Type van de Providers

Er zijn verschillende typen providers, elk met een ander niveau van functionaliteit biedt. Een provider wordt geïmplementeerd als een klasse die is afgeleid van een van de onderliggende objecten van de [System.Management.Automation.SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** klasse. Zie voor meer informatie over de verschillende typen providers [providertypen](./provider-types.md).

## <a name="provider-cmdlets"></a>Provider-cmdlets

Providers kunnen implementeren methoden die overeenkomen met de cmdlets, het maken van aangepaste gedrag voor die cmdlets wanneer gebruikt in een station voor die provider. Afhankelijk van het type provider zijn verschillende sets van cmdlets beschikbaar. Zie voor een volledige lijst van de cmdlets die beschikbaar zijn voor aanpassing in providers [Provider cmdlets](./provider-cmdlets.md).

## <a name="provider-paths"></a>Provider-paden

Gebruikers navigeren provider-stations, zoals bestandssystemen. Als gevolg hiervan, ze verwachten dat de syntaxis van paden overeen te komen met de paden in de bestand system navigatie wordt gebruikt. Wanneer een gebruiker een provider-cmdlet uitvoert, geef ze een pad naar het item dat moet worden geopend. Het pad dat is opgegeven, kan op verschillende manieren worden geïnterpreteerd. Een provider moet ondersteuning voor een of meer van de volgende pad-typen.

### <a name="drive-qualified-paths"></a>Station gekwalificeerde paden

Een station-pad is een combinatie van naam van het item, de container en subcontainers waarin het item zich bevindt en de Windows PowerShell-station waarmee het item wordt geopend. (De stations zijn gedefinieerd door de provider die wordt gebruikt voor toegang tot het gegevensarchief. Dit pad begint met de stationsnaam gevolgd door een dubbele punt (:). Bijvoorbeeld: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Provider gekwalificeerde paden

Als u wilt toestaan dat de Windows PowerShell-engine voor het initialiseren en initialisatie van de provider, moet de provider een pad van de provider ondersteunen. Bijvoorbeeld, de gebruiker kan worden geïnitialiseerd en initialisatie van de provider van het bestandssysteem omdat de volgende provider-pad definieert: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Provider-directe paden

Voor externe toegang tot uw Windows PowerShell-provider, moet er ondersteuning voor een provider-direct pad doorgeven rechtstreeks naar de Windows PowerShell-provider voor de huidige locatie. Bijvoorbeeld, de Windows PowerShell-provider van het register kunt `\\server\regkeypath` als een pad voor de provider-direct.

### <a name="provider-internal-paths"></a>Provider interne paden

Als u wilt toestaan dat de provider-cmdlet voor toegang tot gegevens met behulp van Windows PowerShell application programming interfaces (API's), moet uw Windows PowerShell-provider een provider interne pad ondersteunen. Dit pad wordt aangegeven na het ':: ' in het pad van de provider. Bijvoorbeeld, het provider-interne pad voor de Windows PowerShell-provider van het bestandssysteem is `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Het overschrijven van de cmdlet-parameters

Het gedrag van bepaalde provider-specifieke cmdlets kan worden overschreven door een provider. Zie voor een lijst met parameters die kunnen worden overschreven, en hoe u kunt deze negeren in uw providerklasse [Provider cmdlet-parameters](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Dynamische parameters

Providers kunnen dynamische parameters die worden toegevoegd aan een cmdlet provider wanneer de gebruiker Hiermee geeft u een bepaalde waarde voor een van de statische parameters van de cmdlet definiëren. Een provider doet dit door het implementeren van een of meer dynamische parameter-methoden. Zie voor een lijst van de cmdlet-parameters die kunnen worden gebruikt om toe te voegen dynamische parameter en de methoden die worden gebruikt voor het implementeren ervan [Provider cmdlet dynamische parameters](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Provider-mogelijkheden

De [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming definieert een aantal mogelijkheden die providers kunnen ondersteunen. Hierbij kunnen jokertekens gebruiken, filteritems en ondersteuning voor transacties. Als wilt opgeven mogelijkheden voor een provider, voegt u een lijst met waarden van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming, gecombineerd met een logische `OR` bewerking, als de [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) eigenschap (de tweede parameter van het kenmerk) van de [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk voor de providerklasse. Bijvoorbeeld, het volgende kenmerk geeft aan dat de provider ondersteunt de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **shouldprocess wordt overgeslagen** en [ System.Management.Automation.Provider.ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **transacties** mogelijkheden.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Provider cmdlet help

Bij het schrijven van een provider, kunt u uw eigen Help voor de provider-cmdlets die u kunt implementeren. Dit omvat een enkel help-onderwerp voor elke provider-cmdlet of meerdere versies van een help-onderwerp voor gevallen waarin de cmdlet provider fungeert anders op basis van het gebruik van dynamische parameters. Ter ondersteuning van provider cmdlet-specifieke help uw provider moet implementeren de [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interface.

De Windows PowerShell-engine roept de [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) methode om het Help-onderwerp voor de provider-cmdlets weer te geven. De engine biedt u de naam van de cmdlet die door de gebruiker opgegeven bij het uitvoeren van de `Get-Help` cmdlet en het huidige pad van de gebruiker. Het huidige pad is vereist als uw provider verschillende versies van de dezelfde provider-cmdlet voor verschillende schijven implementeert. De methode moet een tekenreeks zijn met het XML-bestand voor de cmdlet Help retourneren.

De inhoud van het Help-bestand wordt geschreven met behulp van PSMAML XML. Dit is de XML-schema dat wordt gebruikt voor het schrijven van Help-inhoud voor zelfstandige-cmdlets. De inhoud voor uw aangepaste cmdlet Help voor het Help-bestand voor uw provider toevoegen onder de `CmdletHelpPaths` element. Het volgende voorbeeld wordt de `command` -element voor een cmdlet één provider, en deze laat zien hoe u de naam van de provider-cmdlet die uw provider. biedt ondersteuning voor

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Zie ook

[Functionaliteit van Windows PowerShell-Provider](./provider-types.md)

[Provider-Cmdlets](./provider-cmdlets.md)

[Schrijven van een Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)