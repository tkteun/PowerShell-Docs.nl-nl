---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705682"
---
# <span data-ttu-id="a4389-102">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="a4389-102">Get-DscResource</span></span>

## <span data-ttu-id="a4389-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a4389-103">SYNOPSIS</span></span>
<span data-ttu-id="a4389-104">Hiermee worden de resources voor desired state Configuration (DSC) aanwezig op de computer.</span><span class="sxs-lookup"><span data-stu-id="a4389-104">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="a4389-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a4389-105">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="a4389-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a4389-106">DESCRIPTION</span></span>

<span data-ttu-id="a4389-107">`Get-DscResource`Met de cmdlet worden de Power shell DSC-resources opgehaald die aanwezig zijn op de computer.</span><span class="sxs-lookup"><span data-stu-id="a4389-107">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="a4389-108">Met deze cmdlet worden alleen de resources gedetecteerd die in de PSModulePath zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a4389-108">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="a4389-109">Hierin worden de details weer gegeven van ingebouwde en aangepaste providers die door de gebruiker zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a4389-109">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="a4389-110">Met deze cmdlet wordt ook informatie over samengestelde resources weer gegeven. Dit zijn andere configuraties die zijn verpakt als module of tijdens runtime worden gemaakt in de sessie.</span><span class="sxs-lookup"><span data-stu-id="a4389-110">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="a4389-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a4389-111">EXAMPLES</span></span>

### <span data-ttu-id="a4389-112">Voor beeld 1: alle resources op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="a4389-112">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="a4389-113">Met deze opdracht worden alle resources op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a4389-113">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="a4389-114">Voor beeld 2: een resource ophalen door de naam op te geven</span><span class="sxs-lookup"><span data-stu-id="a4389-114">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="a4389-115">Met deze opdracht wordt de resource WindowsFeature opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a4389-115">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="a4389-116">Voor beeld 3: alle resources uit een module ophalen</span><span class="sxs-lookup"><span data-stu-id="a4389-116">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="a4389-117">Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module.</span><span class="sxs-lookup"><span data-stu-id="a4389-117">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="a4389-118">Voor beeld 4: een resource ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="a4389-118">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="a4389-119">Met deze opdracht worden alle resources opgehaald die overeenkomen met het Joker teken patroon dat is opgegeven door de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="a4389-119">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="a4389-120">Voor beeld 5: een resource syntaxis ophalen</span><span class="sxs-lookup"><span data-stu-id="a4389-120">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="a4389-121">Met deze opdracht wordt de resource WindowsFeature opgehaald en wordt de syntaxis voor de resource weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a4389-121">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="a4389-122">Voor beeld 6: alle eigenschappen voor een resource ophalen</span><span class="sxs-lookup"><span data-stu-id="a4389-122">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="a4389-123">Met deze opdracht wordt de gebruikers bron opgehaald, waarna de pijplijn operator wordt gebruikt om alle eigenschappen voor de gebruikers bron te retour neren.</span><span class="sxs-lookup"><span data-stu-id="a4389-123">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="a4389-124">Voor beeld 7: alle resources van een opgegeven module ophalen met een opgegeven versie</span><span class="sxs-lookup"><span data-stu-id="a4389-124">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="a4389-125">Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module met versie 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="a4389-125">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="a4389-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a4389-126">PARAMETERS</span></span>

### <span data-ttu-id="a4389-127">-Module</span><span class="sxs-lookup"><span data-stu-id="a4389-127">-Module</span></span>

<span data-ttu-id="a4389-128">Hiermee geeft u de naam of de volledig gekwalificeerde naam van de module waarvoor u de DSC-resource wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="a4389-128">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

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

### <span data-ttu-id="a4389-129">-Name</span><span class="sxs-lookup"><span data-stu-id="a4389-129">-Name</span></span>

<span data-ttu-id="a4389-130">Hiermee geeft u een matrix met namen van de DSC-resource op die u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="a4389-130">Specifies an array of names of the DSC resource to view.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a4389-131">-Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a4389-131">-Syntax</span></span>

<span data-ttu-id="a4389-132">Geeft aan dat de cmdlet de syntaxis weergave van de opgegeven DSC-resources retourneert.</span><span class="sxs-lookup"><span data-stu-id="a4389-132">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="a4389-133">De geretourneerde syntaxis laat zien hoe u de resources in een Power shell-script gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a4389-133">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

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

### <span data-ttu-id="a4389-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a4389-134">CommonParameters</span></span>

<span data-ttu-id="a4389-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a4389-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a4389-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4389-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a4389-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="a4389-137">INPUTS</span></span>

### <span data-ttu-id="a4389-138">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a4389-138">System.String[]</span></span>

### <span data-ttu-id="a4389-139">System. object</span><span class="sxs-lookup"><span data-stu-id="a4389-139">System.Object</span></span>

## <span data-ttu-id="a4389-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a4389-140">OUTPUTS</span></span>

### <span data-ttu-id="a4389-141">Micro soft. Power shell. DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="a4389-141">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="a4389-142">teken reeks []</span><span class="sxs-lookup"><span data-stu-id="a4389-142">string[]</span></span>

## <span data-ttu-id="a4389-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a4389-143">NOTES</span></span>

## <span data-ttu-id="a4389-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a4389-144">RELATED LINKS</span></span>

[<span data-ttu-id="a4389-145">Overzicht van desired state Configuration van Power shell</span><span class="sxs-lookup"><span data-stu-id="a4389-145">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="a4389-146">Invoke-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="a4389-146">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

