---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705681"
---
# <span data-ttu-id="e0990-102">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="e0990-102">Invoke-DscResource</span></span>

## <span data-ttu-id="e0990-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e0990-103">SYNOPSIS</span></span>
<span data-ttu-id="e0990-104">Hiermee wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e0990-104">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="e0990-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e0990-105">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="e0990-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e0990-106">DESCRIPTION</span></span>

<span data-ttu-id="e0990-107">`Invoke-DscResource`Met de cmdlet wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e0990-107">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="e0990-108">Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e0990-108">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="e0990-109">Met deze cmdlet kunnen Configuration Management-producten Windows of Linux beheren met behulp van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e0990-109">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="e0990-110">Met deze cmdlet schakelt u ook fout opsporing van resources in wanneer de DSC-engine wordt uitgevoerd met fout opsporing ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e0990-110">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="e0990-111">`Invoke-DscResource` is een experimentele functie in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="e0990-111">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="e0990-112">Als u de cmdlet wilt gebruiken, moet u deze inschakelen met de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="e0990-112">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="e0990-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e0990-113">EXAMPLES</span></span>

### <span data-ttu-id="e0990-114">Voor beeld 1: de set-methode van een bron aanroepen door de verplichte eigenschappen op te geven</span><span class="sxs-lookup"><span data-stu-id="e0990-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="e0990-115">In dit voor beeld wordt de **set** -methode van een resource met de naam **WindowsProcess** aangeroepen en worden de eigenschappen van het verplichte **pad** en de **argumenten** geboden om het opgegeven Windows-proces te starten.</span><span class="sxs-lookup"><span data-stu-id="e0990-115">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="e0990-116">Voor beeld 2: de test methode van een resource aanroepen voor een opgegeven module</span><span class="sxs-lookup"><span data-stu-id="e0990-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="e0990-117">In dit voor beeld wordt de **test** methode aangeroepen van een resource met de naam **WindowsProcess**, die zich in de module met de naam **PSDesiredStateConfiguration** bevindt.</span><span class="sxs-lookup"><span data-stu-id="e0990-117">This example invokes the **Test** method of a resource named **WindowsProcess**, which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="e0990-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0990-118">PARAMETERS</span></span>

### <span data-ttu-id="e0990-119">-Methode</span><span class="sxs-lookup"><span data-stu-id="e0990-119">-Method</span></span>

<span data-ttu-id="e0990-120">Hiermee geeft u de methode van de resource op die door deze cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e0990-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="e0990-121">De acceptabele waarden voor deze para meter zijn: **Get**, **set** en **test**.</span><span class="sxs-lookup"><span data-stu-id="e0990-121">The acceptable values for this parameter are: **Get**, **Set**, and **Test**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0990-122">-Module naam</span><span class="sxs-lookup"><span data-stu-id="e0990-122">-ModuleName</span></span>

<span data-ttu-id="e0990-123">Hiermee geeft u de naam van de module op waaruit deze cmdlet de opgegeven resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="e0990-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0990-124">-Name</span><span class="sxs-lookup"><span data-stu-id="e0990-124">-Name</span></span>

<span data-ttu-id="e0990-125">Hiermee geeft u de naam op van de DSC-resource die moet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="e0990-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0990-126">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e0990-126">-Property</span></span>

<span data-ttu-id="e0990-127">Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="e0990-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0990-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0990-128">CommonParameters</span></span>

<span data-ttu-id="e0990-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0990-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0990-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e0990-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0990-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="e0990-131">INPUTS</span></span>

### <span data-ttu-id="e0990-132">System. String</span><span class="sxs-lookup"><span data-stu-id="e0990-132">System.String</span></span>

### <span data-ttu-id="e0990-133">Micro soft. Power shell. commands. ModuleSpecification</span><span class="sxs-lookup"><span data-stu-id="e0990-133">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="e0990-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e0990-134">OUTPUTS</span></span>

### <span data-ttu-id="e0990-135">System. object</span><span class="sxs-lookup"><span data-stu-id="e0990-135">System.Object</span></span>

## <span data-ttu-id="e0990-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e0990-136">NOTES</span></span>

- <span data-ttu-id="e0990-137">Voorheen werden Windows Power shell 5,1-bronnen uitgevoerd onder systeem context, tenzij ze zijn opgegeven met de gebruikers context met de Key **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="e0990-137">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="e0990-138">In Power shell 7,0 worden resources uitgevoerd in de context van de gebruiker en wordt **PsDscRunAsCredential** niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e0990-138">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="e0990-139">Bij eerdere configuraties met deze sleutel wordt een uitzonde ring gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e0990-139">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="e0990-140">Vanaf Power shell 7 `Invoke-DscResource` biedt geen ondersteuning meer voor het aanroepen van WMI DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e0990-140">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="e0990-141">Dit omvat de **Bestands** -en **logboek** bronnen in **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="e0990-141">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="e0990-142">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e0990-142">RELATED LINKS</span></span>

[<span data-ttu-id="e0990-143">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="e0990-143">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="e0990-144">Get-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="e0990-144">Get-DscResource</span></span>](Get-DscResource.md)
