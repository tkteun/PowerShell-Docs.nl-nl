---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705589"
---
# <span data-ttu-id="1b9bd-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="1b9bd-102">New-TemporaryFile</span></span>

## <span data-ttu-id="1b9bd-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1b9bd-103">SYNOPSIS</span></span>
<span data-ttu-id="1b9bd-104">Hiermee maakt u een tijdelijk bestand.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-104">Creates a temporary file.</span></span>

## <span data-ttu-id="1b9bd-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1b9bd-105">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1b9bd-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1b9bd-106">DESCRIPTION</span></span>

<span data-ttu-id="1b9bd-107">Met deze cmdlet maakt u tijdelijke bestanden die u in scripts kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-107">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="1b9bd-108">`New-TemporaryFile`Met de cmdlet maakt u een leeg bestand met de `.tmp` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-108">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="1b9bd-109">Met deze cmdlet wordt het bestand met `tmp<NNNN>.tmp` `<NNNN>` een wille keurig hexadecimaal getal benoemt.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-109">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="1b9bd-110">Met de cmdlet maakt u het bestand in de map **temp** .</span><span class="sxs-lookup"><span data-stu-id="1b9bd-110">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="1b9bd-111">Deze cmdlet gebruikt de methode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) om de map **temp** te vinden.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-111">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="1b9bd-112">Deze methode controleert op het bestaan van omgevings variabelen in de volgende volg orde en maakt gebruik van het eerste pad dat is gevonden:</span><span class="sxs-lookup"><span data-stu-id="1b9bd-112">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="1b9bd-113">Op Windows-platforms:</span><span class="sxs-lookup"><span data-stu-id="1b9bd-113">On Windows platforms:</span></span>

  1. <span data-ttu-id="1b9bd-114">Het pad dat is opgegeven door de variabele TMP-omgeving.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-114">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="1b9bd-115">Het pad dat wordt opgegeven door de omgevings variabele TEMP.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-115">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="1b9bd-116">Het pad dat is opgegeven door de omgevings variabele USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-116">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="1b9bd-117">De Windows-map.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-117">The Windows directory.</span></span>

- <span data-ttu-id="1b9bd-118">Op niet-Windows-platforms: gebruikt het pad dat is opgegeven door de omgevings variabele TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-118">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="1b9bd-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1b9bd-119">EXAMPLES</span></span>

### <span data-ttu-id="1b9bd-120">Voor beeld 1: een tijdelijk bestand maken</span><span class="sxs-lookup"><span data-stu-id="1b9bd-120">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="1b9bd-121">Met deze opdracht wordt een `.tmp` bestand in de tijdelijke map gegenereerd en wordt een verwijzing naar het bestand in de `$TempFile` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-121">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="1b9bd-122">U kunt dit bestand later in uw script gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-122">You can use this file later in your script.</span></span>

## <span data-ttu-id="1b9bd-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b9bd-123">PARAMETERS</span></span>

### <span data-ttu-id="1b9bd-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1b9bd-124">-Confirm</span></span>

<span data-ttu-id="1b9bd-125">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1b9bd-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1b9bd-126">-WhatIf</span></span>

<span data-ttu-id="1b9bd-127">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1b9bd-128">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1b9bd-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b9bd-129">CommonParameters</span></span>

<span data-ttu-id="1b9bd-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b9bd-131">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1b9bd-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="1b9bd-132">INPUTS</span></span>

## <span data-ttu-id="1b9bd-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1b9bd-133">OUTPUTS</span></span>

### <span data-ttu-id="1b9bd-134">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="1b9bd-134">System.IO.FileInfo</span></span>

<span data-ttu-id="1b9bd-135">Met deze cmdlet wordt een **file info** -object geretourneerd dat het tijdelijke bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1b9bd-135">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="1b9bd-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1b9bd-136">NOTES</span></span>

## <span data-ttu-id="1b9bd-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1b9bd-137">RELATED LINKS</span></span>

