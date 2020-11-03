---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: a90ece844d5a271402537f17c601bf2e36b5ed8c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249520"
---
# <span data-ttu-id="c79aa-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="c79aa-103">Get-InstalledScript</span></span>

## <span data-ttu-id="c79aa-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c79aa-104">SYNOPSIS</span></span>
<span data-ttu-id="c79aa-105">Hiermee wordt een geïnstalleerd script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c79aa-105">Gets an installed script.</span></span>

## <span data-ttu-id="c79aa-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c79aa-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="c79aa-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c79aa-107">DESCRIPTION</span></span>

<span data-ttu-id="c79aa-108">De cmdlet **Get-InstalledScript** haalt geïnstalleerde scripts op voor het bereik van CurrentUser en ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="c79aa-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="c79aa-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c79aa-109">EXAMPLES</span></span>

### <span data-ttu-id="c79aa-110">Voor beeld 1: alle geïnstalleerde scripts ophalen</span><span class="sxs-lookup"><span data-stu-id="c79aa-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="c79aa-111">Met deze opdracht worden alle geïnstalleerde scripts opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c79aa-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="c79aa-112">Voor beeld 2: geïnstalleerde scripts op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="c79aa-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="c79aa-113">Met deze opdracht wordt een script opgehaald waarbij de naam begint met vereist-SCRI.</span><span class="sxs-lookup"><span data-stu-id="c79aa-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="c79aa-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c79aa-114">PARAMETERS</span></span>

### <span data-ttu-id="c79aa-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c79aa-115">-AllowPrerelease</span></span>

<span data-ttu-id="c79aa-116">Bevat de resultaten scripts die als Prerelease zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="c79aa-116">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="c79aa-117">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c79aa-117">-MaximumVersion</span></span>

<span data-ttu-id="c79aa-118">Hiermee geeft u het maximum, of de meest recente versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c79aa-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="c79aa-119">De para meters *MaximumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c79aa-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="c79aa-120">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c79aa-120">-MinimumVersion</span></span>

<span data-ttu-id="c79aa-121">Hiermee geeft u de minimum versie op van een script dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c79aa-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="c79aa-122">De para meters *MinimumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c79aa-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="c79aa-123">-Name</span><span class="sxs-lookup"><span data-stu-id="c79aa-123">-Name</span></span>

<span data-ttu-id="c79aa-124">Hiermee geeft u een matrix met namen van te verkrijgen scripts op.</span><span class="sxs-lookup"><span data-stu-id="c79aa-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="c79aa-125">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="c79aa-125">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="c79aa-126">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c79aa-126">-RequiredVersion</span></span>

<span data-ttu-id="c79aa-127">Hiermee geeft u de exacte versie van een script op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c79aa-127">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="c79aa-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c79aa-128">CommonParameters</span></span>

<span data-ttu-id="c79aa-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c79aa-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c79aa-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c79aa-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c79aa-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="c79aa-131">INPUTS</span></span>

### <span data-ttu-id="c79aa-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c79aa-132">System.String[]</span></span>

### <span data-ttu-id="c79aa-133">System. String</span><span class="sxs-lookup"><span data-stu-id="c79aa-133">System.String</span></span>

## <span data-ttu-id="c79aa-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c79aa-134">OUTPUTS</span></span>

### <span data-ttu-id="c79aa-135">System. object</span><span class="sxs-lookup"><span data-stu-id="c79aa-135">System.Object</span></span>

## <span data-ttu-id="c79aa-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c79aa-136">NOTES</span></span>

## <span data-ttu-id="c79aa-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c79aa-137">RELATED LINKS</span></span>

[<span data-ttu-id="c79aa-138">Install-script</span><span class="sxs-lookup"><span data-stu-id="c79aa-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="c79aa-139">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="c79aa-139">Uninstall-Script</span></span>](Uninstall-Script.md)
