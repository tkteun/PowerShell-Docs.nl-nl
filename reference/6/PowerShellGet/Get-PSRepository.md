---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: b4d786cdac183917428b0846ad3c88d41b083ac5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250938"
---
# <span data-ttu-id="52b35-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52b35-103">Get-PSRepository</span></span>

## <span data-ttu-id="52b35-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="52b35-104">SYNOPSIS</span></span>
<span data-ttu-id="52b35-105">Hiermee worden Power shell-opslag plaatsen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="52b35-105">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="52b35-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="52b35-106">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="52b35-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="52b35-107">DESCRIPTION</span></span>

<span data-ttu-id="52b35-108">Met de cmdlet **Get-PSRepository** worden Power shell-module opslagplaatsen opgehaald die zijn geregistreerd voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="52b35-108">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="52b35-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="52b35-109">EXAMPLES</span></span>

### <span data-ttu-id="52b35-110">Voor beeld 1: alle module opslagplaatsen ophalen</span><span class="sxs-lookup"><span data-stu-id="52b35-110">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="52b35-111">Met deze opdracht worden alle module opslagplaatsen die zijn geregistreerd voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="52b35-111">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="52b35-112">Voor beeld 2: module opslagplaatsen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="52b35-112">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="52b35-113">Met deze opdracht worden alle module opslagplaatsen opgehaald die NuGet in hun namen bevatten.</span><span class="sxs-lookup"><span data-stu-id="52b35-113">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="52b35-114">Voor beeld 3: een module opslagplaats ophalen en de uitvoer opmaken</span><span class="sxs-lookup"><span data-stu-id="52b35-114">Example 3: Get a module repository and format the output</span></span>

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

<span data-ttu-id="52b35-115">Met deze opdracht wordt de opslag plaats met de naam Local01 opgehaald en wordt de pijplijn operator gebruikt om dat object door te geven aan de Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52b35-115">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="52b35-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="52b35-116">PARAMETERS</span></span>

### <span data-ttu-id="52b35-117">-Name</span><span class="sxs-lookup"><span data-stu-id="52b35-117">-Name</span></span>

<span data-ttu-id="52b35-118">Hiermee geeft u de namen op van de opslag plaatsen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="52b35-118">Specifies the names of the repositories to get.</span></span>

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

### <span data-ttu-id="52b35-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52b35-119">CommonParameters</span></span>

<span data-ttu-id="52b35-120">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52b35-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52b35-121">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="52b35-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52b35-122">INVOER</span><span class="sxs-lookup"><span data-stu-id="52b35-122">INPUTS</span></span>

### <span data-ttu-id="52b35-123">System.String[]</span><span class="sxs-lookup"><span data-stu-id="52b35-123">System.String[]</span></span>

## <span data-ttu-id="52b35-124">UITVOER</span><span class="sxs-lookup"><span data-stu-id="52b35-124">OUTPUTS</span></span>

### <span data-ttu-id="52b35-125">System. object</span><span class="sxs-lookup"><span data-stu-id="52b35-125">System.Object</span></span>

## <span data-ttu-id="52b35-126">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="52b35-126">NOTES</span></span>

## <span data-ttu-id="52b35-127">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="52b35-127">RELATED LINKS</span></span>

[<span data-ttu-id="52b35-128">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52b35-128">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="52b35-129">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52b35-129">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="52b35-130">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52b35-130">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
