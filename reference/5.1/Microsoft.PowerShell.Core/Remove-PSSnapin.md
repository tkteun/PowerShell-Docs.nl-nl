---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250146"
---
# <span data-ttu-id="2f65a-103">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2f65a-103">Remove-PSSnapin</span></span>

## <span data-ttu-id="2f65a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2f65a-104">SYNOPSIS</span></span>
<span data-ttu-id="2f65a-105">Hiermee verwijdert u de Windows Power shell-modules uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-105">Removes Windows PowerShell snap-ins from the current session.</span></span>

## <span data-ttu-id="2f65a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2f65a-106">SYNTAX</span></span>

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2f65a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2f65a-107">DESCRIPTION</span></span>
<span data-ttu-id="2f65a-108">De cmdlet **Remove-PSSnapin** verwijdert een Windows Power shell-module uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-108">The **Remove-PSSnapin** cmdlet removes a Windows PowerShell snap-in from the current session.</span></span>
<span data-ttu-id="2f65a-109">U kunt deze gebruiken om modules die u hebt toegevoegd aan Windows Power shell te verwijderen, u kunt deze cmdlet niet gebruiken om de modules te verwijderen die met Windows Power shell zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2f65a-109">You can use it to remove snap-ins that you have added to Windows PowerShell You cannot use this cmdlet to remove the snap-ins that are installed with Windows PowerShell.</span></span>

<span data-ttu-id="2f65a-110">Nadat u een module uit de huidige sessie hebt verwijderd, wordt de module nog steeds geladen, maar zijn de cmdlets en providers in de module niet meer beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-110">After you remove a snap-in from the current session, the snap-in is still loaded, but the cmdlets and providers in the snap-in are no longer available in the session.</span></span>

## <span data-ttu-id="2f65a-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2f65a-111">EXAMPLES</span></span>

### <span data-ttu-id="2f65a-112">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="2f65a-112">Example 1: Remove a snap-in</span></span>

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

<span data-ttu-id="2f65a-113">Met deze opdracht wordt de **micro soft. Exchange** -module verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-113">This command removes the **Microsoft.Exchange** snap-in from the current session.</span></span>
<span data-ttu-id="2f65a-114">Wanneer de opdracht is voltooid, zijn de cmdlets en providers die door de module worden ondersteund, niet beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-114">When the command is complete, the cmdlets and providers that the snap-in supported are not available in the session.</span></span>

### <span data-ttu-id="2f65a-115">Voor beeld 2: modules verwijderen door gebruik te maken van namen met de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="2f65a-115">Example 2: Remove snap-ins by using names with the pipeline</span></span>

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

<span data-ttu-id="2f65a-116">Met deze opdracht verwijdert u de Windows Power shell-modules die namen hebben die beginnen met smp vanuit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-116">This command removes the Windows PowerShell snap-ins that have names that start with smp from the current session.</span></span>

<span data-ttu-id="2f65a-117">De opdracht maakt gebruik van de cmdlet **Get-PSSnapin** om objecten op te halen die de modules vertegenwoordigen. De pijplijn operator (|) verzendt de resultaten naar de cmdlet **Remove-PSSnapin** , die deze uit de sessie verwijdert.</span><span class="sxs-lookup"><span data-stu-id="2f65a-117">The command uses the **Get-PSSnapin** cmdlet to get objects that represent the snap-ins. The pipeline operator (|) sends the results to the **Remove-PSSnapin** cmdlet, which removes them from the session.</span></span>
<span data-ttu-id="2f65a-118">De providers en cmdlets die in deze invoeg toepassing worden ondersteund, zijn niet meer beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-118">The providers and cmdlets that this snap-in supports are no longer available in the session.</span></span>

<span data-ttu-id="2f65a-119">Wanneer u objecten pipet om **-PSSnapin te verwijderen** , worden de namen van de objecten gekoppeld aan de para meter *name* , waarmee objecten van de pijp lijn met een **naam** eigenschap worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="2f65a-119">When you pipe objects to **Remove-PSSnapin** , the names of the objects are associated with the *Name* parameter, which accepts objects from the pipeline that have a **Name** property.</span></span>

### <span data-ttu-id="2f65a-120">Voor beeld 3: modules verwijderen met behulp van namen</span><span class="sxs-lookup"><span data-stu-id="2f65a-120">Example 3: Remove snap-ins by using names</span></span>

```
PS C:\> Remove-PSSnapin -Name *event*
```

<span data-ttu-id="2f65a-121">Met deze opdracht worden alle Windows Power shell-modules verwijderd met namen die gebeurtenis bevatten.</span><span class="sxs-lookup"><span data-stu-id="2f65a-121">This command removes all Windows PowerShell snap-ins that have names that include event.</span></span>

## <span data-ttu-id="2f65a-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f65a-122">PARAMETERS</span></span>

### <span data-ttu-id="2f65a-123">-Name</span><span class="sxs-lookup"><span data-stu-id="2f65a-123">-Name</span></span>
<span data-ttu-id="2f65a-124">Hiermee geeft u de namen van Windows Power shell-modules die u wilt verwijderen uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-124">Specifies the names of Windows PowerShell snap-ins to remove from the current session.</span></span>
<span data-ttu-id="2f65a-125">Joker tekens (\*) zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2f65a-125">Wildcard characters (\*) are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f65a-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2f65a-126">-PassThru</span></span>
<span data-ttu-id="2f65a-127">Retourneert een object dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2f65a-127">Returns an object that represents the snap-in.</span></span>
<span data-ttu-id="2f65a-128">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2f65a-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2f65a-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f65a-129">-Confirm</span></span>
<span data-ttu-id="2f65a-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2f65a-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2f65a-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f65a-131">-WhatIf</span></span>
<span data-ttu-id="2f65a-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2f65a-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2f65a-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f65a-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2f65a-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f65a-134">CommonParameters</span></span>
<span data-ttu-id="2f65a-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f65a-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f65a-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f65a-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="2f65a-137">INPUTS</span></span>

### <span data-ttu-id="2f65a-138">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="2f65a-138">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="2f65a-139">U kunt een module-object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f65a-139">You can pipe a snap-in object to this cmdlet.</span></span>

## <span data-ttu-id="2f65a-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2f65a-140">OUTPUTS</span></span>

### <span data-ttu-id="2f65a-141">Geen, System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="2f65a-141">None, System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="2f65a-142">Met deze cmdlet wordt een **System. Management. Automation. PSSnapInInfo** -object gegenereerd dat de module vertegenwoordigt, als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2f65a-142">This cmdlet generates a **System.Management.Automation.PSSnapInInfo** object that represents the snap-in, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="2f65a-143">Standaard wordt met **Remove-PSSnapin** geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2f65a-143">By default, **Remove-PSSnapin** does not generate any output.</span></span>

## <span data-ttu-id="2f65a-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2f65a-144">NOTES</span></span>

* <span data-ttu-id="2f65a-145">**Remove-PSSnapin** controleert de versie van Windows Power shell niet voordat een module uit de sessie wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f65a-145">**Remove-PSSnapin** does not check the version of Windows PowerShell before removing a snap-in from the session.</span></span> <span data-ttu-id="2f65a-146">Als een module niet kan worden verwijderd, wordt een waarschuwing weer gegeven en mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2f65a-146">If a snap-in cannot be removed, a warning appears and the command fails.</span></span>
* <span data-ttu-id="2f65a-147">**Remove-PSSnapin** is alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2f65a-147">**Remove-PSSnapin** affects only the current session.</span></span> <span data-ttu-id="2f65a-148">Als u een Add-PSSnapin-opdracht aan uw Windows Power shell-profiel hebt toegevoegd, moet u de opdracht verwijderen om de module uit toekomstige sessies te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2f65a-148">If you have added an Add-PSSnapin command to your Windows PowerShell profile, you should delete the command to remove the snap-in from future sessions.</span></span> <span data-ttu-id="2f65a-149">Typ voor instructies `Get-Help about_Profiles` .</span><span class="sxs-lookup"><span data-stu-id="2f65a-149">For instructions, type `Get-Help about_Profiles`.</span></span>

## <span data-ttu-id="2f65a-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2f65a-150">RELATED LINKS</span></span>

[<span data-ttu-id="2f65a-151">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2f65a-151">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="2f65a-152">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="2f65a-152">Get-PSSnapin</span></span>](Get-PSSnapin.md)
