---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: baf737a649e96488aff10959e02b59a0323e3ac4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249456"
---
# <span data-ttu-id="d5a89-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d5a89-102">Set-LogProperties</span></span>

## <span data-ttu-id="d5a89-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d5a89-103">SYNOPSIS</span></span>
<span data-ttu-id="d5a89-104">Hiermee wijzigt u de eigenschappen van een Windows-gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="d5a89-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="d5a89-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d5a89-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="d5a89-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d5a89-106">DESCRIPTION</span></span>

<span data-ttu-id="d5a89-107">Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d5a89-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="d5a89-108">Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d5a89-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="d5a89-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="d5a89-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d5a89-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d5a89-110">EXAMPLES</span></span>

### <span data-ttu-id="d5a89-111">Voor beeld 1: de Bewaar instelling van het Windows Power shell-gebeurtenis logboek wijzigen</span><span class="sxs-lookup"><span data-stu-id="d5a89-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="d5a89-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5a89-112">PARAMETERS</span></span>

### <span data-ttu-id="d5a89-113">-Force</span><span class="sxs-lookup"><span data-stu-id="d5a89-113">-Force</span></span>

<span data-ttu-id="d5a89-114">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="d5a89-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="d5a89-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="d5a89-115">-LogDetails</span></span>

<span data-ttu-id="d5a89-116">De bijgewerkte configuratie-instellingen die moeten worden toegewezen aan het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="d5a89-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d5a89-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5a89-117">CommonParameters</span></span>

<span data-ttu-id="d5a89-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d5a89-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5a89-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d5a89-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5a89-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="d5a89-120">INPUTS</span></span>

### <span data-ttu-id="d5a89-121">Micro soft. Power shell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="d5a89-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="d5a89-122">U moet een volledig geconfigureerd **LogDetails** -object door geven aan de `Set-LogProperties` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5a89-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="d5a89-123">Als u één instelling wilt wijzigen, moet u daarom gebruiken `Get-LogProperties` om de huidige configuratie op te halen.</span><span class="sxs-lookup"><span data-stu-id="d5a89-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="d5a89-124">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d5a89-124">OUTPUTS</span></span>

### <span data-ttu-id="d5a89-125">Geen</span><span class="sxs-lookup"><span data-stu-id="d5a89-125">None</span></span>

## <span data-ttu-id="d5a89-126">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d5a89-126">NOTES</span></span>

<span data-ttu-id="d5a89-127">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="d5a89-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d5a89-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d5a89-128">RELATED LINKS</span></span>

[<span data-ttu-id="d5a89-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d5a89-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="d5a89-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d5a89-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="d5a89-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d5a89-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
