---
title: Quick start voor Windows Power shell-provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352358"
---
# <a name="windows-powershell-provider-quickstart"></a>Snelstartgids voor Windows PowerShell-providers

In dit onderwerp wordt uitgelegd hoe u een Windows Power shell-provider maakt met de basis functionaliteit van het maken van een nieuw station. Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor algemene informatie over providers. Voor voor beelden van providers met meer functionaliteit, Zie [provider voorbeelden](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Een Basic-provider schrijven

De belangrijkste functionaliteit van een Windows Power shell-provider is het maken en verwijderen van stations. In dit voor beeld implementeren we de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) van de [ Klasse System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . U zult ook zien hoe u een provider klasse declareert.

Wanneer u een provider schrijft, kunt u standaard stations opgeven die automatisch worden gemaakt wanneer de provider beschikbaar is. U definieert ook een methode voor het maken van nieuwe stations die gebruikmaken van deze provider.

De voor beelden in dit onderwerp zijn gebaseerd op het [AccessDBProviderSample02](./accessdbprovidersample02.md) -voor beeld, dat deel uitmaakt van een groter voor beeld dat een Access-Data Base vertegenwoordigt als een Windows Power Shell-station.

### <a name="setting-up-the-project"></a>Het project instellen

Maak in Visual Studio een Class Library-project met de naam AccessDBProviderSample. Voer de volgende stappen uit om uw project zodanig te configureren dat Windows Power shell wordt gestart en de provider wordt geladen in de sessie, wanneer u uw project bouwt en start.

##### <a name="configure-the-provider-project"></a>Het provider project configureren

1. Voeg de assembly System. Management. Automation toe als referentie voor uw project.

2. Klik op **Project > eigenschappen AccessDBProviderSample > fout opsporing**. Klik in **Start project**op **extern programma starten**en navigeer naar het uitvoer bare Windows Power shell-bestand (meestal c:\windows\system32\windowspowershell\ v1.0\\.powershell.exe).

3. Onder **Start opties**typt u het volgende in het vak **opdracht regel argumenten** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>De provider klasse declareren

Onze provider is afgeleid van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . De meeste providers die echte functionaliteit bieden (het openen en bewerken van items, het navigeren door het gegevens archief en het ophalen en instellen van de inhoud van items), zijn afgeleid van de [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -klasse.

Naast het opgeven dat de klasse is afgeleid van [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), moet u deze versie verf Raaien met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , zoals weer gegeven in het voor beeld .

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

De methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) wordt aangeroepen door de Windows Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) aanroept, waarbij de naam van uw providers. De para meter PSDriveInfo wordt door gegeven door de Windows Power shell-engine en de methode retourneert het nieuwe station naar de Windows Power shell-engine. Deze methode moet worden gedeclareerd in de hierboven gemaakte klasse.

De methode controleert eerst of zowel het object drive als de hoofdmap van het station die zijn door gegeven, bestaat en `null` retour neren als dat niet het geval is. Vervolgens wordt een constructor van de interne klasse AccessDBPSDriveInfo gebruikt voor het maken van een nieuwe schijf en een verbinding met de Access-Data Base die op het station staat.

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

Hieronder ziet u de interne klasse AccessDBPSDriveInfo die de constructor bevat die wordt gebruikt om een nieuw station te maken en bevat de status informatie voor het station.

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

De methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) wordt aangeroepen door de Windows Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) aanroept. De methode in deze provider sluit de verbinding met de Access-Data Base.

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