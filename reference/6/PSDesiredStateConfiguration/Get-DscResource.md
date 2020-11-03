---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: 7eba6a561ff0220d0624c49b109f1558822f1064
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251681"
---
# <span data-ttu-id="9ddde-103">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="9ddde-103">Get-DscResource</span></span>

## <span data-ttu-id="9ddde-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9ddde-104">SYNOPSIS</span></span>
<span data-ttu-id="9ddde-105">Hiermee worden de resources voor desired state Configuration (DSC) aanwezig op de computer.</span><span class="sxs-lookup"><span data-stu-id="9ddde-105">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="9ddde-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9ddde-106">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="9ddde-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9ddde-107">DESCRIPTION</span></span>

<span data-ttu-id="9ddde-108">`Get-DscResource`Met de cmdlet worden de Power shell DSC-resources opgehaald die aanwezig zijn op de computer.</span><span class="sxs-lookup"><span data-stu-id="9ddde-108">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="9ddde-109">Met deze cmdlet worden alleen de resources gedetecteerd die in de PSModulePath zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9ddde-109">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="9ddde-110">Hierin worden de details weer gegeven van ingebouwde en aangepaste providers die door de gebruiker zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9ddde-110">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="9ddde-111">Met deze cmdlet wordt ook informatie over samengestelde resources weer gegeven. Dit zijn andere configuraties die zijn verpakt als module of tijdens runtime worden gemaakt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="9ddde-111">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="9ddde-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9ddde-112">EXAMPLES</span></span>

### <span data-ttu-id="9ddde-113">Voor beeld 1: alle resources op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="9ddde-113">Example 1: Get all resources on the local computer</span></span>

```powershell
 Get-DscResource
```

<span data-ttu-id="9ddde-114">Met deze opdracht worden alle resources op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9ddde-114">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="9ddde-115">Voor beeld 2: een resource ophalen door de naam op te geven</span><span class="sxs-lookup"><span data-stu-id="9ddde-115">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="9ddde-116">Met deze opdracht wordt de resource WindowsFeature opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9ddde-116">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="9ddde-117">Voor beeld 3: alle resources uit een module ophalen</span><span class="sxs-lookup"><span data-stu-id="9ddde-117">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="9ddde-118">Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module.</span><span class="sxs-lookup"><span data-stu-id="9ddde-118">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="9ddde-119">Voor beeld 4: een resource ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="9ddde-119">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="9ddde-120">Met deze opdracht worden alle resources opgehaald die overeenkomen met het Joker teken patroon dat is opgegeven door de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="9ddde-120">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="9ddde-121">Voor beeld 5: een resource syntaxis ophalen</span><span class="sxs-lookup"><span data-stu-id="9ddde-121">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="9ddde-122">Met deze opdracht wordt de resource WindowsFeature opgehaald en wordt de syntaxis voor de resource weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ddde-122">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="9ddde-123">Voor beeld 6: alle eigenschappen voor een resource ophalen</span><span class="sxs-lookup"><span data-stu-id="9ddde-123">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="9ddde-124">Met deze opdracht wordt de gebruikers bron opgehaald, waarna de pijplijn operator wordt gebruikt om alle eigenschappen voor de gebruikers bron te retour neren.</span><span class="sxs-lookup"><span data-stu-id="9ddde-124">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="9ddde-125">Voor beeld 7: alle resources van een opgegeven module ophalen met een opgegeven versie</span><span class="sxs-lookup"><span data-stu-id="9ddde-125">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="9ddde-126">Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module met versie 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="9ddde-126">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="9ddde-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ddde-127">PARAMETERS</span></span>

### <span data-ttu-id="9ddde-128">-Module</span><span class="sxs-lookup"><span data-stu-id="9ddde-128">-Module</span></span>

<span data-ttu-id="9ddde-129">Hiermee geeft u de naam of de volledig gekwalificeerde naam van de module waarvoor u de DSC-resource wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="9ddde-129">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9ddde-130">-Name</span><span class="sxs-lookup"><span data-stu-id="9ddde-130">-Name</span></span>

<span data-ttu-id="9ddde-131">Hiermee geeft u een matrix met namen van de DSC-resource op die u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="9ddde-131">Specifies an array of names of the DSC resource to view.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9ddde-132">-Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9ddde-132">-Syntax</span></span>

<span data-ttu-id="9ddde-133">Geeft aan dat de cmdlet de syntaxis weergave van de opgegeven DSC-resources retourneert.</span><span class="sxs-lookup"><span data-stu-id="9ddde-133">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="9ddde-134">De geretourneerde syntaxis laat zien hoe u de resources in een Power shell-script gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9ddde-134">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

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

### <span data-ttu-id="9ddde-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ddde-135">CommonParameters</span></span>

<span data-ttu-id="9ddde-136">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ddde-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ddde-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9ddde-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ddde-138">INVOER</span><span class="sxs-lookup"><span data-stu-id="9ddde-138">INPUTS</span></span>

### <span data-ttu-id="9ddde-139">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9ddde-139">System.String[]</span></span>

### <span data-ttu-id="9ddde-140">System. object</span><span class="sxs-lookup"><span data-stu-id="9ddde-140">System.Object</span></span>

## <span data-ttu-id="9ddde-141">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9ddde-141">OUTPUTS</span></span>

### <span data-ttu-id="9ddde-142">Micro soft. Power shell. DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="9ddde-142">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="9ddde-143">teken reeks []</span><span class="sxs-lookup"><span data-stu-id="9ddde-143">string[]</span></span>

## <span data-ttu-id="9ddde-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9ddde-144">NOTES</span></span>

- <span data-ttu-id="9ddde-145">`Get-DscResource` vindt geen op klassen gebaseerde DSC-resources in Power shell-versies onder 7,0.</span><span class="sxs-lookup"><span data-stu-id="9ddde-145">`Get-DscResource` does not find Class based DSC resources in PowerShell versions below 7.0.</span></span>

## <span data-ttu-id="9ddde-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9ddde-146">RELATED LINKS</span></span>

[<span data-ttu-id="9ddde-147">Overzicht van desired state Configuration van Power shell</span><span class="sxs-lookup"><span data-stu-id="9ddde-147">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="9ddde-148">Invoke-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="9ddde-148">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
