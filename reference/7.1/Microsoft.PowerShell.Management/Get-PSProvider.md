---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: e11a62163f70615f33825c46999d37077b1c3d93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249921"
---
# <span data-ttu-id="e4958-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e4958-103">Get-PSProvider</span></span>

## <span data-ttu-id="e4958-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e4958-104">SYNOPSIS</span></span>
<span data-ttu-id="e4958-105">Hiermee haalt u informatie op over de opgegeven Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="e4958-105">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="e4958-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e4958-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e4958-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e4958-107">DESCRIPTION</span></span>

<span data-ttu-id="e4958-108">De `Get-PSProvider` cmdlet haalt de Power shell-providers in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="e4958-108">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="e4958-109">U kunt een bepaald station of alle stations in de sessie ophalen.</span><span class="sxs-lookup"><span data-stu-id="e4958-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="e4958-110">Power shell-providers stellen u in staat om toegang te krijgen tot diverse gegevens archieven, alsof ze bestandssysteem stations zijn.</span><span class="sxs-lookup"><span data-stu-id="e4958-110">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="e4958-111">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="e4958-111">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e4958-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e4958-112">EXAMPLES</span></span>

### <span data-ttu-id="e4958-113">Voor beeld 1: een lijst met alle beschik bare providers weer geven</span><span class="sxs-lookup"><span data-stu-id="e4958-113">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="e4958-114">Met deze opdracht wordt een lijst weer gegeven met alle beschik bare Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="e4958-114">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="e4958-115">Voor beeld 2: een lijst weer geven van alle Power shell-providers die met de opgegeven letters beginnen</span><span class="sxs-lookup"><span data-stu-id="e4958-115">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="e4958-116">Met deze opdracht wordt een lijst weer gegeven met alle Power shell-providers met namen die beginnen met de letter f of r.</span><span class="sxs-lookup"><span data-stu-id="e4958-116">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="e4958-117">Voor beeld 3: modules of modules zoeken die providers aan uw sessie hebben toegevoegd</span><span class="sxs-lookup"><span data-stu-id="e4958-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
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
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="e4958-118">Met deze opdrachten worden de Power shell-modules of-modules gevonden die providers aan uw sessie hebben toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e4958-118">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="e4958-119">Alle Power shell-elementen, inclusief providers, zijn afkomstig uit een module of een module.</span><span class="sxs-lookup"><span data-stu-id="e4958-119">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="e4958-120">Deze opdrachten gebruiken de eigenschappen PSSnapin en module van het **ProviderInfo** -object dat `Get-PSProvider` retourneert.</span><span class="sxs-lookup"><span data-stu-id="e4958-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="e4958-121">De waarden van deze eigenschappen bevatten de naam van de module of module die de provider toevoegt.</span><span class="sxs-lookup"><span data-stu-id="e4958-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="e4958-122">Met de eerste opdracht worden alle providers in de sessie opgehaald en opgemaakt in een tabel met de waarden van hun naam, module en PSSnapin eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e4958-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="e4958-123">De tweede opdracht gebruikt de `Where-Object` cmdlet om de providers op te halen die afkomstig zijn uit de module **micro soft. Power shell. Security** .</span><span class="sxs-lookup"><span data-stu-id="e4958-123">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="e4958-124">Voor beeld 4: het pad naar de start-eigenschap van de bestandssysteem provider oplossen</span><span class="sxs-lookup"><span data-stu-id="e4958-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="e4958-125">In dit voor beeld ziet u dat het tilde-symbool (~) de waarde vertegenwoordigt van de eigenschap **Home** van de File System-Provider.</span><span class="sxs-lookup"><span data-stu-id="e4958-125">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="e4958-126">De waarde van de eigenschap **Home** is optioneel, maar voor de **bestandssysteem** provider wordt deze gedefinieerd als `$env:homedrive\$env:homepath` of `$home` .</span><span class="sxs-lookup"><span data-stu-id="e4958-126">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="e4958-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4958-127">PARAMETERS</span></span>

### <span data-ttu-id="e4958-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e4958-128">-PSProvider</span></span>

<span data-ttu-id="e4958-129">Hiermee geeft u de naam of namen van de Power shell-providers waarover deze cmdlet informatie ophaalt.</span><span class="sxs-lookup"><span data-stu-id="e4958-129">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

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

### <span data-ttu-id="e4958-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4958-130">CommonParameters</span></span>

<span data-ttu-id="e4958-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4958-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4958-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e4958-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e4958-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="e4958-133">INPUTS</span></span>

### <span data-ttu-id="e4958-134">Teken reeks []</span><span class="sxs-lookup"><span data-stu-id="e4958-134">String[]</span></span>

<span data-ttu-id="e4958-135">U kunt een of meer provider naam reeksen door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4958-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="e4958-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e4958-136">OUTPUTS</span></span>

### <span data-ttu-id="e4958-137">System. Management. Automation. ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="e4958-137">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="e4958-138">Deze cmdlet retourneert objecten die de Power shell-providers in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="e4958-138">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="e4958-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e4958-139">NOTES</span></span>

## <span data-ttu-id="e4958-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e4958-140">RELATED LINKS</span></span>

