---
title: Windows PowerShell-Provider snelstartgids | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: ab78bcad301215bca9b5324bdb8de863899edec6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851112"
---
# <a name="windows-powershell-provider-quickstart"></a>Snelstartgids voor Windows PowerShell-providers

In dit onderwerp wordt uitgelegd hoe u een Windows PowerShell-provider met de basisfunctionaliteit van het maken van een nieuw station maken. Raadpleeg voor algemene informatie over providers [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md). Zie voor meer voorbeelden van providers met volledige functionaliteit [Provider voorbeelden](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Schrijven van een basic-provider

De belangrijkste functionaliteit van een Windows PowerShell-provider is het maken en verwijderen van schijven. In dit voorbeeld implementeren we de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methoden voor het [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse. U ziet ook hoe u een providerklasse declareren.

Wanneer u een provider schrijft, kunt u standaard stations-stations die automatisch worden gemaakt wanneer de provider beschikbaar is. U ook definiëren een methode voor het maken van nieuwe schijven die gebruikmaken van die provider.

De voorbeelden in dit onderwerp zijn gebaseerd op de [AccessDBProviderSample02](./accessdbprovidersample02.md) voorbeeld, dat deel uitmaakt van een grotere voorbeeldtoepassing die staat voor een Access-database als een Windows PowerShell-station.

### <a name="setting-up-the-project"></a>Instellen van het project

Maak een Class Library-project met de naam AccessDBProviderSample in Visual Studio. De volgende stappen voor het configureren van uw project, zodat Windows PowerShell wordt gestart en de provider geladen in de sessie worden, wanneer u bouwen en uw project te starten.

##### <a name="configure-the-provider-project"></a>Configureer de provider-project

1. De assembly System.Management.Automation toevoegen als een verwijzing naar uw project.

2. Klik op **Project > Eigenschappen AccessDBProviderSample > fouten opsporen in**. In **Spustit projekt**, klikt u op **Start extern programma**, en navigeer naar het uitvoerbare bestand van Windows PowerShell (meestal c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Onder **startopties**, voert u het volgende in de **opdrachtregelargumenten** vak: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>De providerklasse declareren

Onze-provider is afgeleid van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse. De meeste providers die echte functionaliteit (toegang tot en items bewerken, navigeren door het gegevensarchief ophalen en instellen van de inhoud van items) worden afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse.

Naast het opgeven van dat de klasse is afgeleid van [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), moet u deze met bepaalt de [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) zoals wordt weergegeven in het voorbeeld.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>NewDrive implementeren

De [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode wordt aangeroepen door de Windows PowerShell-engine als een gebruiker roept de [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet op te geven de naam van uw provider. De parameter PSDriveInfo is doorgegeven door de Windows PowerShell-engine en de methode retourneert het nieuwe station met de Windows PowerShell-engine. Deze methode moet worden gedeclareerd in de klasse die eerder is gemaakt.

De methode wordt eerst gecontroleerd om ervoor te zorgen dat zowel de hoofdmap van station die zijn doorgegeven als het stationsobject bestaat, retourneert `null` als een van beide niet. Vervolgens wordt een constructor met de interne klasse AccessDBPSDriveInfo gebruikt om een nieuwe station te maken en een verbinding met het station van de Access-database vertegenwoordigt.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

Hier volgt de AccessDBPSDriveInfo interne klasse die de constructor gebruikt voor het maken van een nieuwe schijf bevat, en bevat de informatie over de status van het station.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>RemoveDrive implementeren

De [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode wordt aangeroepen door de Windows PowerShell-engine als een gebruiker roept de [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. De verbinding met de Access-database van de methode in deze provider wordt gesloten.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```