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
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855210"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="044a1-102">Een Windows PowerShell-stationprovider maken</span><span class="sxs-lookup"><span data-stu-id="044a1-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="044a1-103">In dit onderwerp wordt beschreven hoe u een Windows PowerShell-station provider waarmee u een manier om een gegevensarchief toegang via een Windows PowerShell-station te maken.</span><span class="sxs-lookup"><span data-stu-id="044a1-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="044a1-104">Dit type provider is ook Windows PowerShell-station providers genoemd.</span><span class="sxs-lookup"><span data-stu-id="044a1-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="044a1-105">De Windows PowerShell-stations die worden gebruikt door de provider bieden de mogelijkheid om verbinding maken met het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="044a1-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="044a1-106">De Windows PowerShell-station-provider die hier worden beschreven, biedt toegang tot een Microsoft Access-database.</span><span class="sxs-lookup"><span data-stu-id="044a1-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="044a1-107">Voor deze provider, de Windows PowerShell-station de database (dit is mogelijk een willekeurig aantal stations toevoegen aan een station-provider), vertegenwoordigt de containers op het hoogste niveau van het station staan voor de tabellen in de database en de rijen in de items van de containers vertegenwoordigen de tabellen.</span><span class="sxs-lookup"><span data-stu-id="044a1-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="044a1-108">De Windows PowerShell-Provider-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="044a1-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="044a1-109">Uw provider station moet een .NET-klasse die is afgeleid van definiëren de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="044a1-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="044a1-110">Hier volgt de definitie van de klasse voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="044a1-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="044a1-111">U ziet dat in dit voorbeeld wordt de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk Hiermee geeft u een gebruiksvriendelijke naam voor de provider en de Windows PowerShell-specifieke mogelijkheden die de provider beschikbaar stelt aan de Windows PowerShell-runtime tijdens de verwerking van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="044a1-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="044a1-112">De mogelijke waarden voor de provider-mogelijkheden zijn gedefinieerd door de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming.</span><span class="sxs-lookup"><span data-stu-id="044a1-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="044a1-113">Deze provider station biedt geen ondersteuning van deze mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="044a1-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="044a1-114">Basisfunctionaliteit definiëren</span><span class="sxs-lookup"><span data-stu-id="044a1-114">Defining Base Functionality</span></span>

<span data-ttu-id="044a1-115">Zoals beschreven in [ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse is afgeleid van de [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basisklasse die de methoden die nodig zijn definieert voor het initialiseren en uninitializing van de provider.</span><span class="sxs-lookup"><span data-stu-id="044a1-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="044a1-116">Zie voor het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="044a1-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="044a1-117">De meeste providers (met inbegrip van de provider die hier worden beschreven) kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="044a1-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="044a1-118">Het maken van informatie over de status van station</span><span class="sxs-lookup"><span data-stu-id="044a1-118">Creating Drive State Information</span></span>

<span data-ttu-id="044a1-119">Alle Windows PowerShell-providers worden beschouwd als staatloze items, wat betekent dat uw provider station moet maken van alle informatie over de status die nodig is voor door de Windows PowerShell-runtime wordt uw provider.</span><span class="sxs-lookup"><span data-stu-id="044a1-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="044a1-120">Voor deze provider station bevat informatie over de status de verbinding met de database die als onderdeel van de stationsinformatie wordt bijgehouden.</span><span class="sxs-lookup"><span data-stu-id="044a1-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="044a1-121">Dit is de code die laat hoe deze gegevens worden opgeslagen zien de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station wordt beschreven:</span><span class="sxs-lookup"><span data-stu-id="044a1-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="044a1-122">Het maken van een station</span><span class="sxs-lookup"><span data-stu-id="044a1-122">Creating a Drive</span></span>

<span data-ttu-id="044a1-123">Als u wilt toestaan dat de Windows PowerShell-runtime maken van een station, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode.</span><span class="sxs-lookup"><span data-stu-id="044a1-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="044a1-124">De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="044a1-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="044a1-125">Het onderdrukken van deze methode moet het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="044a1-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="044a1-126">Controleer de [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) lid bestaat en dat een verbinding met het gegevensarchief kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="044a1-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="044a1-127">Een station maken en vullen van het lid van de verbinding, ter ondersteuning van de `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="044a1-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="044a1-128">Valideer de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object voor het voorgestelde station.</span><span class="sxs-lookup"><span data-stu-id="044a1-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="044a1-129">Wijzig de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object met de beschrijving van het station met de vereiste prestaties of betrouwbaarheid informatie of het bieden van extra gegevens voor bellers met behulp van het station.</span><span class="sxs-lookup"><span data-stu-id="044a1-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="044a1-130">Afhandelen van fouten met behulp van de [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode en vervolgens terug `null`.</span><span class="sxs-lookup"><span data-stu-id="044a1-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="044a1-131">Deze methode retourneert een van beide de stationsinformatie die is doorgegeven aan de methode of een provider-versie van het.</span><span class="sxs-lookup"><span data-stu-id="044a1-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="044a1-132">Dynamische Parameters te koppelen aan NewDrive</span><span class="sxs-lookup"><span data-stu-id="044a1-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="044a1-133">De `New-PSDrive` cmdlet ondersteund door uw provider station mogelijk extra parameters.</span><span class="sxs-lookup"><span data-stu-id="044a1-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="044a1-134">Als u wilt deze dynamische parameters koppelen aan de cmdlet, de provider implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methode.</span><span class="sxs-lookup"><span data-stu-id="044a1-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="044a1-135">Deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span><span class="sxs-lookup"><span data-stu-id="044a1-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="044a1-136">Deze methode wordt niet door deze provider station worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="044a1-136">This drive provider does not override this method.</span></span> <span data-ttu-id="044a1-137">De volgende code toont echter de standaardimplementatie van deze methode:</span><span class="sxs-lookup"><span data-stu-id="044a1-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="044a1-138">Verwijderen van een station</span><span class="sxs-lookup"><span data-stu-id="044a1-138">Removing a Drive</span></span>

<span data-ttu-id="044a1-139">Als u wilt sluiten verbinding met de database, de schijfprovider moet implementeren de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode.</span><span class="sxs-lookup"><span data-stu-id="044a1-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="044a1-140">Deze methode wordt de verbinding met het station na het opschonen van de provider-specifieke informatie gesloten.</span><span class="sxs-lookup"><span data-stu-id="044a1-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="044a1-141">De volgende code toont de uitvoering van de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode voor deze provider station:</span><span class="sxs-lookup"><span data-stu-id="044a1-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="044a1-142">Als het station kan worden verwijderd, de methode de informatie die is doorgegeven aan de methode via moet retourneren de `drive` parameter.</span><span class="sxs-lookup"><span data-stu-id="044a1-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="044a1-143">Als het station kan niet worden verwijderd, de methode moet schrijven van een uitzondering en ga vervolgens terug `null`.</span><span class="sxs-lookup"><span data-stu-id="044a1-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="044a1-144">Als deze methode wordt niet door uw provider worden overschreven, retourneert de standaardimplementatie van deze methode alleen de stationsinformatie doorgegeven als invoer.</span><span class="sxs-lookup"><span data-stu-id="044a1-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="044a1-145">Tijdens de initialisatie van standaard stations</span><span class="sxs-lookup"><span data-stu-id="044a1-145">Initializing Default Drives</span></span>

<span data-ttu-id="044a1-146">Uw provider station implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode voor het koppelen van stations.</span><span class="sxs-lookup"><span data-stu-id="044a1-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="044a1-147">De Active Directory-provider kan bijvoorbeeld een station voor de standaard-naamgevingscontext als de computer is toegevoegd aan een domein te koppelen.</span><span class="sxs-lookup"><span data-stu-id="044a1-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="044a1-148">Deze methode retourneert een verzameling van stationsinformatie over de geïnitialiseerd stations of een lege verzameling.</span><span class="sxs-lookup"><span data-stu-id="044a1-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="044a1-149">De aanroep naar deze methode wordt uitgevoerd na het aanroepen van de Windows PowerShell-runtime de [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) methode om te initialiseren van de provider.</span><span class="sxs-lookup"><span data-stu-id="044a1-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="044a1-150">Deze provider station niet overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode.</span><span class="sxs-lookup"><span data-stu-id="044a1-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="044a1-151">De volgende code toont echter de standaardimplementatie, een verzameling leeg station retourneert:</span><span class="sxs-lookup"><span data-stu-id="044a1-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="044a1-152">Om te onthouden over het implementeren van InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="044a1-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="044a1-153">Alle providers van station moeten een basisstation om de gebruiker met zichtbaarheid te koppelen.</span><span class="sxs-lookup"><span data-stu-id="044a1-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="044a1-154">Het basisstation kan lijst met locaties die als toegangspunten voor andere gekoppelde schijven fungeren.</span><span class="sxs-lookup"><span data-stu-id="044a1-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="044a1-155">Bijvoorbeeld, de Active Directory-provider kan maken van een station met een lijst met de naamgevingscontexten gevonden in de `namingContext` kenmerken in de hoofdmap gedistribueerde systeemomgeving (DSE).</span><span class="sxs-lookup"><span data-stu-id="044a1-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="044a1-156">Hierdoor kunnen gebruikers koppelpunten voor andere stations detecteren.</span><span class="sxs-lookup"><span data-stu-id="044a1-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="044a1-157">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="044a1-157">Code Sample</span></span>

<span data-ttu-id="044a1-158">Zie voor een compleet voorbeeld van code, [AccessDbProviderSample02 codevoorbeeld](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="044a1-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="044a1-159">Testen van de Provider van Windows PowerShell-station</span><span class="sxs-lookup"><span data-stu-id="044a1-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="044a1-160">Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel, met inbegrip van alle cmdlets beschikbaar gesteld door afleiding.</span><span class="sxs-lookup"><span data-stu-id="044a1-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="044a1-161">De schijfprovider voorbeeld gaan we testen.</span><span class="sxs-lookup"><span data-stu-id="044a1-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="044a1-162">Voer de `Get-PSProvider` cmdlet voor het ophalen van de lijst met providers om ervoor te zorgen dat de schijfprovider AccessDB aanwezig is:</span><span class="sxs-lookup"><span data-stu-id="044a1-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="044a1-163">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="044a1-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="044a1-164">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="044a1-164">The following output appears:</span></span>

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

2. <span data-ttu-id="044a1-165">Zorg ervoor dat de naam van een database-server (DSN) voor de database door het openen van bestaat de **gegevensbronnen** gedeelte van de **Systeembeheer** voor het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="044a1-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="044a1-166">In de **gebruiker DSN** tabel, dubbelklikt u op **MS Access-Database** en het pad naar station C:\ps\northwind.mdb toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="044a1-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="044a1-167">Maak een nieuw station met de voorbeeld-station-provider:</span><span class="sxs-lookup"><span data-stu-id="044a1-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="044a1-168">**PS > nieuwe psdrive-naam mydb-hoofdmap c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="044a1-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="044a1-169">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="044a1-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="044a1-170">De verbinding valideren.</span><span class="sxs-lookup"><span data-stu-id="044a1-170">Validate the connection.</span></span> <span data-ttu-id="044a1-171">Omdat de verbinding is gedefinieerd als een lid van het station, kunt u met behulp van de cmdlet Get-PDDrive kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="044a1-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="044a1-172">De gebruiker kan niet nog communiceren met de provider als een station, zoals de provider functionaliteit van de container voor die interactie moet.</span><span class="sxs-lookup"><span data-stu-id="044a1-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="044a1-173">Zie voor meer informatie, [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="044a1-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="044a1-174">**PS > .connection (get-psdrive mydb)**</span><span class="sxs-lookup"><span data-stu-id="044a1-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="044a1-175">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="044a1-175">The following output appears:</span></span>

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

5. <span data-ttu-id="044a1-176">Verwijderen van het station en de shell afsluiten:</span><span class="sxs-lookup"><span data-stu-id="044a1-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="044a1-177">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="044a1-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="044a1-178">**PS > afsluiten**</span><span class="sxs-lookup"><span data-stu-id="044a1-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="044a1-179">Zie ook</span><span class="sxs-lookup"><span data-stu-id="044a1-179">See Also</span></span>

[<span data-ttu-id="044a1-180">Het maken van Windows PowerShell-Providers</span><span class="sxs-lookup"><span data-stu-id="044a1-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="044a1-181">Ontwerp van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="044a1-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="044a1-182">Het maken van een eenvoudige Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="044a1-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)