---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250765"
---
# <span data-ttu-id="032fd-103">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="032fd-103">Restore-DscConfiguration</span></span>

## <span data-ttu-id="032fd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="032fd-104">SYNOPSIS</span></span>
<span data-ttu-id="032fd-105">Hiermee wordt de vorige configuratie van het knoop punt opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="032fd-105">Reapplies the previous configuration for the node.</span></span>

## <span data-ttu-id="032fd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="032fd-106">SYNTAX</span></span>

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="032fd-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="032fd-107">DESCRIPTION</span></span>
<span data-ttu-id="032fd-108">Met de cmdlet **Restore-DscConfiguration** wordt de vorige configuratie voor het knoop punt opnieuw toegepast als er een vorige configuratie bestaat.</span><span class="sxs-lookup"><span data-stu-id="032fd-108">The **Restore-DscConfiguration** cmdlet reapplies the previous configuration for the node, if a previous configuration exists.</span></span>
<span data-ttu-id="032fd-109">Geef computers op met behulp van Common Information Model (CIM)-sessies.</span><span class="sxs-lookup"><span data-stu-id="032fd-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="032fd-110">Als u geen doel computer opgeeft, herstelt de cmdlet de configuratie van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="032fd-110">If you do not specify a target computer, the cmdlet restores the configuration of the local computer.</span></span>
<span data-ttu-id="032fd-111">Als er geen eerdere configuratie voor een bepaald knoop punt is, retourneert deze cmdlet een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="032fd-111">If there is no previous configuration for a particular node, this cmdlet returns an error message.</span></span>

<span data-ttu-id="032fd-112">Deze cmdlet biedt geen ondersteuning voor de **confirm** -para meter.</span><span class="sxs-lookup"><span data-stu-id="032fd-112">This cmdlet does not support the **Confirm** parameter.</span></span>

## <span data-ttu-id="032fd-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="032fd-113">EXAMPLES</span></span>

### <span data-ttu-id="032fd-114">Voor beeld 1: de configuratie voor de lokale computer herstellen</span><span class="sxs-lookup"><span data-stu-id="032fd-114">Example 1: Restore the configuration for the local computer</span></span>

```
PS C:\> Restore-DscConfiguration
```

<span data-ttu-id="032fd-115">Met deze opdracht wordt de configuratie voor de lokale computer hersteld.</span><span class="sxs-lookup"><span data-stu-id="032fd-115">This command restores the configuration for the local computer.</span></span>

### <span data-ttu-id="032fd-116">Voor beeld 2: de configuratie herstellen voor een opgegeven computer</span><span class="sxs-lookup"><span data-stu-id="032fd-116">Example 2: Restore configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

<span data-ttu-id="032fd-117">In dit voor beeld wordt de configuratie hersteld op een computer die is opgegeven door een CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="032fd-117">This example restores configuration on a computer specified by a CIM session.</span></span>
<span data-ttu-id="032fd-118">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="032fd-118">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="032fd-119">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="032fd-119">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="032fd-120">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="032fd-120">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="032fd-121">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="032fd-121">The command prompts you for a password.</span></span>
<span data-ttu-id="032fd-122">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="032fd-122">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="032fd-123">Met de tweede opdracht wordt de configuratie teruggezet voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele $Session, in dit geval de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="032fd-123">The second command restores the configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="032fd-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="032fd-124">PARAMETERS</span></span>

### <span data-ttu-id="032fd-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="032fd-125">-AsJob</span></span>
<span data-ttu-id="032fd-126">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="032fd-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="032fd-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="032fd-127">-CimSession</span></span>
<span data-ttu-id="032fd-128">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="032fd-128">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="032fd-129">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet **New-CimSession** of **Get-CimSession** .</span><span class="sxs-lookup"><span data-stu-id="032fd-129">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="032fd-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="032fd-130">-ThrottleLimit</span></span>
<span data-ttu-id="032fd-131">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="032fd-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="032fd-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="032fd-132">-Confirm</span></span>
<span data-ttu-id="032fd-133">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="032fd-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="032fd-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="032fd-134">-WhatIf</span></span>
<span data-ttu-id="032fd-135">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="032fd-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="032fd-136">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="032fd-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="032fd-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="032fd-137">CommonParameters</span></span>
<span data-ttu-id="032fd-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="032fd-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="032fd-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="032fd-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="032fd-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="032fd-140">INPUTS</span></span>

## <span data-ttu-id="032fd-141">UITVOER</span><span class="sxs-lookup"><span data-stu-id="032fd-141">OUTPUTS</span></span>

## <span data-ttu-id="032fd-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="032fd-142">NOTES</span></span>

## <span data-ttu-id="032fd-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="032fd-143">RELATED LINKS</span></span>

[<span data-ttu-id="032fd-144">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="032fd-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="032fd-145">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="032fd-145">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="032fd-146">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="032fd-146">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="032fd-147">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="032fd-147">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="032fd-148">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="032fd-148">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
