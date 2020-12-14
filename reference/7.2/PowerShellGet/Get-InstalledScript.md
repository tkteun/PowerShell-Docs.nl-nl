---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: fe5fc0feb34fda87dab987f33140992a346017a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706144"
---
# <span data-ttu-id="e6ed2-102">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="e6ed2-102">Get-InstalledScript</span></span>

## <span data-ttu-id="e6ed2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e6ed2-103">SYNOPSIS</span></span>
<span data-ttu-id="e6ed2-104">Hiermee wordt een geïnstalleerd script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-104">Gets an installed script.</span></span>

## <span data-ttu-id="e6ed2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e6ed2-105">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="e6ed2-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e6ed2-106">DESCRIPTION</span></span>

<span data-ttu-id="e6ed2-107">De cmdlet **Get-InstalledScript** haalt geïnstalleerde scripts op voor het bereik van CurrentUser en ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-107">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="e6ed2-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e6ed2-108">EXAMPLES</span></span>

### <span data-ttu-id="e6ed2-109">Voor beeld 1: alle geïnstalleerde scripts ophalen</span><span class="sxs-lookup"><span data-stu-id="e6ed2-109">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="e6ed2-110">Met deze opdracht worden alle geïnstalleerde scripts opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-110">This command gets all installed scripts.</span></span>

### <span data-ttu-id="e6ed2-111">Voor beeld 2: geïnstalleerde scripts op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="e6ed2-111">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="e6ed2-112">Met deze opdracht wordt een script opgehaald waarbij de naam begint met vereist-SCRI.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-112">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="e6ed2-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e6ed2-113">PARAMETERS</span></span>

### <span data-ttu-id="e6ed2-114">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e6ed2-114">-AllowPrerelease</span></span>

<span data-ttu-id="e6ed2-115">Bevat de resultaten scripts die als Prerelease zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-115">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="e6ed2-116">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e6ed2-116">-MaximumVersion</span></span>

<span data-ttu-id="e6ed2-117">Hiermee geeft u het maximum, of de meest recente versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-117">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="e6ed2-118">De para meters *MaximumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-118">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e6ed2-119">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e6ed2-119">-MinimumVersion</span></span>

<span data-ttu-id="e6ed2-120">Hiermee geeft u de minimum versie op van een script dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-120">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="e6ed2-121">De para meters *MinimumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-121">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e6ed2-122">-Name</span><span class="sxs-lookup"><span data-stu-id="e6ed2-122">-Name</span></span>

<span data-ttu-id="e6ed2-123">Hiermee geeft u een matrix met namen van te verkrijgen scripts op.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-123">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="e6ed2-124">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-124">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e6ed2-125">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e6ed2-125">-RequiredVersion</span></span>

<span data-ttu-id="e6ed2-126">Hiermee geeft u de exacte versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-126">Specifies the exact version of a script to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e6ed2-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e6ed2-127">CommonParameters</span></span>

<span data-ttu-id="e6ed2-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e6ed2-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e6ed2-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e6ed2-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="e6ed2-130">INPUTS</span></span>

### <span data-ttu-id="e6ed2-131">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e6ed2-131">System.String[]</span></span>

### <span data-ttu-id="e6ed2-132">System. String</span><span class="sxs-lookup"><span data-stu-id="e6ed2-132">System.String</span></span>

## <span data-ttu-id="e6ed2-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e6ed2-133">OUTPUTS</span></span>

### <span data-ttu-id="e6ed2-134">System. object</span><span class="sxs-lookup"><span data-stu-id="e6ed2-134">System.Object</span></span>

## <span data-ttu-id="e6ed2-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e6ed2-135">NOTES</span></span>

## <span data-ttu-id="e6ed2-136">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e6ed2-136">RELATED LINKS</span></span>

[<span data-ttu-id="e6ed2-137">Install-script</span><span class="sxs-lookup"><span data-stu-id="e6ed2-137">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="e6ed2-138">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="e6ed2-138">Uninstall-Script</span></span>](Uninstall-Script.md)

