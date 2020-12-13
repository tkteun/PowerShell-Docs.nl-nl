---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-module schrijven
description: Een Windows PowerShell-module schrijven
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659452"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a8ace-103">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="a8ace-103">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="a8ace-104">In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft die kan worden gebruikt voor het registreren van alle cmdlets en Windows Power shell-providers in een assembly.</span><span class="sxs-lookup"><span data-stu-id="a8ace-104">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="a8ace-105">Met dit type module selecteert u niet welke cmdlets en providers u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="a8ace-105">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="a8ace-106">Zie [een aangepaste Windows Power shell-module schrijven](./writing-a-custom-windows-powershell-snap-in.md)voor informatie over het schrijven van een module waarmee u kunt selecteren wat er is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="a8ace-106">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="a8ace-107">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="a8ace-107">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="a8ace-108">Voeg het kenmerk RunInstallerAttribute toe.</span><span class="sxs-lookup"><span data-stu-id="a8ace-108">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="a8ace-109">Maak een open bare klasse die is afgeleid van de klasse [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="a8ace-109">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="a8ace-110">In dit voor beeld is de naam van de klasse ' GetProcPSSnapIn01 '.</span><span class="sxs-lookup"><span data-stu-id="a8ace-110">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="a8ace-111">Voeg een open bare eigenschap toe voor de naam van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="a8ace-111">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="a8ace-112">Gebruik bij het benoemen van modules geen van de volgende tekens: `#` , `.` , `,` , `(` , `)` ,,,,,, `{` ,, `}` `[` `]` `&` `-` `/` `\` , `$` , `;` , `:` , `"` ,,, `'` `<` ,, `>` `|` `?` , `@` , `` ` `` ,,,,,,,,,, `*`</span><span class="sxs-lookup"><span data-stu-id="a8ace-112">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="a8ace-113">In dit voor beeld is de naam van de module ' GetProcPSSnapIn01 '.</span><span class="sxs-lookup"><span data-stu-id="a8ace-113">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="a8ace-114">Voeg een open bare eigenschap toe voor de leverancier van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="a8ace-114">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="a8ace-115">In dit voor beeld is de leverancier ' micro soft '.</span><span class="sxs-lookup"><span data-stu-id="a8ace-115">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="a8ace-116">Een open bare eigenschap voor de leveranciers resource van de module toevoegen (optioneel).</span><span class="sxs-lookup"><span data-stu-id="a8ace-116">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a8ace-117">In dit voor beeld is de resource van de leverancier "GetProcPSSnapIn01, micro soft".</span><span class="sxs-lookup"><span data-stu-id="a8ace-117">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="a8ace-118">Voeg een open bare eigenschap toe voor de beschrijving van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="a8ace-118">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="a8ace-119">In dit voor beeld is de beschrijving "Dit is een Windows Power shell-module die de cmdlet Get-proc" registreert.</span><span class="sxs-lookup"><span data-stu-id="a8ace-119">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="a8ace-120">Voeg een open bare eigenschap voor de beschrijvings resource van de module toe (optioneel).</span><span class="sxs-lookup"><span data-stu-id="a8ace-120">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="a8ace-121">In dit voor beeld is de resource van de leverancier ' GetProcPSSnapIn01, dit is een Windows Power shell-module die de Get-proc-cmdlet registreert '.</span><span class="sxs-lookup"><span data-stu-id="a8ace-121">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="a8ace-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a8ace-122">Example</span></span>

<span data-ttu-id="a8ace-123">In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft die kan worden gebruikt om de Get-Proc-cmdlet te registreren in de Windows Power shell-shell.</span><span class="sxs-lookup"><span data-stu-id="a8ace-123">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="a8ace-124">Houd er rekening mee dat in dit voor beeld de volledige assembly alleen de module GetProcPSSnapIn01 en de `Get-Proc` klasse cmdlet bevat.</span><span class="sxs-lookup"><span data-stu-id="a8ace-124">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a8ace-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a8ace-125">See Also</span></span>

<span data-ttu-id="a8ace-126">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="a8ace-126">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="a8ace-127">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="a8ace-127">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
