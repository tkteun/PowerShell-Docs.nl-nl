---
title: Het maken van een Provider van Windows PowerShell-artikel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081866"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Een Windows PowerShell-itemprovider maken

Dit onderwerp beschrijft het maken van een Windows PowerShell-provider die de gegevens in een gegevensarchief kunt bewerken. In dit onderwerp worden de elementen van de gegevens in de store bedoeld om op te slaan als 'items' van de gegevens. Als gevolg hiervan wordt een provider die u kunt de gegevens in de store bewerken aangeduid als een Windows PowerShell-item-provider.

> [!NOTE]
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider03.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

De Windows PowerShell-item-provider in dit onderwerp beschreven haalt gegevens uit een Access-database. Een 'item' is in dit geval wordt een tabel in de Access-database of een rij in een tabel.

De volgende lijst bevat de secties in dit onderwerp. Als u niet bekend bent met het schrijven van een Windows PowerShell-item-provider, lees deze gedeeltes in de volgorde waarin ze worden weergegeven. Echter, als u bekend bent met het schrijven van een Windows PowerShell-item-provider, gaat u rechtstreeks naar de informatie die u nodig hebt:

- [De Windows PowerShell-Provider van een itemklasse definiëren](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Basisfunctionaliteit definiëren](#Defining-Base-Functionality)

- [Controleren op pad geldigheid](#Checking-for-Path-Validity)

- [Bepalen of een Item bestaat](#Determining-if-an-Item-Exists)

- [Bezig met koppelen van dynamische Parameters voor de `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Bij het ophalen van een Item](#Retrieving-an-Item)

- [Bezig met koppelen van dynamische Parameters voor de `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Instellen van een Item](#Setting-an-Item)

- [Bezig met koppelen van dynamische Parameters voor de `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Een Item uit te schakelen](#Clearing-an-Item)

- [Dynamische Parameters toevoegen aan de Cmdlet Clear-Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Uitvoeren van een standaardactie voor een Item](#Performing-a-Default-Action-for-an-Item)

- [Bij het ophalen van dynamische Parameters voor InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementatie van Help-methoden en klassen](#Implementing-Helper-Methods-and-Classes)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak](#Defining-Object-Types-and-Formatting)

- [Het bouwen van de Windows PowerShell-Provider](#Building-the-Windows-PowerShell-provider)

- [De Windows PowerShell-Provider testen](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>De Windows PowerShell-Provider van een itemklasse definiëren

Een Windows PowerShell-item-provider moet definiëren van een .NET-klasse die is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basisklasse. Hier volgt de definitie van de klasse voor de item-provider in deze sectie beschreven.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Houd er rekening mee dat in deze klassedefinitie, de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk bevat twee parameters. De eerste parameter geeft u een gebruiksvriendelijke naam voor de provider die wordt gebruikt door Windows PowerShell. De tweede parameter geeft u de Windows PowerShell-specifieke mogelijkheden die de provider wordt aangegeven in de Windows PowerShell-runtime tijdens de verwerking van de opdracht. Er zijn geen extra specifieke mogelijkheden van Windows PowerShell voor deze provider.

## <a name="defining-base-functionality"></a>Basisfunctionaliteit definiëren

Zoals beschreven in [ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse is afgeleid van diverse andere klassen die verschillende opgegeven provider-functionaliteit. De provider van een Windows PowerShell-item, daarom moet definiëren van de functionaliteit van de bovenliggende klassen.

Zie voor meer informatie over het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De meeste providers, met inbegrip van de provider hier beschreven, kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.

Voordat de Windows PowerShell-item-provider de items in de store manipuleren kan, moet deze de methoden voor het implementeren de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse voor de toegang tot het gegevensarchief. Zie voor meer informatie over het implementeren van deze klasse [het maken van een Windows PowerShell station Provider](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Controleren op pad geldigheid

Bij het zoeken naar een artikel van gegevens, de Windows PowerShell-runtime het levert een Windows PowerShell-pad naar de provider, zoals gedefinieerd in de sectie 'PSPath concepten' van [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Een Windows PowerShell-item-provider moet controleren of de syntactische en semantische geldigheid van een pad dat is doorgegeven aan het door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode. Deze methode retourneert `true` als het pad geldig is, en `false` anders. Houd er rekening mee dat de implementatie van deze methode niet moet controleren of de aanwezigheid van het item in het pad, maar alleen dat het pad de syntaxis is en semantisch juist zijn.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode voor deze provider. Houd er rekening mee dat deze implementatie een NormalizePath Help-methode als u wilt converteren van alle scheidingstekens in het pad naar een uniform aanroept.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Bepalen of een Item bestaat

Nadat u hebt gecontroleerd van het pad, moet de Windows PowerShell-runtime bepalen of een item van de gegevens op het opgegeven pad bestaat. Ter ondersteuning van dit type query, de provider van Windows PowerShell-item implementeert de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode. Deze methode retourneert `true` een item is gevonden op het opgegeven pad en `false` (standaard) anders.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode voor deze provider. Houd er rekening mee dat deze methode de helpermethoden PathIsDrive ChunkPath en GetTable roept en maakt gebruik van een provider gedefinieerd DatabaseTableInfo-object.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Om te onthouden over het implementeren van ItemExists

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Bij het definiëren van de providerklasse, een Windows PowerShell-item-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode moet ervoor zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- De uitvoering van deze methode moet een vorm van toegang tot het item dat het item zichtbaar te voor de gebruiker maken kan verwerken. Bijvoorbeeld, als een gebruiker toegang voor schrijven naar een bestand via de bestandssysteem-provider heeft (geleverd door Windows PowerShell), maar niet de toegang lezen, het bestand nog bestaat en [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourneert `true`. Uw implementatie mogelijk controleren van een bovenliggend item om te zien als het onderliggende item kan worden geïnventariseerd.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Test-pad

Soms de `Test-Path` cmdlet die worden aangeroepen [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) vereist extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters de Windows PowerShell-provider item moet worden geïmplementeerd de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Test-Path` cmdlet.

Deze Windows PowerShell-item-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Bij het ophalen van een Item

Als u wilt ophalen van een item, de Windows PowerShell-item-provider moet onderdrukken [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor de ondersteuning van aanroepen vanuit de `Get-Item` cmdlet. Deze methode schrijft het item met de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor deze provider. Houd er rekening mee dat deze methode maakt gebruik van de helpermethoden GetTable en GetRow ophalen van items die tabellen in de Access-database of rijen in een tabel met gegevens zijn.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Om te onthouden over het implementeren van GetItem

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-item-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) moet ervoor zorgen dat het pad dat is doorgegeven aan de methode aan deze vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van objecten die in het algemeen van de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Bijvoorbeeld, de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor de provider bestandssysteem controles de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap voordat wordt geprobeerd om aan te roepen [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) verborgen of systeembestanden.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Get-Item

Soms de `Get-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters de Windows PowerShell-provider item moet worden geïmplementeerd de [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Get-Item` cmdlet.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Instellen van een Item

Om een item, de Windows PowerShell-item-provider moet overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode voor de ondersteuning van aanroepen vanuit de `Set-Item` cmdlet. Deze methode stelt de waarde van het item in het opgegeven pad.

Deze provider biedt geen een onderdrukking voor de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode. Het volgende is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Om te onthouden over het implementeren van SetItem

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-item-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) moet ervoor zorgen dat het pad dat is doorgegeven aan de methode aan deze vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ingesteld of schrijven van objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden verzonden naar de [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode als het pad naar een verborgen item vertegenwoordigt en [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

- De implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)en controleer of de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in het gegevensarchief, bijvoorbeeld: verwijderen van bestanden. De [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) methode worden verzonden, de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met de opdrachtregel instellingen of de voorkeursvariabelen bij het bepalen van wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bericht naar de gebruiker om toe te staan van feedback om te controleren of als de bewerking moet worden voortgezet. De aanroep van [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kunt u een extra controle voor wijzigingen die mogelijk schadelijke system.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Bij het ophalen van dynamische Parameters voor SetItem

Soms de `Set-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters de Windows PowerShell-provider item moet worden geïmplementeerd de [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Set-Item` cmdlet.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Een Item uit te schakelen

Schakel een item, de provider van Windows PowerShell-item implementeert de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) methode voor de ondersteuning van aanroepen vanuit de `Clear-Item` cmdlet. Deze methode worden gewist van het gegevensitem in het opgegeven pad.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Om te onthouden over het implementeren van ClearItem

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-item-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) moet ervoor zorgen dat het pad dat is doorgegeven aan de methode aan deze vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ingesteld of schrijven van objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden verzonden naar de [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode als het pad vertegenwoordigt een item dat is verborgen voor de gebruiker en [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

- De implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)en controleer of de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in het gegevensarchief, bijvoorbeeld: verwijderen van bestanden. De [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) methode worden verzonden, de naam van de resource moet worden gewijzigd voor de gebruiker, met de Windows PowerShell-runtime en de verwerking van opdrachtregel instellingen of voorkeur de variabelen bij het bepalen van wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bericht naar de gebruiker om toe te staan van feedback om te controleren of als de bewerking moet worden voortgezet. De aanroep van [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kunt u een extra controle voor wijzigingen die mogelijk schadelijke system.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Dynamische Parameters voor ClearItem ophalen

Soms de `Clear-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters de Windows PowerShell-provider item moet worden geïmplementeerd de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Clear-Item` cmdlet.

Deze methode wordt niet geïmplementeerd door de provider van dit item. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Uitvoeren van een standaardactie voor een Item

De provider van een Windows PowerShell-item kunt implementeren de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) methode voor de ondersteuning van aanroepen vanuit de `Invoke-Item` cmdlet, waardoor de provider op een standaardactie uitvoeren voor het item in het opgegeven pad. De provider van het bestandssysteem mogelijk bijvoorbeeld deze methode gebruiken om aan te roepen ShellExecute voor een specifiek item.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Om te onthouden over het implementeren van InvokeDefaultAction

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Bij het definiëren van de providerklasse, een Windows PowerShell-item-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de implementatie van [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) moet ervoor zorgen dat het pad dat is doorgegeven aan de methode aan deze vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ingesteld of schrijven van objecten die zijn verborgen voor de gebruiker, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden verzonden naar de [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode als het pad vertegenwoordigt een item dat is verborgen voor de gebruiker en [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Dynamische Parameters voor InvokeDefaultAction ophalen

Soms de `Invoke-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters de Windows PowerShell-provider item moet worden geïmplementeerd de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de dynamische parameters voor de `Invoke-Item` cmdlet.

Deze methode wordt niet geïmplementeerd door de provider van dit item. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementatie van Help-methoden en klassen

Deze provider item verschillende hulpmethoden implementeert en klassen die worden gebruikt door de openbare methoden die zijn gedefinieerd door de Windows PowerShell overschrijven. De code voor deze Help-methoden en -klassen worden weergegeven in de [codevoorbeeld](#Code-Sample) sectie.

### <a name="normalizepath-method"></a>Methode NormalizePath

Deze provider item implementeert een NormalizePath Help-methode om ervoor te zorgen dat het pad een vaste indeling heeft. De opgegeven indeling maakt gebruik van een backslash (\\) als scheidingsteken.

### <a name="pathisdrive-method"></a>Methode PathIsDrive

Deze provider item implementeert een PathIsDrive Help-methode om te bepalen of het opgegeven pad daadwerkelijk de naam van de schijf.

### <a name="chunkpath-method"></a>Methode ChunkPath

Deze provider item implementeert een ChunkPath helpermethode die het opgegeven pad breekt zodat de provider van de afzonderlijke elementen kunt identificeren. Retourneert dat een matrix van de elementen van het pad bestaat.

### <a name="gettable-method"></a>GetTable methode

Deze provider item implementeert de GetTables Help-methode waarmee een DatabaseTableInfo-object dat staat voor informatie over de tabel die is opgegeven in de aanroep wordt geretourneerd.

### <a name="getrow-method"></a>Methode GetRow

De [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode van de provider van dit item de GetRows Help-methode aanroept. In dit Help-methode haalt een DatabaseRowInfo-object dat staat voor informatie over de opgegeven rij in de tabel.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo klasse

Dit item provider definieert een DatabaseTableInfo-klasse die staat voor een verzameling van gegevens in een tabel in de database. Deze klasse is vergelijkbaar met de [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) klasse.

De voorbeeld-item provider definieert een DatabaseTableInfo.GetTables-methode retourneert een verzameling van objecten van tabel informatie definiëren van de tabellen in de database. Deze methode omvat een try/catch-blok bevinden om ervoor te zorgen dat elke databasefout weergegeven als een rij met nul vermeldingen wordt.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo Class

Dit item provider definieert de DatabaseRowInfo helperklasse die een rij in een tabel van de database vertegenwoordigt. Deze klasse is vergelijkbaar met de [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) klasse.

De voorbeeld-provider definieert een DatabaseRowInfo.GetRows-methode voor het retourneren van een verzameling van objecten van de rij gegevens voor de opgegeven tabel. Deze methode omvat een try/catch-blok trap uitzonderingen. Eventuele fouten resulteert in geen rij gegevens.

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample03 codevoorbeeld](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Bij het schrijven van een provider, is het mogelijk dat het nodig zijn voor leden toevoegen aan bestaande objecten of nieuwe objecten te definiëren. Wanneer u klaar bent, maakt u een typen-bestand dat Windows PowerShell gebruiken om de leden van het object te identificeren en een indelingsbestand waarmee wordt gedefinieerd hoe het object wordt weergegeven. Zie voor meer informatie over [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Het bouwen van de Windows PowerShell-provider

Zie [over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>De Windows PowerShell-provider testen

Als deze Windows PowerShell-item-provider is geregistreerd met Windows PowerShell, kunt u alleen testen van de basic en functionaliteit van de provider station. Als u wilt testen het bewerken van items, moet u ook beschreven container-functionaliteit implementeren [implementeren van een Container Windows PowerShell-Provider](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Het ontwerpen van uw Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Het maken van een Container Windows PowerShell-provider](./creating-a-windows-powershell-container-provider.md)

[Het maken van een station Windows PowerShell-provider](./creating-a-windows-powershell-drive-provider.md)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)