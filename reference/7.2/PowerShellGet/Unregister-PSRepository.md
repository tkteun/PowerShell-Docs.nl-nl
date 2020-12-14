---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705411"
---
# <span data-ttu-id="a465f-102">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a465f-102">Unregister-PSRepository</span></span>

## <span data-ttu-id="a465f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a465f-103">SYNOPSIS</span></span>
<span data-ttu-id="a465f-104">Hiermee wordt de registratie van een opslag plaats ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a465f-104">Unregisters a repository.</span></span>

## <span data-ttu-id="a465f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a465f-105">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="a465f-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a465f-106">DESCRIPTION</span></span>

<span data-ttu-id="a465f-107">Met de cmdlet wordt de `Unregister-PSRepository` registratie van een opslag plaats voor de huidige gebruiker ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a465f-107">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="a465f-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a465f-108">EXAMPLES</span></span>

### <span data-ttu-id="a465f-109">Voor beeld 1: de registratie van een opslag plaats opheffen</span><span class="sxs-lookup"><span data-stu-id="a465f-109">Example 1: Unregister a repository</span></span>

<span data-ttu-id="a465f-110">In dit voor beeld wordt de registratie van de opslag plaats met de naam myNuGetSource ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a465f-110">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="a465f-111">Voor beeld 2: alle opslag plaatsen ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="a465f-111">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="a465f-112">In dit voor beeld worden `Get-PSRepository` alle geregistreerde opslag plaatsen gebruikt en wordt de pijplijn operator gebruikt om de `Unregister-PSRepository` registratie ervan ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="a465f-112">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="a465f-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a465f-113">PARAMETERS</span></span>

### <span data-ttu-id="a465f-114">-Name</span><span class="sxs-lookup"><span data-stu-id="a465f-114">-Name</span></span>

<span data-ttu-id="a465f-115">Hiermee geeft u een matrix met namen op van de opslag plaatsen die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a465f-115">Specifies an array of names of the repositories to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a465f-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a465f-116">CommonParameters</span></span>

<span data-ttu-id="a465f-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a465f-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a465f-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a465f-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a465f-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="a465f-119">INPUTS</span></span>

### <span data-ttu-id="a465f-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a465f-120">System.String[]</span></span>

## <span data-ttu-id="a465f-121">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a465f-121">OUTPUTS</span></span>

### <span data-ttu-id="a465f-122">System. object</span><span class="sxs-lookup"><span data-stu-id="a465f-122">System.Object</span></span>

## <span data-ttu-id="a465f-123">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a465f-123">NOTES</span></span>

## <span data-ttu-id="a465f-124">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a465f-124">RELATED LINKS</span></span>

[<span data-ttu-id="a465f-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a465f-125">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="a465f-126">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a465f-126">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="a465f-127">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a465f-127">Set-PSRepository</span></span>](Set-PSRepository.md)
