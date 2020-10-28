---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-stationprovider maken
description: Een Windows PowerShell-stationprovider maken
ms.openlocfilehash: 639518fce27d941b7529b091364c5905c91a5c0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663030"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Een Windows PowerShell-stationprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-schijf provider maakt die een manier biedt om toegang te krijgen tot een gegevens archief via een Windows Power Shell-station. Dit type provider wordt ook wel Windows Power shell-schijf providers genoemd. De Windows Power Shell-stations die worden gebruikt door de provider bieden de mogelijkheid om verbinding te maken met het gegevens archief.

De Windows Power shell-schijf provider die hier wordt beschreven, biedt toegang tot een micro soft Access-Data Base.
Het Windows Power Shell-station vertegenwoordigt de data base (het is mogelijk om een wille keurig aantal stations toe te voegen aan een schijf provider), de containers op het hoogste niveau van het station vertegenwoordigen de tabellen in de data base en de items in de containers vertegenwoordigen de rijen in de tabellen.

## <a name="defining-the-windows-powershell-provider-class"></a>De Windows Power shell-provider klasse definiëren

De provider van het station moet een .NET-klasse definiëren die is afgeleid van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Hier volgt de klassedefinitie voor deze schijf provider:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

In dit voor beeld geeft het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) een beschrijvende naam op voor de provider en de specifieke Windows Power shell-mogelijkheden die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens de verwerking van de opdracht.
De mogelijke waarden voor de provider mogelijkheden worden gedefinieerd door de inventarisatie [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Deze schijf provider biedt geen ondersteuning voor een van deze mogelijkheden.

## <a name="defining-base-functionality"></a>Basis functionaliteit definiëren

Zoals beschreven in het [ontwerp van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) afgeleid van de basis klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) die de methoden definieert die nodig zijn voor het initialiseren en ongedaan maakt van de initialisatie van de provider. Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor informatie over het implementeren van de functionaliteit voor het toevoegen van toepassingsspecifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.
De meeste providers (met inbegrip van de hier beschreven provider) kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit die wordt verschaft door Windows Power shell.

## <a name="creating-drive-state-information"></a>Informatie over de status van stations maken

Alle Windows Power shell-providers worden beschouwd als stateless, wat betekent dat de provider van het station status informatie moet maken die nodig is voor de Windows Power shell-runtime wanneer deze uw provider aanroept.

De status informatie voor deze schijf provider bevat de verbinding met de data base die wordt bewaard als onderdeel van de informatie van het station. Hier volgt een code die laat zien hoe deze informatie wordt opgeslagen in het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station beschrijft:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a>Een station maken

Om ervoor te zorgen dat Windows Power shell runtime een station kan maken, moet de provider van het station de methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) implementeren. De volgende code toont de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) voor deze schijf provider:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

Uw onderdrukking van deze methode moet het volgende doen:

- Controleer of de [System.Management.Automation.PSDriveinfo. Hoofdmap *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) lid bestaat en er kan een verbinding met het gegevens archief worden gemaakt.
- Maak een station en vul het lid van de verbinding in voor ondersteuning van de `New-PSDrive` cmdlet.
- Valideer het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object voor het voorgestelde station.
- Wijzig het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station beschrijft met de vereiste prestatie-of betrouwbaarheids gegevens, of geef extra gegevens op voor aanroepers met behulp van het station.
- Los fouten op met behulp van de methode [System. Management. Automation. provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) en retour neer `null` .

  Deze methode retourneert de stationsgegevens die zijn door gegeven aan de methode of een providerspecifieke versie van de schijf.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Dynamische para meters aan NewDrive koppelen

`New-PSDrive`Voor de cmdlet die door de provider van de schijf wordt ondersteund, zijn mogelijk extra para meters vereist. Om deze dynamische para meters aan de cmdlet te koppelen, implementeert de provider de methode [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) . Deze methode retourneert een object met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object.

Deze schijf provider overschrijft deze methode niet. De volgende code toont echter de standaard implementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Een station verwijderen

De provider van het station moet de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) implementeren om de database verbinding te sluiten. Met deze methode wordt de verbinding met het station gesloten na het opschonen van specifieke informatie over de provider.

De volgende code toont de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) voor deze schijf provider:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

Als het station kan worden verwijderd, moet de methode de informatie retour neren die wordt door gegeven aan de methode via de `drive` para meter. Als het station niet kan worden verwijderd, moet de methode een uitzonde ring schrijven en vervolgens terugkeren `null` . Als uw provider deze methode niet overschrijft, retourneert de standaard implementatie van deze methode alleen de stationsgegevens die zijn door gegeven als invoer.

## <a name="initializing-default-drives"></a>Standaard stations initialiseren

De provider van uw station implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -methode om stations te koppelen. Zo kan de Active Directory provider een station koppelen voor de standaard naamgevings context als de computer lid is van een domein.

Deze methode retourneert een verzameling station gegevens over de geïnitialiseerde stations of een lege verzameling. De aanroep van deze methode wordt uitgevoerd nadat de Windows Power shell-runtime de methode [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) aanroept om de provider te initialiseren.

Deze stations-provider overschrijft de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -methode niet. De volgende code toont echter de standaard implementatie, waarmee een lege stations verzameling wordt geretourneerd:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Wat u moet weten over implementatie van InitializeDefaultDrives

Alle providers van stations moeten een basis station koppelen om de gebruiker te helpen met vind baarheid. In het hoofd station kunnen locaties worden weer geven die fungeren als Roots voor andere gekoppelde schijven. Zo kan de Active Directory provider een station maken met een lijst met de naamgevings contexten die zijn gevonden in de `namingContext` kenmerken van de basis gedistribueerde systeem omgeving (DSE). Dit helpt gebruikers bij het detecteren van koppel punten voor andere stations.

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample02 code sample](./accessdbprovidersample02-code-sample.md)voor een volledige voorbeeld code.

## <a name="testing-the-windows-powershell-drive-provider"></a>De provider van het Windows Power Shell-station testen

Wanneer uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel, inclusief alle cmdlets die beschikbaar zijn gemaakt door afleiding. We gaan de provider van het voorbeeld station testen.

1. Voer de `Get-PSProvider` cmdlet uit om de lijst met providers op te halen om ervoor te zorgen dat de AccessDB-schijf provider aanwezig is:

   **PS-> `Get-PSProvider`**

   De volgende uitvoer wordt weergegeven:

   ```Output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Zorg ervoor dat er een DSN (Data Base Server name) bestaat voor de data base door toegang te krijgen tot het gedeelte **gegevens bronnen** van de **beheer Programma's** voor het besturings systeem. Dubbel klik in de tabel **gebruikers-DSN** op **MS Access-Data Base** en voeg het stationspad toe `C:\ps\northwind.mdb` .

3. Maak een nieuw station met behulp van de provider van het voorbeeld station:

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   De volgende uitvoer wordt weergegeven:

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Valideer de verbinding. Omdat de verbinding als een lid van het station is gedefinieerd, kunt u deze controleren met behulp van de cmdlet Get-PDDrive.

   > [!NOTE]
   > De gebruiker kan nog niet communiceren met de provider als een station, omdat de provider container functionaliteit voor die interactie nodig heeft. Zie [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md)voor meer informatie.

   **PS> (Get-psdrive myDb). Connection**

   De volgende uitvoer wordt weergegeven:

   ```Output
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

5. Verwijder het station en sluit de shell:

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a>Zie ook

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Een eenvoudige Windows PowerShell-provider ontwerpen](./creating-a-basic-windows-powershell-provider.md)
