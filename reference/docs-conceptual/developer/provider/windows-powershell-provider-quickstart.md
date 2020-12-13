---
ms.date: 09/13/2016
ms.topic: reference
title: Snelstartgids voor Windows PowerShell-providers
description: Snelstartgids voor Windows PowerShell-providers
ms.openlocfilehash: f0fe0ad60e9d10efd505cda60af995c597226b92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664348"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="a1367-103">Snelstartgids voor Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="a1367-103">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="a1367-104">In dit onderwerp wordt uitgelegd hoe u een Windows Power shell-provider maakt met de basis functionaliteit van het maken van een nieuw station.</span><span class="sxs-lookup"><span data-stu-id="a1367-104">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="a1367-105">Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor algemene informatie over providers.</span><span class="sxs-lookup"><span data-stu-id="a1367-105">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="a1367-106">Voor voor beelden van providers met meer functionaliteit, Zie [provider voorbeelden](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1367-106">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="a1367-107">Een Basic-provider schrijven</span><span class="sxs-lookup"><span data-stu-id="a1367-107">Writing a basic provider</span></span>

<span data-ttu-id="a1367-108">De belangrijkste functionaliteit van een Windows Power shell-provider is het maken en verwijderen van stations.</span><span class="sxs-lookup"><span data-stu-id="a1367-108">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="a1367-109">In dit voor beeld implementeren we de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a1367-109">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="a1367-110">U zult ook zien hoe u een provider klasse declareert.</span><span class="sxs-lookup"><span data-stu-id="a1367-110">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="a1367-111">Wanneer u een provider schrijft, kunt u standaard stations opgeven die automatisch worden gemaakt wanneer de provider beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="a1367-111">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="a1367-112">U definieert ook een methode voor het maken van nieuwe stations die gebruikmaken van deze provider.</span><span class="sxs-lookup"><span data-stu-id="a1367-112">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="a1367-113">De voor beelden in dit onderwerp zijn gebaseerd op het [AccessDBProviderSample02](./accessdbprovidersample02.md) -voor beeld, dat deel uitmaakt van een groter voor beeld dat een Access-Data Base vertegenwoordigt als een Windows Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="a1367-113">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="a1367-114">Het project instellen</span><span class="sxs-lookup"><span data-stu-id="a1367-114">Setting up the project</span></span>

<span data-ttu-id="a1367-115">Maak in Visual Studio een Class Library-project met de naam AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="a1367-115">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="a1367-116">Voer de volgende stappen uit om uw project zodanig te configureren dat Windows Power shell wordt gestart en de provider wordt geladen in de sessie, wanneer u uw project bouwt en start.</span><span class="sxs-lookup"><span data-stu-id="a1367-116">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="a1367-117">Het provider project configureren</span><span class="sxs-lookup"><span data-stu-id="a1367-117">Configure the provider project</span></span>

1. <span data-ttu-id="a1367-118">Voeg de assembly System. Management. Automation toe als referentie voor uw project.</span><span class="sxs-lookup"><span data-stu-id="a1367-118">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="a1367-119">Klik op **Project > eigenschappen AccessDBProviderSample > fout opsporing**.</span><span class="sxs-lookup"><span data-stu-id="a1367-119">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="a1367-120">Klik in **Start project** op **extern programma starten** en navigeer naar het uitvoer bare Windows Power shell-bestand (meestal c:\Windows\System32\WindowsPowerShell\v1.0 \\.powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="a1367-120">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="a1367-121">Onder **Start opties** typt u het volgende in het vak **opdracht regel argumenten** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="a1367-121">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="a1367-122">De provider klasse declareren</span><span class="sxs-lookup"><span data-stu-id="a1367-122">Declaring the provider class</span></span>

<span data-ttu-id="a1367-123">Onze provider is afgeleid van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="a1367-123">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="a1367-124">De meeste providers die echte functionaliteit bieden (het openen en bewerken van items, het navigeren door het gegevens archief en het ophalen en instellen van de inhoud van items), zijn afgeleid van de [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -klasse.</span><span class="sxs-lookup"><span data-stu-id="a1367-124">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="a1367-125">Naast het opgeven dat de klasse is afgeleid van [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), moet u deze versie verf Raaien met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , zoals weer gegeven in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="a1367-125">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="a1367-126">NewDrive implementeren</span><span class="sxs-lookup"><span data-stu-id="a1367-126">Implementing NewDrive</span></span>

<span data-ttu-id="a1367-127">De methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) wordt aangeroepen door de Windows Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) aanroept en de naam van uw provider opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a1367-127">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="a1367-128">De para meter PSDriveInfo wordt door gegeven door de Windows Power shell-engine en de methode retourneert het nieuwe station naar de Windows Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="a1367-128">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="a1367-129">Deze methode moet worden gedeclareerd in de hierboven gemaakte klasse.</span><span class="sxs-lookup"><span data-stu-id="a1367-129">This method must be declared within the class created above.</span></span>

<span data-ttu-id="a1367-130">Met de methode wordt eerst gecontroleerd of zowel het object station als de hoofdmap van het station die zijn door gegeven, aanwezig zijn, `null` indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="a1367-130">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="a1367-131">Vervolgens wordt een constructor van de interne klasse AccessDBPSDriveInfo gebruikt voor het maken van een nieuwe schijf en een verbinding met de Access-Data Base die op het station staat.</span><span class="sxs-lookup"><span data-stu-id="a1367-131">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="a1367-132">Hieronder ziet u de interne klasse AccessDBPSDriveInfo die de constructor bevat die wordt gebruikt om een nieuw station te maken en bevat de status informatie voor het station.</span><span class="sxs-lookup"><span data-stu-id="a1367-132">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="a1367-133">RemoveDrive implementeren</span><span class="sxs-lookup"><span data-stu-id="a1367-133">Implementing RemoveDrive</span></span>

<span data-ttu-id="a1367-134">De methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) wordt aangeroepen door de Windows Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="a1367-134">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="a1367-135">De methode in deze provider sluit de verbinding met de Access-Data Base.</span><span class="sxs-lookup"><span data-stu-id="a1367-135">The method in this provider closes the connection to the Access database.</span></span>

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
