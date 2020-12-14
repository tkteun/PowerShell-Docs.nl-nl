---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 25da03724603b0000c46ae2da69d63cdf2f36cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891680"
---
# <span data-ttu-id="e1dfe-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-103">Update-Script</span></span>

## <span data-ttu-id="e1dfe-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e1dfe-104">SYNOPSIS</span></span>
<span data-ttu-id="e1dfe-105">Hiermee wordt een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-105">Updates a script.</span></span>

## <span data-ttu-id="e1dfe-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e1dfe-106">SYNTAX</span></span>

### <span data-ttu-id="e1dfe-107">Alles</span><span class="sxs-lookup"><span data-stu-id="e1dfe-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e1dfe-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e1dfe-108">DESCRIPTION</span></span>

<span data-ttu-id="e1dfe-109">`Update-Script`Met de cmdlet wordt een script bijgewerkt dat is geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="e1dfe-110">Het bijgewerkte script wordt gedownload uit dezelfde opslag plaats als de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="e1dfe-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e1dfe-111">EXAMPLES</span></span>

### <span data-ttu-id="e1dfe-112">Voor beeld 1: het opgegeven script bijwerken</span><span class="sxs-lookup"><span data-stu-id="e1dfe-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="e1dfe-113">In dit voor beeld wordt een geïnstalleerd script bijgewerkt en wordt de bijgewerkte versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="e1dfe-114">`Update-Script` maakt gebruik van de para meter **name** om het script op te geven dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="e1dfe-115">De **RequiredVersion** para meter geeft u de script versie op.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="e1dfe-116">`Get-InstalledScript` Hiermee wordt de bijgewerkte versie van het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="e1dfe-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1dfe-117">PARAMETERS</span></span>

### <span data-ttu-id="e1dfe-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="e1dfe-118">-AcceptLicense</span></span>

<span data-ttu-id="e1dfe-119">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="e1dfe-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e1dfe-120">-AllowPrerelease</span></span>

<span data-ttu-id="e1dfe-121">Hiermee kunt u een script bijwerken met het nieuwere script dat is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="e1dfe-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e1dfe-122">-Confirm</span></span>

<span data-ttu-id="e1dfe-123">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="e1dfe-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="e1dfe-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="e1dfe-124">-Credential</span></span>

<span data-ttu-id="e1dfe-125">Hiermee geeft u een gebruikers account op dat gemachtigd is om een script bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-125">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="e1dfe-126">-Force</span><span class="sxs-lookup"><span data-stu-id="e1dfe-126">-Force</span></span>

<span data-ttu-id="e1dfe-127">Er wordt geforceerd `Update-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e1dfe-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e1dfe-128">-MaximumVersion</span></span>

<span data-ttu-id="e1dfe-129">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="e1dfe-130">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e1dfe-131">-Name</span><span class="sxs-lookup"><span data-stu-id="e1dfe-131">-Name</span></span>

<span data-ttu-id="e1dfe-132">Hiermee geeft u één script naam of een matrix met script namen op die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-132">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="e1dfe-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e1dfe-133">-PassThru</span></span>

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

### <span data-ttu-id="e1dfe-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e1dfe-134">-Proxy</span></span>

<span data-ttu-id="e1dfe-135">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="e1dfe-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e1dfe-136">-ProxyCredential</span></span>

<span data-ttu-id="e1dfe-137">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e1dfe-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e1dfe-138">-RequiredVersion</span></span>

<span data-ttu-id="e1dfe-139">Hiermee geeft u het exacte versie nummer van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="e1dfe-140">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e1dfe-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e1dfe-141">-WhatIf</span></span>

<span data-ttu-id="e1dfe-142">Hier wordt weer gegeven wat er gebeurt als er `Update-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="e1dfe-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e1dfe-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1dfe-144">CommonParameters</span></span>

<span data-ttu-id="e1dfe-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1dfe-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1dfe-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="e1dfe-147">INPUTS</span></span>

### <span data-ttu-id="e1dfe-148">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e1dfe-148">System.String[]</span></span>

### <span data-ttu-id="e1dfe-149">System. String</span><span class="sxs-lookup"><span data-stu-id="e1dfe-149">System.String</span></span>

### <span data-ttu-id="e1dfe-150">System. URI</span><span class="sxs-lookup"><span data-stu-id="e1dfe-150">System.Uri</span></span>

### <span data-ttu-id="e1dfe-151">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e1dfe-151">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="e1dfe-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e1dfe-152">OUTPUTS</span></span>

### <span data-ttu-id="e1dfe-153">System. object</span><span class="sxs-lookup"><span data-stu-id="e1dfe-153">System.Object</span></span>

## <span data-ttu-id="e1dfe-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e1dfe-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1dfe-155">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e1dfe-156">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e1dfe-157">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="e1dfe-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e1dfe-158">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1dfe-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e1dfe-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e1dfe-159">RELATED LINKS</span></span>

[<span data-ttu-id="e1dfe-160">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-160">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="e1dfe-161">Install-script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-161">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="e1dfe-162">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-162">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="e1dfe-163">Save-Script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-163">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="e1dfe-164">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="e1dfe-164">Uninstall-Script</span></span>](Uninstall-Script.md)

