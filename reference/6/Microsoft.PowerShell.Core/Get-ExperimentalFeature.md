---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251243"
---
# <span data-ttu-id="21691-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="21691-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="21691-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="21691-103">SYNOPSIS</span></span>
<span data-ttu-id="21691-104">Hiermee worden experimentele functies opgehaald.</span><span class="sxs-lookup"><span data-stu-id="21691-104">Gets experimental features.</span></span>

## <span data-ttu-id="21691-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="21691-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="21691-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="21691-106">DESCRIPTION</span></span>

<span data-ttu-id="21691-107">De `Get-ExperimentalFeature` cmdlet retourneert alle experimentele functies die zijn gedetecteerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="21691-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="21691-108">Experimentele functies kunnen afkomstig zijn uit modules of de Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="21691-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="21691-109">Met experimentele functies kunnen gebruikers veilig nieuwe functies testen en feedback geven (meestal via GitHub) voordat het ontwerp als voltooid wordt beschouwd en alle wijzigingen kunnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="21691-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="21691-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="21691-110">EXAMPLES</span></span>

### <span data-ttu-id="21691-111">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="21691-111">Example 1</span></span>

<span data-ttu-id="21691-112">Hiermee wordt de lijst met momenteel geregistreerde experimentele functies en de huidige status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="21691-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="21691-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21691-113">PARAMETERS</span></span>

### <span data-ttu-id="21691-114">-Name</span><span class="sxs-lookup"><span data-stu-id="21691-114">-Name</span></span>

<span data-ttu-id="21691-115">Naam of namen van specifieke experimentele functies die moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="21691-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21691-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21691-116">CommonParameters</span></span>

<span data-ttu-id="21691-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21691-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21691-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21691-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21691-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="21691-119">INPUTS</span></span>

### <span data-ttu-id="21691-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="21691-120">System.String[]</span></span>

<span data-ttu-id="21691-121">Naam of namen van experimentele functies die moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="21691-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="21691-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="21691-122">OUTPUTS</span></span>

### <span data-ttu-id="21691-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="21691-123">ExperimentalFeature</span></span>

<span data-ttu-id="21691-124">Retourneert instanties die overeenkomen met de aangevraagde namen of alle experimentele functies als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="21691-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="21691-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="21691-125">NOTES</span></span>

## <span data-ttu-id="21691-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="21691-126">RELATED LINKS</span></span>

[<span data-ttu-id="21691-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="21691-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="21691-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="21691-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
