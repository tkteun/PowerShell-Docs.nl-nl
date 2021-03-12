---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 447d8a07c6e5d6ba4f47685819907937c75711db
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193993"
---
# <span data-ttu-id="9ebf2-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9ebf2-102">Get-LogProperties</span></span>

## <span data-ttu-id="9ebf2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9ebf2-103">SYNOPSIS</span></span>
<span data-ttu-id="9ebf2-104">Hiermee worden de eigenschappen van een Windows-gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="9ebf2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9ebf2-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <string> [<CommonParameters>]
```

## <span data-ttu-id="9ebf2-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9ebf2-106">DESCRIPTION</span></span>

<span data-ttu-id="9ebf2-107">Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="9ebf2-108">Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="9ebf2-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9ebf2-109">EXAMPLES</span></span>

### <span data-ttu-id="9ebf2-110">Voor beeld 1: de configuratie-instellingen van het Windows Power shell-gebeurtenis logboek ophalen</span><span class="sxs-lookup"><span data-stu-id="9ebf2-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="9ebf2-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ebf2-111">PARAMETERS</span></span>

### <span data-ttu-id="9ebf2-112">-Name</span><span class="sxs-lookup"><span data-stu-id="9ebf2-112">-Name</span></span>

<span data-ttu-id="9ebf2-113">De naam van de provider van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-113">The name of the event provider.</span></span>

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

### <span data-ttu-id="9ebf2-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ebf2-114">CommonParameters</span></span>

<span data-ttu-id="9ebf2-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ebf2-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ebf2-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="9ebf2-117">INPUTS</span></span>

### <span data-ttu-id="9ebf2-118">System. object</span><span class="sxs-lookup"><span data-stu-id="9ebf2-118">System.Object</span></span>

## <span data-ttu-id="9ebf2-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9ebf2-119">OUTPUTS</span></span>

### <span data-ttu-id="9ebf2-120">Micro soft. Power shell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="9ebf2-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="9ebf2-121">De **PSDiagnostics** -module voegt de klasse **LogDetails** toe aan de `Microsoft.PowerShell.Diagnostics` naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="9ebf2-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="9ebf2-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9ebf2-122">NOTES</span></span>

## <span data-ttu-id="9ebf2-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9ebf2-123">RELATED LINKS</span></span>

[<span data-ttu-id="9ebf2-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9ebf2-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="9ebf2-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9ebf2-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="9ebf2-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9ebf2-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
