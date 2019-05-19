---
title: Het maken van een eenvoudige Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 5ebc22067b20f0e1d35d31d5f33e599f50cb7564
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855068"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Een eenvoudige Windows PowerShell-provider ontwerpen

In dit onderwerp is het beginpunt voor het leren over het maken van een Windows PowerShell-provider. De basic-provider die hier worden beschreven biedt methoden voor het starten en stoppen van de provider en hoewel deze provider geen een manier toegang tot een gegevensarchief biedt of als u wilt ophalen of instellen van de gegevens in het gegevensarchief, biedt de essentiële functionaliteit die is vereist voor alle providers.

Zoals eerder vermeld, de basic-provider beschreven hier implementeert methoden voor het starten en stoppen van de provider. De Windows PowerShell-runtime roept deze methoden voor het initialiseren en initialisatie van de provider.

> [!NOTE]
> U vindt een voorbeeld van deze provider in het bestand AccessDBSampleProvider01.cs is geleverd door Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>De Windows PowerShell-Provider-klasse definiëren

De eerste stap bij het maken van een Windows PowerShell-provider is voor het definiëren van de .NET-klasse. Deze eenvoudige provider definieert een klasse genaamd `AccessDBProvider` die is afgeleid van de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse.

Het wordt aanbevolen dat u plaatst u de klassen van de provider in een `Providers` naamruimte van de naamruimte van uw API, bijvoorbeeld: xxx. PowerShell.Providers. Maakt gebruik van deze provider de `Microsoft.Samples.PowerShell.Provider` naamruimte, waarin alle voorbeelden van Windows PowerShell-provider wordt uitgevoerd.

> [!NOTE]
> De klasse voor een Windows PowerShell-provider moet expliciet gemarkeerd als openbaar. Klassen die niet zijn gemarkeerd als openbare standaard ingesteld op interne en zal niet worden gevonden door de Windows PowerShell-runtime.

Hier volgt de definitie van de klasse voor deze provider basic:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Vlak voor de klassendefinitie van de die u moet declareren het [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk met de syntaxis van de [CmdletProvider()].

U kunt instellen dat kenmerk trefwoorden voor de klasse verder declareren indien nodig. U ziet dat de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk hier gedeclareerd bevat twee parameters. De eerste parameter van kenmerk Hiermee geeft u de standaard-beschrijvende naam voor de provider, die de gebruiker later kunt wijzigen. De tweede parameter geeft u de mogelijkheden van Windows PowerShell-gedefinieerd die de provider wordt aangegeven in de Windows PowerShell-runtime tijdens de verwerking van de opdracht. De mogelijke waarden voor de provider-mogelijkheden zijn gedefinieerd door de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. Omdat dit een basis-provider, ondersteunt geen mogelijkheden.

> [!NOTE]
> De volledig gekwalificeerde naam van de Windows PowerShell-provider bevat de assembly-naam en andere kenmerken bepaald door de Windows PowerShell bij de registratie van de provider.

## <a name="defining-provider-specific-state-information"></a>Informatie over de status van de Provider-specifieke definiëren

De [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse en alle afgeleide klassen worden beschouwd als stateless omdat de Windows PowerShell-runtime provider instanties zoals vereist maakt. Als uw provider volledig beheer en onderhoud van de status voor de provider-specifieke gegevens moet, moet deze daarom een klasse vanuit afleiden de [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) klasse. De afgeleide klasse de leden die nodig zijn voor het onderhouden van de status, zodat de provider-specifieke gegevens kunnen worden geopend wanneer de Windows PowerShell-runtime-aanroepen moet definiëren de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode om te initialiseren van de provider.

Een Windows PowerShell-provider kan de status op basis van een verbinding ook onderhouden. Zie voor meer informatie over het onderhouden van de verbindingsstatus [het maken van een PowerShell-Provider station](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Tijdens de initialisatie van de Provider

Initialiseren van de provider van het aanroepen van de Windows PowerShell-runtime de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode wanneer Windows PowerShell wordt gestart. Uw provider kunt voor het overgrote deel de standaardimplementatie van deze methode retourneert de [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -object dat uw provider beschrijft. Echter, in het geval waar u informatie over de extra initialisatie toevoegen, moet u implementeren uw eigen [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode een gewijzigde versie van de retourneert[ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -object dat wordt doorgegeven aan uw provider. In het algemeen deze methode moet retourneren de opgegeven [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object doorgegeven aan deze of een gewijzigde [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object dat bevat informatie over de andere initialisatie.

Deze methode wordt niet door deze eenvoudige provider worden overschreven. De volgende code toont echter de standaardimplementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

De provider van de status van de provider-specifieke informatie kunt bijhouden, zoals beschreven in [definiëren Provider-specifieke gegevens status](#defining-provider-specific-state-information). In dit geval uw implementatie moet overschrijven de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode om te retourneren van een exemplaar van de afgeleide klasse.

## <a name="start-dynamic-parameters"></a>Dynamische Parameters starten

De providerimplementatie van de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode mogelijk extra parameters. In dit geval de provider moet worden overschreven de [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) methode en retourneren een object met eigenschappen en velden met het parseren van die vergelijkbaar is met kenmerken een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.

Deze methode wordt niet door deze eenvoudige provider worden overschreven. De volgende code toont echter de standaardimplementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>De Provider uninitializing

Voor gratis resources die gebruikmaakt van de Windows PowerShell-provider, de provider moet implementeren een eigen [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) methode. Deze methode wordt aangeroepen door de Windows PowerShell-runtime initialisatie van de provider op de sluiting van een sessie.

Deze methode wordt niet door deze eenvoudige provider worden overschreven. De volgende code toont echter de standaardimplementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample01 codevoorbeeld](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>De Windows PowerShell-Provider testen

Zodra uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel. Voor deze provider basic, uitvoeren van de nieuwe shell en gebruik de `Get-PSProvider` cmdlet voor het ophalen van de lijst met providers en zorg ervoor dat de provider AccessDb aanwezig is.

```powershell
Get-PSProvider
```

De volgende uitvoer wordt weergegeven:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Zie ook

[Het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)