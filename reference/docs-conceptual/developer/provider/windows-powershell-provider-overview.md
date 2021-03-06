---
ms.date: 09/13/2016
ms.topic: reference
title: Overzicht van Windows PowerShell-providers
description: Overzicht van Windows PowerShell-providers
ms.openlocfilehash: 2f1c5f5991a64fb2b85ece7feba915164ebd34ee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355507"
---
# <a name="windows-powershell-provider-overview"></a>Overzicht van Windows PowerShell-providers

Met een Windows Power shell-provider kan elk gegevens archief worden weer gegeven als een bestands systeem alsof het een gekoppeld station is. Zo kunt u met de ingebouwde register provider navigeren in het REGI ster, net zoals u zou navigeren door het `c` station van de computer. Een provider kan ook de `Item` cmdlets (bijvoorbeeld, `Get-Item` `Set-Item` enzovoort) overschrijven, zodat de gegevens in uw gegevens archief kunnen worden behandeld als bestanden en mappen die worden behandeld bij het navigeren door een bestands systeem. Zie [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)voor meer informatie over providers en stations en de ingebouwde providers in Windows Power shell.

## <a name="providers-and-drives"></a>Providers en stations

Een provider definieert de logica die wordt gebruikt om een gegevens archief te openen, te navigeren en te bewerken, terwijl een station een specifiek toegangs punt geeft aan een gegevens archief (of een deel van een gegevens archief) van het type dat is gedefinieerd door de provider. Zo kunt u met de register provider toegang krijgen tot componenten en sleutels in een REGI ster, en de HKLM-en HKCU-stations geven de corresponderende componenten in het REGI ster. De HKLM-en HKCU-stations gebruiken beide de register provider.

Wanneer u een provider schrijft, kunt u standaard stations opgeven die automatisch worden gemaakt wanneer de provider beschikbaar is. U definieert ook een methode voor het maken van nieuwe stations die gebruikmaken van deze provider.

## <a name="type-of-providers"></a>Type providers

Er zijn verschillende typen providers, die elk een ander niveau van functionaliteit bieden. Een provider wordt ge??mplementeerd als een klasse die is afgeleid van een van de descendanten van de klasse [System. Management. Automation. SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory) 
 **CmdletProvider** . Zie voor meer informatie over de verschillende typen providers [provider typen](./provider-types.md).

## <a name="provider-cmdlets"></a>Provider-cmdlets

Providers kunnen methoden implementeren die overeenkomen met cmdlets, waarbij aangepaste gedragingen worden gemaakt voor deze cmdlets wanneer ze worden gebruikt in een station voor die provider. Afhankelijk van het type provider zijn er verschillende sets cmdlets beschikbaar. Zie [provider-cmdlets](./provider-cmdlets.md)voor een volledige lijst met de cmdlets die beschikbaar zijn voor aanpassing in providers.

## <a name="provider-paths"></a>Provider paden

Gebruikers navigeren naar provider stations als bestands systemen. Daarom verwachten ze de syntaxis van paden om overeen te komen met de paden die worden gebruikt in bestandssysteem navigatie. Wanneer een gebruiker een provider-cmdlet uitvoert, geven ze een pad op naar het item dat moet worden geopend. Het pad dat is opgegeven, kan op verschillende manieren worden ge??nterpreteerd. Een provider moet ondersteuning bieden voor een of meer van de volgende typen paden.

### <a name="drive-qualified-paths"></a>Drive-gekwalificeerde paden

Een stationspad is een combi natie van de naam van het item, de container en de subcontainers waarin het item zich bevindt en het Windows Power Shell-station waarmee het item wordt geopend. (Stations worden gedefinieerd door de provider die wordt gebruikt voor toegang tot het gegevens archief. Dit pad begint met de stationsnaam gevolgd door een dubbele punt (:). Bijvoorbeeld: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Door de provider gekwalificeerde paden

De provider moet een pad naar een provider ondersteunen om de Windows Power shell-engine in staat te stellen om uw provider te initialiseren en ongedaan te maken. De gebruiker kan bijvoorbeeld de bestandssysteem provider initialiseren en de initialisatie ongedaan te maakt, omdat hiermee het volgende provider-gekwalificeerde pad wordt gedefinieerd: `FileSystem::\\uncshare\abc\bar` .

### <a name="provider-direct-paths"></a>Provider-directe paden

Als u externe toegang tot uw Windows Power shell-provider wilt toestaan, moet het een provider-direct-pad ondersteunen om rechtstreeks door te geven aan de Windows Power shell-provider voor de huidige locatie. Het REGI ster van Windows Power shell-provider kan bijvoorbeeld worden gebruikt `\\server\regkeypath` als een provider-direct-pad.

### <a name="provider-internal-paths"></a>Provider-interne paden

Uw Windows Power shell-provider moet een provider-intern pad ondersteunen om de provider-cmdlet toegang te geven tot gegevens met behulp van niet-Windows Power shell-Api's (Application Programming Interfaces). Dit pad wordt aangegeven na ':: ' in het provider-pad. Bijvoorbeeld: het pad van de provider-intern voor de Windows Power shell-provider van het bestands systeem is `\\uncshare\abc\bar` .

## <a name="overriding-cmdlet-parameters"></a>Cmdlet-para meters overschrijven

Het gedrag van sommige providerspecifieke cmdlets kan worden overschreven door een provider. Zie [para meters](./provider-cmdlet-parameters.md) voor de cmdlet van de provider voor een lijst met para meters die kunnen worden overschreven en hoe u deze onderdrukking in uw provider klasse.

## <a name="dynamic-parameters"></a>Dynamische parameters

Providers kunnen dynamische para meters defini??ren die worden toegevoegd aan een provider-cmdlet wanneer de gebruiker een bepaalde waarde voor een van de statische para meters van de cmdlet opgeeft. Dit doet u door een of meer dynamische parameter methoden te implementeren. Zie voor een lijst met cmdlet-para meters die kunnen worden gebruikt om dynamische para meter toe te voegen en de methoden die worden gebruikt voor het implementeren van de cmdlets [dynamische para meters](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Provider mogelijkheden

De opsomming [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) definieert een aantal mogelijkheden die providers kunnen ondersteunen. Dit zijn onder andere de mogelijkheid om joker tekens te gebruiken, items te filteren en trans acties te ondersteunen. Als u mogelijkheden voor een provider wilt opgeven, voegt u een lijst met waarden van de inventarisatie [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) toe, gecombineerd met een logische `OR` bewerking, als [System. Management. Automation. provider. Cmdletproviderattribute. Providercapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) (de tweede para meter van het kenmerk) van het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) voor uw provider klasse. Het volgende kenmerk geeft bijvoorbeeld aan dat de provider de functies [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 
 **ShouldProcess** en [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)- 
 **trans acties** ondersteunt.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Help voor provider-cmdlets

Wanneer u een provider schrijft, kunt u uw eigen Help implementeren voor de provider-cmdlets die u ondersteunt.
Dit omvat ????n Help-onderwerp voor elke provider-cmdlet of meerdere versies van een Help-onderwerp voor gevallen waarbij de provider-cmdlet anders reageert op basis van het gebruik van dynamische para meters. Ter ondersteuning van de cmdlet-specifieke Help van de provider moet uw provider de interface [System. Management. Automation. provider. Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) implementeren.

De Windows Power shell-engine roept de methode [System. Management. Automation. provider. Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) aan om het Help-onderwerp voor uw provider-cmdlets weer te geven. De engine bevat de naam van de cmdlet die de gebruiker heeft opgegeven bij het uitvoeren `Get-Help` van de cmdlet en het huidige pad van de gebruiker.
Het huidige pad is vereist als uw provider verschillende versies van dezelfde provider-cmdlet voor verschillende stations implementeert. De-methode moet een teken reeks retour neren die de XML voor de Help van de cmdlet bevat.

De inhoud van het Help-bestand wordt geschreven met behulp van PSMAML XML. Dit is hetzelfde XML-schema dat wordt gebruikt voor het schrijven van Help-inhoud voor zelfstandige cmdlets. Voeg de inhoud voor de Help van uw aangepaste cmdlet toe aan het Help-bestand voor uw provider onder het- `CmdletHelpPaths` element. In het volgende voor beeld ziet `command` u het-element voor een cmdlet van ????n provider en ziet u hoe u de naam van de provider-cmdlet opgeeft die uw provider heeft. steun

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

[Functionaliteit van Windows Power shell-provider](./provider-types.md)

[Provider-cmdlets](./provider-cmdlets.md)

[Een Windows PowerShell-provider schrijven](./writing-a-windows-powershell-provider.md)
