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
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846667"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="23694-102">Een Windows PowerShell-stationprovider maken</span><span class="sxs-lookup"><span data-stu-id="23694-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="23694-103">In dit onderwerp wordt beschreven hoe u een Windows PowerShell-station provider waarmee u een manier om een gegevensarchief toegang via een Windows PowerShell-station te maken.</span><span class="sxs-lookup"><span data-stu-id="23694-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="23694-104">Dit type provider is ook Windows PowerShell-station providers genoemd.</span><span class="sxs-lookup"><span data-stu-id="23694-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="23694-105">De Windows PowerShell-stations die worden gebruikt door de provider bieden de mogelijkheid om verbinding maken met het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="23694-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="23694-106">De Windows PowerShell-station-provider die hier worden beschreven, biedt toegang tot een Microsoft Access-database.</span><span class="sxs-lookup"><span data-stu-id="23694-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="23694-107">Voor deze provider, de Windows PowerShell-station de database (dit is mogelijk een willekeurig aantal stations toevoegen aan een station-provider), vertegenwoordigt de containers op het hoogste niveau van het station staan voor de tabellen in de database en de rijen in de items van de containers vertegenwoordigen de tabellen.</span><span class="sxs-lookup"><span data-stu-id="23694-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="23694-108">Hier volgt een lijst van de secties in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="23694-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="23694-109">Als u niet bekend bent met het schrijven van een provider van Windows PowerShell-station, lees deze gedeeltes in de volgorde waarin ze worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23694-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="23694-110">Echter, als u bekend bent met het schrijven van de provider van een station, gaat u rechtstreeks naar de informatie die u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="23694-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="23694-111">De Windows PowerShell-Provider-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="23694-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="23694-112">Basisfunctionaliteit definiëren</span><span class="sxs-lookup"><span data-stu-id="23694-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="23694-113">Het maken van informatie over de status van station</span><span class="sxs-lookup"><span data-stu-id="23694-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="23694-114">Het maken van een station</span><span class="sxs-lookup"><span data-stu-id="23694-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="23694-115">Dynamische Parameters te koppelen aan NewDrive</span><span class="sxs-lookup"><span data-stu-id="23694-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="23694-116">Verwijderen van een station</span><span class="sxs-lookup"><span data-stu-id="23694-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="23694-117">Tijdens de initialisatie van standaard stations</span><span class="sxs-lookup"><span data-stu-id="23694-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="23694-118">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="23694-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="23694-119">Testen van de Provider van Windows PowerShell-station</span><span class="sxs-lookup"><span data-stu-id="23694-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="23694-120">De Windows PowerShell-Provider-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="23694-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="23694-121">Uw provider station moet een .NET-klasse die is afgeleid van definiëren de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="23694-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="23694-122">Hier volgt de definitie van de klasse voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="23694-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="23694-123">U ziet dat in dit voorbeeld wordt de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk Hiermee geeft u een gebruiksvriendelijke naam voor de provider en de Windows PowerShell-specifieke mogelijkheden die de provider beschikbaar stelt aan de Windows PowerShell-runtime tijdens de verwerking van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="23694-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="23694-124">De mogelijke waarden voor de provider-mogelijkheden zijn gedefinieerd door de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming.</span><span class="sxs-lookup"><span data-stu-id="23694-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="23694-125">Deze provider station biedt geen ondersteuning van deze mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="23694-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="23694-126">Basisfunctionaliteit definiëren</span><span class="sxs-lookup"><span data-stu-id="23694-126">Defining Base Functionality</span></span>

<span data-ttu-id="23694-127">Zoals beschreven in [ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse is afgeleid van de [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse die de methoden die nodig zijn definieert voor het initialiseren en uninitializing van de provider.</span><span class="sxs-lookup"><span data-stu-id="23694-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="23694-128">Zie voor het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="23694-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="23694-129">De meeste providers (met inbegrip van de provider die hier worden beschreven) kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="23694-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="23694-130">Het maken van informatie over de status van station</span><span class="sxs-lookup"><span data-stu-id="23694-130">Creating Drive State Information</span></span>

<span data-ttu-id="23694-131">Alle Windows PowerShell-providers worden beschouwd als staatloze items, wat betekent dat uw provider station moet maken van alle informatie over de status die nodig is voor door de Windows PowerShell-runtime wordt uw provider.</span><span class="sxs-lookup"><span data-stu-id="23694-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="23694-132">Voor deze provider station bevat informatie over de status de verbinding met de database die als onderdeel van de stationsinformatie wordt bijgehouden.</span><span class="sxs-lookup"><span data-stu-id="23694-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="23694-133">Dit is de code die laat hoe deze gegevens worden opgeslagen zien de [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station wordt beschreven:</span><span class="sxs-lookup"><span data-stu-id="23694-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="23694-134">Het maken van een station</span><span class="sxs-lookup"><span data-stu-id="23694-134">Creating a Drive</span></span>

<span data-ttu-id="23694-135">Als u wilt toestaan dat de Windows PowerShell-runtime maken van een station, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode.</span><span class="sxs-lookup"><span data-stu-id="23694-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="23694-136">De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="23694-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="23694-137">Het onderdrukken van deze methode moet het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="23694-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="23694-138">Controleer de [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) lid bestaat en dat een verbinding met het gegevensarchief kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23694-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="23694-139">Een station maken en vullen van het lid van de verbinding, ter ondersteuning van de `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23694-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="23694-140">Valideer de [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object voor het voorgestelde station.</span><span class="sxs-lookup"><span data-stu-id="23694-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="23694-141">Wijzig de [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object met de beschrijving van het station met de vereiste prestaties of betrouwbaarheid informatie of het bieden van extra gegevens voor bellers met behulp van het station.</span><span class="sxs-lookup"><span data-stu-id="23694-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="23694-142">Afhandelen van fouten met behulp van de [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode en vervolgens terug `null`.</span><span class="sxs-lookup"><span data-stu-id="23694-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="23694-143">Deze methode retourneert een van beide de stationsinformatie die is doorgegeven aan de methode of een provider-versie van het.</span><span class="sxs-lookup"><span data-stu-id="23694-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="23694-144">Dynamische Parameters te koppelen aan NewDrive</span><span class="sxs-lookup"><span data-stu-id="23694-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="23694-145">De `New-PSDrive` cmdlet ondersteund door uw provider station mogelijk extra parameters.</span><span class="sxs-lookup"><span data-stu-id="23694-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="23694-146">Als u wilt deze dynamische parameters koppelen aan de cmdlet, de provider implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methode.</span><span class="sxs-lookup"><span data-stu-id="23694-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="23694-147">Deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span><span class="sxs-lookup"><span data-stu-id="23694-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="23694-148">Deze methode wordt niet door deze provider station worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="23694-148">This drive provider does not override this method.</span></span> <span data-ttu-id="23694-149">De volgende code toont echter de standaardimplementatie van deze methode:</span><span class="sxs-lookup"><span data-stu-id="23694-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="23694-150">Verwijderen van een station</span><span class="sxs-lookup"><span data-stu-id="23694-150">Removing a Drive</span></span>

<span data-ttu-id="23694-151">Als u wilt sluiten verbinding met de database, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode.</span><span class="sxs-lookup"><span data-stu-id="23694-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="23694-152">Deze methode wordt de verbinding met het station na het opschonen van de provider-specifieke informatie gesloten.</span><span class="sxs-lookup"><span data-stu-id="23694-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="23694-153">De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="23694-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="23694-154">Als het station kan worden verwijderd, de methode de informatie die is doorgegeven aan de methode via moet retourneren de `drive` parameter.</span><span class="sxs-lookup"><span data-stu-id="23694-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="23694-155">Als het station kan niet worden verwijderd, de methode moet schrijven van een uitzondering en ga vervolgens terug `null`.</span><span class="sxs-lookup"><span data-stu-id="23694-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="23694-156">Als deze methode wordt niet door uw provider worden overschreven, retourneert de standaardimplementatie van deze methode alleen de stationsinformatie doorgegeven als invoer.</span><span class="sxs-lookup"><span data-stu-id="23694-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="23694-157">Tijdens de initialisatie van standaard stations</span><span class="sxs-lookup"><span data-stu-id="23694-157">Initializing Default Drives</span></span>

<span data-ttu-id="23694-158">Uw provider station implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode voor het koppelen van stations.</span><span class="sxs-lookup"><span data-stu-id="23694-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="23694-159">De Active Directory-provider kan bijvoorbeeld een station voor de standaard-naamgevingscontext als de computer is toegevoegd aan een domein te koppelen.</span><span class="sxs-lookup"><span data-stu-id="23694-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="23694-160">Deze methode retourneert een verzameling van stationsinformatie over de geïnitialiseerd stations of een lege verzameling.</span><span class="sxs-lookup"><span data-stu-id="23694-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="23694-161">De aanroep naar deze methode wordt uitgevoerd na het aanroepen van de Windows PowerShell-runtime de [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode om te initialiseren van de provider.</span><span class="sxs-lookup"><span data-stu-id="23694-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="23694-162">Deze provider station niet overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode.</span><span class="sxs-lookup"><span data-stu-id="23694-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="23694-163">De volgende code toont echter de standaardimplementatie, een verzameling leeg station retourneert:</span><span class="sxs-lookup"><span data-stu-id="23694-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="23694-164">Om te onthouden over het implementeren van InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="23694-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="23694-165">Alle providers van station moeten een basisstation om de gebruiker met zichtbaarheid te koppelen.</span><span class="sxs-lookup"><span data-stu-id="23694-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="23694-166">Het basisstation kan lijst met locaties die als toegangspunten voor andere gekoppelde schijven fungeren.</span><span class="sxs-lookup"><span data-stu-id="23694-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="23694-167">Bijvoorbeeld, de Active Directory-provider kan maken van een station met een lijst met de naamgevingscontexten gevonden in de `namingContext` kenmerken in de hoofdmap gedistribueerde systeemomgeving (DSE).</span><span class="sxs-lookup"><span data-stu-id="23694-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="23694-168">Hierdoor kunnen gebruikers koppelpunten voor andere stations detecteren.</span><span class="sxs-lookup"><span data-stu-id="23694-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="23694-169">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="23694-169">Code Sample</span></span>

<span data-ttu-id="23694-170">Zie voor een compleet voorbeeld van code, [AccessDbProviderSample02 codevoorbeeld](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="23694-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="23694-171">Testen van de Provider van Windows PowerShell-station</span><span class="sxs-lookup"><span data-stu-id="23694-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="23694-172">Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel, met inbegrip van alle cmdlets beschikbaar gesteld door afleiding.</span><span class="sxs-lookup"><span data-stu-id="23694-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="23694-173">De schijfprovider voorbeeld gaan we testen.</span><span class="sxs-lookup"><span data-stu-id="23694-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="23694-174">Voer de `Get-PSProvider` cmdlet voor het ophalen van de lijst met providers om ervoor te zorgen dat de schijfprovider AccessDB aanwezig is:</span><span class="sxs-lookup"><span data-stu-id="23694-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="23694-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="23694-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="23694-176">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="23694-176">The following output appears:</span></span>

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

2. <span data-ttu-id="23694-177">Zorg ervoor dat de naam van een database-server (DSN) voor de database door het openen van bestaat de **gegevensbronnen** gedeelte van de **Systeembeheer** voor het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="23694-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="23694-178">In de **gebruiker DSN** tabel, dubbelklikt u op **MS Access-Database** en het pad naar station C:\ps\northwind.mdb toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="23694-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="23694-179">Maak een nieuw station met de voorbeeld-station-provider:</span><span class="sxs-lookup"><span data-stu-id="23694-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="23694-180">**PS > nieuwe psdrive-naam mydb-hoofdmap c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="23694-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="23694-181">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="23694-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="23694-182">De verbinding valideren.</span><span class="sxs-lookup"><span data-stu-id="23694-182">Validate the connection.</span></span> <span data-ttu-id="23694-183">Omdat de verbinding is gedefinieerd als een lid van het station, kunt u met behulp van de cmdlet Get-PDDrive kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="23694-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="23694-184">De gebruiker kan niet nog communiceren met de provider als een station, zoals de provider functionaliteit van de container voor die interactie moet.</span><span class="sxs-lookup"><span data-stu-id="23694-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="23694-185">Zie voor meer informatie, [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="23694-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="23694-186">**PS > .connection (get-psdrive mydb)**</span><span class="sxs-lookup"><span data-stu-id="23694-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="23694-187">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="23694-187">The following output appears:</span></span>

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

5. <span data-ttu-id="23694-188">Verwijderen van het station en de shell afsluiten:</span><span class="sxs-lookup"><span data-stu-id="23694-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="23694-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="23694-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="23694-190">**PS > afsluiten**</span><span class="sxs-lookup"><span data-stu-id="23694-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="23694-191">Zie ook</span><span class="sxs-lookup"><span data-stu-id="23694-191">See Also</span></span>

[<span data-ttu-id="23694-192">Het maken van Windows PowerShell-Providers</span><span class="sxs-lookup"><span data-stu-id="23694-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="23694-193">Ontwerp van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="23694-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="23694-194">Het maken van een eenvoudige Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="23694-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)