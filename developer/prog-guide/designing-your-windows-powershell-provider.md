---
title: Het ontwerpen van uw Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429938"
---
# <a name="designing-your-windows-powershell-provider"></a>Uw Windows PowerShell-provider ontwerpen

Als uw product of de configuratie bevat een set opgeslagen gegevens, zoals een database die de gebruiker het navigeren of blader wilt, moet u een Windows PowerShell-provider implementeren. Bovendien, als uw product een container, biedt zelfs als het is niet een container met meerdere niveaus, zinvol het om te implementeren van een Windows PowerShell-provider. Bijvoorbeeld, als u wilt implementeren van een Windows PowerShell-container-provider als de cmdlet term kopiëren, verplaatsen, naam, nieuw, of verwijderen zinvol als een bewerking op de gegevens van uw product of configuratie.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell-paden identificeren uw Provider

De Windows PowerShell-runtime maakt gebruik van Windows PowerShell-paden voor toegang tot de juiste Windows PowerShell-provider. De runtime weet welke provider moet worden gebruikt voor toegang tot de gekoppelde gegevensopslag wanneer een cmdlet Hiermee geeft u een van deze paden. Deze paden zijn station gekwalificeerde paden, provider gekwalificeerde paden, provider-directe paden en provider interne paden. Elke Windows PowerShell-provider moet ondersteuning voor een of meer van deze paden.

Zie voor meer informatie over Windows PowerShell-paden, hoe Windows PowerShell werkt.

### <a name="defining-a-drive-qualified-path"></a>Een station: pad definiëren

Als u wilt toestaan dat de gebruiker toegang tot gegevens die zich bevinden op een fysiek station, moet uw Windows PowerShell-provider een station: pad ondersteunen. Dit pad begint met de stationsnaam gevolgd door een dubbele punt (:), bijvoorbeeld mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Het definiëren van een Provider-pad

Als u wilt toestaan dat de Windows PowerShell-runtime voor het initialiseren en initialisatie van de provider, moet uw Windows PowerShell-provider ondersteuning voor een provider-pad. Bijvoorbeeld, bestandssysteem::\\\uncshare\abc\bar is het pad van de provider voor de provider van het bestandssysteem geleverd door Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Het pad van een Provider-Direct definiëren

Voor externe toegang tot uw Windows PowerShell-provider, moet er ondersteuning voor een provider-direct pad doorgeven rechtstreeks naar de Windows PowerShell-provider voor de huidige locatie. Bijvoorbeeld, de Windows PowerShell-provider van het register kunt \\\server\regkeypath als een pad voor de provider-direct.

### <a name="defining-a-provider-internal-path"></a>Een Provider interne pad definiëren

Als u wilt toestaan dat de provider-cmdlet voor toegang tot gegevens met behulp van Windows PowerShell application programming interfaces (API's), moet uw Windows PowerShell-provider een provider interne pad ondersteunen. Dit pad wordt aangegeven na het ':: ' in het pad van de provider. Bijvoorbeeld, het provider-interne pad voor de Windows PowerShell-provider van het bestandssysteem is \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Het wijzigen van opgeslagen gegevens

Onderdrukken van de methoden die het onderliggende gegevensarchief wijzigen, altijd aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode met de meest recente versie van het item gewijzigd door methode. De provider-infrastructuur bepaalt of het itemobject worden doorgegeven aan de pijplijn moet, zoals wanneer de gebruiker Hiermee geeft u de parameter - PassThru gebruikt. Als bij het ophalen van de meest actuele item is een dure bewerking (performance-wise), kunt u de eigenschap Context.PassThru om te bepalen of u werkelijk moet het resulterende item schrijven testen.

## <a name="choose-a-base-class-for-your-provider"></a>Kies een basisklasse voor uw Provider

Windows PowerShell biedt een aantal basisklassen die u gebruiken kunt voor het implementeren van uw eigen Windows PowerShell-provider. Bij het ontwerpen van een provider, kiest u de basisklasse, dat wordt beschreven in deze sectie is het meest geschikt is voor uw vereisten.

Elke basisklasse van Windows PowerShell-provider maakt beschikbaar een set van cmdlets. In deze sectie worden de cmdlets beschreven, maar de bijbehorende parameters wordt niet beschreven.

Met behulp van de sessiestatus, de Windows PowerShell-runtime maakt verschillende locatie-cmdlets beschikbaar voor bepaalde Windows PowerShell-providers, zoals de `Get-Location`, `Set-Location`, `Pop-Location`, en `Push-Location` cmdlets. U kunt de `Get-Help` cmdlet om informatie over deze cmdlets locatie te verkrijgen.

### <a name="cmdletprovider-base-class"></a>CmdletProvider basisklasse

De [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse definieert een eenvoudige Windows PowerShell-provider. Deze klasse biedt ondersteuning voor de provider-declaratie en levert een aantal eigenschappen en methoden die beschikbaar voor alle Windows PowerShell-providers zijn. De klasse wordt aangeroepen door de `Get-PSProvider` cmdlet om alle beschikbare providers voor een sessie weer te geven. De uitvoering van deze cmdlet wordt geleverd door de sessiestatus.

> [!NOTE]
> Windows PowerShell-providers zijn beschikbaar voor alle scopes in Windows PowerShell-taal.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider basisklasse

De [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse definieert een Windows PowerShell-station-provider die ondersteuning biedt voor bewerkingen voor nieuwe schijven toe te voegen, bestaande stations verwijderen en het initialiseren van standaard stations. Bijvoorbeeld, initialiseert de bestandssysteem-provider die is geleverd door Windows PowerShell de schijven voor alle volumes die zijn gekoppeld, zoals harde schijven en CD/DVD-stations voor apparaat.

Deze klasse is afgeleid van de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse. De volgende tabel bevat de cmdlets die worden weergegeven door deze klasse. Naast de genoemde, de `Get-PSDrive` cmdlet (die worden weergegeven door de status van de sessie) is een bijbehorende cmdlet die wordt gebruikt om op te halen van de beschikbare schijven.

|Cmdlet|Definitie|
|------------|----------------|
|`New-PSDrive`|Hiermee maakt u een nieuw station voor de sessie en stationsinformatie streams.|
|`Remove-PSDrive`|Hiermee verwijdert u een station van de sessie.|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider basisklasse

De [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse definieert een Windows PowerShell-item-provider die bewerkingen worden uitgevoerd op de afzonderlijke items van het gegevensarchief en er wordt een willekeurige container niet vanuit gegaan of navigatiemogelijkheden. Deze klasse is afgeleid van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse. De volgende tabel bevat de cmdlets die worden weergegeven door deze klasse.

|Cmdlet|Definitie|
|------------|----------------|
|`Clear-Item`|Wist u de huidige inhoud van items op de opgegeven locatie en vervangt deze door de "wissen" waarde die is opgegeven door de provider. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Get-Item`|Hiermee worden items opgehaald uit de opgegeven locatie en de resulterende objecten streams.|
|`Invoke-Item`|Hiermee wordt de standaardactie voor het item in het opgegeven pad.|
|`Set-Item`|Hiermee stelt u een item op de opgegeven locatie met de opgegeven waarde. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Resolve-Path`|Oplossing voor de jokertekens voor een Windows PowerShell-pad, en informatie over het pad van de stromen.|
|`Test-Path`|Test voor het opgegeven pad, en retourneert `true` als deze bestaat en `false` anders. Deze cmdlet is geïmplementeerd ter ondersteuning van de `IsContainer` parameter voor de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode.|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider basisklasse

De [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse definieert een Windows PowerShell-container-provider die wordt aangegeven dat een container voor data store items aan de gebruiker. Let erop dat de provider van een Windows PowerShell-container kan worden gebruikt alleen wanneer er een container (geen geneste containers) met items erin. Als er geneste containers, moet u een Windows PowerShell-provider voor navigatie implementeren.

Deze klasse is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basisklasse. De volgende tabel definieert de cmdlets door deze klasse geïmplementeerd.

|Cmdlet|Definitie|
|------------|----------------|
|`Copy-Item`|Items gekopieerd van de ene locatie naar een andere. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Get-Childitem`|Haalt de onderliggende items op de opgegeven locatie op en verzendt deze als objecten.|
|`New-Item`|Nieuwe items maakt op de opgegeven locatie en het resulterende object streams.|
|`Remove-Item`|Hiermee verwijdert u items uit de opgegeven locatie.|
|`Rename-Item`|Naam van een item op de opgegeven locatie. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider basisklasse

De [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse definieert een Windows PowerShell-navigatie-provider dat bewerkingen voor items die gebruikmaken van meer dan één container uitvoert. Deze klasse is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basisklasse. De onderstaande lijst de cmdlets die worden weergegeven door deze klasse.

|Cmdlet|Definitie|
|------------|----------------|
|Combine-Path|Combineert twee paden in één pad op, met behulp van een provider-specifieke als scheidingsteken tussen paden. Deze cmdlet streamt tekenreeksen.|
|`Move-Item`|Items verplaatst naar de opgegeven locatie. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|

Een gerelateerde cmdlet is de basic Parse-Path-cmdlet geleverd door Windows PowerShell. Deze cmdlet kan worden gebruikt voor het parseren van een Windows PowerShell-pad voor de ondersteuning van de `Parent` parameter. Deze streams tekenreeks voor het bovenliggende pad.

## <a name="select-provider-interfaces-to-support"></a>Provider-Interfaces om ondersteuning te selecteren

Naast het afleiden van een van de Windows PowerShell-basisklassen, kan uw Windows PowerShell-provider ondersteuning van andere functies door die is afgeleid van een of meer van de volgende provider-interfaces. In deze sectie definieert deze interfaces en de cmdlets die door elk worden ondersteund. De parameters voor de cmdlets interface ondersteund wordt hier niet beschreven. Informatie over de cmdlet-parameters is beschikbaar online met behulp van de `Get-Command` en `Get-Help` cmdlets.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

De [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface definieert een inhoudsprovider die bewerkingen op de inhoud van een gegevensitem worden uitgevoerd. De volgende tabel bevat de cmdlets die worden weergegeven door deze interface.

|Cmdlet|Definitie|
|------------|----------------|
|`Add-Content`|De lengte van de opgegeven waarde toegevoegd aan de inhoud van het opgegeven item. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Clear-Content`|Hiermee stelt u de inhoud van het opgegeven item op de waarde "wissen". Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Get-Content`|De inhoud van de opgegeven items opgehaald en de resulterende objecten streams.|
|`Set-Content`|Vervangt de bestaande inhoud voor de opgegeven items. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

De [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface definieert een eigenschap Windows PowerShell-provider die bewerkingen worden uitgevoerd op de eigenschappen van items in het gegevensarchief. De volgende tabel bevat de cmdlets die worden weergegeven door deze interface.

> [!NOTE]
> De `Path` parameter op deze cmdlets geeft aan dat een pad naar een item in plaats van een eigenschap te identificeren.

|Cmdlet|Definitie|
|------------|----------------|
|`Clear-ItemProperty`|Hiermee stelt u eigenschappen van de opgegeven items op de waarde "wissen". Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Get-ItemProperty`|Eigenschappen van de opgegeven items opgehaald en de resulterende objecten streams.|
|`Set-ItemProperty`|Hiermee stelt u eigenschappen van de opgegeven items met de opgegeven waarden. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) -interface, afgeleid van [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definieert een de provider die dynamische parameters voor de ondersteunde cmdlets. Dit type provider verwerkt bewerkingen waarvoor eigenschappen worden gedefinieerd tijdens runtime, bijvoorbeeld een nieuwe eigenschap bewerking. Deze bewerkingen zijn niet mogelijk op items die statisch eigenschappen gedefinieerd. De volgende tabel bevat de cmdlets die worden weergegeven door deze interface.

|Cmdlet|Definitie|
|------------|----------------|
|`Copy-ItemProperty`|Een eigenschap opgehaald uit het opgegeven item naar een ander item. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`Move-ItemProperty`|Een eigenschap verplaatst van het opgegeven item naar een ander item. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|
|`New-ItemProperty`|Hiermee maakt u een eigenschap op de opgegeven items en de resulterende objecten streams.|
|`Remove-ItemProperty`|Hiermee verwijdert u een eigenschap voor de opgegeven items.|
|`Rename-ItemProperty`|Naam van een eigenschap van de opgegeven items. Deze cmdlet geeft niet een uitvoerobject via de pijplijn, tenzij de `PassThru` parameter is opgegeven.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

De [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interface security descriptor functionaliteit wordt toegevoegd aan een provider. Deze interface kunt de gebruiker ophalen en instellen van security descriptor-informatie voor een item in het gegevensarchief. De volgende tabel bevat de cmdlets die worden weergegeven door deze interface.

|Cmdlet|Definitie|
|------------|----------------|
|`Get-Acl`|De informatie die deel uitmaken van een toegangsbeheerlijst (ACL), die deel uitmaakt van een beveiligingsdescriptor die wordt gebruikt ter bescherming van besturingssysteem-resources, bijvoorbeeld, een bestand of een object opgehaald.|
|`Set-Acl`|Hiermee stelt u de gegevens voor een ACL. Het is in de vorm van een exemplaar van [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) op het item (s) toegewezen voor het opgegeven pad. Deze cmdlet kunt informatie over de bestanden, sleutels en subsleutels instellen in het register of een andere provider-item, als de Windows PowerShell-provider de instelling van de beveiligingsgegevens ondersteunt.|

## <a name="see-also"></a>Zie ook

[Het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)