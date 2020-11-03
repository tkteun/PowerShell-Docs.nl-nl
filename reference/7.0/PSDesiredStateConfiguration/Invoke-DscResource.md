---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "93251815"
---
# <span data-ttu-id="10b74-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="10b74-103">Invoke-DscResource</span></span>

## <span data-ttu-id="10b74-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="10b74-104">SYNOPSIS</span></span>
<span data-ttu-id="10b74-105">Hiermee wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.</span><span class="sxs-lookup"><span data-stu-id="10b74-105">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="10b74-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="10b74-106">SYNTAX</span></span>

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="10b74-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="10b74-107">DESCRIPTION</span></span>

<span data-ttu-id="10b74-108">`Invoke-DscResource`Met de cmdlet wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.</span><span class="sxs-lookup"><span data-stu-id="10b74-108">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="10b74-109">Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="10b74-109">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="10b74-110">Met deze cmdlet kunnen Configuration Management-producten Windows of Linux beheren met behulp van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="10b74-110">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="10b74-111">Met deze cmdlet schakelt u ook fout opsporing van resources in wanneer de DSC-engine wordt uitgevoerd met fout opsporing ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="10b74-111">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="10b74-112">`Invoke-DscResource` is een experimentele functie in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="10b74-112">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="10b74-113">Als u de cmdlet wilt gebruiken, moet u deze inschakelen met de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="10b74-113">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="10b74-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="10b74-114">EXAMPLES</span></span>

### <span data-ttu-id="10b74-115">Voor beeld 1: de set-methode van een bron aanroepen door de verplichte eigenschappen op te geven</span><span class="sxs-lookup"><span data-stu-id="10b74-115">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="10b74-116">In dit voor beeld wordt de **set** -methode van een resource met de naam **WindowsProcess** aangeroepen en worden de eigenschappen van het verplichte **pad** en de **argumenten** geboden om het opgegeven Windows-proces te starten.</span><span class="sxs-lookup"><span data-stu-id="10b74-116">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="10b74-117">Voor beeld 2: de test methode van een resource aanroepen voor een opgegeven module</span><span class="sxs-lookup"><span data-stu-id="10b74-117">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="10b74-118">In dit voor beeld wordt de **test** methode aangeroepen van een resource met de naam **WindowsProcess** , die zich in de module met de naam **PSDesiredStateConfiguration** bevindt.</span><span class="sxs-lookup"><span data-stu-id="10b74-118">This example invokes the **Test** method of a resource named **WindowsProcess** , which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="10b74-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10b74-119">PARAMETERS</span></span>

### <span data-ttu-id="10b74-120">-Methode</span><span class="sxs-lookup"><span data-stu-id="10b74-120">-Method</span></span>

<span data-ttu-id="10b74-121">Hiermee geeft u de methode van de resource op die door deze cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="10b74-121">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="10b74-122">De acceptabele waarden voor deze para meter zijn: **Get** , **set** en **test**.</span><span class="sxs-lookup"><span data-stu-id="10b74-122">The acceptable values for this parameter are: **Get** , **Set** , and **Test**.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="10b74-123">-Module naam</span><span class="sxs-lookup"><span data-stu-id="10b74-123">-ModuleName</span></span>

<span data-ttu-id="10b74-124">Hiermee geeft u de naam van de module op waaruit deze cmdlet de opgegeven resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="10b74-124">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="10b74-125">-Name</span><span class="sxs-lookup"><span data-stu-id="10b74-125">-Name</span></span>

<span data-ttu-id="10b74-126">Hiermee geeft u de naam op van de DSC-resource die moet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="10b74-126">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="10b74-127">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="10b74-127">-Property</span></span>

<span data-ttu-id="10b74-128">Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="10b74-128">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="10b74-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10b74-129">CommonParameters</span></span>

<span data-ttu-id="10b74-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10b74-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10b74-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10b74-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10b74-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="10b74-132">INPUTS</span></span>

## <span data-ttu-id="10b74-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="10b74-133">OUTPUTS</span></span>

### <span data-ttu-id="10b74-134">Micro soft. Management. Infrastructure. CimInstance, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="10b74-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="10b74-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="10b74-135">NOTES</span></span>

- <span data-ttu-id="10b74-136">Voorheen werden Windows Power shell 5,1-bronnen uitgevoerd onder systeem context, tenzij ze zijn opgegeven met de gebruikers context met de Key **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="10b74-136">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="10b74-137">In Power shell 7,0 worden resources uitgevoerd in de context van de gebruiker en wordt **PsDscRunAsCredential** niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="10b74-137">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="10b74-138">Bij eerdere configuraties met deze sleutel wordt een uitzonde ring gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="10b74-138">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="10b74-139">Vanaf Power shell 7 `Invoke-DscResource` biedt geen ondersteuning meer voor het aanroepen van WMI DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="10b74-139">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="10b74-140">Dit omvat de **Bestands** -en **logboek** bronnen in **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="10b74-140">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="10b74-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="10b74-141">RELATED LINKS</span></span>

[<span data-ttu-id="10b74-142">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="10b74-142">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="10b74-143">Get-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="10b74-143">Get-DscResource</span></span>](Get-DscResource.md)
