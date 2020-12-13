---
ms.date: 09/13/2016
ms.topic: reference
title: Een aangepaste Windows PowerShell-module schrijven
description: Een aangepaste Windows PowerShell-module schrijven
ms.openlocfilehash: e79c0c3db583fa0add9287745e97958a71360592
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659539"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Een aangepaste Windows PowerShell-module schrijven

In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft waarmee specifieke cmdlets worden geregistreerd.

Met dit type module kunt u opgeven welke cmdlets, providers, typen of indelingen u wilt registreren. Zie [een Windows Power shell-module schrijven](./writing-a-windows-powershell-snap-in.md)voor meer informatie over het schrijven van een module voor het registreren van alle cmdlets en providers in een assembly.

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Een Windows Power shell-module schrijven waarin specifieke cmdlets worden geregistreerd.

1. Voeg het kenmerk RunInstallerAttribute toe.
2. Maak een open bare klasse die is afgeleid van de klasse [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

   In dit voor beeld is de naam van de klasse ' CustomPSSnapinTest '.

3. Voeg een open bare eigenschap toe voor de naam van de module (vereist). Gebruik bij het benoemen van modules geen van de volgende tekens: `#` , `.` , `,` , `(` , `)` ,,,,,, `{` ,, `}` `[` `]` `&` `-` `/` `\` , `$` , `;` , `:` , `"` ,,, `'` `<` ,, `>` `|` `?` , `@` , `` ` `` ,,,,,,,,,, `*`

   In dit voor beeld is de naam van de module ' CustomPSSnapInTest '.

4. Voeg een open bare eigenschap toe voor de leverancier van de module (vereist).

   In dit voor beeld is de leverancier ' micro soft '.

5. Een open bare eigenschap voor de leveranciers resource van de module toevoegen (optioneel).

   In dit voor beeld is de resource van de leverancier "CustomPSSnapInTest, micro soft".

6. Voeg een open bare eigenschap toe voor de beschrijving van de module (vereist).

   In dit voor beeld is de beschrijving: ' Dit is een aangepaste Windows Power shell-module die de `Test-HelloWorld` `Test-CustomSnapinTest` cmdlets bevat.

7. Voeg een open bare eigenschap voor de beschrijvings resource van de module toe (optioneel).

   In dit voor beeld is de resource van de leverancier:

   > CustomPSSnapInTest is dit een aangepaste Windows Power shell-module die de Test-HelloWorld en Test-CustomSnapinTest-cmdlets bevat.

8. Geef de cmdlets op die deel uitmaken van de aangepaste module (optioneel) met behulp van de klasse [System. Management. Automation. Runspaces. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) . De hier toegevoegde informatie bevat de naam van de cmdlet, het bijbehorende .NET-type en de Help-bestands naam van de cmdlet (de indeling van de Help-bestands naam van de cmdlet moet zijn `name.dll-help.xml` ).

   In dit voor beeld worden de cmdlets Test-HelloWorld en TestCustomSnapinTest toegevoegd.

9. Geef de providers op die deel uitmaken van de aangepaste module (optioneel).

   In dit voor beeld worden geen providers opgegeven.

10. Geef de typen op die bij de aangepaste module horen (optioneel).

    In dit voor beeld worden geen typen opgegeven.

11. Geef de indelingen op die deel uitmaken van de aangepaste module (optioneel).

    In dit voor beeld worden geen indelingen opgegeven.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u een aangepaste Windows Power shell-module schrijft die kan worden gebruikt om de `Test-HelloWorld` cmdlets en te registreren `Test-CustomSnapinTest` . Houd er rekening mee dat in dit voor beeld de volledige assembly andere cmdlets en providers zou kunnen bevatten die niet door deze module zouden worden geregistreerd.

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

Zie voor meer informatie over het registreren van modules [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)) in de [hand leiding voor Windows Power shell-programmeurs](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Zie ook

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Windows Power shell shell SDK](../windows-powershell-reference.md)
