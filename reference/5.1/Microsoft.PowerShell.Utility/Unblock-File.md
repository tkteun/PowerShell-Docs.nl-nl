---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 57c8c6f2ceda124b3dc89c363c6cf942680781ca
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344504"
---
# <span data-ttu-id="66a92-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="66a92-103">Unblock-File</span></span>

## <span data-ttu-id="66a92-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="66a92-104">SYNOPSIS</span></span>
<span data-ttu-id="66a92-105">De blok kering van bestanden die zijn gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="66a92-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="66a92-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="66a92-106">SYNTAX</span></span>

### <span data-ttu-id="66a92-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="66a92-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66a92-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="66a92-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="66a92-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="66a92-109">DESCRIPTION</span></span>

<span data-ttu-id="66a92-110">`Unblock-File`Met de cmdlet kunt u bestanden openen die zijn gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="66a92-110">The `Unblock-File` cmdlet lets you open files that were downloaded from the Internet.</span></span> <span data-ttu-id="66a92-111">Power shell-script bestanden die zijn gedownload van het Internet, worden gedeblokkeerd, zodat u ze kunt uitvoeren, zelfs wanneer het Power shell-uitvoerings beleid **RemoteSigned** is.</span><span class="sxs-lookup"><span data-stu-id="66a92-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="66a92-112">Deze bestanden worden standaard geblokkeerd om de computer te beschermen tegen niet-vertrouwde bestanden.</span><span class="sxs-lookup"><span data-stu-id="66a92-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="66a92-113">Voordat u de `Unblock-File` cmdlet gebruikt, controleert u het bestand en de bron en controleert u of het veilig is om te openen.</span><span class="sxs-lookup"><span data-stu-id="66a92-113">Before using the `Unblock-File` cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="66a92-114">Intern verwijdert de `Unblock-File` cmdlet de zone. id alternatieve gegevens stroom, met de waarde ' 3 ' om aan te geven dat deze is gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="66a92-114">Internally, the `Unblock-File` cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="66a92-115">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="66a92-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="66a92-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="66a92-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="66a92-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="66a92-117">EXAMPLES</span></span>

### <span data-ttu-id="66a92-118">Voor beeld 1: de blok kering van een bestand opheffen</span><span class="sxs-lookup"><span data-stu-id="66a92-118">Example 1: Unblock a file</span></span>

<span data-ttu-id="66a92-119">Met deze opdracht wordt het bestand PowerShellTips. chm gedeblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="66a92-119">This command unblocks the PowerShellTips.chm file.</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### <span data-ttu-id="66a92-120">Voor beeld 2: meerdere bestanden deblokkeren</span><span class="sxs-lookup"><span data-stu-id="66a92-120">Example 2: Unblock multiple files</span></span>

<span data-ttu-id="66a92-121">Met deze opdracht wordt de blok kering van alle bestanden in de map met de `C:\Downloads` naam Power shell opgeheven.</span><span class="sxs-lookup"><span data-stu-id="66a92-121">This command unblocks all of the files in the `C:\Downloads` directory whose names include "PowerShell".</span></span> <span data-ttu-id="66a92-122">Voer een opdracht zoals deze pas uit nadat u hebt gecontroleerd of alle bestanden veilig zijn.</span><span class="sxs-lookup"><span data-stu-id="66a92-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### <span data-ttu-id="66a92-123">Voor beeld 3: scripts zoeken en deblokkeren</span><span class="sxs-lookup"><span data-stu-id="66a92-123">Example 3: Find and unblock scripts</span></span>

<span data-ttu-id="66a92-124">Met deze opdracht wordt uitgelegd hoe u Power shell-scripts kunt vinden en deblokkeren.</span><span class="sxs-lookup"><span data-stu-id="66a92-124">This command shows how to find and unblock PowerShell scripts.</span></span>

<span data-ttu-id="66a92-125">In de eerste opdracht wordt de para meter **Stream** van de cmdlet *Get-item* gebruikt voor het ophalen van bestanden met de zone. id-stroom.</span><span class="sxs-lookup"><span data-stu-id="66a92-125">The first command uses the **Stream** parameter of the *Get-Item* cmdlet get files with the Zone.Identifier stream.</span></span>

<span data-ttu-id="66a92-126">Met de tweede opdracht wordt aangegeven wat er gebeurt wanneer u een geblokkeerd script uitvoert in een Power shell-sessie waarin het uitvoerings beleid is **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="66a92-126">The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="66a92-127">Het RemoteSigned-beleid voor komt dat u scripts kunt uitvoeren die van Internet worden gedownload, tenzij ze digitaal zijn ondertekend.</span><span class="sxs-lookup"><span data-stu-id="66a92-127">The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.</span></span>

<span data-ttu-id="66a92-128">De derde opdracht gebruikt de `Unblock-File` cmdlet om het script uit te blok keren zodat dit in de sessie kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a92-128">The third command uses the `Unblock-File` cmdlet to unblock the script so it can run in the session.</span></span>

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## <span data-ttu-id="66a92-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="66a92-129">PARAMETERS</span></span>

### <span data-ttu-id="66a92-130">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="66a92-130">-LiteralPath</span></span>

<span data-ttu-id="66a92-131">Hiermee geeft u de bestanden op die u wilt deblokkeren.</span><span class="sxs-lookup"><span data-stu-id="66a92-131">Specifies the files to unblock.</span></span> <span data-ttu-id="66a92-132">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="66a92-132">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="66a92-133">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="66a92-133">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="66a92-134">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="66a92-134">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="66a92-135">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="66a92-135">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="66a92-136">-Path</span><span class="sxs-lookup"><span data-stu-id="66a92-136">-Path</span></span>

<span data-ttu-id="66a92-137">Hiermee geeft u de bestanden op die u wilt deblokkeren.</span><span class="sxs-lookup"><span data-stu-id="66a92-137">Specifies the files to unblock.</span></span> <span data-ttu-id="66a92-138">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="66a92-138">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="66a92-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="66a92-139">-Confirm</span></span>

<span data-ttu-id="66a92-140">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="66a92-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="66a92-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="66a92-141">-WhatIf</span></span>

<span data-ttu-id="66a92-142">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="66a92-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="66a92-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a92-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="66a92-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66a92-144">CommonParameters</span></span>

<span data-ttu-id="66a92-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="66a92-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66a92-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66a92-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="66a92-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="66a92-147">INPUTS</span></span>

### <span data-ttu-id="66a92-148">System. String</span><span class="sxs-lookup"><span data-stu-id="66a92-148">System.String</span></span>

<span data-ttu-id="66a92-149">U kunt een bestandspad door sluizen naar `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="66a92-149">You can pipe a file path to `Unblock-File`.</span></span>

## <span data-ttu-id="66a92-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="66a92-150">OUTPUTS</span></span>

### <span data-ttu-id="66a92-151">Geen</span><span class="sxs-lookup"><span data-stu-id="66a92-151">None</span></span>

<span data-ttu-id="66a92-152">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="66a92-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="66a92-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="66a92-153">NOTES</span></span>

- <span data-ttu-id="66a92-154">De `Unblock-File` cmdlet werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="66a92-154">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="66a92-155">`Unblock-File` voert dezelfde bewerking uit als de knop voor het **opheffen van de blok kering** in het dialoog venster **Eigenschappen** in Verkenner.</span><span class="sxs-lookup"><span data-stu-id="66a92-155">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="66a92-156">Als u de `Unblock-File` cmdlet gebruikt voor een bestand dat niet is geblokkeerd, heeft de opdracht geen effect op het niet-geblokkeerde bestand en worden er geen fouten gegenereerd door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66a92-156">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="66a92-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="66a92-157">RELATED LINKS</span></span>

[<span data-ttu-id="66a92-158">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="66a92-158">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="66a92-159">Get-item</span><span class="sxs-lookup"><span data-stu-id="66a92-159">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="66a92-160">Out-file</span><span class="sxs-lookup"><span data-stu-id="66a92-160">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="66a92-161">Bestandssysteem provider</span><span class="sxs-lookup"><span data-stu-id="66a92-161">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
