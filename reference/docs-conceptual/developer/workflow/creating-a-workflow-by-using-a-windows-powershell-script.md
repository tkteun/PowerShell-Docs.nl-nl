---
title: Een werk stroom maken met behulp van een Windows Power shell-script | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557445"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="45b7e-102">Een werkstroom maken met behulp van een Windows PowerShell-script</span><span class="sxs-lookup"><span data-stu-id="45b7e-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="45b7e-103">U kunt een werk stroom maken door een Windows Power shell-script te schrijven.</span><span class="sxs-lookup"><span data-stu-id="45b7e-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="45b7e-104">Als u een werk stroom wilt maken, gebruikt u het tref woord workflow gevolgd door een naam voor de werk stroom vóór de hoofd tekst van het script.</span><span class="sxs-lookup"><span data-stu-id="45b7e-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="45b7e-105">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="45b7e-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="45b7e-106">U vindt de werk stroom op dezelfde manier als elke andere Windows Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="45b7e-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="45b7e-107">Parallelle en sequentieel implementeren</span><span class="sxs-lookup"><span data-stu-id="45b7e-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="45b7e-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) ondersteunt de uitvoering van activiteiten parallel.</span><span class="sxs-lookup"><span data-stu-id="45b7e-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="45b7e-109">Als u deze functie in een Windows Power shell-script wilt implementeren, gebruikt u het `parallel` sleutel woord voor een script blok.</span><span class="sxs-lookup"><span data-stu-id="45b7e-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="45b7e-110">U kunt ook de `foreach -parallel` constructie gebruiken om een verzameling objecten parallel te herhalen.</span><span class="sxs-lookup"><span data-stu-id="45b7e-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="45b7e-111">Als u een groep activiteiten in sequentiële volg orde binnen een parallel blok wilt uitvoeren, sluit u die groep activiteiten in een script blok en plaatst u de blok kering met het sleutel woord sequence.</span><span class="sxs-lookup"><span data-stu-id="45b7e-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="45b7e-112">Computers toevoegen aan een domein</span><span class="sxs-lookup"><span data-stu-id="45b7e-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="45b7e-113">Met het volgende script wordt een werk stroom gemaakt waarmee de domein status wordt gecontroleerd van een groep door de gebruiker opgegeven computers, wordt toegevoegd aan een domein als ze nog niet zijn gekoppeld, waarna de status opnieuw wordt gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="45b7e-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="45b7e-114">Dit is een script versie van de XAML-werk stroom die wordt uitgelegd in [een werk stroom maken met Windows Power shell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="45b7e-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```
