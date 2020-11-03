---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: 6a69108694d5ba614bb7f195004d2d37ac6de092
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250939"
---
# <span data-ttu-id="51896-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="51896-103">Get-InstalledScript</span></span>

## <span data-ttu-id="51896-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="51896-104">SYNOPSIS</span></span>
<span data-ttu-id="51896-105">Hiermee wordt een geïnstalleerd script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51896-105">Gets an installed script.</span></span>

## <span data-ttu-id="51896-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="51896-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="51896-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="51896-107">DESCRIPTION</span></span>

<span data-ttu-id="51896-108">De cmdlet **Get-InstalledScript** haalt geïnstalleerde scripts op voor het bereik van CurrentUser en ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="51896-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="51896-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="51896-109">EXAMPLES</span></span>

### <span data-ttu-id="51896-110">Voor beeld 1: alle geïnstalleerde scripts ophalen</span><span class="sxs-lookup"><span data-stu-id="51896-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="51896-111">Met deze opdracht worden alle geïnstalleerde scripts opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51896-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="51896-112">Voor beeld 2: geïnstalleerde scripts op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="51896-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="51896-113">Met deze opdracht wordt een script opgehaald waarbij de naam begint met vereist-SCRI.</span><span class="sxs-lookup"><span data-stu-id="51896-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="51896-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51896-114">PARAMETERS</span></span>

### <span data-ttu-id="51896-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="51896-115">-AllowPrerelease</span></span>

<span data-ttu-id="51896-116">Bevat de resultaten scripts die als Prerelease zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="51896-116">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="51896-117">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="51896-117">-MaximumVersion</span></span>

<span data-ttu-id="51896-118">Hiermee geeft u het maximum, of de meest recente versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51896-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="51896-119">De para meters *MaximumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="51896-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="51896-120">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="51896-120">-MinimumVersion</span></span>

<span data-ttu-id="51896-121">Hiermee geeft u de minimum versie op van een script dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51896-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="51896-122">De para meters *MinimumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="51896-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="51896-123">-Name</span><span class="sxs-lookup"><span data-stu-id="51896-123">-Name</span></span>

<span data-ttu-id="51896-124">Hiermee geeft u een matrix met namen van te verkrijgen scripts op.</span><span class="sxs-lookup"><span data-stu-id="51896-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="51896-125">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="51896-125">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="51896-126">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="51896-126">-RequiredVersion</span></span>

<span data-ttu-id="51896-127">Hiermee geeft u de exacte versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51896-127">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="51896-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51896-128">CommonParameters</span></span>

<span data-ttu-id="51896-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51896-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51896-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="51896-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51896-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="51896-131">INPUTS</span></span>

### <span data-ttu-id="51896-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="51896-132">System.String[]</span></span>

### <span data-ttu-id="51896-133">System. String</span><span class="sxs-lookup"><span data-stu-id="51896-133">System.String</span></span>

## <span data-ttu-id="51896-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="51896-134">OUTPUTS</span></span>

### <span data-ttu-id="51896-135">System. object</span><span class="sxs-lookup"><span data-stu-id="51896-135">System.Object</span></span>

## <span data-ttu-id="51896-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="51896-136">NOTES</span></span>

## <span data-ttu-id="51896-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="51896-137">RELATED LINKS</span></span>

[<span data-ttu-id="51896-138">Install-script</span><span class="sxs-lookup"><span data-stu-id="51896-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="51896-139">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="51896-139">Uninstall-Script</span></span>](Uninstall-Script.md)
