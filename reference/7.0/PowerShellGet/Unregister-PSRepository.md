---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0f1173cbfab139438d55ff49272f9625579820dc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249794"
---
# <span data-ttu-id="c499e-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c499e-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="c499e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c499e-104">SYNOPSIS</span></span>
<span data-ttu-id="c499e-105">Hiermee wordt de registratie van een opslag plaats ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c499e-105">Unregisters a repository.</span></span>

## <span data-ttu-id="c499e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c499e-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="c499e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c499e-107">DESCRIPTION</span></span>

<span data-ttu-id="c499e-108">Met de cmdlet wordt de `Unregister-PSRepository` registratie van een opslag plaats voor de huidige gebruiker ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c499e-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="c499e-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c499e-109">EXAMPLES</span></span>

### <span data-ttu-id="c499e-110">Voor beeld 1: de registratie van een opslag plaats opheffen</span><span class="sxs-lookup"><span data-stu-id="c499e-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="c499e-111">In dit voor beeld wordt de registratie van de opslag plaats met de naam myNuGetSource ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c499e-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="c499e-112">Voor beeld 2: alle opslag plaatsen ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="c499e-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="c499e-113">In dit voor beeld worden `Get-PSRepository` alle geregistreerde opslag plaatsen gebruikt en wordt de pijplijn operator gebruikt om de `Unregister-PSRepository` registratie ervan ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="c499e-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="c499e-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c499e-114">PARAMETERS</span></span>

### <span data-ttu-id="c499e-115">-Name</span><span class="sxs-lookup"><span data-stu-id="c499e-115">-Name</span></span>

<span data-ttu-id="c499e-116">Hiermee geeft u een matrix met namen op van de opslag plaatsen die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c499e-116">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="c499e-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c499e-117">CommonParameters</span></span>

<span data-ttu-id="c499e-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c499e-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c499e-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c499e-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c499e-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="c499e-120">INPUTS</span></span>

### <span data-ttu-id="c499e-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c499e-121">System.String[]</span></span>

## <span data-ttu-id="c499e-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c499e-122">OUTPUTS</span></span>

### <span data-ttu-id="c499e-123">System. object</span><span class="sxs-lookup"><span data-stu-id="c499e-123">System.Object</span></span>

## <span data-ttu-id="c499e-124">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c499e-124">NOTES</span></span>

## <span data-ttu-id="c499e-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c499e-125">RELATED LINKS</span></span>

[<span data-ttu-id="c499e-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c499e-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="c499e-127">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c499e-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="c499e-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c499e-128">Set-PSRepository</span></span>](Set-PSRepository.md)
