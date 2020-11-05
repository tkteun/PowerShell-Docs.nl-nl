---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 5b95fe3bc643c9e12a3d216523c086d9b0cdf901
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249881"
---
# <span data-ttu-id="65a47-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="65a47-102">Get-LogProperties</span></span>

## <span data-ttu-id="65a47-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="65a47-103">SYNOPSIS</span></span>
<span data-ttu-id="65a47-104">Hiermee worden de eigenschappen van een Windows-gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="65a47-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="65a47-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="65a47-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="65a47-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="65a47-106">DESCRIPTION</span></span>

<span data-ttu-id="65a47-107">Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="65a47-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="65a47-108">Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="65a47-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="65a47-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="65a47-109">EXAMPLES</span></span>

### <span data-ttu-id="65a47-110">Voor beeld 1: de configuratie-instellingen van het Windows Power shell-gebeurtenis logboek ophalen</span><span class="sxs-lookup"><span data-stu-id="65a47-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="65a47-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="65a47-111">PARAMETERS</span></span>

### <span data-ttu-id="65a47-112">-Name</span><span class="sxs-lookup"><span data-stu-id="65a47-112">-Name</span></span>

<span data-ttu-id="65a47-113">De naam van de provider van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="65a47-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="65a47-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65a47-114">CommonParameters</span></span>

<span data-ttu-id="65a47-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65a47-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65a47-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="65a47-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65a47-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="65a47-117">INPUTS</span></span>

### <span data-ttu-id="65a47-118">System. String</span><span class="sxs-lookup"><span data-stu-id="65a47-118">System.String</span></span>

## <span data-ttu-id="65a47-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="65a47-119">OUTPUTS</span></span>

### <span data-ttu-id="65a47-120">Micro soft. Power shell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="65a47-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="65a47-121">De **PSDiagnostics** -module voegt de klasse **LogDetails** toe aan de `Microsoft.PowerShell.Diagnostics` naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="65a47-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="65a47-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="65a47-122">NOTES</span></span>

## <span data-ttu-id="65a47-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="65a47-123">RELATED LINKS</span></span>

[<span data-ttu-id="65a47-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="65a47-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="65a47-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="65a47-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="65a47-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="65a47-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
