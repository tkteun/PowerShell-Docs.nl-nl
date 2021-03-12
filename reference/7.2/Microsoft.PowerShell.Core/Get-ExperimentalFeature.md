---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 2b6bbc6e3e0c535d777509a545edfe10fed7d727
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194934"
---
# <span data-ttu-id="6bf8f-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6bf8f-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="6bf8f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6bf8f-103">SYNOPSIS</span></span>
<span data-ttu-id="6bf8f-104">Hiermee worden experimentele functies opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-104">Gets experimental features.</span></span>

## <span data-ttu-id="6bf8f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6bf8f-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6bf8f-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6bf8f-106">DESCRIPTION</span></span>

<span data-ttu-id="6bf8f-107">De `Get-ExperimentalFeature` cmdlet retourneert alle experimentele functies die zijn gedetecteerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="6bf8f-108">Experimentele functies kunnen afkomstig zijn uit modules of de Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="6bf8f-109">Met experimentele functies kunnen gebruikers veilig nieuwe functies testen en feedback geven (meestal via GitHub) voordat het ontwerp als voltooid wordt beschouwd en alle wijzigingen kunnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="6bf8f-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6bf8f-110">EXAMPLES</span></span>

### <span data-ttu-id="6bf8f-111">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="6bf8f-111">Example 1</span></span>

<span data-ttu-id="6bf8f-112">Hiermee wordt de lijst met momenteel geregistreerde experimentele functies en de huidige status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="6bf8f-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6bf8f-113">PARAMETERS</span></span>

### <span data-ttu-id="6bf8f-114">-Name</span><span class="sxs-lookup"><span data-stu-id="6bf8f-114">-Name</span></span>

<span data-ttu-id="6bf8f-115">Naam of namen van specifieke experimentele functies die moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-115">Name or names of specific experimental features to return.</span></span>

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

### <span data-ttu-id="6bf8f-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bf8f-116">CommonParameters</span></span>

<span data-ttu-id="6bf8f-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bf8f-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6bf8f-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="6bf8f-119">INPUTS</span></span>

### <span data-ttu-id="6bf8f-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6bf8f-120">System.String[]</span></span>

<span data-ttu-id="6bf8f-121">Naam of namen van experimentele functies die moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="6bf8f-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6bf8f-122">OUTPUTS</span></span>

### <span data-ttu-id="6bf8f-123">System. Management. Automation. ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6bf8f-123">System.Management.Automation.ExperimentalFeature</span></span>

<span data-ttu-id="6bf8f-124">Retourneert instanties die overeenkomen met de aangevraagde namen of alle experimentele functies als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6bf8f-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="6bf8f-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6bf8f-125">RELATED LINKS</span></span>

[<span data-ttu-id="6bf8f-126">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6bf8f-126">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="6bf8f-127">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6bf8f-127">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
