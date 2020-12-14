---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 0fa537e463464fe055ea14aeab05cbb3ac5d1012
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890403"
---
# <span data-ttu-id="61883-102">Update-Script</span><span class="sxs-lookup"><span data-stu-id="61883-102">Update-Script</span></span>

## <span data-ttu-id="61883-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="61883-103">SYNOPSIS</span></span>
<span data-ttu-id="61883-104">Hiermee wordt een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61883-104">Updates a script.</span></span>

## <span data-ttu-id="61883-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="61883-105">SYNTAX</span></span>

### <span data-ttu-id="61883-106">Alles</span><span class="sxs-lookup"><span data-stu-id="61883-106">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="61883-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="61883-107">DESCRIPTION</span></span>

<span data-ttu-id="61883-108">`Update-Script`Met de cmdlet wordt een script bijgewerkt dat is geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="61883-108">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="61883-109">Het bijgewerkte script wordt gedownload uit dezelfde opslag plaats als de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="61883-109">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="61883-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="61883-110">EXAMPLES</span></span>

### <span data-ttu-id="61883-111">Voor beeld 1: het opgegeven script bijwerken</span><span class="sxs-lookup"><span data-stu-id="61883-111">Example 1: Update the specified script</span></span>

<span data-ttu-id="61883-112">In dit voor beeld wordt een geïnstalleerd script bijgewerkt en wordt de bijgewerkte versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="61883-112">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="61883-113">`Update-Script` maakt gebruik van de para meter **name** om het script op te geven dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61883-113">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="61883-114">De **RequiredVersion** para meter geeft u de script versie op.</span><span class="sxs-lookup"><span data-stu-id="61883-114">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="61883-115">`Get-InstalledScript` Hiermee wordt de bijgewerkte versie van het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="61883-115">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="61883-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="61883-116">PARAMETERS</span></span>

### <span data-ttu-id="61883-117">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="61883-117">-AcceptLicense</span></span>

<span data-ttu-id="61883-118">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="61883-118">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="61883-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="61883-119">-AllowPrerelease</span></span>

<span data-ttu-id="61883-120">Hiermee kunt u een script bijwerken met het nieuwere script dat is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="61883-120">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="61883-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="61883-121">-Confirm</span></span>

<span data-ttu-id="61883-122">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="61883-122">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="61883-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="61883-123">-Credential</span></span>

<span data-ttu-id="61883-124">Hiermee geeft u een gebruikers account op dat gemachtigd is om een script bij te werken.</span><span class="sxs-lookup"><span data-stu-id="61883-124">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="61883-125">-Force</span><span class="sxs-lookup"><span data-stu-id="61883-125">-Force</span></span>

<span data-ttu-id="61883-126">Er wordt geforceerd `Update-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="61883-126">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="61883-127">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="61883-127">-MaximumVersion</span></span>

<span data-ttu-id="61883-128">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61883-128">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="61883-129">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="61883-129">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="61883-130">-Name</span><span class="sxs-lookup"><span data-stu-id="61883-130">-Name</span></span>

<span data-ttu-id="61883-131">Hiermee geeft u één script naam of een matrix met script namen op die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61883-131">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="61883-132">-PassThru</span><span class="sxs-lookup"><span data-stu-id="61883-132">-PassThru</span></span>

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

### <span data-ttu-id="61883-133">-Proxy</span><span class="sxs-lookup"><span data-stu-id="61883-133">-Proxy</span></span>

<span data-ttu-id="61883-134">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="61883-134">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="61883-135">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="61883-135">-ProxyCredential</span></span>

<span data-ttu-id="61883-136">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="61883-136">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="61883-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="61883-137">-RequiredVersion</span></span>

<span data-ttu-id="61883-138">Hiermee geeft u het exacte versie nummer van het script op dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61883-138">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="61883-139">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="61883-139">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="61883-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="61883-140">-WhatIf</span></span>

<span data-ttu-id="61883-141">Hier wordt weer gegeven wat er gebeurt als er `Update-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61883-141">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="61883-142">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61883-142">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="61883-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61883-143">CommonParameters</span></span>

<span data-ttu-id="61883-144">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61883-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61883-145">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="61883-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="61883-146">INVOER</span><span class="sxs-lookup"><span data-stu-id="61883-146">INPUTS</span></span>

### <span data-ttu-id="61883-147">System.String[]</span><span class="sxs-lookup"><span data-stu-id="61883-147">System.String[]</span></span>

### <span data-ttu-id="61883-148">System. String</span><span class="sxs-lookup"><span data-stu-id="61883-148">System.String</span></span>

### <span data-ttu-id="61883-149">System. URI</span><span class="sxs-lookup"><span data-stu-id="61883-149">System.Uri</span></span>

### <span data-ttu-id="61883-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="61883-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="61883-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="61883-151">OUTPUTS</span></span>

### <span data-ttu-id="61883-152">System. object</span><span class="sxs-lookup"><span data-stu-id="61883-152">System.Object</span></span>

## <span data-ttu-id="61883-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="61883-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61883-154">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="61883-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="61883-155">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="61883-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="61883-156">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="61883-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="61883-157">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="61883-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="61883-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="61883-158">RELATED LINKS</span></span>

[<span data-ttu-id="61883-159">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="61883-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="61883-160">Install-script</span><span class="sxs-lookup"><span data-stu-id="61883-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="61883-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="61883-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="61883-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="61883-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="61883-163">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="61883-163">Uninstall-Script</span></span>](Uninstall-Script.md)
