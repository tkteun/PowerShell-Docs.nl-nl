---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 406675d8bde1b6b9a28913c09d5374393705f93b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251281"
---
# <span data-ttu-id="cdd3b-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="cdd3b-103">New-TemporaryFile</span></span>

## <span data-ttu-id="cdd3b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cdd3b-104">SYNOPSIS</span></span>
<span data-ttu-id="cdd3b-105">Hiermee maakt u een tijdelijk bestand.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-105">Creates a temporary file.</span></span>

## <span data-ttu-id="cdd3b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cdd3b-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cdd3b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cdd3b-107">DESCRIPTION</span></span>

<span data-ttu-id="cdd3b-108">Met deze cmdlet maakt u tijdelijke bestanden die u in scripts kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="cdd3b-109">`New-TemporaryFile`Met de cmdlet maakt u een leeg bestand met de `.tmp` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="cdd3b-110">Met deze cmdlet wordt het bestand met `tmp<NNNN>.tmp` `<NNNN>` een wille keurig hexadecimaal getal benoemt.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="cdd3b-111">Met de cmdlet maakt u het bestand in de map **temp** .</span><span class="sxs-lookup"><span data-stu-id="cdd3b-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="cdd3b-112">Deze cmdlet gebruikt de methode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) om de map **temp** te vinden.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="cdd3b-113">Deze methode controleert op het bestaan van omgevings variabelen in de volgende volg orde en maakt gebruik van het eerste pad dat is gevonden:</span><span class="sxs-lookup"><span data-stu-id="cdd3b-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="cdd3b-114">Op Windows-platforms:</span><span class="sxs-lookup"><span data-stu-id="cdd3b-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="cdd3b-115">Het pad dat is opgegeven door de variabele TMP-omgeving.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="cdd3b-116">Het pad dat wordt opgegeven door de omgevings variabele TEMP.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="cdd3b-117">Het pad dat is opgegeven door de omgevings variabele USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="cdd3b-118">De Windows-map.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-118">The Windows directory.</span></span>

- <span data-ttu-id="cdd3b-119">Op niet-Windows-platforms: gebruikt het pad dat is opgegeven door de omgevings variabele TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="cdd3b-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cdd3b-120">EXAMPLES</span></span>

### <span data-ttu-id="cdd3b-121">Voor beeld 1: een tijdelijk bestand maken</span><span class="sxs-lookup"><span data-stu-id="cdd3b-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="cdd3b-122">Met deze opdracht wordt een `.tmp` bestand in de tijdelijke map gegenereerd en wordt een verwijzing naar het bestand in de `$TempFile` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="cdd3b-123">U kunt dit bestand later in uw script gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="cdd3b-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cdd3b-124">PARAMETERS</span></span>

### <span data-ttu-id="cdd3b-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cdd3b-125">-Confirm</span></span>

<span data-ttu-id="cdd3b-126">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cdd3b-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cdd3b-127">-WhatIf</span></span>

<span data-ttu-id="cdd3b-128">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cdd3b-129">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cdd3b-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cdd3b-130">CommonParameters</span></span>

<span data-ttu-id="cdd3b-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cdd3b-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cdd3b-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="cdd3b-133">INPUTS</span></span>

## <span data-ttu-id="cdd3b-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cdd3b-134">OUTPUTS</span></span>

### <span data-ttu-id="cdd3b-135">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="cdd3b-135">System.IO.FileInfo</span></span>

<span data-ttu-id="cdd3b-136">Met deze cmdlet wordt een **file info** -object geretourneerd dat het tijdelijke bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cdd3b-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="cdd3b-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cdd3b-137">NOTES</span></span>

## <span data-ttu-id="cdd3b-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cdd3b-138">RELATED LINKS</span></span>

