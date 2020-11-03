---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 5a43e3382990209c365bb8fe5c0b320624ddfe18
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250981"
---
# <span data-ttu-id="9ef45-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="9ef45-103">Update-Script</span></span>

## <span data-ttu-id="9ef45-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9ef45-104">SYNOPSIS</span></span>
<span data-ttu-id="9ef45-105">Hiermee wordt een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9ef45-105">Updates a script.</span></span>

## <span data-ttu-id="9ef45-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9ef45-106">SYNTAX</span></span>

### <span data-ttu-id="9ef45-107">Alles</span><span class="sxs-lookup"><span data-stu-id="9ef45-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9ef45-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9ef45-108">DESCRIPTION</span></span>

<span data-ttu-id="9ef45-109">`Update-Script`Met de cmdlet wordt een script bijgewerkt dat is geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9ef45-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="9ef45-110">Het bijgewerkte script wordt gedownload uit dezelfde opslag plaats als de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="9ef45-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="9ef45-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9ef45-111">EXAMPLES</span></span>

### <span data-ttu-id="9ef45-112">Voor beeld 1: het opgegeven script bijwerken</span><span class="sxs-lookup"><span data-stu-id="9ef45-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="9ef45-113">In dit voor beeld wordt een geïnstalleerd script bijgewerkt en wordt de bijgewerkte versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ef45-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="9ef45-114">`Update-Script` maakt gebruik van de para meter **name** om het script op te geven dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9ef45-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="9ef45-115">De **RequiredVersion** para meter geeft u de script versie op.</span><span class="sxs-lookup"><span data-stu-id="9ef45-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="9ef45-116">`Get-InstalledScript` Hiermee wordt de bijgewerkte versie van het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ef45-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="9ef45-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ef45-117">PARAMETERS</span></span>

### <span data-ttu-id="9ef45-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="9ef45-118">-AcceptLicense</span></span>

<span data-ttu-id="9ef45-119">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="9ef45-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="9ef45-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9ef45-120">-AllowPrerelease</span></span>

<span data-ttu-id="9ef45-121">Hiermee kunt u een script bijwerken met het nieuwere script dat is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="9ef45-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="9ef45-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9ef45-122">-Confirm</span></span>

<span data-ttu-id="9ef45-123">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="9ef45-123">Prompts you for confirmation before running `Update-Script`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="9ef45-124">-Credential</span></span>

<span data-ttu-id="9ef45-125">Hiermee geeft u een gebruikers account op dat gemachtigd is om een script bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9ef45-125">Specifies a user account that has permission to update a script.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-126">-Force</span><span class="sxs-lookup"><span data-stu-id="9ef45-126">-Force</span></span>

<span data-ttu-id="9ef45-127">Er wordt geforceerd `Update-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9ef45-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9ef45-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9ef45-128">-MaximumVersion</span></span>

<span data-ttu-id="9ef45-129">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9ef45-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="9ef45-130">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9ef45-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="9ef45-131">-Name</span><span class="sxs-lookup"><span data-stu-id="9ef45-131">-Name</span></span>

<span data-ttu-id="9ef45-132">Hiermee geeft u één script naam of een matrix met script namen op die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9ef45-132">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="9ef45-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9ef45-133">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="9ef45-134">-Proxy</span></span>

<span data-ttu-id="9ef45-135">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="9ef45-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="9ef45-136">-ProxyCredential</span></span>

<span data-ttu-id="9ef45-137">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="9ef45-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9ef45-138">-RequiredVersion</span></span>

<span data-ttu-id="9ef45-139">Hiermee geeft u het exacte versie nummer van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9ef45-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="9ef45-140">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9ef45-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="9ef45-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9ef45-141">-WhatIf</span></span>

<span data-ttu-id="9ef45-142">Hier wordt weer gegeven wat er gebeurt als er `Update-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ef45-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="9ef45-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ef45-143">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ef45-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ef45-144">CommonParameters</span></span>

<span data-ttu-id="9ef45-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ef45-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ef45-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9ef45-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ef45-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="9ef45-147">INPUTS</span></span>

## <span data-ttu-id="9ef45-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9ef45-148">OUTPUTS</span></span>

## <span data-ttu-id="9ef45-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9ef45-149">NOTES</span></span>

## <span data-ttu-id="9ef45-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9ef45-150">RELATED LINKS</span></span>

[<span data-ttu-id="9ef45-151">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="9ef45-151">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="9ef45-152">Install-script</span><span class="sxs-lookup"><span data-stu-id="9ef45-152">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="9ef45-153">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="9ef45-153">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="9ef45-154">Save-Script</span><span class="sxs-lookup"><span data-stu-id="9ef45-154">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="9ef45-155">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="9ef45-155">Uninstall-Script</span></span>](Uninstall-Script.md)
