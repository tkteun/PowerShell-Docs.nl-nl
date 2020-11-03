---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: ff51e4c30c2554ba58aa28862c44bb5fdbfd78d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250327"
---
# <span data-ttu-id="53dd9-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="53dd9-102">Set-LogProperties</span></span>

## <span data-ttu-id="53dd9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="53dd9-103">SYNOPSIS</span></span>
<span data-ttu-id="53dd9-104">Hiermee wijzigt u de eigenschappen van een Windows-gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="53dd9-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="53dd9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="53dd9-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="53dd9-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="53dd9-106">DESCRIPTION</span></span>

<span data-ttu-id="53dd9-107">Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="53dd9-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="53dd9-108">Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="53dd9-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="53dd9-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="53dd9-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="53dd9-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="53dd9-110">EXAMPLES</span></span>

### <span data-ttu-id="53dd9-111">Voor beeld 1: de Bewaar instelling van het Windows Power shell-gebeurtenis logboek wijzigen</span><span class="sxs-lookup"><span data-stu-id="53dd9-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="53dd9-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53dd9-112">PARAMETERS</span></span>

### <span data-ttu-id="53dd9-113">-Force</span><span class="sxs-lookup"><span data-stu-id="53dd9-113">-Force</span></span>

<span data-ttu-id="53dd9-114">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="53dd9-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="53dd9-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="53dd9-115">-LogDetails</span></span>

<span data-ttu-id="53dd9-116">De bijgewerkte configuratie-instellingen die moeten worden toegewezen aan het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="53dd9-116">The updated configuration settings to be assigned to the event log.</span></span>

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

### <span data-ttu-id="53dd9-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53dd9-117">CommonParameters</span></span>

<span data-ttu-id="53dd9-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53dd9-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53dd9-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="53dd9-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53dd9-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="53dd9-120">INPUTS</span></span>

### <span data-ttu-id="53dd9-121">Micro soft. Power shell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="53dd9-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="53dd9-122">U moet een volledig geconfigureerd **LogDetails** -object door geven aan de `Set-LogProperties` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53dd9-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="53dd9-123">Als u één instelling wilt wijzigen, moet u daarom gebruiken `Get-LogProperties` om de huidige configuratie op te halen.</span><span class="sxs-lookup"><span data-stu-id="53dd9-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="53dd9-124">UITVOER</span><span class="sxs-lookup"><span data-stu-id="53dd9-124">OUTPUTS</span></span>

### <span data-ttu-id="53dd9-125">System. object</span><span class="sxs-lookup"><span data-stu-id="53dd9-125">System.Object</span></span>

## <span data-ttu-id="53dd9-126">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="53dd9-126">NOTES</span></span>

<span data-ttu-id="53dd9-127">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="53dd9-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="53dd9-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="53dd9-128">RELATED LINKS</span></span>

[<span data-ttu-id="53dd9-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="53dd9-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="53dd9-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="53dd9-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="53dd9-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="53dd9-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
