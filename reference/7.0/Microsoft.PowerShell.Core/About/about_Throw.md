---
description: Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: d4bf0ea00145c03522d4db952be201c877c9d50c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252060"
---
# <a name="about-throw"></a><span data-ttu-id="28247-104">Over throw</span><span class="sxs-lookup"><span data-stu-id="28247-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="28247-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="28247-105">Short description</span></span>
<span data-ttu-id="28247-106">Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="28247-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="28247-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="28247-107">Long description</span></span>

<span data-ttu-id="28247-108">Het sleutel woord throw veroorzaakt een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="28247-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="28247-109">U kunt het sleutel woord throw gebruiken om de verwerking van een opdracht, functie of script te stoppen.</span><span class="sxs-lookup"><span data-stu-id="28247-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="28247-110">U kunt bijvoorbeeld het sleutel woord throw in het script blok van een if-instructie gebruiken om te reageren op een voor waarde of in het blok catch van een try-catch-finally-instructie.</span><span class="sxs-lookup"><span data-stu-id="28247-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="28247-111">U kunt ook het sleutel woord throw in een parameter declaratie gebruiken om een functie parameter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="28247-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="28247-112">Het sleutel woord throw kan elk object genereren, zoals een gebruikers bericht teken reeks of het object dat de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="28247-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="28247-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="28247-113">Syntax</span></span>

<span data-ttu-id="28247-114">De syntaxis van het sleutel woord throw is als volgt:</span><span class="sxs-lookup"><span data-stu-id="28247-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="28247-115">De expressie in de syntaxis van de throw is optioneel.</span><span class="sxs-lookup"><span data-stu-id="28247-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="28247-116">Wanneer de instructie throw niet wordt weer gegeven in een catch-blok en geen expressie bevat, wordt er een ScriptHalted-fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="28247-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="28247-117">Als het sleutel woord throw wordt gebruikt in een catch-blok zonder expressie, wordt de huidige RuntimeException opnieuw gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="28247-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="28247-118">Zie about_Try_Catch_Finally voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="28247-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="28247-119">Een teken reeks activeren</span><span class="sxs-lookup"><span data-stu-id="28247-119">Throwing a string</span></span>

<span data-ttu-id="28247-120">De optionele expressie in een instructie throw kan een teken reeks zijn, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="28247-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="28247-121">Andere objecten activeren</span><span class="sxs-lookup"><span data-stu-id="28247-121">Throwing other objects</span></span>

<span data-ttu-id="28247-122">De expressie kan ook een object zijn dat het object genereert dat het Power Shell-proces vertegenwoordigt, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="28247-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="28247-123">U kunt de eigenschap target object van het object ErrorRecord in de variabele $error Automatic gebruiken om de fout te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="28247-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="28247-124">U kunt ook een ErrorRecord-object of een .NET-uitzonde ring genereren.</span><span class="sxs-lookup"><span data-stu-id="28247-124">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="28247-125">In het volgende voor beeld wordt het sleutel woord throw gebruikt voor het genereren van een System. FormatException-object.</span><span class="sxs-lookup"><span data-stu-id="28247-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="28247-126">De resulterende fout</span><span class="sxs-lookup"><span data-stu-id="28247-126">The resulting error</span></span>

<span data-ttu-id="28247-127">Met het sleutel woord throw kan een ErrorRecord-object worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="28247-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="28247-128">De eigenschap Exception van het object ErrorRecord bevat een RuntimeException-object.</span><span class="sxs-lookup"><span data-stu-id="28247-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="28247-129">De rest van het ErrorRecord-object en het RuntimeException-object verschillen met het object dat het sleutel woord throw genereert.</span><span class="sxs-lookup"><span data-stu-id="28247-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="28247-130">Het RunTimeException-object wordt verpakt in een ErrorRecord-object en het ErrorRecord-object wordt automatisch opgeslagen in de variabele $Error Automatic.</span><span class="sxs-lookup"><span data-stu-id="28247-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="28247-131">Een verplichte para meter maken met behulp van throw</span><span class="sxs-lookup"><span data-stu-id="28247-131">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="28247-132">In tegens telling tot eerdere versies van Power shell, moet u het sleutel woord throw niet gebruiken voor de validatie van de para meters.</span><span class="sxs-lookup"><span data-stu-id="28247-132">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="28247-133">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="28247-133">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="28247-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="28247-134">See also</span></span>

- [<span data-ttu-id="28247-135">about_Break</span><span class="sxs-lookup"><span data-stu-id="28247-135">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="28247-136">about_Continue</span><span class="sxs-lookup"><span data-stu-id="28247-136">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="28247-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="28247-137">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="28247-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="28247-138">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="28247-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="28247-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
