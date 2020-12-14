---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705895"
---
# <span data-ttu-id="2cf18-102">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="2cf18-102">Invoke-History</span></span>

## <span data-ttu-id="2cf18-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2cf18-103">SYNOPSIS</span></span>
<span data-ttu-id="2cf18-104">Voert opdrachten uit vanuit de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-104">Runs commands from the session history.</span></span>

## <span data-ttu-id="2cf18-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2cf18-105">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2cf18-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2cf18-106">DESCRIPTION</span></span>

<span data-ttu-id="2cf18-107">De `Invoke-History` cmdlet voert opdrachten uit vanuit de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-107">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="2cf18-108">U kunt objecten die de opdrachten vertegenwoordigen van Get-History door geven `Invoke-History` , of u kunt opdrachten in de huidige geschiedenis identificeren met behulp van hun **id-** nummer.</span><span class="sxs-lookup"><span data-stu-id="2cf18-108">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="2cf18-109">Gebruik de cmdlet om het id-nummer van een opdracht te vinden `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="2cf18-109">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="2cf18-110">De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="2cf18-110">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="2cf18-111">Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="2cf18-111">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="2cf18-112">Deze cmdlet werkt alleen met de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-112">This cmdlet only works with the session history.</span></span> <span data-ttu-id="2cf18-113">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2cf18-113">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="2cf18-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2cf18-114">EXAMPLES</span></span>

### <span data-ttu-id="2cf18-115">Voor beeld 1: de meest recente opdracht in de geschiedenis uitvoeren</span><span class="sxs-lookup"><span data-stu-id="2cf18-115">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="2cf18-116">In dit voor beeld wordt de laatste, of meest recente, opdracht uitgevoerd in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-116">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="2cf18-117">U kunt deze opdracht afkorten als `r` de alias voor `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="2cf18-117">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="2cf18-118">Voor beeld 2: Voer de opdracht uit met een opgegeven ID</span><span class="sxs-lookup"><span data-stu-id="2cf18-118">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="2cf18-119">In dit voor beeld wordt de opdracht uitgevoerd in de sessie geschiedenis met de **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="2cf18-119">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="2cf18-120">Omdat de naam van de para meter **id** optioneel is, kunt u deze opdracht als volgt afkorten: `Invoke-History 132` , `ihy 132` of `r 132` .</span><span class="sxs-lookup"><span data-stu-id="2cf18-120">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="2cf18-121">Voor beeld 3: Voer de meest recente opdracht uit met behulp van de opdracht tekst</span><span class="sxs-lookup"><span data-stu-id="2cf18-121">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="2cf18-122">In dit voor beeld wordt de meest recente `Get-Process` opdracht uitgevoerd in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-122">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="2cf18-123">Wanneer u tekens voor de para meter **id** typt, `Invoke-History` wordt de eerste opdracht uitgevoerd die overeenkomt met het patroon, te beginnen met de meest recente opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2cf18-123">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="2cf18-124">Joker tekens zijn niet hoofdletter gevoelig, maar het patroon komt overeen met het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="2cf18-124">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="2cf18-125">Voor beeld 4: een reeks opdrachten uit de geschiedenis uitvoeren</span><span class="sxs-lookup"><span data-stu-id="2cf18-125">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="2cf18-126">In dit voor beeld worden de opdrachten 16 tot en met 24 uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2cf18-126">This example runs commands 16 through 24.</span></span> <span data-ttu-id="2cf18-127">Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.</span><span class="sxs-lookup"><span data-stu-id="2cf18-127">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="2cf18-128">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="2cf18-128">Example 5</span></span>

<span data-ttu-id="2cf18-129">In dit voor beeld worden de zeven opdrachten uitgevoerd in de geschiedenis die eindigen op de opdracht 255 (249 tot en met 255).</span><span class="sxs-lookup"><span data-stu-id="2cf18-129">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="2cf18-130">De cmdlet wordt gebruikt `Get-History` om de opdrachten op te halen.</span><span class="sxs-lookup"><span data-stu-id="2cf18-130">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="2cf18-131">Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.</span><span class="sxs-lookup"><span data-stu-id="2cf18-131">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="2cf18-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2cf18-132">PARAMETERS</span></span>

### <span data-ttu-id="2cf18-133">-Id</span><span class="sxs-lookup"><span data-stu-id="2cf18-133">-Id</span></span>

<span data-ttu-id="2cf18-134">Hiermee geeft u de **id** op van een opdracht in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-134">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="2cf18-135">U kunt het **id-** nummer van de opdracht of de eerste paar tekens van de opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="2cf18-135">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="2cf18-136">Als u tekens typt, `Invoke-History` komt het eerst overeen met de meest recente opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2cf18-136">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="2cf18-137">Als u deze para meter weglaat, `Invoke-History` wordt de laatste of meest recente opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2cf18-137">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="2cf18-138">Gebruik de cmdlet om het **id-** nummer van een opdracht te vinden `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="2cf18-138">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

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

### <span data-ttu-id="2cf18-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2cf18-139">-Confirm</span></span>

<span data-ttu-id="2cf18-140">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2cf18-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2cf18-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2cf18-141">-WhatIf</span></span>

<span data-ttu-id="2cf18-142">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2cf18-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2cf18-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2cf18-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2cf18-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2cf18-144">CommonParameters</span></span>

<span data-ttu-id="2cf18-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2cf18-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2cf18-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2cf18-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2cf18-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="2cf18-147">INPUTS</span></span>

### <span data-ttu-id="2cf18-148">System. String</span><span class="sxs-lookup"><span data-stu-id="2cf18-148">System.String</span></span>

<span data-ttu-id="2cf18-149">U kunt een geschiedenis **-id** door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2cf18-149">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="2cf18-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2cf18-150">OUTPUTS</span></span>

### <span data-ttu-id="2cf18-151">Geen</span><span class="sxs-lookup"><span data-stu-id="2cf18-151">None</span></span>

<span data-ttu-id="2cf18-152">Met deze cmdlet wordt geen uitvoer gegenereerd, maar de uitvoer kan worden gegenereerd door de opdrachten die worden `Invoke-History` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2cf18-152">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="2cf18-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2cf18-153">NOTES</span></span>

<span data-ttu-id="2cf18-154">De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="2cf18-154">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="2cf18-155">De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2cf18-155">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="2cf18-156">Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2cf18-156">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="2cf18-157">Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2cf18-157">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="2cf18-158">U kunt ook verwijzen naar `Invoke-History` de ingebouwde aliassen `r` en `ihy` .</span><span class="sxs-lookup"><span data-stu-id="2cf18-158">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="2cf18-159">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2cf18-159">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="2cf18-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2cf18-160">RELATED LINKS</span></span>

[<span data-ttu-id="2cf18-161">Toevoegen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="2cf18-161">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="2cf18-162">Wissen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="2cf18-162">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="2cf18-163">Get-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="2cf18-163">Get-History</span></span>](Get-History.md)

