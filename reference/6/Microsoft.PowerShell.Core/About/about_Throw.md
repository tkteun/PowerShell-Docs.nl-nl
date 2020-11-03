---
description: Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: dce019e9dc77d24843f254f978224cf5820d31aa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252205"
---
# <a name="about-throw"></a><span data-ttu-id="369d8-104">Over throw</span><span class="sxs-lookup"><span data-stu-id="369d8-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="369d8-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="369d8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="369d8-106">Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="369d8-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="369d8-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="369d8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="369d8-108">Het sleutel woord throw veroorzaakt een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="369d8-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="369d8-109">U kunt het sleutel woord throw gebruiken om de verwerking van een opdracht, functie of script te stoppen.</span><span class="sxs-lookup"><span data-stu-id="369d8-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="369d8-110">U kunt bijvoorbeeld het sleutel woord throw in het script blok van een if-instructie gebruiken om te reageren op een voor waarde of in het blok catch van een try-catch-finally-instructie.</span><span class="sxs-lookup"><span data-stu-id="369d8-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="369d8-111">U kunt ook het sleutel woord throw in een parameter declaratie gebruiken om een functie parameter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="369d8-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="369d8-112">Het sleutel woord throw kan elk object genereren, zoals een gebruikers bericht teken reeks of het object dat de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="369d8-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="369d8-113">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="369d8-113">SYNTAX</span></span>

<span data-ttu-id="369d8-114">De syntaxis van het sleutel woord throw is als volgt:</span><span class="sxs-lookup"><span data-stu-id="369d8-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="369d8-115">De expressie in de syntaxis van de throw is optioneel.</span><span class="sxs-lookup"><span data-stu-id="369d8-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="369d8-116">Wanneer de instructie throw niet wordt weer gegeven in een catch-blok en geen expressie bevat, wordt er een ScriptHalted-fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="369d8-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="369d8-117">Als het sleutel woord throw wordt gebruikt in een catch-blok zonder expressie, wordt de huidige RuntimeException opnieuw gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="369d8-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="369d8-118">Zie about_Try_Catch_Finally voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="369d8-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="369d8-119">EEN TEKEN REEKS ACTIVEREN</span><span class="sxs-lookup"><span data-stu-id="369d8-119">THROWING A STRING</span></span>

<span data-ttu-id="369d8-120">De optionele expressie in een instructie throw kan een teken reeks zijn, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="369d8-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="369d8-121">ANDERE OBJECTEN ACTIVEREN</span><span class="sxs-lookup"><span data-stu-id="369d8-121">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="369d8-122">De expressie kan ook een object zijn dat het object genereert dat het Power Shell-proces vertegenwoordigt, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="369d8-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

<span data-ttu-id="369d8-123">U kunt de eigenschap target object van het object ErrorRecord in de variabele $error Automatic gebruiken om de fout te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="369d8-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="369d8-124">U kunt ook een ErrorRecord-object of een Microsoft .NET Framework-uitzonde ring genereren.</span><span class="sxs-lookup"><span data-stu-id="369d8-124">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="369d8-125">In het volgende voor beeld wordt het sleutel woord throw gebruikt voor het genereren van een System. FormatException-object.</span><span class="sxs-lookup"><span data-stu-id="369d8-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a><span data-ttu-id="369d8-126">RESULTERENDE FOUT</span><span class="sxs-lookup"><span data-stu-id="369d8-126">RESULTING ERROR</span></span>

<span data-ttu-id="369d8-127">Met het sleutel woord throw kan een ErrorRecord-object worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="369d8-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="369d8-128">De eigenschap Exception van het object ErrorRecord bevat een RuntimeException-object.</span><span class="sxs-lookup"><span data-stu-id="369d8-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="369d8-129">De rest van het ErrorRecord-object en het RuntimeException-object verschillen met het object dat het sleutel woord throw genereert.</span><span class="sxs-lookup"><span data-stu-id="369d8-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="369d8-130">Het RunTimeException-object wordt verpakt in een ErrorRecord-object en het ErrorRecord-object wordt automatisch opgeslagen in de variabele $Error Automatic.</span><span class="sxs-lookup"><span data-stu-id="369d8-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="369d8-131">EEN VERPLICHTE PARA METER MAKEN MET BEHULP VAN THROW</span><span class="sxs-lookup"><span data-stu-id="369d8-131">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="369d8-132">U kunt het sleutel woord throw gebruiken om een functie parameter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="369d8-132">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="369d8-133">Dit is een alternatief voor het gebruik van de verplichte para meter van het sleutel woord para meter.</span><span class="sxs-lookup"><span data-stu-id="369d8-133">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="369d8-134">Wanneer u de verplichte para meter gebruikt, vraagt het systeem de gebruiker om de vereiste parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="369d8-134">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="369d8-135">Wanneer u het sleutel woord throw gebruikt, wordt de opdracht gestopt en wordt de fout record weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="369d8-135">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="369d8-136">Het sleutel woord throw in de subexpressie van para meters maakt bijvoorbeeld de para meter Path een vereiste para meter in de functie.</span><span class="sxs-lookup"><span data-stu-id="369d8-136">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="369d8-137">In dit geval genereert het sleutel woord throw een bericht teken reeks, maar het is de aanwezigheid van het sleutel woord throw waarmee de afsluit fout wordt gegenereerd als de para meter Path niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="369d8-137">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="369d8-138">De expressie die volgt op throw is optioneel.</span><span class="sxs-lookup"><span data-stu-id="369d8-138">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="369d8-139">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="369d8-139">SEE ALSO</span></span>

[<span data-ttu-id="369d8-140">about_Break</span><span class="sxs-lookup"><span data-stu-id="369d8-140">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="369d8-141">about_Continue</span><span class="sxs-lookup"><span data-stu-id="369d8-141">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="369d8-142">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="369d8-142">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="369d8-143">about_Trap</span><span class="sxs-lookup"><span data-stu-id="369d8-143">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="369d8-144">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="369d8-144">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
