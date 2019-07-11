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
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734856"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="fbd17-102">Snelstartgids voor Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="fbd17-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="fbd17-103">In dit onderwerp wordt uitgelegd hoe u een Windows PowerShell-provider met de basisfunctionaliteit van het maken van een nieuw station maken.</span><span class="sxs-lookup"><span data-stu-id="fbd17-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="fbd17-104">Raadpleeg voor algemene informatie over providers [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fbd17-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="fbd17-105">Zie voor meer voorbeelden van providers met volledige functionaliteit [Provider voorbeelden](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbd17-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="fbd17-106">Schrijven van een basic-provider</span><span class="sxs-lookup"><span data-stu-id="fbd17-106">Writing a basic provider</span></span>

<span data-ttu-id="fbd17-107">De belangrijkste functionaliteit van een Windows PowerShell-provider is het maken en verwijderen van schijven.</span><span class="sxs-lookup"><span data-stu-id="fbd17-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="fbd17-108">In dit voorbeeld implementeren we de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methoden voor het [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="fbd17-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="fbd17-109">U ziet ook hoe u een providerklasse declareren.</span><span class="sxs-lookup"><span data-stu-id="fbd17-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="fbd17-110">Wanneer u een provider schrijft, kunt u standaard stations-stations die automatisch worden gemaakt wanneer de provider beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="fbd17-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="fbd17-111">U ook definiëren een methode voor het maken van nieuwe schijven die gebruikmaken van die provider.</span><span class="sxs-lookup"><span data-stu-id="fbd17-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="fbd17-112">De voorbeelden in dit onderwerp zijn gebaseerd op de [AccessDBProviderSample02](./accessdbprovidersample02.md) voorbeeld, dat deel uitmaakt van een grotere voorbeeldtoepassing die staat voor een Access-database als een Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="fbd17-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="fbd17-113">Instellen van het project</span><span class="sxs-lookup"><span data-stu-id="fbd17-113">Setting up the project</span></span>

<span data-ttu-id="fbd17-114">Maak een Class Library-project met de naam AccessDBProviderSample in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fbd17-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="fbd17-115">De volgende stappen voor het configureren van uw project, zodat Windows PowerShell wordt gestart en de provider geladen in de sessie worden, wanneer u bouwen en uw project te starten.</span><span class="sxs-lookup"><span data-stu-id="fbd17-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="fbd17-116">Configureer de provider-project</span><span class="sxs-lookup"><span data-stu-id="fbd17-116">Configure the provider project</span></span>

1. <span data-ttu-id="fbd17-117">De assembly System.Management.Automation toevoegen als een verwijzing naar uw project.</span><span class="sxs-lookup"><span data-stu-id="fbd17-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="fbd17-118">Klik op **Project > Eigenschappen AccessDBProviderSample > fouten opsporen in**.</span><span class="sxs-lookup"><span data-stu-id="fbd17-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="fbd17-119">In **Spustit projekt**, klikt u op **Start extern programma**, en navigeer naar het uitvoerbare bestand van Windows PowerShell (meestal c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="fbd17-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="fbd17-120">Onder **startopties**, voert u het volgende in de **opdrachtregelargumenten** vak: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="fbd17-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="fbd17-121">De providerklasse declareren</span><span class="sxs-lookup"><span data-stu-id="fbd17-121">Declaring the provider class</span></span>

<span data-ttu-id="fbd17-122">Onze-provider is afgeleid van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="fbd17-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="fbd17-123">De meeste providers die echte functionaliteit (toegang tot en items bewerken, navigeren door het gegevensarchief ophalen en instellen van de inhoud van items) worden afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="fbd17-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="fbd17-124">Naast het opgeven van dat de klasse is afgeleid van [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), moet u deze met bepaalt de [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) zoals wordt weergegeven in het voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="fbd17-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="fbd17-125">NewDrive implementeren</span><span class="sxs-lookup"><span data-stu-id="fbd17-125">Implementing NewDrive</span></span>

<span data-ttu-id="fbd17-126">De [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode wordt aangeroepen door de Windows PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet op te geven de naam van uw provider.</span><span class="sxs-lookup"><span data-stu-id="fbd17-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="fbd17-127">De parameter PSDriveInfo is doorgegeven door de Windows PowerShell-engine en de methode retourneert het nieuwe station met de Windows PowerShell-engine.</span><span class="sxs-lookup"><span data-stu-id="fbd17-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="fbd17-128">Deze methode moet worden gedeclareerd in de klasse die eerder is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fbd17-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="fbd17-129">De methode wordt eerst gecontroleerd om ervoor te zorgen dat zowel de hoofdmap van station die zijn doorgegeven als het stationsobject bestaat, retourneert `null` als een van beide niet.</span><span class="sxs-lookup"><span data-stu-id="fbd17-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="fbd17-130">Vervolgens wordt een constructor met de interne klasse AccessDBPSDriveInfo gebruikt om een nieuwe station te maken en een verbinding met het station van de Access-database vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fbd17-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="fbd17-131">Hier volgt de AccessDBPSDriveInfo interne klasse die de constructor gebruikt voor het maken van een nieuwe schijf bevat, en bevat de informatie over de status van het station.</span><span class="sxs-lookup"><span data-stu-id="fbd17-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="fbd17-132">RemoveDrive implementeren</span><span class="sxs-lookup"><span data-stu-id="fbd17-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="fbd17-133">De [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode wordt aangeroepen door de Windows PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.RemovePSDriveCommand ](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbd17-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="fbd17-134">De verbinding met de Access-database van de methode in deze provider wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="fbd17-134">The method in this provider closes the connection to the Access database.</span></span>

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