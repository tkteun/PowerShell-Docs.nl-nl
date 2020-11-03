---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: b12b95cc46f6966c63fd8fd60c42d5417c4c7868
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253192"
---
# <span data-ttu-id="94bf3-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="94bf3-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="94bf3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="94bf3-104">SYNOPSIS</span></span>
<span data-ttu-id="94bf3-105">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="94bf3-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="94bf3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="94bf3-106">SYNTAX</span></span>

### <span data-ttu-id="94bf3-107">Script Block</span><span class="sxs-lookup"><span data-stu-id="94bf3-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="94bf3-108">Functie</span><span class="sxs-lookup"><span data-stu-id="94bf3-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="94bf3-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="94bf3-109">DESCRIPTION</span></span>

<span data-ttu-id="94bf3-110">Met de `Set-PSReadLineKeyHandler` cmdlet wordt het resultaat aangepast wanneer een toets of reeks sleutels wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="94bf3-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="94bf3-111">Met door de gebruiker gedefinieerde sleutel bindingen kunt u bijna alles doen die mogelijk is vanuit een Power shell-script.</span><span class="sxs-lookup"><span data-stu-id="94bf3-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="94bf3-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="94bf3-112">EXAMPLES</span></span>

### <span data-ttu-id="94bf3-113">Voor beeld 1: de pijl sleutel binden aan een functie</span><span class="sxs-lookup"><span data-stu-id="94bf3-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="94bf3-114">Met deze opdracht wordt de pijl-omhoog gekoppeld aan de functie **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="94bf3-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="94bf3-115">Met deze functie wordt de opdracht geschiedenis doorzocht op opdracht regels die beginnen met de huidige inhoud van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="94bf3-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="94bf3-116">Voor beeld 2: een sleutel binden aan een script blok</span><span class="sxs-lookup"><span data-stu-id="94bf3-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="94bf3-117">In dit voor beeld ziet u hoe een enkele sleutel kan worden gebruikt om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="94bf3-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="94bf3-118">Met de opdracht wordt de sleutel gebonden `Ctrl+B` aan een script blok waarmee de regel wordt gewist, wordt het woord build ingevoegd en wordt de regel vervolgens geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="94bf3-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="94bf3-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="94bf3-119">PARAMETERS</span></span>

### <span data-ttu-id="94bf3-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="94bf3-120">-BriefDescription</span></span>

<span data-ttu-id="94bf3-121">Een korte beschrijving van de sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="94bf3-121">A brief description of the key binding.</span></span> <span data-ttu-id="94bf3-122">Deze beschrijving wordt weer gegeven door de `Get-PSReadLineKeyHandler` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94bf3-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-123">-Koord</span><span class="sxs-lookup"><span data-stu-id="94bf3-123">-Chord</span></span>

<span data-ttu-id="94bf3-124">De sleutel of reeks sleutels die moeten worden gebonden aan een functie of script blok.</span><span class="sxs-lookup"><span data-stu-id="94bf3-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="94bf3-125">Gebruik één teken reeks om één binding op te geven.</span><span class="sxs-lookup"><span data-stu-id="94bf3-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="94bf3-126">Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="94bf3-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

<span data-ttu-id="94bf3-127">Deze para meter accepteert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="94bf3-127">This parameter accepts an array of strings.</span></span> <span data-ttu-id="94bf3-128">Elke teken reeks is een afzonderlijke binding, geen reeks sleutels voor één binding.</span><span class="sxs-lookup"><span data-stu-id="94bf3-128">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-129">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="94bf3-129">-Description</span></span>

<span data-ttu-id="94bf3-130">Hiermee geeft u een gedetailleerde beschrijving op van de sleutel binding die zichtbaar is in de uitvoer van de `Get-PSReadLineKeyHandler` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94bf3-130">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-131">-Functie</span><span class="sxs-lookup"><span data-stu-id="94bf3-131">-Function</span></span>

<span data-ttu-id="94bf3-132">Hiermee geeft u de naam op van een bestaande sleutel-handler die wordt opgegeven door PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="94bf3-132">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="94bf3-133">Met deze para meter kunt u bestaande sleutel bindingen opnieuw binden of een handler binden die momenteel niet is gebonden.</span><span class="sxs-lookup"><span data-stu-id="94bf3-133">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-134">-Script Block</span><span class="sxs-lookup"><span data-stu-id="94bf3-134">-ScriptBlock</span></span>

<span data-ttu-id="94bf3-135">Hiermee geeft u een script blok waarde op die moet worden uitgevoerd wanneer de koorde wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="94bf3-135">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="94bf3-136">PSReadLine geeft een of twee para meters door aan dit script blok.</span><span class="sxs-lookup"><span data-stu-id="94bf3-136">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="94bf3-137">De eerste para meter is een **ConsoleKeyInfo** -object waarmee de toets wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="94bf3-137">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="94bf3-138">Het tweede argument kan elk object zijn, afhankelijk van de context.</span><span class="sxs-lookup"><span data-stu-id="94bf3-138">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-139">-ViMode</span><span class="sxs-lookup"><span data-stu-id="94bf3-139">-ViMode</span></span>

<span data-ttu-id="94bf3-140">Geef op op welke VI-modus de binding van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="94bf3-140">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="94bf3-141">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="94bf3-141">Valid values are:</span></span>

- <span data-ttu-id="94bf3-142">Invoegen</span><span class="sxs-lookup"><span data-stu-id="94bf3-142">Insert</span></span>
- <span data-ttu-id="94bf3-143">Opdracht</span><span class="sxs-lookup"><span data-stu-id="94bf3-143">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94bf3-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94bf3-144">CommonParameters</span></span>

<span data-ttu-id="94bf3-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="94bf3-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94bf3-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="94bf3-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94bf3-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="94bf3-147">INPUTS</span></span>

### <span data-ttu-id="94bf3-148">Geen</span><span class="sxs-lookup"><span data-stu-id="94bf3-148">None</span></span>

<span data-ttu-id="94bf3-149">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="94bf3-149">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="94bf3-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="94bf3-150">OUTPUTS</span></span>

### <span data-ttu-id="94bf3-151">Geen</span><span class="sxs-lookup"><span data-stu-id="94bf3-151">None</span></span>

<span data-ttu-id="94bf3-152">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="94bf3-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="94bf3-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="94bf3-153">NOTES</span></span>

## <span data-ttu-id="94bf3-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="94bf3-154">RELATED LINKS</span></span>

[<span data-ttu-id="94bf3-155">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="94bf3-155">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="94bf3-156">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="94bf3-156">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="94bf3-157">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="94bf3-157">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="94bf3-158">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="94bf3-158">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
