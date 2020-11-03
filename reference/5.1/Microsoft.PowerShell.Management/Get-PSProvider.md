---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250791"
---
# <span data-ttu-id="6cba7-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="6cba7-103">Get-PSProvider</span></span>

## <span data-ttu-id="6cba7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6cba7-104">SYNOPSIS</span></span>
<span data-ttu-id="6cba7-105">Hiermee haalt u informatie op over de opgegeven Windows Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="6cba7-105">Gets information about the specified Windows PowerShell provider.</span></span>

## <span data-ttu-id="6cba7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6cba7-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6cba7-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6cba7-107">DESCRIPTION</span></span>
<span data-ttu-id="6cba7-108">Met de cmdlet **Get-PSProvider** worden de Windows Power shell-providers in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6cba7-108">The **Get-PSProvider** cmdlet gets the Windows PowerShell providers in the current session.</span></span>
<span data-ttu-id="6cba7-109">U kunt een bepaald station of alle stations in de sessie ophalen.</span><span class="sxs-lookup"><span data-stu-id="6cba7-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="6cba7-110">Windows Power shell-providers stellen u in staat om toegang te krijgen tot diverse gegevens archieven, alsof ze bestandssysteem stations zijn.</span><span class="sxs-lookup"><span data-stu-id="6cba7-110">Windows PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="6cba7-111">Zie about_Providers voor meer informatie over Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="6cba7-111">For information about Windows PowerShell providers, see about_Providers.</span></span>

## <span data-ttu-id="6cba7-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6cba7-112">EXAMPLES</span></span>

### <span data-ttu-id="6cba7-113">Voor beeld 1: een lijst met alle beschik bare providers weer geven</span><span class="sxs-lookup"><span data-stu-id="6cba7-113">Example 1: Display a list of all available providers</span></span>

```
PS C:\> Get-PSProvider
```

<span data-ttu-id="6cba7-114">Met deze opdracht wordt een lijst weer gegeven met alle beschik bare Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="6cba7-114">This command displays a list of all available Windows PowerShell providers.</span></span>

### <span data-ttu-id="6cba7-115">Voor beeld 2: een lijst weer geven met alle Windows Power shell-providers die beginnen met opgegeven letters</span><span class="sxs-lookup"><span data-stu-id="6cba7-115">Example 2: Display a list of all Windows PowerShell providers that begin with specified letters</span></span>

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="6cba7-116">Met deze opdracht wordt een lijst weer gegeven met alle Windows Power shell-providers met namen die beginnen met de letter f of r.</span><span class="sxs-lookup"><span data-stu-id="6cba7-116">This command displays a list of all Windows PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="6cba7-117">Voor beeld 3: modules of modules zoeken die providers aan uw sessie hebben toegevoegd</span><span class="sxs-lookup"><span data-stu-id="6cba7-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="6cba7-118">Met deze opdrachten vindt u de Windows Power shell-modules die providers hebben toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="6cba7-118">These commands find the Windows PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="6cba7-119">Alle Windows Power shell-elementen, inclusief providers, zijn afkomstig uit een module of een module.</span><span class="sxs-lookup"><span data-stu-id="6cba7-119">All Windows PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="6cba7-120">Deze opdrachten gebruiken de eigenschappen PSSnapin en module van het **ProviderInfo** -object die **Get-PSProvider** retourneert.</span><span class="sxs-lookup"><span data-stu-id="6cba7-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that **Get-PSProvider** returns.</span></span>
<span data-ttu-id="6cba7-121">De waarden van deze eigenschappen bevatten de naam van de module of module die de provider toevoegt.</span><span class="sxs-lookup"><span data-stu-id="6cba7-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="6cba7-122">Met de eerste opdracht worden alle providers in de sessie opgehaald en opgemaakt in een tabel met de waarden van hun naam, module en PSSnapin eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="6cba7-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="6cba7-123">De tweede opdracht gebruikt de cmdlet Where-Object om de providers op te halen die afkomstig zijn uit de module **micro soft. Power shell. Security** .</span><span class="sxs-lookup"><span data-stu-id="6cba7-123">The second command uses the Where-Object cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="6cba7-124">Voor beeld 4: het pad naar de start-eigenschap van de bestandssysteem provider oplossen</span><span class="sxs-lookup"><span data-stu-id="6cba7-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

<span data-ttu-id="6cba7-125">In dit voor beeld ziet u dat het tilde-symbool (~) de waarde vertegenwoordigt van de eigenschap Home van de File System-Provider.</span><span class="sxs-lookup"><span data-stu-id="6cba7-125">This example shows that the tilde symbol (~) represents the value of the Home property of the FileSystem provider.</span></span>
<span data-ttu-id="6cba7-126">De waarde van de eigenschap Home is optioneel, maar voor de bestandssysteem provider is deze gedefinieerd als $env: HOMEDRIVE \$ env: homepath of $Home.</span><span class="sxs-lookup"><span data-stu-id="6cba7-126">The Home property value is optional, but for the FileSystem provider, it is defined as $env:homedrive\$env:homepath or $home.</span></span>

## <span data-ttu-id="6cba7-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6cba7-127">PARAMETERS</span></span>

### <span data-ttu-id="6cba7-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="6cba7-128">-PSProvider</span></span>
<span data-ttu-id="6cba7-129">Hiermee geeft u de naam of namen van de Windows Power shell-providers waarover deze cmdlet informatie ophaalt.</span><span class="sxs-lookup"><span data-stu-id="6cba7-129">Specifies the name or names of the Windows PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6cba7-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6cba7-130">CommonParameters</span></span>
<span data-ttu-id="6cba7-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6cba7-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6cba7-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6cba7-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6cba7-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="6cba7-133">INPUTS</span></span>

### <span data-ttu-id="6cba7-134">Teken reeks []</span><span class="sxs-lookup"><span data-stu-id="6cba7-134">String[]</span></span>

<span data-ttu-id="6cba7-135">U kunt een of meer provider naam reeksen door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6cba7-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="6cba7-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6cba7-136">OUTPUTS</span></span>

### <span data-ttu-id="6cba7-137">System. Management. Automation. ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="6cba7-137">System.Management.Automation.ProviderInfo</span></span>
<span data-ttu-id="6cba7-138">Deze cmdlet retourneert objecten die de Windows Power shell-providers in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="6cba7-138">This cmdlet returns objects that represent the Windows PowerShell providers in the session.</span></span>

## <span data-ttu-id="6cba7-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6cba7-139">NOTES</span></span>

## <span data-ttu-id="6cba7-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6cba7-140">RELATED LINKS</span></span>

## <span data-ttu-id="6cba7-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6cba7-141">RELATED LINKS</span></span>
