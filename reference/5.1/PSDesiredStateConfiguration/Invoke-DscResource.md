---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250769"
---
# <span data-ttu-id="e7f12-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="e7f12-103">Invoke-DscResource</span></span>

## <span data-ttu-id="e7f12-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e7f12-104">SYNOPSIS</span></span>
<span data-ttu-id="e7f12-105">Hiermee wordt een methode van een opgegeven DSC-resource uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e7f12-105">Runs a method of a specified DSC resource.</span></span>

## <span data-ttu-id="e7f12-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e7f12-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## <span data-ttu-id="e7f12-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e7f12-107">DESCRIPTION</span></span>
<span data-ttu-id="e7f12-108">Met de cmdlet **invoke-dscresource bieden** wordt een methode uitgevoerd van een opgegeven Windows Power shell-resource voor desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="e7f12-108">The **Invoke-DscResource** cmdlet runs a method of a specified Windows PowerShell Desired State Configuration (DSC) resource.</span></span>
<span data-ttu-id="e7f12-109">Voordat u deze cmdlet uitvoert, stelt u de vernieuwings modus van de lokale Configuration Manager (LCM) in op uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e7f12-109">Before you run this cmdlet, set the refresh mode of the Local Configuration Manager (LCM) to Disabled.</span></span>

<span data-ttu-id="e7f12-110">Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e7f12-110">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span>
<span data-ttu-id="e7f12-111">Met deze cmdlet kunnen Configuration Management-producten Windows beheren met behulp van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e7f12-111">Using this cmdlet, configuration management products can manage windows by using DSC resources.</span></span>
<span data-ttu-id="e7f12-112">Met deze cmdlet wordt ook fout opsporing van resources mogelijk wanneer de DSC-Engine of de LCM wordt uitgevoerd met de fout opsporing is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e7f12-112">This cmdlet also enables debugging of resources when the DSC engine or LCM is running with debugging enabled.</span></span>

## <span data-ttu-id="e7f12-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e7f12-113">EXAMPLES</span></span>

### <span data-ttu-id="e7f12-114">Voor beeld 1: de set-methode van een bron aanroepen door de verplichte eigenschappen op te geven</span><span class="sxs-lookup"><span data-stu-id="e7f12-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="e7f12-115">Met deze opdracht wordt de **set** -methode aangeroepen van een resource met de naam log en wordt er een **bericht** eigenschap voor opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e7f12-115">This command invokes the **Set** method of a resource named Log and specifies a **Message** property for it.</span></span>

### <span data-ttu-id="e7f12-116">Voor beeld 2: de test methode van een resource aanroepen voor een opgegeven module</span><span class="sxs-lookup"><span data-stu-id="e7f12-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="e7f12-117">Met deze opdracht wordt de **test** methode aangeroepen van een resource met de naam WindowsProcess, die zich in de module met de naam PSDesiredStateConfiguration bevindt.</span><span class="sxs-lookup"><span data-stu-id="e7f12-117">This command invokes the **Test** method of a resource named WindowsProcess, which is in the module named PSDesiredStateConfiguration.</span></span>

## <span data-ttu-id="e7f12-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e7f12-118">PARAMETERS</span></span>

### <span data-ttu-id="e7f12-119">-Methode</span><span class="sxs-lookup"><span data-stu-id="e7f12-119">-Method</span></span>
<span data-ttu-id="e7f12-120">Hiermee geeft u de methode van de resource op die door deze cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e7f12-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="e7f12-121">De acceptabele waarden voor deze para meter zijn: Get, set en test.</span><span class="sxs-lookup"><span data-stu-id="e7f12-121">The acceptable values for this parameter are: Get, Set, and Test.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7f12-122">-Module naam</span><span class="sxs-lookup"><span data-stu-id="e7f12-122">-ModuleName</span></span>
<span data-ttu-id="e7f12-123">Hiermee geeft u de naam van de module op waaruit deze cmdlet de opgegeven resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="e7f12-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7f12-124">-Name</span><span class="sxs-lookup"><span data-stu-id="e7f12-124">-Name</span></span>
<span data-ttu-id="e7f12-125">Hiermee geeft u de naam op van de DSC-resource die moet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="e7f12-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7f12-126">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e7f12-126">-Property</span></span>
<span data-ttu-id="e7f12-127">Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="e7f12-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e7f12-128">Gebruik de cmdlet **Get-dscresource bieden** om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="e7f12-128">Use the **Get-DscResource** cmdlet to discover resource properties and their types.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7f12-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7f12-129">CommonParameters</span></span>
<span data-ttu-id="e7f12-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7f12-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7f12-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e7f12-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7f12-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="e7f12-132">INPUTS</span></span>

## <span data-ttu-id="e7f12-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e7f12-133">OUTPUTS</span></span>

### <span data-ttu-id="e7f12-134">Micro soft. Management. Infrastructure. CimInstance, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="e7f12-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="e7f12-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e7f12-135">NOTES</span></span>

## <span data-ttu-id="e7f12-136">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e7f12-136">RELATED LINKS</span></span>

[<span data-ttu-id="e7f12-137">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="e7f12-137">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="e7f12-138">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7f12-138">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="e7f12-139">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="e7f12-139">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="e7f12-140">Get-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="e7f12-140">Get-DscResource</span></span>](Get-DscResource.md)

[<span data-ttu-id="e7f12-141">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7f12-141">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="e7f12-142">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e7f12-142">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

[<span data-ttu-id="e7f12-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7f12-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="e7f12-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7f12-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
