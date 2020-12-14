---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 177e32106f37c59593bbecac13843f6603327cc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706009"
---
# <span data-ttu-id="23e46-102">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="23e46-102">Write-Verbose</span></span>

## <span data-ttu-id="23e46-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="23e46-103">SYNOPSIS</span></span>
<span data-ttu-id="23e46-104">Schrijft tekst naar de uitgebreide berichten stroom.</span><span class="sxs-lookup"><span data-stu-id="23e46-104">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="23e46-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="23e46-105">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="23e46-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="23e46-106">DESCRIPTION</span></span>

<span data-ttu-id="23e46-107">De `Write-Verbose` cmdlet schrijft tekst naar de uitgebreide berichten stroom in Power shell.</span><span class="sxs-lookup"><span data-stu-id="23e46-107">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="23e46-108">Normaal gesp roken wordt de uitgebreide berichten stroom gebruikt om meer gedetailleerde informatie over de verwerking van opdrachten te bieden.</span><span class="sxs-lookup"><span data-stu-id="23e46-108">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="23e46-109">De uitgebreide berichten stroom wordt standaard niet weer gegeven, maar u kunt deze weer geven door de waarde van de variabele te wijzigen `$VerbosePreference` of door de **uitgebreide** para meter in een wille keurige opdracht te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="23e46-109">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="23e46-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="23e46-110">EXAMPLES</span></span>

### <span data-ttu-id="23e46-111">Voor beeld 1: een status bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="23e46-111">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="23e46-112">Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="23e46-112">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="23e46-113">Het bericht wordt standaard niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="23e46-113">By default, the message is not displayed.</span></span>

<span data-ttu-id="23e46-114">De tweede opdracht maakt gebruik van de **uitgebreide** algemene para meter, waarmee alle uitgebreide berichten worden weer gegeven, ongeacht de waarde van de `$VerbosePreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="23e46-114">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="23e46-115">Voor beeld 2: $VerbosePreference instellen en een status bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="23e46-115">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="23e46-116">Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="23e46-116">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="23e46-117">Het bericht wordt standaard niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="23e46-117">By default, the message is not displayed.</span></span>

<span data-ttu-id="23e46-118">Met de eerste opdracht wordt een waarde van door gaan naar de `$VerbosePreference` Voorkeurs variabele toegewezen.</span><span class="sxs-lookup"><span data-stu-id="23e46-118">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="23e46-119">De standaard waarde, `SilentlyContinue` , onderdrukt uitgebreide berichten.</span><span class="sxs-lookup"><span data-stu-id="23e46-119">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="23e46-120">Met de tweede opdracht wordt een uitgebreid bericht geschreven.</span><span class="sxs-lookup"><span data-stu-id="23e46-120">The second command writes a verbose message.</span></span>

## <span data-ttu-id="23e46-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23e46-121">PARAMETERS</span></span>

### <span data-ttu-id="23e46-122">-Bericht</span><span class="sxs-lookup"><span data-stu-id="23e46-122">-Message</span></span>

<span data-ttu-id="23e46-123">Hiermee geeft u het bericht op dat moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="23e46-123">Specifies the message to display.</span></span> <span data-ttu-id="23e46-124">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="23e46-124">This parameter is required.</span></span> <span data-ttu-id="23e46-125">U kunt ook een bericht teken reeks door sluizen naar `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="23e46-125">You can also pipe a message string to `Write-Verbose`.</span></span>

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

### <span data-ttu-id="23e46-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23e46-126">CommonParameters</span></span>

<span data-ttu-id="23e46-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23e46-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23e46-128">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23e46-128">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="23e46-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="23e46-129">INPUTS</span></span>

### <span data-ttu-id="23e46-130">System. String</span><span class="sxs-lookup"><span data-stu-id="23e46-130">System.String</span></span>

<span data-ttu-id="23e46-131">U kunt een teken reeks die het bericht bevat door sluizen naar `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="23e46-131">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="23e46-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="23e46-132">OUTPUTS</span></span>

### <span data-ttu-id="23e46-133">Geen</span><span class="sxs-lookup"><span data-stu-id="23e46-133">None</span></span>

<span data-ttu-id="23e46-134">`Write-Verbose` schrijft alleen naar de uitgebreide berichten stroom.</span><span class="sxs-lookup"><span data-stu-id="23e46-134">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="23e46-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="23e46-135">NOTES</span></span>

- <span data-ttu-id="23e46-136">Uitgebreide berichten worden alleen geretourneerd als de opdracht de **uitgebreide** para meter common gebruikt.</span><span class="sxs-lookup"><span data-stu-id="23e46-136">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="23e46-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23e46-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="23e46-138">In Windows Power shell-achtergrond taken en externe opdrachten `$VerbosePreference` wordt met de variabele in de taak sessie en externe sessie bepaald of het uitgebreide bericht standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="23e46-138">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="23e46-139">Zie about_Preference_Variables voor meer informatie over de `$VerbosePreference` variabele [](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="23e46-139">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="23e46-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="23e46-140">RELATED LINKS</span></span>

[<span data-ttu-id="23e46-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="23e46-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="23e46-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="23e46-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="23e46-143">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="23e46-143">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="23e46-144">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="23e46-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="23e46-145">Write-host</span><span class="sxs-lookup"><span data-stu-id="23e46-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="23e46-146">Write-Information</span><span class="sxs-lookup"><span data-stu-id="23e46-146">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="23e46-147">Write-output</span><span class="sxs-lookup"><span data-stu-id="23e46-147">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="23e46-148">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="23e46-148">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="23e46-149">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="23e46-149">Write-Warning</span></span>](Write-Warning.md)
