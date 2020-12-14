---
description: Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: 2984e0a9e5f470594dd1e5987b69b92f91ce4913
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706204"
---
# <a name="about-throw"></a><span data-ttu-id="b5980-103">Over throw</span><span class="sxs-lookup"><span data-stu-id="b5980-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="b5980-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5980-104">Short description</span></span>
<span data-ttu-id="b5980-105">Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b5980-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="b5980-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5980-106">Long description</span></span>

<span data-ttu-id="b5980-107">Het sleutel woord throw veroorzaakt een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="b5980-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="b5980-108">U kunt het sleutel woord throw gebruiken om de verwerking van een opdracht, functie of script te stoppen.</span><span class="sxs-lookup"><span data-stu-id="b5980-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="b5980-109">U kunt bijvoorbeeld het sleutel woord throw in het script blok van een if-instructie gebruiken om te reageren op een voor waarde of in het blok catch van een try-catch-finally-instructie.</span><span class="sxs-lookup"><span data-stu-id="b5980-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="b5980-110">U kunt ook het sleutel woord throw in een parameter declaratie gebruiken om een functie parameter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="b5980-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="b5980-111">Het sleutel woord throw kan elk object genereren, zoals een gebruikers bericht teken reeks of het object dat de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="b5980-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5980-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5980-112">Syntax</span></span>

<span data-ttu-id="b5980-113">De syntaxis van het sleutel woord throw is als volgt:</span><span class="sxs-lookup"><span data-stu-id="b5980-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="b5980-114">De expressie in de syntaxis van de throw is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b5980-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="b5980-115">Wanneer de instructie throw niet wordt weer gegeven in een catch-blok en geen expressie bevat, wordt er een ScriptHalted-fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b5980-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="b5980-116">Als het sleutel woord throw wordt gebruikt in een catch-blok zonder expressie, wordt de huidige RuntimeException opnieuw gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b5980-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="b5980-117">Zie about_Try_Catch_Finally voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5980-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="b5980-118">Een teken reeks activeren</span><span class="sxs-lookup"><span data-stu-id="b5980-118">Throwing a string</span></span>

<span data-ttu-id="b5980-119">De optionele expressie in een instructie throw kan een teken reeks zijn, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="b5980-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="b5980-120">Andere objecten activeren</span><span class="sxs-lookup"><span data-stu-id="b5980-120">Throwing other objects</span></span>

<span data-ttu-id="b5980-121">De expressie kan ook een object zijn dat het object genereert dat het Power Shell-proces vertegenwoordigt, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="b5980-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="b5980-122">U kunt de eigenschap target object van het object ErrorRecord in de variabele $error Automatic gebruiken om de fout te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="b5980-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="b5980-123">U kunt ook een ErrorRecord-object of een .NET-uitzonde ring genereren.</span><span class="sxs-lookup"><span data-stu-id="b5980-123">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="b5980-124">In het volgende voor beeld wordt het sleutel woord throw gebruikt voor het genereren van een System. FormatException-object.</span><span class="sxs-lookup"><span data-stu-id="b5980-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="b5980-125">De resulterende fout</span><span class="sxs-lookup"><span data-stu-id="b5980-125">The resulting error</span></span>

<span data-ttu-id="b5980-126">Met het sleutel woord throw kan een ErrorRecord-object worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b5980-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="b5980-127">De eigenschap Exception van het object ErrorRecord bevat een RuntimeException-object.</span><span class="sxs-lookup"><span data-stu-id="b5980-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="b5980-128">De rest van het ErrorRecord-object en het RuntimeException-object verschillen met het object dat het sleutel woord throw genereert.</span><span class="sxs-lookup"><span data-stu-id="b5980-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="b5980-129">Het RunTimeException-object wordt verpakt in een ErrorRecord-object en het ErrorRecord-object wordt automatisch opgeslagen in de variabele $Error Automatic.</span><span class="sxs-lookup"><span data-stu-id="b5980-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="b5980-130">Een verplichte para meter maken met behulp van throw</span><span class="sxs-lookup"><span data-stu-id="b5980-130">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="b5980-131">In tegens telling tot eerdere versies van Power shell, moet u het sleutel woord throw niet gebruiken voor de validatie van de para meters.</span><span class="sxs-lookup"><span data-stu-id="b5980-131">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="b5980-132">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="b5980-132">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5980-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b5980-133">See also</span></span>

- [<span data-ttu-id="b5980-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="b5980-134">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="b5980-135">about_Continue</span><span class="sxs-lookup"><span data-stu-id="b5980-135">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="b5980-136">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b5980-136">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="b5980-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="b5980-137">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="b5980-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="b5980-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
