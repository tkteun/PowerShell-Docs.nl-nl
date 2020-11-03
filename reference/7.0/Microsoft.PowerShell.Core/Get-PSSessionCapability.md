---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: cc660b80a29d2e27a0b3928c1073168b2575af8f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249778"
---
# <span data-ttu-id="83e85-103">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="83e85-103">Get-PSSessionCapability</span></span>

## <span data-ttu-id="83e85-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="83e85-104">SYNOPSIS</span></span>
<span data-ttu-id="83e85-105">Hiermee worden de mogelijkheden van een specifieke gebruiker voor een beperkte sessie configuratie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="83e85-105">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="83e85-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="83e85-106">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="83e85-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="83e85-107">DESCRIPTION</span></span>

<span data-ttu-id="83e85-108">Met de cmdlet **Get-PSSessionCapability** worden de mogelijkheden van een specifieke gebruiker voor een beperkte sessie configuratie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="83e85-108">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="83e85-109">Gebruik deze cmdlet om aangepaste sessie configuraties voor gebruikers te controleren.</span><span class="sxs-lookup"><span data-stu-id="83e85-109">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="83e85-110">Vanuit Windows Power shell 5,0 kunt u de eigenschap **RoleDefinitions** in een sessie configuratie bestand (. pssc) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="83e85-110">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="83e85-111">Met deze eigenschap kunt u gebruikers verschillende mogelijkheden geven op een enkel beperkt eind punt op basis van groepslid maatschap.</span><span class="sxs-lookup"><span data-stu-id="83e85-111">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="83e85-112">De cmdlet **Get-PSSessionCapability** vermindert de complexiteit bij het controleren van deze eind punten door u de exacte mogelijkheden te bepalen die aan een gebruiker worden verleend.</span><span class="sxs-lookup"><span data-stu-id="83e85-112">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="83e85-113">De cmdlet **Get-PSSessionCapability** retourneert standaard een lijst met opdrachten die de opgegeven gebruiker kan uitvoeren in het opgegeven eind punt.</span><span class="sxs-lookup"><span data-stu-id="83e85-113">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="83e85-114">Dit is gelijk aan de gebruiker die **Get-opdracht** uitvoert in het opgegeven eind punt.</span><span class="sxs-lookup"><span data-stu-id="83e85-114">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="83e85-115">Wanneer u uitvoert met de *volledige* para meter, retourneert deze cmdlet een **InitialSessionState** -object.</span><span class="sxs-lookup"><span data-stu-id="83e85-115">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="83e85-116">Dit object bevat details over de Power shell-runs Pace waarmee de opgegeven gebruiker communiceert voor het opgegeven eind punt.</span><span class="sxs-lookup"><span data-stu-id="83e85-116">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="83e85-117">Het bevat informatie zoals de taal modus, het uitvoerings beleid en omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="83e85-117">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="83e85-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="83e85-118">EXAMPLES</span></span>

### <span data-ttu-id="83e85-119">Voor beeld 1: opdrachten ophalen die beschikbaar zijn voor een gebruiker</span><span class="sxs-lookup"><span data-stu-id="83e85-119">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="83e85-120">In dit voor beeld worden de opdrachten die beschikbaar zijn voor de gebruiker CONTOSO\User wanneer verbinding wordt gemaakt met het Endpoint1 beperkte eind punt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="83e85-120">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="83e85-121">Voor beeld 2: Details over een runs Pace voor een gebruiker ophalen</span><span class="sxs-lookup"><span data-stu-id="83e85-121">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="83e85-122">In dit voor beeld worden details geretourneerd over de runs Pace waarmee de gebruiker CONTOSO\User zou communiceren wanneer er verbinding wordt gemaakt met het Endpoint1-beperkt eind punt.</span><span class="sxs-lookup"><span data-stu-id="83e85-122">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="83e85-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="83e85-123">PARAMETERS</span></span>

### <span data-ttu-id="83e85-124">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="83e85-124">-ConfigurationName</span></span>

<span data-ttu-id="83e85-125">Hiermee geeft u de beperkte sessie configuratie (eind punt) op die u wilt inspecteren.</span><span class="sxs-lookup"><span data-stu-id="83e85-125">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83e85-126">-Volledig</span><span class="sxs-lookup"><span data-stu-id="83e85-126">-Full</span></span>

<span data-ttu-id="83e85-127">Geeft aan dat deze cmdlet de volledige initiële sessie status retourneert voor de opgegeven gebruiker op het opgegeven beperkte eind punt.</span><span class="sxs-lookup"><span data-stu-id="83e85-127">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83e85-128">-Gebruikers naam</span><span class="sxs-lookup"><span data-stu-id="83e85-128">-Username</span></span>

<span data-ttu-id="83e85-129">Hiermee geeft u de gebruiker waarvan u de mogelijkheden wilt inspecteren.</span><span class="sxs-lookup"><span data-stu-id="83e85-129">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83e85-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83e85-130">CommonParameters</span></span>

<span data-ttu-id="83e85-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83e85-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83e85-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83e85-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83e85-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="83e85-133">INPUTS</span></span>

## <span data-ttu-id="83e85-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="83e85-134">OUTPUTS</span></span>

### <span data-ttu-id="83e85-135">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="83e85-135">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="83e85-136">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="83e85-136">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="83e85-137">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="83e85-137">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="83e85-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="83e85-138">NOTES</span></span>

## <span data-ttu-id="83e85-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="83e85-139">RELATED LINKS</span></span>

[<span data-ttu-id="83e85-140">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="83e85-140">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)
