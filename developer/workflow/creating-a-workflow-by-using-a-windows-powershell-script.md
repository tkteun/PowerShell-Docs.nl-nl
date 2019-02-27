---
title: Het maken van een werkstroom met behulp van een Windows PowerShell-Script | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844742"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="f588b-102">Een werkstroom maken met behulp van een Windows PowerShell-script</span><span class="sxs-lookup"><span data-stu-id="f588b-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="f588b-103">U kunt een werkstroom maken door een Windows PowerShell-script te schrijven.</span><span class="sxs-lookup"><span data-stu-id="f588b-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="f588b-104">Gebruik het sleutelwoord workflow gevolgd door een naam op voor de werkstroom voor de hoofdtekst van het script voor het maken van een werkstroom.</span><span class="sxs-lookup"><span data-stu-id="f588b-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="f588b-105">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f588b-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="f588b-106">U vindt de werkstroom in de dezelfde manier als andere Windows PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="f588b-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="f588b-107">Parallelle en Takenreeksen implementeren</span><span class="sxs-lookup"><span data-stu-id="f588b-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="f588b-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) ondersteunt de uitvoering van activiteiten parallel.</span><span class="sxs-lookup"><span data-stu-id="f588b-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="f588b-109">Voor het implementeren van deze mogelijkheid in een Windows PowerShell-script, gebruikt u de `parallel` sleutelwoord vóór een scriptblok.</span><span class="sxs-lookup"><span data-stu-id="f588b-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="f588b-110">U kunt ook de `foreach -parallel` bouw aan een verzameling van objecten tegelijk doorlopen.</span><span class="sxs-lookup"><span data-stu-id="f588b-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="f588b-111">Als u wilt een groep activiteiten worden uitgevoerd in opeenvolgende volgorde binnen een parallel blok, plaatst u deze groep van activiteiten in een scriptblok en voorafgaan aan het blok met het trefwoord volgorde.</span><span class="sxs-lookup"><span data-stu-id="f588b-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="f588b-112">Computers toevoegen aan een domein</span><span class="sxs-lookup"><span data-stu-id="f588b-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="f588b-113">Het volgende script maakt u een werkstroom die controleert de domeinstatus van een groep computers door gebruiker opgegeven, maakt u ze lid aan een domein als ze niet al zijn gekoppeld, en de status vervolgens opnieuw controleert.</span><span class="sxs-lookup"><span data-stu-id="f588b-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="f588b-114">Dit is een scriptversie van de XAML-werkstroom uitgelegd in [het maken van een werkstroom met Windows PowerShell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f588b-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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