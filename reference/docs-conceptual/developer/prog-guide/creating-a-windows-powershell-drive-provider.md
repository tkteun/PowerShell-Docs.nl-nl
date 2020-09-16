---
title: Een Windows Power shell-schijf provider maken | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.openlocfilehash: 2a2178714ed548986fe1a1a4de8828e8e0a938cb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787186"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="72d4f-102">Een Windows PowerShell-stationprovider maken</span><span class="sxs-lookup"><span data-stu-id="72d4f-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="72d4f-103">In dit onderwerp wordt beschreven hoe u een Windows Power shell-schijf provider maakt die een manier biedt om toegang te krijgen tot een gegevens archief via een Windows Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="72d4f-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="72d4f-104">Dit type provider wordt ook wel Windows Power shell-schijf providers genoemd.</span><span class="sxs-lookup"><span data-stu-id="72d4f-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="72d4f-105">De Windows Power Shell-stations die worden gebruikt door de provider bieden de mogelijkheid om verbinding te maken met het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="72d4f-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="72d4f-106">De Windows Power shell-schijf provider die hier wordt beschreven, biedt toegang tot een micro soft Access-Data Base.</span><span class="sxs-lookup"><span data-stu-id="72d4f-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span>
<span data-ttu-id="72d4f-107">Het Windows Power Shell-station vertegenwoordigt de data base (het is mogelijk om een wille keurig aantal stations toe te voegen aan een schijf provider), de containers op het hoogste niveau van het station vertegenwoordigen de tabellen in de data base en de items in de containers vertegenwoordigen de rijen in de tabellen.</span><span class="sxs-lookup"><span data-stu-id="72d4f-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="72d4f-108">De Windows Power shell-provider klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="72d4f-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="72d4f-109">De provider van het station moet een .NET-klasse definiëren die is afgeleid van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="72d4f-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="72d4f-110">Hier volgt de klassedefinitie voor deze schijf provider:</span><span class="sxs-lookup"><span data-stu-id="72d4f-110">Here is the class definition for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

<span data-ttu-id="72d4f-111">In dit voor beeld geeft het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) een beschrijvende naam op voor de provider en de specifieke Windows Power shell-mogelijkheden die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens de verwerking van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="72d4f-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span>
<span data-ttu-id="72d4f-112">De mogelijke waarden voor de provider mogelijkheden worden gedefinieerd door de inventarisatie [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) .</span><span class="sxs-lookup"><span data-stu-id="72d4f-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="72d4f-113">Deze schijf provider biedt geen ondersteuning voor een van deze mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="72d4f-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="72d4f-114">Basis functionaliteit definiëren</span><span class="sxs-lookup"><span data-stu-id="72d4f-114">Defining Base Functionality</span></span>

<span data-ttu-id="72d4f-115">Zoals beschreven in het [ontwerp van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) afgeleid van de basis klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) die de methoden definieert die nodig zijn voor het initialiseren en ongedaan maakt van de initialisatie van de provider.</span><span class="sxs-lookup"><span data-stu-id="72d4f-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="72d4f-116">Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor informatie over het implementeren van de functionaliteit voor het toevoegen van toepassingsspecifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.</span><span class="sxs-lookup"><span data-stu-id="72d4f-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="72d4f-117">De meeste providers (met inbegrip van de hier beschreven provider) kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit die wordt verschaft door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="72d4f-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="72d4f-118">Informatie over de status van stations maken</span><span class="sxs-lookup"><span data-stu-id="72d4f-118">Creating Drive State Information</span></span>

<span data-ttu-id="72d4f-119">Alle Windows Power shell-providers worden beschouwd als stateless, wat betekent dat de provider van het station status informatie moet maken die nodig is voor de Windows Power shell-runtime wanneer deze uw provider aanroept.</span><span class="sxs-lookup"><span data-stu-id="72d4f-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="72d4f-120">De status informatie voor deze schijf provider bevat de verbinding met de data base die wordt bewaard als onderdeel van de informatie van het station.</span><span class="sxs-lookup"><span data-stu-id="72d4f-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="72d4f-121">Hier volgt een code die laat zien hoe deze informatie wordt opgeslagen in het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station beschrijft:</span><span class="sxs-lookup"><span data-stu-id="72d4f-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a><span data-ttu-id="72d4f-122">Een station maken</span><span class="sxs-lookup"><span data-stu-id="72d4f-122">Creating a Drive</span></span>

<span data-ttu-id="72d4f-123">Om ervoor te zorgen dat Windows Power shell runtime een station kan maken, moet de provider van het station de methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) implementeren.</span><span class="sxs-lookup"><span data-stu-id="72d4f-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="72d4f-124">De volgende code toont de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) voor deze schijf provider:</span><span class="sxs-lookup"><span data-stu-id="72d4f-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

<span data-ttu-id="72d4f-125">Uw onderdrukking van deze methode moet het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="72d4f-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="72d4f-126">Controleer of de [System.Management.Automation.PSDriveinfo. Hoofdmap \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) lid bestaat en er kan een verbinding met het gegevens archief worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="72d4f-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>
- <span data-ttu-id="72d4f-127">Maak een station en vul het lid van de verbinding in voor ondersteuning van de `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d4f-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>
- <span data-ttu-id="72d4f-128">Valideer het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object voor het voorgestelde station.</span><span class="sxs-lookup"><span data-stu-id="72d4f-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>
- <span data-ttu-id="72d4f-129">Wijzig het [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -object dat het station beschrijft met de vereiste prestatie-of betrouwbaarheids gegevens, of geef extra gegevens op voor aanroepers met behulp van het station.</span><span class="sxs-lookup"><span data-stu-id="72d4f-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>
- <span data-ttu-id="72d4f-130">Los fouten op met behulp van de methode [System. Management. Automation. provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) en retour neer `null` .</span><span class="sxs-lookup"><span data-stu-id="72d4f-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="72d4f-131">Deze methode retourneert de stationsgegevens die zijn door gegeven aan de methode of een providerspecifieke versie van de schijf.</span><span class="sxs-lookup"><span data-stu-id="72d4f-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="72d4f-132">Dynamische para meters aan NewDrive koppelen</span><span class="sxs-lookup"><span data-stu-id="72d4f-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="72d4f-133">`New-PSDrive`Voor de cmdlet die door de provider van de schijf wordt ondersteund, zijn mogelijk extra para meters vereist.</span><span class="sxs-lookup"><span data-stu-id="72d4f-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="72d4f-134">Om deze dynamische para meters aan de cmdlet te koppelen, implementeert de provider de methode [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="72d4f-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="72d4f-135">Deze methode retourneert een object met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object.</span><span class="sxs-lookup"><span data-stu-id="72d4f-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="72d4f-136">Deze schijf provider overschrijft deze methode niet.</span><span class="sxs-lookup"><span data-stu-id="72d4f-136">This drive provider does not override this method.</span></span> <span data-ttu-id="72d4f-137">De volgende code toont echter de standaard implementatie van deze methode:</span><span class="sxs-lookup"><span data-stu-id="72d4f-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="72d4f-138">Een station verwijderen</span><span class="sxs-lookup"><span data-stu-id="72d4f-138">Removing a Drive</span></span>

<span data-ttu-id="72d4f-139">De provider van het station moet de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) implementeren om de database verbinding te sluiten.</span><span class="sxs-lookup"><span data-stu-id="72d4f-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="72d4f-140">Met deze methode wordt de verbinding met het station gesloten na het opschonen van specifieke informatie over de provider.</span><span class="sxs-lookup"><span data-stu-id="72d4f-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="72d4f-141">De volgende code toont de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) voor deze schijf provider:</span><span class="sxs-lookup"><span data-stu-id="72d4f-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

<span data-ttu-id="72d4f-142">Als het station kan worden verwijderd, moet de methode de informatie retour neren die wordt door gegeven aan de methode via de `drive` para meter.</span><span class="sxs-lookup"><span data-stu-id="72d4f-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="72d4f-143">Als het station niet kan worden verwijderd, moet de methode een uitzonde ring schrijven en vervolgens terugkeren `null` .</span><span class="sxs-lookup"><span data-stu-id="72d4f-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="72d4f-144">Als uw provider deze methode niet overschrijft, retourneert de standaard implementatie van deze methode alleen de stationsgegevens die zijn door gegeven als invoer.</span><span class="sxs-lookup"><span data-stu-id="72d4f-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="72d4f-145">Standaard stations initialiseren</span><span class="sxs-lookup"><span data-stu-id="72d4f-145">Initializing Default Drives</span></span>

<span data-ttu-id="72d4f-146">De provider van uw station implementeert de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -methode om stations te koppelen.</span><span class="sxs-lookup"><span data-stu-id="72d4f-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="72d4f-147">Zo kan de Active Directory provider een station koppelen voor de standaard naamgevings context als de computer lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="72d4f-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="72d4f-148">Deze methode retourneert een verzameling station gegevens over de geïnitialiseerde stations of een lege verzameling.</span><span class="sxs-lookup"><span data-stu-id="72d4f-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="72d4f-149">De aanroep van deze methode wordt uitgevoerd nadat de Windows Power shell-runtime de methode [System. Management. Automation. provider. Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) aanroept om de provider te initialiseren.</span><span class="sxs-lookup"><span data-stu-id="72d4f-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="72d4f-150">Deze stations-provider overschrijft de [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -methode niet.</span><span class="sxs-lookup"><span data-stu-id="72d4f-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="72d4f-151">De volgende code toont echter de standaard implementatie, waarmee een lege stations verzameling wordt geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="72d4f-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="72d4f-152">Wat u moet weten over implementatie van InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="72d4f-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="72d4f-153">Alle providers van stations moeten een basis station koppelen om de gebruiker te helpen met vind baarheid.</span><span class="sxs-lookup"><span data-stu-id="72d4f-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="72d4f-154">In het hoofd station kunnen locaties worden weer geven die fungeren als Roots voor andere gekoppelde schijven.</span><span class="sxs-lookup"><span data-stu-id="72d4f-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="72d4f-155">Zo kan de Active Directory provider een station maken met een lijst met de naamgevings contexten die zijn gevonden in de `namingContext` kenmerken van de basis gedistribueerde systeem omgeving (DSE).</span><span class="sxs-lookup"><span data-stu-id="72d4f-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="72d4f-156">Dit helpt gebruikers bij het detecteren van koppel punten voor andere stations.</span><span class="sxs-lookup"><span data-stu-id="72d4f-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="72d4f-157">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="72d4f-157">Code Sample</span></span>

<span data-ttu-id="72d4f-158">Zie [AccessDbProviderSample02 code sample](./accessdbprovidersample02-code-sample.md)voor een volledige voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="72d4f-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="72d4f-159">De provider van het Windows Power Shell-station testen</span><span class="sxs-lookup"><span data-stu-id="72d4f-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="72d4f-160">Wanneer uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel, inclusief alle cmdlets die beschikbaar zijn gemaakt door afleiding.</span><span class="sxs-lookup"><span data-stu-id="72d4f-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="72d4f-161">We gaan de provider van het voorbeeld station testen.</span><span class="sxs-lookup"><span data-stu-id="72d4f-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="72d4f-162">Voer de `Get-PSProvider` cmdlet uit om de lijst met providers op te halen om ervoor te zorgen dat de AccessDB-schijf provider aanwezig is:</span><span class="sxs-lookup"><span data-stu-id="72d4f-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="72d4f-163">**PS-> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="72d4f-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="72d4f-164">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="72d4f-164">The following output appears:</span></span>

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

2. <span data-ttu-id="72d4f-165">Zorg ervoor dat er een DSN (Data Base Server name) bestaat voor de data base door toegang te krijgen tot het gedeelte **gegevens bronnen** van de **beheer Programma's** voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="72d4f-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="72d4f-166">Dubbel klik in de tabel **gebruikers-DSN** op **MS Access-Data Base** en voeg het stationspad toe `C:\ps\northwind.mdb` .</span><span class="sxs-lookup"><span data-stu-id="72d4f-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path `C:\ps\northwind.mdb`.</span></span>

3. <span data-ttu-id="72d4f-167">Maak een nieuw station met behulp van de provider van het voorbeeld station:</span><span class="sxs-lookup"><span data-stu-id="72d4f-167">Create a new drive using the sample drive provider:</span></span>

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   <span data-ttu-id="72d4f-168">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="72d4f-168">The following output appears:</span></span>

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="72d4f-169">Valideer de verbinding.</span><span class="sxs-lookup"><span data-stu-id="72d4f-169">Validate the connection.</span></span> <span data-ttu-id="72d4f-170">Omdat de verbinding als een lid van het station is gedefinieerd, kunt u deze controleren met behulp van de Get-PDDrive-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d4f-170">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="72d4f-171">De gebruiker kan nog niet communiceren met de provider als een station, omdat de provider container functionaliteit voor die interactie nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="72d4f-171">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="72d4f-172">Zie [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72d4f-172">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="72d4f-173">**PS> (Get-psdrive myDb). Connection**</span><span class="sxs-lookup"><span data-stu-id="72d4f-173">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="72d4f-174">De volgende uitvoer wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="72d4f-174">The following output appears:</span></span>

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

5. <span data-ttu-id="72d4f-175">Verwijder het station en sluit de shell:</span><span class="sxs-lookup"><span data-stu-id="72d4f-175">Remove the drive and exit the shell:</span></span>

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a><span data-ttu-id="72d4f-176">Zie ook</span><span class="sxs-lookup"><span data-stu-id="72d4f-176">See Also</span></span>

[<span data-ttu-id="72d4f-177">Windows Power shell-providers maken</span><span class="sxs-lookup"><span data-stu-id="72d4f-177">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="72d4f-178">Uw Windows Power shell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="72d4f-178">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="72d4f-179">Een eenvoudige Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="72d4f-179">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
