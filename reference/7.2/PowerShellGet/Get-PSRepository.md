---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705992"
---
# <span data-ttu-id="a2f28-102">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a2f28-102">Get-PSRepository</span></span>

## <span data-ttu-id="a2f28-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a2f28-103">SYNOPSIS</span></span>
<span data-ttu-id="a2f28-104">Hiermee worden Power shell-opslag plaatsen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a2f28-104">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="a2f28-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a2f28-105">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a2f28-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a2f28-106">DESCRIPTION</span></span>

<span data-ttu-id="a2f28-107">Met de cmdlet **Get-PSRepository** worden Power shell-module opslagplaatsen opgehaald die zijn geregistreerd voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a2f28-107">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="a2f28-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a2f28-108">EXAMPLES</span></span>

### <span data-ttu-id="a2f28-109">Voor beeld 1: alle module opslagplaatsen ophalen</span><span class="sxs-lookup"><span data-stu-id="a2f28-109">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="a2f28-110">Met deze opdracht worden alle module opslagplaatsen die zijn geregistreerd voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a2f28-110">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="a2f28-111">Voor beeld 2: module opslagplaatsen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="a2f28-111">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="a2f28-112">Met deze opdracht worden alle module opslagplaatsen opgehaald die NuGet in hun namen bevatten.</span><span class="sxs-lookup"><span data-stu-id="a2f28-112">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="a2f28-113">Voor beeld 3: een module opslagplaats ophalen en de uitvoer opmaken</span><span class="sxs-lookup"><span data-stu-id="a2f28-113">Example 3: Get a module repository and format the output</span></span>

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

<span data-ttu-id="a2f28-114">Met deze opdracht wordt de opslag plaats met de naam Local01 opgehaald en wordt de pijplijn operator gebruikt om dat object door te geven aan de Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2f28-114">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="a2f28-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a2f28-115">PARAMETERS</span></span>

### <span data-ttu-id="a2f28-116">-Name</span><span class="sxs-lookup"><span data-stu-id="a2f28-116">-Name</span></span>

<span data-ttu-id="a2f28-117">Hiermee geeft u de namen op van de opslag plaatsen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a2f28-117">Specifies the names of the repositories to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2f28-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2f28-118">CommonParameters</span></span>

<span data-ttu-id="a2f28-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a2f28-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a2f28-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a2f28-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a2f28-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="a2f28-121">INPUTS</span></span>

### <span data-ttu-id="a2f28-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a2f28-122">System.String[]</span></span>

## <span data-ttu-id="a2f28-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a2f28-123">OUTPUTS</span></span>

### <span data-ttu-id="a2f28-124">System. object</span><span class="sxs-lookup"><span data-stu-id="a2f28-124">System.Object</span></span>

## <span data-ttu-id="a2f28-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a2f28-125">NOTES</span></span>

## <span data-ttu-id="a2f28-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a2f28-126">RELATED LINKS</span></span>

[<span data-ttu-id="a2f28-127">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a2f28-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="a2f28-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a2f28-128">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="a2f28-129">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a2f28-129">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

