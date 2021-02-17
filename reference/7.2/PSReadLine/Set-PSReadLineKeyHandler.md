---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 86386cb8d97e16ebdd869e2ec554fc947d788f67
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563279"
---
# <span data-ttu-id="9f96d-102">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9f96d-102">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="9f96d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9f96d-103">SYNOPSIS</span></span>
<span data-ttu-id="9f96d-104">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="9f96d-104">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="9f96d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9f96d-105">SYNTAX</span></span>

### <span data-ttu-id="9f96d-106">Script Block</span><span class="sxs-lookup"><span data-stu-id="9f96d-106">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="9f96d-107">Functie</span><span class="sxs-lookup"><span data-stu-id="9f96d-107">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="9f96d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9f96d-108">DESCRIPTION</span></span>

<span data-ttu-id="9f96d-109">Met de `Set-PSReadLineKeyHandler` cmdlet wordt het resultaat aangepast wanneer een toets of reeks sleutels wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="9f96d-109">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="9f96d-110">Met door de gebruiker gedefinieerde sleutel bindingen kunt u bijna alles doen die mogelijk is vanuit een Power shell-script.</span><span class="sxs-lookup"><span data-stu-id="9f96d-110">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="9f96d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9f96d-111">EXAMPLES</span></span>

### <span data-ttu-id="9f96d-112">Voor beeld 1: de pijl sleutel binden aan een functie</span><span class="sxs-lookup"><span data-stu-id="9f96d-112">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="9f96d-113">Met deze opdracht wordt de pijl-omhoog gekoppeld aan de functie **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="9f96d-113">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="9f96d-114">Met deze functie wordt de opdracht geschiedenis doorzocht op opdracht regels die beginnen met de huidige inhoud van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="9f96d-114">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="9f96d-115">Voor beeld 2: een sleutel binden aan een script blok</span><span class="sxs-lookup"><span data-stu-id="9f96d-115">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="9f96d-116">In dit voor beeld ziet u hoe een enkele sleutel kan worden gebruikt om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9f96d-116">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="9f96d-117">Met de opdracht wordt de sleutel gebonden `Ctrl+B` aan een script blok waarmee de regel wordt gewist, wordt het woord build ingevoegd en wordt de regel vervolgens geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="9f96d-117">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="9f96d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f96d-118">PARAMETERS</span></span>

### <span data-ttu-id="9f96d-119">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="9f96d-119">-BriefDescription</span></span>

<span data-ttu-id="9f96d-120">Een korte beschrijving van de sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="9f96d-120">A brief description of the key binding.</span></span> <span data-ttu-id="9f96d-121">Deze beschrijving wordt weer gegeven door de `Get-PSReadLineKeyHandler` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f96d-121">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="9f96d-122">-Koord</span><span class="sxs-lookup"><span data-stu-id="9f96d-122">-Chord</span></span>

<span data-ttu-id="9f96d-123">De sleutel of reeks sleutels die moeten worden gebonden aan een functie of script blok.</span><span class="sxs-lookup"><span data-stu-id="9f96d-123">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="9f96d-124">Gebruik één teken reeks om één binding op te geven.</span><span class="sxs-lookup"><span data-stu-id="9f96d-124">Use a single string to specify a single binding.</span></span> <span data-ttu-id="9f96d-125">Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="9f96d-125">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

> [!NOTE]
> <span data-ttu-id="9f96d-126">De para meter **koorde** vanaf PSReadLine 2.0.0 is **hoofdletter gevoelig**.</span><span class="sxs-lookup"><span data-stu-id="9f96d-126">As of PSReadLine 2.0.0, the **Chord** parameter is **case-sensitive**.</span></span> <span data-ttu-id="9f96d-127">Dat wil zeggen dat `Ctrl+X` `Ctrl+x` er verschillende bindingen worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9f96d-127">Meaning, `Ctrl+X` and `Ctrl+x` will create different bindings.</span></span>

<span data-ttu-id="9f96d-128">Deze para meter accepteert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="9f96d-128">This parameter accepts an array of strings.</span></span> <span data-ttu-id="9f96d-129">Elke teken reeks is een afzonderlijke binding, geen reeks sleutels voor één binding.</span><span class="sxs-lookup"><span data-stu-id="9f96d-129">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="9f96d-130">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f96d-130">-Description</span></span>

<span data-ttu-id="9f96d-131">Hiermee geeft u een gedetailleerde beschrijving op van de sleutel binding die zichtbaar is in de uitvoer van de `Get-PSReadLineKeyHandler` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f96d-131">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="9f96d-132">-Functie</span><span class="sxs-lookup"><span data-stu-id="9f96d-132">-Function</span></span>

<span data-ttu-id="9f96d-133">Hiermee geeft u de naam op van een bestaande sleutel-handler die wordt opgegeven door PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="9f96d-133">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="9f96d-134">Met deze para meter kunt u bestaande sleutel bindingen opnieuw binden of een handler binden die momenteel niet is gebonden.</span><span class="sxs-lookup"><span data-stu-id="9f96d-134">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

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

### <span data-ttu-id="9f96d-135">-Script Block</span><span class="sxs-lookup"><span data-stu-id="9f96d-135">-ScriptBlock</span></span>

<span data-ttu-id="9f96d-136">Hiermee geeft u een script blok waarde op die moet worden uitgevoerd wanneer de koorde wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f96d-136">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="9f96d-137">PSReadLine geeft een of twee para meters door aan dit script blok.</span><span class="sxs-lookup"><span data-stu-id="9f96d-137">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="9f96d-138">De eerste para meter is een **ConsoleKeyInfo** -object waarmee de toets wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="9f96d-138">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="9f96d-139">Het tweede argument kan elk object zijn, afhankelijk van de context.</span><span class="sxs-lookup"><span data-stu-id="9f96d-139">The second argument can be any object depending on the context.</span></span>

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

### <span data-ttu-id="9f96d-140">-ViMode</span><span class="sxs-lookup"><span data-stu-id="9f96d-140">-ViMode</span></span>

<span data-ttu-id="9f96d-141">Geef op op welke VI-modus de binding van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="9f96d-141">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="9f96d-142">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="9f96d-142">Valid values are:</span></span>

- <span data-ttu-id="9f96d-143">Invoegen</span><span class="sxs-lookup"><span data-stu-id="9f96d-143">Insert</span></span>
- <span data-ttu-id="9f96d-144">Opdracht</span><span class="sxs-lookup"><span data-stu-id="9f96d-144">Command</span></span>

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

### <span data-ttu-id="9f96d-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f96d-145">CommonParameters</span></span>

<span data-ttu-id="9f96d-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f96d-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f96d-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f96d-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f96d-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="9f96d-148">INPUTS</span></span>

### <span data-ttu-id="9f96d-149">Geen</span><span class="sxs-lookup"><span data-stu-id="9f96d-149">None</span></span>

<span data-ttu-id="9f96d-150">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="9f96d-150">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9f96d-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9f96d-151">OUTPUTS</span></span>

### <span data-ttu-id="9f96d-152">Geen</span><span class="sxs-lookup"><span data-stu-id="9f96d-152">None</span></span>

<span data-ttu-id="9f96d-153">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9f96d-153">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9f96d-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9f96d-154">NOTES</span></span>

## <span data-ttu-id="9f96d-155">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9f96d-155">RELATED LINKS</span></span>

[<span data-ttu-id="9f96d-156">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9f96d-156">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="9f96d-157">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9f96d-157">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="9f96d-158">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9f96d-158">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="9f96d-159">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9f96d-159">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

