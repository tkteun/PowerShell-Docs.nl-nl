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
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851952"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Een aangepaste Windows PowerShell-module schrijven

In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die bepaalde cmdlets registreert.

Met dit type-module kan opgeven u welke cmdlets, providers, typen of indelingen te registreren. Zie voor meer informatie over het schrijven van een module die de cmdlets en providers in een assembly registreert, [schrijven van een Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Het schrijven van een Windows PowerShell-Snap-in die specifieke cmdlets registreert.

1. Het kenmerk RunInstallerAttribute toevoegen.

2. Maak een openbare klasse die is afgeleid van de [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasse.

   In dit voorbeeld is de naam van de klasse 'CustomPSSnapinTest'.

3. Toevoegen van een openbare eigenschap voor de naam van de module (vereist). Als naming-modules, gebruik dan niet een van de volgende tekens bevatten: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   In dit voorbeeld is de naam van de module 'CustomPSSnapInTest'.

4. Voeg een openbare eigenschap toe voor de leverancier van de module (vereist).

   In dit voorbeeld wordt is de leverancier 'Microsoft'.

5. Toevoegen van een openbare eigenschap van de bron van de leverancier van de module (optioneel).

   In dit voorbeeld is de leverancierresource 'CustomPSSnapInTest, Microsoft'.

6. Toevoegen van een openbare eigenschap voor de beschrijving van de module (vereist).

   In dit voorbeeld wordt de beschrijving is: 'Dit is een aangepaste Windows PowerShell-module met de Test-HelloWorld en Test-CustomSnapinTest cmdlets'.

7. Toevoegen van een openbare eigenschap van de bron van de beschrijving van de module (optioneel).

   In dit voorbeeld is de leverancierresource "CustomPSSnapInTest, dit is een aangepaste Windows PowerShell-module met de cmdlets voor Test-HelloWorld en Test-CustomSnapinTest".

8. Geef de cmdlets die deel uitmaken van de aangepaste-module (optioneel) met behulp van de [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klasse. De informatie die is toegevoegd, bevat de naam van de cmdlet, de .NET-type en de bestandsnaam van de cmdlet Help (is c:\WINNT\system32\inetsrv\bestandsnaam.dll help.xml moet in de indeling van de naam van de cmdlet Help-bestand).

   In dit voorbeeld wordt de Test-HelloWorld en TestCustomSnapinTest-cmdlets toegevoegd.

9. Geef de providers die deel uitmaken van de aangepaste-module (optioneel).

   In dit voorbeeld is niet opgegeven voor alle providers.

10. Geef de typen die deel uitmaken van de aangepaste-module (optioneel).

    In dit voorbeeld geeft geen enkel type.

11. Geef de indelingen die deel uitmaken van de aangepaste-module (optioneel).

    In dit voorbeeld geeft geen eventuele indelingen.

## <a name="example"></a>Voorbeeld

In dit voorbeeld laat zien hoe het schrijven van een aangepaste Windows PowerShell-module die kan worden gebruikt om de Test-HelloWorld en Test-CustomSnapinTest-cmdlets te registreren. Let erop dat in dit voorbeeld wordt de volledige assembly bevatten kan andere cmdlets en providers die niet door deze module zou worden geregistreerd.

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

Zie voor meer informatie over het registreren van modules [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in de [Windows PowerShell-programmeergids](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Zie ook

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
