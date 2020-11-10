---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 846aca6974190863a073773fe5148f0c57d77dc3
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388192"
---
# <span data-ttu-id="389b6-103">Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="389b6-103">Export-ODataEndpointProxy</span></span>

## <span data-ttu-id="389b6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="389b6-104">SYNOPSIS</span></span>
<span data-ttu-id="389b6-105">Genereert een module die cmdlets bevat voor het beheren van een OData-eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-105">Generates a module that contains cmdlets to manage an OData endpoint.</span></span>

## <span data-ttu-id="389b6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="389b6-106">SYNTAX</span></span>

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="389b6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="389b6-107">DESCRIPTION</span></span>

<span data-ttu-id="389b6-108">De `Export-ODataEndpointProxy` cmdlet gebruikt de meta gegevens van een OData-eind punt om een module te genereren die cmdlets bevat die u kunt gebruiken voor het beheren van het odata-eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-108">The `Export-ODataEndpointProxy` cmdlet uses the metadata of an OData endpoint to generate a module that contains cmdlets you can use to manage that OData endpoint.</span></span> <span data-ttu-id="389b6-109">De module is gebaseerd op CDXML.</span><span class="sxs-lookup"><span data-stu-id="389b6-109">The module is based on CDXML.</span></span> <span data-ttu-id="389b6-110">Nadat deze cmdlet de module heeft gegenereerd, wordt die module opgeslagen in het pad en de bestands naam die is opgegeven door de para meter **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="389b6-110">After this cmdlet generates the module, it saves that module to the path and file name specified by the **OutputModule** parameter.</span></span>

<span data-ttu-id="389b6-111">`Export-ODataEndpointProxy` genereert cmdlets voor maken, lezen, bijwerken en verwijderen (ruwe) bewerkingen, niet-ruwe acties en koppelings manipulatie.</span><span class="sxs-lookup"><span data-stu-id="389b6-111">`Export-ODataEndpointProxy` generates cmdlets for create, read, update, and delete (CRUD) operations, non-CRUD actions, and association manipulation.</span></span>

<span data-ttu-id="389b6-112">`Export-ODataEndpointProxy` Hiermee wordt één CDXML-bestand per eindpunt resource gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="389b6-112">`Export-ODataEndpointProxy` generates one CDXML file per endpoint resource.</span></span> <span data-ttu-id="389b6-113">U kunt deze CDXML-bestanden bewerken nadat de module is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="389b6-113">You can edit these CDXML files after the module is generated.</span></span> <span data-ttu-id="389b6-114">Als u bijvoorbeeld de naam van de zelfstandig naam woord of de werk woorden wilt wijzigen van de cmdlets die u wilt uitlijnen met de naamgevings richtlijnen voor Windows Power shell-cmdlets, kunt u het bestand wijzigen.</span><span class="sxs-lookup"><span data-stu-id="389b6-114">For example, if you want to change the noun or verb names of the cmdlets to align with Windows PowerShell cmdlet naming guidelines, you can modify the file.</span></span>

<span data-ttu-id="389b6-115">Elke cmdlet in een gegenereerde module moet een **ConnectionURI** -para meter bevatten om verbinding te maken met het eind punt dat door de module wordt beheerd.</span><span class="sxs-lookup"><span data-stu-id="389b6-115">Every cmdlet in a generated module must include a **ConnectionURI** parameter in order to connect to the endpoint that the module manages.</span></span>

## <span data-ttu-id="389b6-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="389b6-116">EXAMPLES</span></span>

### <span data-ttu-id="389b6-117">Voor beeld 1: een module genereren voor het beheren van een retail-webservice-eind punt</span><span class="sxs-lookup"><span data-stu-id="389b6-117">Example 1: Generate a module to manage a retail web service endpoint</span></span>

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

<span data-ttu-id="389b6-118">Met deze opdracht wordt een module gegenereerd voor het beheren van een retail service-eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-118">This command generates a module to manage a retail service endpoint.</span></span> <span data-ttu-id="389b6-119">De opdracht geeft de URI van het eind punt en de URI van de meta gegevens van het eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-119">The command specifies the URI of the endpoint and the URI of the endpoint metadata.</span></span> <span data-ttu-id="389b6-120">De opdracht biedt ook een uitvoerpad en script module naam als de waarde van de para meter **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="389b6-120">The command also provides an output path and script module name as the value of the **OutputModule** parameter.</span></span> <span data-ttu-id="389b6-121">Voor de waarde van de para meter **ResourceNameMapping** biedt de opdracht een hash-tabel waarmee de naam van de resource verzameling wordt toegewezen aan het gewenste zelfstandige woord voor de cmdlet-Set.</span><span class="sxs-lookup"><span data-stu-id="389b6-121">For the value of the **ResourceNameMapping** parameter, the command provides a hashtable that maps the resource collection name to the desired noun for the cmdlet set.</span></span> <span data-ttu-id="389b6-122">In dit voor beeld zijn producten de naam van de resource verzameling en de **handels** plaats is het zelfstandige zelfstandig.</span><span class="sxs-lookup"><span data-stu-id="389b6-122">In this example, Products is the resource collection name and **Merchandise** is the noun.</span></span> <span data-ttu-id="389b6-123">Als u verbindingen met niet-SSL-sites, in plaats van HTTPS, wilt toestaan, voegt u de para meter **AllowUnsecureConnection** toe.</span><span class="sxs-lookup"><span data-stu-id="389b6-123">To allow connections to non-SSL sites, HTTP, as opposed to HTTPS, add the **AllowUnsecureConnection** parameter.</span></span>

## <span data-ttu-id="389b6-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="389b6-124">PARAMETERS</span></span>

### <span data-ttu-id="389b6-125">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="389b6-125">-AllowClobber</span></span>

<span data-ttu-id="389b6-126">Geeft aan dat deze cmdlet een bestaande module vervangt.</span><span class="sxs-lookup"><span data-stu-id="389b6-126">Indicates that this cmdlet replaces an existing module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-127">-AllowUnsecureConnection</span><span class="sxs-lookup"><span data-stu-id="389b6-127">-AllowUnsecureConnection</span></span>

<span data-ttu-id="389b6-128">Geeft aan dat deze module verbinding kan maken met Uri's die niet met SSL zijn beveiligd.</span><span class="sxs-lookup"><span data-stu-id="389b6-128">Indicates that this module can connect to URIs that are not SSL-secured.</span></span> <span data-ttu-id="389b6-129">De module kan HTTP-sites naast HTTPS-sites beheren.</span><span class="sxs-lookup"><span data-stu-id="389b6-129">The module can manage HTTP sites in addition to HTTPS sites.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-130">-CmdletAdapter</span><span class="sxs-lookup"><span data-stu-id="389b6-130">-CmdletAdapter</span></span>

<span data-ttu-id="389b6-131">Hiermee geeft u de cmdlet-adapter op.</span><span class="sxs-lookup"><span data-stu-id="389b6-131">Specifies the cmdlet adapter.</span></span> <span data-ttu-id="389b6-132">De acceptabele waarden voor deze para meter zijn: ODataAdapter en NetworkControllerAdapter.</span><span class="sxs-lookup"><span data-stu-id="389b6-132">The acceptable values for this parameter are: ODataAdapter and NetworkControllerAdapter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-133">-CreateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="389b6-133">-CreateRequestMethod</span></span>

<span data-ttu-id="389b6-134">Hiermee geeft u de aanvraag methode op.</span><span class="sxs-lookup"><span data-stu-id="389b6-134">Specifies the request method.</span></span> <span data-ttu-id="389b6-135">De acceptabele waarden voor deze para meter zijn: PUT, POST en PATCH.</span><span class="sxs-lookup"><span data-stu-id="389b6-135">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="389b6-136">-Credential</span></span>

<span data-ttu-id="389b6-137">Hiermee geeft u een gebruikers account op dat toegang heeft tot het OData-eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-137">Specifies a user account that has access to the OData endpoint.</span></span> <span data-ttu-id="389b6-138">De standaard waarde is de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="389b6-138">The default value is the current user.</span></span> <span data-ttu-id="389b6-139">Als op een externe computer Windows Vista of een latere versie van het Windows-besturings systeem wordt uitgevoerd, vraagt de cmdlet u om referenties.</span><span class="sxs-lookup"><span data-stu-id="389b6-139">If a remote computer runs Windows Vista or a later release of the Windows operating system, the cmdlet prompts you for credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-140">-CustomData</span><span class="sxs-lookup"><span data-stu-id="389b6-140">-CustomData</span></span>

<span data-ttu-id="389b6-141">Hiermee geeft u een hash-tabel met aangepaste gegevens op.</span><span class="sxs-lookup"><span data-stu-id="389b6-141">Specifies a hash table of custom data.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-142">-Force</span><span class="sxs-lookup"><span data-stu-id="389b6-142">-Force</span></span>

<span data-ttu-id="389b6-143">Geeft aan dat deze cmdlet een bestaande gegenereerde module met dezelfde naam overschrijft in een bestaande `Modules` map.</span><span class="sxs-lookup"><span data-stu-id="389b6-143">Indicates that this cmdlet overwrites an existing generated module of the same name in an existing `Modules` folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-144">-Headers</span><span class="sxs-lookup"><span data-stu-id="389b6-144">-Headers</span></span>

<span data-ttu-id="389b6-145">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="389b6-145">Specifies the headers of the web request.</span></span> <span data-ttu-id="389b6-146">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="389b6-146">Enter a hash table or dictionary.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-147">-MetadataUri</span><span class="sxs-lookup"><span data-stu-id="389b6-147">-MetadataUri</span></span>

<span data-ttu-id="389b6-148">Hiermee geeft u de URI op van de meta gegevens van het eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-148">Specifies the URI of the metadata of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-149">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="389b6-149">-OutputModule</span></span>

<span data-ttu-id="389b6-150">Hiermee geeft u het pad en de module naam op waarmee deze cmdlet de gegenereerde module van proxy opdrachten opslaat.</span><span class="sxs-lookup"><span data-stu-id="389b6-150">Specifies the path and module name to which this cmdlet saves the generated module of proxy commands.</span></span>

<span data-ttu-id="389b6-151">Met deze cmdlet worden een binaire module, een module manifest en een opmaak bestand, indien van toepassing, gekopieerd naar de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="389b6-151">This cmdlet copies a binary module, module manifest, and formatting file, if applicable, to the specified folder.</span></span> <span data-ttu-id="389b6-152">Als u alleen de naam van de module opgeeft, wordt `Export-ODataEndpointProxy` de module opgeslagen in de `$home\Documents\WindowsPowerShell\Modules` map.</span><span class="sxs-lookup"><span data-stu-id="389b6-152">If you specify only the name of the module, `Export-ODataEndpointProxy` saves the module in the `$home\Documents\WindowsPowerShell\Modules` folder.</span></span> <span data-ttu-id="389b6-153">Als u een pad opgeeft, maakt de cmdlet de map module in dat pad.</span><span class="sxs-lookup"><span data-stu-id="389b6-153">If you specify a path, the cmdlet creates the module folder in that path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-154">-ResourceNameMapping</span><span class="sxs-lookup"><span data-stu-id="389b6-154">-ResourceNameMapping</span></span>

<span data-ttu-id="389b6-155">Hiermee geeft u een hashtabel op die toewijzingen bevat waarmee u de gegenereerde cmdlets kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="389b6-155">Specifies a hashtable that contains mappings that let you customize the generated cmdlets.</span></span> <span data-ttu-id="389b6-156">In deze hashtabel is de naam van de resource verzameling de sleutel.</span><span class="sxs-lookup"><span data-stu-id="389b6-156">In this hashtable, the resource collection name is the key.</span></span> <span data-ttu-id="389b6-157">De gewenste zelfstandige cmdlet is de waarde.</span><span class="sxs-lookup"><span data-stu-id="389b6-157">The desired cmdlet noun is the value.</span></span>

<span data-ttu-id="389b6-158">In de tabel hash `@{Products = 'Merchandise'}` is bijvoorbeeld de naam **Products** van de resource verzameling die fungeert als de sleutel.</span><span class="sxs-lookup"><span data-stu-id="389b6-158">For example, in the hash table `@{Products = 'Merchandise'}`, **Products** is the resource collection name that serves as the key.</span></span> <span data-ttu-id="389b6-159">**Merchandisen** is de resulterende cmdlet-zelfstandig naam.</span><span class="sxs-lookup"><span data-stu-id="389b6-159">**Merchandise** is the resulting cmdlet noun.</span></span> <span data-ttu-id="389b6-160">De gegenereerde cmdlet-namen kunnen mogelijk niet worden uitgelijnd met de naamgevings richtlijnen voor Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="389b6-160">The generated cmdlet names might not align to Windows PowerShell cmdlet naming guidelines.</span></span> <span data-ttu-id="389b6-161">U kunt het resource CDXML-bestand wijzigen om de namen van de cmdlets te wijzigen nadat deze cmdlet de module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="389b6-161">You can modify the resource CDXML file to change the cmdlet names after this cmdlet creates the module.</span></span> <span data-ttu-id="389b6-162">Zie voor meer informatie [sterk aanbevolen ontwikkel richtlijnen](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span><span class="sxs-lookup"><span data-stu-id="389b6-162">For more information, see [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-163">-UpdateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="389b6-163">-UpdateRequestMethod</span></span>

<span data-ttu-id="389b6-164">Hiermee geeft u de methode voor het bijwerken van aanvragen.</span><span class="sxs-lookup"><span data-stu-id="389b6-164">Specifies the update request method.</span></span> <span data-ttu-id="389b6-165">De acceptabele waarden voor deze para meter zijn: PUT, POST en PATCH.</span><span class="sxs-lookup"><span data-stu-id="389b6-165">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-166">-URI</span><span class="sxs-lookup"><span data-stu-id="389b6-166">-Uri</span></span>

<span data-ttu-id="389b6-167">Hiermee geeft u de URI van het eind punt.</span><span class="sxs-lookup"><span data-stu-id="389b6-167">Specifies the URI of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="389b6-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="389b6-168">-Confirm</span></span>

<span data-ttu-id="389b6-169">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="389b6-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="389b6-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="389b6-170">-WhatIf</span></span>

<span data-ttu-id="389b6-171">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="389b6-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="389b6-172">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="389b6-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="389b6-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="389b6-173">CommonParameters</span></span>

<span data-ttu-id="389b6-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="389b6-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="389b6-175">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="389b6-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="389b6-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="389b6-176">INPUTS</span></span>

## <span data-ttu-id="389b6-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="389b6-177">OUTPUTS</span></span>

## <span data-ttu-id="389b6-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="389b6-178">NOTES</span></span>

## <span data-ttu-id="389b6-179">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="389b6-179">RELATED LINKS</span></span>

<span data-ttu-id="389b6-180">[OData-bibliotheek](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="389b6-180">[OData Library](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span></span>

[<span data-ttu-id="389b6-181">Wat is het OData-Protocol?</span><span class="sxs-lookup"><span data-stu-id="389b6-181">What is the OData Protocol?</span></span>](https://www.odata.org/)

[<span data-ttu-id="389b6-182">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="389b6-182">Invoke-RestMethod</span></span>](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
