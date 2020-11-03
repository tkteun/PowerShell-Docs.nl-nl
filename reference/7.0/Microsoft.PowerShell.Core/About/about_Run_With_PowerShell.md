---
description: Hierin wordt uitgelegd hoe u de functie uitvoeren met Power shell gebruikt om een script uit te voeren vanuit een bestandssysteem station.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: c5b1ca5d924c6eddd6371a269f694a5304510b25
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252861"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="f04e5-104">Over uitvoeren met Power shell</span><span class="sxs-lookup"><span data-stu-id="f04e5-104">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="f04e5-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f04e5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f04e5-106">Hierin wordt uitgelegd hoe u de functie uitvoeren met Power shell gebruikt om een script uit te voeren vanuit een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="f04e5-106">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="f04e5-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f04e5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f04e5-108">Vanaf Windows Power Shell 3,0 kunt u de functie uitvoeren met Power shell gebruiken om scripts uit te voeren vanuit Verkenner in Windows 8 en Windows Server 2012 en Windows Verkenner in eerdere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="f04e5-108">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="f04e5-109">De functie ' uitvoeren met Power shell ' is ontworpen voor het uitvoeren van scripts waarvoor geen vereiste para meters zijn en die geen uitvoer retour neren naar de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="f04e5-109">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="f04e5-110">Wanneer u de functie ' uitvoeren met Power shell ' gebruikt, wordt het Power shell-console venster alleen kort weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f04e5-110">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="f04e5-111">U kunt er niet mee communiceren.</span><span class="sxs-lookup"><span data-stu-id="f04e5-111">You cannot interact with it.</span></span>

<span data-ttu-id="f04e5-112">De functie ' uitvoeren met Power shell ' gebruiken:</span><span class="sxs-lookup"><span data-stu-id="f04e5-112">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="f04e5-113">Klik in Verkenner (of Windows Verkenner) met de rechter muisknop op de naam van het script bestand en selecteer vervolgens uitvoeren met Power shell.</span><span class="sxs-lookup"><span data-stu-id="f04e5-113">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="f04e5-114">De functie uitvoeren met Power shell start een Power shell-sessie met een uitvoerings beleid voor overs Laan, voert het script uit en sluit de sessie.</span><span class="sxs-lookup"><span data-stu-id="f04e5-114">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="f04e5-115">Er wordt een opdracht uitgevoerd met de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="f04e5-115">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="f04e5-116">Met ' uitvoeren met Power shell ' stelt u het uitvoerings beleid overs Laan alleen in voor de sessie (het huidige exemplaar van het Power Shell-proces) waarin het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f04e5-116">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="f04e5-117">Deze functie wijzigt het uitvoerings beleid voor de computer of de gebruiker niet.</span><span class="sxs-lookup"><span data-stu-id="f04e5-117">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="f04e5-118">De functie ' uitvoeren met Power shell ' is alleen van invloed op het uitvoerings beleid voor alles ondertekend.</span><span class="sxs-lookup"><span data-stu-id="f04e5-118">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="f04e5-119">Als het alles ondertekend-uitvoerings beleid van kracht is voor de computer of de gebruiker, voert ' uitvoeren met Power shell ' alleen ondertekende scripts uit.</span><span class="sxs-lookup"><span data-stu-id="f04e5-119">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="f04e5-120">' Uitvoeren met Power shell ' wordt niet beïnvloed door andere uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="f04e5-120">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="f04e5-121">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f04e5-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="f04e5-122">Opmerking voor probleem oplossing: met de Power shell-opdracht wordt u mogelijk gevraagd de wijziging van het uitvoerings beleid te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="f04e5-122">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="f04e5-123">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="f04e5-123">SEE ALSO</span></span>

[<span data-ttu-id="f04e5-124">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="f04e5-124">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="f04e5-125">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="f04e5-125">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="f04e5-126">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="f04e5-126">about_Scripts</span></span>](about_Scripts.md)
