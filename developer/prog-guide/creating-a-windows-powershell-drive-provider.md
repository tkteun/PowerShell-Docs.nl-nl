---
title: Het maken van een Provider van Windows PowerShell-station | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055645"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Een Windows PowerShell-stationprovider maken

In dit onderwerp wordt beschreven hoe u een Windows PowerShell-station provider waarmee u een manier om een gegevensarchief toegang via een Windows PowerShell-station te maken. Dit type provider is ook Windows PowerShell-station providers genoemd. De Windows PowerShell-stations die worden gebruikt door de provider bieden de mogelijkheid om verbinding maken met het gegevensarchief.

De Windows PowerShell-station-provider die hier worden beschreven, biedt toegang tot een Microsoft Access-database. Voor deze provider, de Windows PowerShell-station de database (dit is mogelijk een willekeurig aantal stations toevoegen aan een station-provider), vertegenwoordigt de containers op het hoogste niveau van het station staan voor de tabellen in de database en de rijen in de items van de containers vertegenwoordigen de tabellen.

Hier volgt een lijst van de secties in dit onderwerp. Als u niet bekend bent met het schrijven van een provider van Windows PowerShell-station, lees deze gedeeltes in de volgorde waarin ze worden weergegeven. Echter, als u bekend bent met het schrijven van de provider van een station, gaat u rechtstreeks naar de informatie die u nodig hebt.

- [De Windows PowerShell-Provider-klasse definiëren](#Defining-the-Windows-PowerShell-Provider-Class)

- [Basisfunctionaliteit definiëren](#Defining-Base-Functionality)

- [Het maken van informatie over de status van station](#Creating-Drive-State-Information)

- [Het maken van een station](#Creating-a-Drive)

- [Dynamische Parameters te koppelen aan NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Verwijderen van een station](#Removing-a-Drive)

- [Tijdens de initialisatie van standaard stations](#Initializing-Default-Drives)

- [Voorbeeld van code](#Code-Sample)

- [Testen van de Provider van Windows PowerShell-station](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>De Windows PowerShell-Provider-klasse definiëren

Uw provider station moet een .NET-klasse die is afgeleid van definiëren de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse. Hier volgt de definitie van de klasse voor deze provider station:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

U ziet dat in dit voorbeeld wordt de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk Hiermee geeft u een gebruiksvriendelijke naam voor de provider en de Windows PowerShell-specifieke mogelijkheden die de provider beschikbaar stelt aan de Windows PowerShell-runtime tijdens de verwerking van de opdracht. De mogelijke waarden voor de provider-mogelijkheden zijn gedefinieerd door de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. Deze provider station biedt geen ondersteuning van deze mogelijkheden.

## <a name="defining-base-functionality"></a>Basisfunctionaliteit definiëren

Zoals beschreven in [ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse is afgeleid van de [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse die de methoden die nodig zijn definieert voor het initialiseren en uninitializing van de provider. Zie voor het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De meeste providers (met inbegrip van de provider die hier worden beschreven) kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.

## <a name="creating-drive-state-information"></a>Het maken van informatie over de status van station

Alle Windows PowerShell-providers worden beschouwd als staatloze items, wat betekent dat uw provider station moet maken van alle informatie over de status die nodig is voor door de Windows PowerShell-runtime wordt uw provider.

Voor deze provider station bevat informatie over de status de verbinding met de database die als onderdeel van de stationsinformatie wordt bijgehouden. Dit is de code die laat hoe deze gegevens worden opgeslagen zien de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station wordt beschreven:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Het maken van een station

Als u wilt toestaan dat de Windows PowerShell-runtime maken van een station, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode. De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode voor deze provider station:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Het onderdrukken van deze methode moet het volgende doen:

- Controleer de [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) lid bestaat en dat een verbinding met het gegevensarchief kan worden uitgevoerd.

- Een station maken en vullen van het lid van de verbinding, ter ondersteuning van de `New-PSDrive` cmdlet.

- Valideer de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object voor het voorgestelde station.

- Wijzig de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object met de beschrijving van het station met de vereiste prestaties of betrouwbaarheid informatie of het bieden van extra gegevens voor bellers met behulp van het station.

- Afhandelen van fouten met behulp van de [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode en vervolgens terug `null`.

  Deze methode retourneert een van beide de stationsinformatie die is doorgegeven aan de methode of een provider-versie van het.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Dynamische Parameters te koppelen aan NewDrive

De `New-PSDrive` cmdlet ondersteund door uw provider station mogelijk extra parameters. Als u wilt deze dynamische parameters koppelen aan de cmdlet, de provider implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methode. Deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.

Deze methode wordt niet door deze provider station worden overschreven. De volgende code toont echter de standaardimplementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Verwijderen van een station

Als u wilt sluiten verbinding met de database, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode. Deze methode wordt de verbinding met het station na het opschonen van de provider-specifieke informatie gesloten.

De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode voor deze provider station:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Als het station kan worden verwijderd, de methode de informatie die is doorgegeven aan de methode via moet retourneren de `drive` parameter. Als het station kan niet worden verwijderd, de methode moet schrijven van een uitzondering en ga vervolgens terug `null`. Als deze methode wordt niet door uw provider worden overschreven, retourneert de standaardimplementatie van deze methode alleen de stationsinformatie doorgegeven als invoer.

## <a name="initializing-default-drives"></a>Tijdens de initialisatie van standaard stations

Uw provider station implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode voor het koppelen van stations. De Active Directory-provider kan bijvoorbeeld een station voor de standaard-naamgevingscontext als de computer is toegevoegd aan een domein te koppelen.

Deze methode retourneert een verzameling van stationsinformatie over de geïnitialiseerd stations of een lege verzameling. De aanroep naar deze methode wordt uitgevoerd na het aanroepen van de Windows PowerShell-runtime de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode om te initialiseren van de provider.

Deze provider station niet overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode. De volgende code toont echter de standaardimplementatie, een verzameling leeg station retourneert:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Om te onthouden over het implementeren van InitializeDefaultDrives

Alle providers van station moeten een basisstation om de gebruiker met zichtbaarheid te koppelen. Het basisstation kan lijst met locaties die als toegangspunten voor andere gekoppelde schijven fungeren. Bijvoorbeeld, de Active Directory-provider kan maken van een station met een lijst met de naamgevingscontexten gevonden in de `namingContext` kenmerken in de hoofdmap gedistribueerde systeemomgeving (DSE). Hierdoor kunnen gebruikers koppelpunten voor andere stations detecteren.

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample02 codevoorbeeld](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testen van de Provider van Windows PowerShell-station

Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel, met inbegrip van alle cmdlets beschikbaar gesteld door afleiding. De schijfprovider voorbeeld gaan we testen.

1. Voer de `Get-PSProvider` cmdlet voor het ophalen van de lijst met providers om ervoor te zorgen dat de schijfprovider AccessDB aanwezig is:

   **PS> `Get-PSProvider`**

   De volgende uitvoer wordt weergegeven:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Zorg ervoor dat de naam van een database-server (DSN) voor de database door het openen van bestaat de **gegevensbronnen** gedeelte van de **Systeembeheer** voor het besturingssysteem. In de **gebruiker DSN** tabel, dubbelklikt u op **MS Access-Database** en het pad naar station C:\ps\northwind.mdb toe te voegen.

3. Maak een nieuw station met de voorbeeld-station-provider:

   **PS > nieuwe psdrive-naam mydb-hoofdmap c:\ps\northwind.mdb - psprovider AccessDb**

   De volgende uitvoer wordt weergegeven:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. De verbinding valideren. Omdat de verbinding is gedefinieerd als een lid van het station, kunt u met behulp van de cmdlet Get-PDDrive kunt controleren.

   > [!NOTE]
   > De gebruiker kan niet nog communiceren met de provider als een station, zoals de provider functionaliteit van de container voor die interactie moet. Zie voor meer informatie, [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (get-psdrive mydb)**

   De volgende uitvoer wordt weergegeven:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Verwijderen van het station en de shell afsluiten:

   **PS > remove-psdrive mydb**

   **PS > afsluiten**

## <a name="see-also"></a>Zie ook

[Het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)