---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 34e8d6edd7199921254a3835a9f13b6331c2d26e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253025"
---
# <span data-ttu-id="59fa9-103">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="59fa9-103">Write-Verbose</span></span>

## <span data-ttu-id="59fa9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="59fa9-104">SYNOPSIS</span></span>
<span data-ttu-id="59fa9-105">Schrijft tekst naar de uitgebreide berichten stroom.</span><span class="sxs-lookup"><span data-stu-id="59fa9-105">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="59fa9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="59fa9-106">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="59fa9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="59fa9-107">DESCRIPTION</span></span>

<span data-ttu-id="59fa9-108">De `Write-Verbose` cmdlet schrijft tekst naar de uitgebreide berichten stroom in Power shell.</span><span class="sxs-lookup"><span data-stu-id="59fa9-108">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="59fa9-109">Normaal gesp roken wordt de uitgebreide berichten stroom gebruikt om meer gedetailleerde informatie over de verwerking van opdrachten te bieden.</span><span class="sxs-lookup"><span data-stu-id="59fa9-109">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="59fa9-110">De uitgebreide berichten stroom wordt standaard niet weer gegeven, maar u kunt deze weer geven door de waarde van de variabele te wijzigen `$VerbosePreference` of door de **uitgebreide** para meter in een wille keurige opdracht te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="59fa9-110">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="59fa9-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="59fa9-111">EXAMPLES</span></span>

### <span data-ttu-id="59fa9-112">Voor beeld 1: een status bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="59fa9-112">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="59fa9-113">Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-113">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="59fa9-114">Het bericht wordt standaard niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-114">By default, the message is not displayed.</span></span>

<span data-ttu-id="59fa9-115">De tweede opdracht maakt gebruik van de **uitgebreide** algemene para meter, waarmee alle uitgebreide berichten worden weer gegeven, ongeacht de waarde van de `$VerbosePreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="59fa9-115">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="59fa9-116">Voor beeld 2: $VerbosePreference instellen en een status bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="59fa9-116">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="59fa9-117">Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-117">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="59fa9-118">Het bericht wordt standaard niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-118">By default, the message is not displayed.</span></span>

<span data-ttu-id="59fa9-119">Met de eerste opdracht wordt een waarde van door gaan naar de `$VerbosePreference` Voorkeurs variabele toegewezen.</span><span class="sxs-lookup"><span data-stu-id="59fa9-119">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="59fa9-120">De standaard waarde, `SilentlyContinue` , onderdrukt uitgebreide berichten.</span><span class="sxs-lookup"><span data-stu-id="59fa9-120">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="59fa9-121">Met de tweede opdracht wordt een uitgebreid bericht geschreven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-121">The second command writes a verbose message.</span></span>

## <span data-ttu-id="59fa9-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="59fa9-122">PARAMETERS</span></span>

### <span data-ttu-id="59fa9-123">-Bericht</span><span class="sxs-lookup"><span data-stu-id="59fa9-123">-Message</span></span>

<span data-ttu-id="59fa9-124">Hiermee geeft u het bericht op dat moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-124">Specifies the message to display.</span></span> <span data-ttu-id="59fa9-125">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="59fa9-125">This parameter is required.</span></span> <span data-ttu-id="59fa9-126">U kunt ook een bericht teken reeks door sluizen naar `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="59fa9-126">You can also pipe a message string to `Write-Verbose`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="59fa9-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59fa9-127">CommonParameters</span></span>

<span data-ttu-id="59fa9-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59fa9-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59fa9-129">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="59fa9-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="59fa9-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="59fa9-130">INPUTS</span></span>

### <span data-ttu-id="59fa9-131">System. String</span><span class="sxs-lookup"><span data-stu-id="59fa9-131">System.String</span></span>

<span data-ttu-id="59fa9-132">U kunt een teken reeks die het bericht bevat door sluizen naar `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="59fa9-132">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="59fa9-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="59fa9-133">OUTPUTS</span></span>

### <span data-ttu-id="59fa9-134">Geen</span><span class="sxs-lookup"><span data-stu-id="59fa9-134">None</span></span>

<span data-ttu-id="59fa9-135">`Write-Verbose` schrijft alleen naar de uitgebreide berichten stroom.</span><span class="sxs-lookup"><span data-stu-id="59fa9-135">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="59fa9-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="59fa9-136">NOTES</span></span>

- <span data-ttu-id="59fa9-137">Uitgebreide berichten worden alleen geretourneerd als de opdracht de **uitgebreide** para meter common gebruikt.</span><span class="sxs-lookup"><span data-stu-id="59fa9-137">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="59fa9-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="59fa9-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="59fa9-139">In Windows Power shell-achtergrond taken en externe opdrachten `$VerbosePreference` wordt met de variabele in de taak sessie en externe sessie bepaald of het uitgebreide bericht standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59fa9-139">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="59fa9-140">Zie about_Preference_Variables voor meer informatie over de `$VerbosePreference` variabele [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="59fa9-140">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="59fa9-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="59fa9-141">RELATED LINKS</span></span>

[<span data-ttu-id="59fa9-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="59fa9-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="59fa9-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="59fa9-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="59fa9-144">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="59fa9-144">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="59fa9-145">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="59fa9-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="59fa9-146">Write-host</span><span class="sxs-lookup"><span data-stu-id="59fa9-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="59fa9-147">Write-Information</span><span class="sxs-lookup"><span data-stu-id="59fa9-147">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="59fa9-148">Write-output</span><span class="sxs-lookup"><span data-stu-id="59fa9-148">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="59fa9-149">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="59fa9-149">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="59fa9-150">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="59fa9-150">Write-Warning</span></span>](Write-Warning.md)
