---
title: Schrijven van een PowerShell-module Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845246"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="52f22-102">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="52f22-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="52f22-103">In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die kan worden gebruikt voor het registreren van de cmdlets en providers van Windows PowerShell in een assembly.</span><span class="sxs-lookup"><span data-stu-id="52f22-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="52f22-104">Met dit type-module kan selecteert u niet welke cmdlets en providers die u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="52f22-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="52f22-105">Zie voor het schrijven van een module die kunt u selecteren wat is geregistreerd, [schrijven van een aangepaste Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="52f22-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="52f22-106">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="52f22-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="52f22-107">Het kenmerk RunInstallerAttribute toevoegen.</span><span class="sxs-lookup"><span data-stu-id="52f22-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="52f22-108">Maak een openbare klasse die is afgeleid van de [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) klasse.</span><span class="sxs-lookup"><span data-stu-id="52f22-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="52f22-109">In dit voorbeeld is de naam van de klasse 'GetProcPSSnapIn01'.</span><span class="sxs-lookup"><span data-stu-id="52f22-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="52f22-110">Toevoegen van een openbare eigenschap voor de naam van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="52f22-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="52f22-111">Als naming-modules, gebruik dan niet een van de volgende tekens bevatten: #.</span><span class="sxs-lookup"><span data-stu-id="52f22-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="52f22-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="52f22-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="52f22-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="52f22-113">@ \` \*</span></span>

    <span data-ttu-id="52f22-114">In dit voorbeeld is de naam van de module 'GetProcPSSnapIn01'.</span><span class="sxs-lookup"><span data-stu-id="52f22-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="52f22-115">Voeg een openbare eigenschap toe voor de leverancier van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="52f22-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="52f22-116">In dit voorbeeld wordt is de leverancier 'Microsoft'.</span><span class="sxs-lookup"><span data-stu-id="52f22-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="52f22-117">Toevoegen van een openbare eigenschap van de bron van de leverancier van de module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="52f22-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="52f22-118">In dit voorbeeld is de leverancierresource 'GetProcPSSnapIn01, Microsoft'.</span><span class="sxs-lookup"><span data-stu-id="52f22-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="52f22-119">Toevoegen van een openbare eigenschap voor de beschrijving van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="52f22-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="52f22-120">In dit voorbeeld wordt is de beschrijving "Dit is een Windows PowerShell-module die de cmdlet get-proc registreert".</span><span class="sxs-lookup"><span data-stu-id="52f22-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="52f22-121">Toevoegen van een openbare eigenschap van de bron van de beschrijving van de module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="52f22-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="52f22-122">In dit voorbeeld is de leverancierresource "GetProcPSSnapIn01, dit is een Windows PowerShell-module die de cmdlet get-proc registreert".</span><span class="sxs-lookup"><span data-stu-id="52f22-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="52f22-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="52f22-123">Example</span></span>

<span data-ttu-id="52f22-124">In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die kan worden gebruikt voor het registreren van de cmdlet Get-procedure in de Windows PowerShell-shell.</span><span class="sxs-lookup"><span data-stu-id="52f22-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="52f22-125">Let erop dat in dit voorbeeld wordt de volledige assembly alleen de GetProcPSSnapIn01-module-klasse en de cmdlet Get-Proc klasse bevatten zou.</span><span class="sxs-lookup"><span data-stu-id="52f22-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="52f22-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="52f22-126">See Also</span></span>

[<span data-ttu-id="52f22-127">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="52f22-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="52f22-128">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="52f22-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="52f22-129">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="52f22-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
