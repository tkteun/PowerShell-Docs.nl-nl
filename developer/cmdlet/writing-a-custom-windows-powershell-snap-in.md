---
title: Schrijven van aangepaste Windows PowerShell module | Microsoft Docs
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
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067022"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="1f2ae-102">Een aangepaste Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="1f2ae-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="1f2ae-103">In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die bepaalde cmdlets registreert.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="1f2ae-104">Met dit type-module kan opgeven u welke cmdlets, providers, typen of indelingen te registreren.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="1f2ae-105">Zie voor meer informatie over het schrijven van een module die de cmdlets en providers in een assembly registreert, [schrijven van een Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="1f2ae-106">Het schrijven van een Windows PowerShell-Snap-in die specifieke cmdlets registreert.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="1f2ae-107">Het kenmerk RunInstallerAttribute toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="1f2ae-108">Maak een openbare klasse die is afgeleid van de [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasse.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="1f2ae-109">In dit voorbeeld is de naam van de klasse 'CustomPSSnapinTest'.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="1f2ae-110">Toevoegen van een openbare eigenschap voor de naam van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="1f2ae-111">Als naming-modules, gebruik dan niet een van de volgende tekens bevatten: #.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="1f2ae-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="1f2ae-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="1f2ae-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="1f2ae-113">@ \` \*</span></span>

   <span data-ttu-id="1f2ae-114">In dit voorbeeld is de naam van de module 'CustomPSSnapInTest'.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="1f2ae-115">Voeg een openbare eigenschap toe voor de leverancier van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="1f2ae-116">In dit voorbeeld wordt is de leverancier 'Microsoft'.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="1f2ae-117">Toevoegen van een openbare eigenschap van de bron van de leverancier van de module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="1f2ae-118">In dit voorbeeld is de leverancierresource 'CustomPSSnapInTest, Microsoft'.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="1f2ae-119">Toevoegen van een openbare eigenschap voor de beschrijving van de module (vereist).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="1f2ae-120">In dit voorbeeld wordt de beschrijving is: 'Dit is een aangepaste Windows PowerShell-module met de Test-HelloWorld en Test-CustomSnapinTest cmdlets'.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="1f2ae-121">Toevoegen van een openbare eigenschap van de bron van de beschrijving van de module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="1f2ae-122">In dit voorbeeld is de leverancierresource "CustomPSSnapInTest, dit is een aangepaste Windows PowerShell-module met de cmdlets voor Test-HelloWorld en Test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="1f2ae-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="1f2ae-123">Geef de cmdlets die deel uitmaken van de aangepaste-module (optioneel) met behulp van de [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klasse.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="1f2ae-124">De informatie die is toegevoegd, bevat de naam van de cmdlet, de .NET-type en de bestandsnaam van de cmdlet Help (is c:\WINNT\system32\inetsrv\bestandsnaam.dll help.xml moet in de indeling van de naam van de cmdlet Help-bestand).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="1f2ae-125">In dit voorbeeld wordt de Test-HelloWorld en TestCustomSnapinTest-cmdlets toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="1f2ae-126">Geef de providers die deel uitmaken van de aangepaste-module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="1f2ae-127">In dit voorbeeld is niet opgegeven voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="1f2ae-128">Geef de typen die deel uitmaken van de aangepaste-module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="1f2ae-129">In dit voorbeeld geeft geen enkel type.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="1f2ae-130">Geef de indelingen die deel uitmaken van de aangepaste-module (optioneel).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="1f2ae-131">In dit voorbeeld geeft geen eventuele indelingen.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="1f2ae-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1f2ae-132">Example</span></span>

<span data-ttu-id="1f2ae-133">In dit voorbeeld laat zien hoe het schrijven van een aangepaste Windows PowerShell-module die kan worden gebruikt om de Test-HelloWorld en Test-CustomSnapinTest-cmdlets te registreren.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="1f2ae-134">Let erop dat in dit voorbeeld wordt de volledige assembly bevatten kan andere cmdlets en providers die niet door deze module zou worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="1f2ae-135">Zie voor meer informatie over het registreren van modules [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in de [Windows PowerShell-programmeergids](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f2ae-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1f2ae-136">See Also</span></span>

[<span data-ttu-id="1f2ae-137">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="1f2ae-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="1f2ae-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="1f2ae-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
