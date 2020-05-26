---
title: Een aangepaste Windows Power shell-module schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 9cf4499ec2992c6cfea83fc5d0bf51d0bbfaa96a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811133"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="98aeb-102">Een aangepaste Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="98aeb-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="98aeb-103">In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft waarmee specifieke cmdlets worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="98aeb-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="98aeb-104">Met dit type module kunt u opgeven welke cmdlets, providers, typen of indelingen u wilt registreren.</span><span class="sxs-lookup"><span data-stu-id="98aeb-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="98aeb-105">Zie [een Windows Power shell-module schrijven](./writing-a-windows-powershell-snap-in.md)voor meer informatie over het schrijven van een module voor het registreren van alle cmdlets en providers in een assembly.</span><span class="sxs-lookup"><span data-stu-id="98aeb-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="98aeb-106">Een Windows Power shell-module schrijven waarin specifieke cmdlets worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="98aeb-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="98aeb-107">Voeg het kenmerk RunInstallerAttribute toe.</span><span class="sxs-lookup"><span data-stu-id="98aeb-107">Add the RunInstallerAttribute attribute.</span></span>
2. <span data-ttu-id="98aeb-108">Maak een open bare klasse die is afgeleid van de klasse [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="98aeb-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="98aeb-109">In dit voor beeld is de naam van de klasse ' CustomPSSnapinTest '.</span><span class="sxs-lookup"><span data-stu-id="98aeb-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="98aeb-110">Voeg een open bare eigenschap toe voor de naam van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="98aeb-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="98aeb-111">Gebruik bij het benoemen van modules geen van de volgende tekens: `#` , `.` , `,` , `(` , `)` ,,,,,, `{` ,, `}` `[` `]` `&` `-` `/` `\` , `$` , `;` , `:` , `"` ,,, `'` `<` ,, `>` `|` `?` , `@` , `` ` `` ,,,,,,,,,,`*`</span><span class="sxs-lookup"><span data-stu-id="98aeb-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

   <span data-ttu-id="98aeb-112">In dit voor beeld is de naam van de module ' CustomPSSnapInTest '.</span><span class="sxs-lookup"><span data-stu-id="98aeb-112">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="98aeb-113">Voeg een open bare eigenschap toe voor de leverancier van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="98aeb-113">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="98aeb-114">In dit voor beeld is de leverancier ' micro soft '.</span><span class="sxs-lookup"><span data-stu-id="98aeb-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="98aeb-115">Een open bare eigenschap voor de leveranciers resource van de module toevoegen (optioneel).</span><span class="sxs-lookup"><span data-stu-id="98aeb-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="98aeb-116">In dit voor beeld is de resource van de leverancier "CustomPSSnapInTest, micro soft".</span><span class="sxs-lookup"><span data-stu-id="98aeb-116">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="98aeb-117">Voeg een open bare eigenschap toe voor de beschrijving van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="98aeb-117">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="98aeb-118">In dit voor beeld is de beschrijving: ' Dit is een aangepaste Windows Power shell-module die de `Test-HelloWorld` `Test-CustomSnapinTest` cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="98aeb-118">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets".</span></span>

7. <span data-ttu-id="98aeb-119">Voeg een open bare eigenschap voor de beschrijvings resource van de module toe (optioneel).</span><span class="sxs-lookup"><span data-stu-id="98aeb-119">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="98aeb-120">In dit voor beeld is de resource van de leverancier:</span><span class="sxs-lookup"><span data-stu-id="98aeb-120">In this example, the vendor resource is:</span></span>

   > <span data-ttu-id="98aeb-121">CustomPSSnapInTest is dit een aangepaste Windows Power shell-module die de cmdlets test-HelloWorld en test-CustomSnapinTest bevat.</span><span class="sxs-lookup"><span data-stu-id="98aeb-121">CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="98aeb-122">Geef de cmdlets op die deel uitmaken van de aangepaste module (optioneel) met behulp van de klasse [System. Management. Automation. Runspaces. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="98aeb-122">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="98aeb-123">De hier toegevoegde informatie bevat de naam van de cmdlet, het bijbehorende .NET-type en de Help-bestands naam van de cmdlet (de indeling van de Help-bestands naam van de cmdlet moet zijn `name.dll-help.xml` ).</span><span class="sxs-lookup"><span data-stu-id="98aeb-123">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be `name.dll-help.xml`).</span></span>

   <span data-ttu-id="98aeb-124">In dit voor beeld worden de cmdlets test-HelloWorld en TestCustomSnapinTest toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="98aeb-124">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="98aeb-125">Geef de providers op die deel uitmaken van de aangepaste module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="98aeb-125">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="98aeb-126">In dit voor beeld worden geen providers opgegeven.</span><span class="sxs-lookup"><span data-stu-id="98aeb-126">This example does not specify any providers.</span></span>

10. <span data-ttu-id="98aeb-127">Geef de typen op die bij de aangepaste module horen (optioneel).</span><span class="sxs-lookup"><span data-stu-id="98aeb-127">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="98aeb-128">In dit voor beeld worden geen typen opgegeven.</span><span class="sxs-lookup"><span data-stu-id="98aeb-128">This example does not specify any types.</span></span>

11. <span data-ttu-id="98aeb-129">Geef de indelingen op die deel uitmaken van de aangepaste module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="98aeb-129">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="98aeb-130">In dit voor beeld worden geen indelingen opgegeven.</span><span class="sxs-lookup"><span data-stu-id="98aeb-130">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="98aeb-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="98aeb-131">Example</span></span>

<span data-ttu-id="98aeb-132">In dit voor beeld ziet u hoe u een aangepaste Windows Power shell-module schrijft die kan worden gebruikt om de `Test-HelloWorld` cmdlets en te registreren `Test-CustomSnapinTest` .</span><span class="sxs-lookup"><span data-stu-id="98aeb-132">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets.</span></span> <span data-ttu-id="98aeb-133">Houd er rekening mee dat in dit voor beeld de volledige assembly andere cmdlets en providers zou kunnen bevatten die niet door deze module zouden worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="98aeb-133">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="98aeb-134">Zie voor meer informatie over het registreren van modules [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)) in de [hand leiding voor Windows Power shell-programmeurs](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="98aeb-134">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98aeb-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="98aeb-135">See Also</span></span>

<span data-ttu-id="98aeb-136">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="98aeb-136">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="98aeb-137">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="98aeb-137">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
