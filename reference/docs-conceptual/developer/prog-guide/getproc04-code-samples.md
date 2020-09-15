---
title: Voor beelden van GetProc04-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771954"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="5d098-102">GetProc04-codevoorbeelden</span><span class="sxs-lookup"><span data-stu-id="5d098-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="5d098-103">Hier volgen de code voorbeelden voor de voor beeld-cmdlet GetProc04.</span><span class="sxs-lookup"><span data-stu-id="5d098-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="5d098-104">Dit is het `Get-Process` cmdlet-voor beeld dat wordt beschreven in het toevoegen van niet- [afsluitende fout rapportage aan uw cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="5d098-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="5d098-105">Met deze `Get-Process` cmdlet wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen wanneer er een ongeldige bewerkings uitzondering optreedt tijdens het ophalen van proces gegevens.</span><span class="sxs-lookup"><span data-stu-id="5d098-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="5d098-106">U kunt het C#-bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="5d098-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5d098-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="5d098-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5d098-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="5d098-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="5d098-109">Zie de volgende onderwerpen voor een volledige voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="5d098-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="5d098-110">Taal</span><span class="sxs-lookup"><span data-stu-id="5d098-110">Language</span></span>|<span data-ttu-id="5d098-111">Onderwerp</span><span class="sxs-lookup"><span data-stu-id="5d098-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="5d098-112">C#</span><span class="sxs-lookup"><span data-stu-id="5d098-112">C#</span></span>|[<span data-ttu-id="5d098-113">GetProc04-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="5d098-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="5d098-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="5d098-114">VB.NET</span></span>|[<span data-ttu-id="5d098-115">GetProc04-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="5d098-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="5d098-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5d098-116">See Also</span></span>

[<span data-ttu-id="5d098-117">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="5d098-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5d098-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5d098-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
