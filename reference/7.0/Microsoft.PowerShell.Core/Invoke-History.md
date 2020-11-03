---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: baedf2be8bb3fca2223c65c33beb21f01ed84969
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249775"
---
# <span data-ttu-id="a55b4-103">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="a55b4-103">Invoke-History</span></span>

## <span data-ttu-id="a55b4-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a55b4-104">SYNOPSIS</span></span>
<span data-ttu-id="a55b4-105">Voert opdrachten uit vanuit de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-105">Runs commands from the session history.</span></span>

## <span data-ttu-id="a55b4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a55b4-106">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a55b4-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a55b4-107">DESCRIPTION</span></span>

<span data-ttu-id="a55b4-108">De `Invoke-History` cmdlet voert opdrachten uit vanuit de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-108">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="a55b4-109">U kunt objecten die de opdrachten vertegenwoordigen van Get-History door geven `Invoke-History` , of u kunt opdrachten in de huidige geschiedenis identificeren met behulp van hun **id-** nummer.</span><span class="sxs-lookup"><span data-stu-id="a55b4-109">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="a55b4-110">Gebruik de cmdlet om het id-nummer van een opdracht te vinden `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="a55b4-110">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="a55b4-111">De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="a55b4-111">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="a55b4-112">Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="a55b4-112">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="a55b4-113">Deze cmdlet werkt alleen met de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-113">This cmdlet only works with the session history.</span></span> <span data-ttu-id="a55b4-114">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a55b4-114">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="a55b4-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a55b4-115">EXAMPLES</span></span>

### <span data-ttu-id="a55b4-116">Voor beeld 1: de meest recente opdracht in de geschiedenis uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a55b4-116">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="a55b4-117">In dit voor beeld wordt de laatste, of meest recente, opdracht uitgevoerd in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-117">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="a55b4-118">U kunt deze opdracht afkorten als `r` de alias voor `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="a55b4-118">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="a55b4-119">Voor beeld 2: Voer de opdracht uit met een opgegeven ID</span><span class="sxs-lookup"><span data-stu-id="a55b4-119">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="a55b4-120">In dit voor beeld wordt de opdracht uitgevoerd in de sessie geschiedenis met de **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="a55b4-120">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="a55b4-121">Omdat de naam van de para meter **id** optioneel is, kunt u deze opdracht als volgt afkorten: `Invoke-History 132` , `ihy 132` of `r 132` .</span><span class="sxs-lookup"><span data-stu-id="a55b4-121">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="a55b4-122">Voor beeld 3: Voer de meest recente opdracht uit met behulp van de opdracht tekst</span><span class="sxs-lookup"><span data-stu-id="a55b4-122">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="a55b4-123">In dit voor beeld wordt de meest recente `Get-Process` opdracht uitgevoerd in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-123">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="a55b4-124">Wanneer u tekens voor de para meter **id** typt, `Invoke-History` wordt de eerste opdracht uitgevoerd die overeenkomt met het patroon, te beginnen met de meest recente opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a55b4-124">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="a55b4-125">Joker tekens zijn niet hoofdletter gevoelig, maar het patroon komt overeen met het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="a55b4-125">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="a55b4-126">Voor beeld 4: een reeks opdrachten uit de geschiedenis uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a55b4-126">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="a55b4-127">In dit voor beeld worden de opdrachten 16 tot en met 24 uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a55b4-127">This example runs commands 16 through 24.</span></span> <span data-ttu-id="a55b4-128">Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.</span><span class="sxs-lookup"><span data-stu-id="a55b4-128">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="a55b4-129">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="a55b4-129">Example 5</span></span>

<span data-ttu-id="a55b4-130">In dit voor beeld worden de zeven opdrachten uitgevoerd in de geschiedenis die eindigen op de opdracht 255 (249 tot en met 255).</span><span class="sxs-lookup"><span data-stu-id="a55b4-130">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="a55b4-131">De cmdlet wordt gebruikt `Get-History` om de opdrachten op te halen.</span><span class="sxs-lookup"><span data-stu-id="a55b4-131">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="a55b4-132">Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.</span><span class="sxs-lookup"><span data-stu-id="a55b4-132">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="a55b4-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a55b4-133">PARAMETERS</span></span>

### <span data-ttu-id="a55b4-134">-Id</span><span class="sxs-lookup"><span data-stu-id="a55b4-134">-Id</span></span>

<span data-ttu-id="a55b4-135">Hiermee geeft u de **id** op van een opdracht in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-135">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="a55b4-136">U kunt het **id-** nummer van de opdracht of de eerste paar tekens van de opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="a55b4-136">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="a55b4-137">Als u tekens typt, `Invoke-History` komt het eerst overeen met de meest recente opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a55b4-137">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="a55b4-138">Als u deze para meter weglaat, `Invoke-History` wordt de laatste of meest recente opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a55b4-138">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="a55b4-139">Gebruik de cmdlet om het **id-** nummer van een opdracht te vinden `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="a55b4-139">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a55b4-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a55b4-140">-Confirm</span></span>

<span data-ttu-id="a55b4-141">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a55b4-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a55b4-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a55b4-142">-WhatIf</span></span>

<span data-ttu-id="a55b4-143">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a55b4-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a55b4-144">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a55b4-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a55b4-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a55b4-145">CommonParameters</span></span>

<span data-ttu-id="a55b4-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a55b4-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a55b4-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a55b4-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a55b4-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="a55b4-148">INPUTS</span></span>

### <span data-ttu-id="a55b4-149">System. String</span><span class="sxs-lookup"><span data-stu-id="a55b4-149">System.String</span></span>

<span data-ttu-id="a55b4-150">U kunt een geschiedenis **-id** door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a55b4-150">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="a55b4-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a55b4-151">OUTPUTS</span></span>

### <span data-ttu-id="a55b4-152">Geen</span><span class="sxs-lookup"><span data-stu-id="a55b4-152">None</span></span>

<span data-ttu-id="a55b4-153">Met deze cmdlet wordt geen uitvoer gegenereerd, maar de uitvoer kan worden gegenereerd door de opdrachten die worden `Invoke-History` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a55b4-153">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="a55b4-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a55b4-154">NOTES</span></span>

<span data-ttu-id="a55b4-155">De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="a55b4-155">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="a55b4-156">De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a55b4-156">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="a55b4-157">Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a55b4-157">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="a55b4-158">Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a55b4-158">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="a55b4-159">U kunt ook verwijzen naar `Invoke-History` de ingebouwde aliassen `r` en `ihy` .</span><span class="sxs-lookup"><span data-stu-id="a55b4-159">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="a55b4-160">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a55b4-160">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="a55b4-161">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a55b4-161">RELATED LINKS</span></span>

[<span data-ttu-id="a55b4-162">Toevoegen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="a55b4-162">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="a55b4-163">Wissen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="a55b4-163">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="a55b4-164">Get-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="a55b4-164">Get-History</span></span>](Get-History.md)
