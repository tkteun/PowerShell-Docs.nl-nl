---
title: Een Windows Power shell-module schrijven | Microsoft Docs
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
ms.openlocfilehash: d12a66e354a23041fffb0f8fa286c849849ec2b0
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811112"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module schrijven

In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft die kan worden gebruikt voor het registreren van alle cmdlets en Windows Power shell-providers in een assembly.

Met dit type module selecteert u niet welke cmdlets en providers u wilt registreren. Zie [een aangepaste Windows Power shell-module schrijven](./writing-a-custom-windows-powershell-snap-in.md)voor informatie over het schrijven van een module waarmee u kunt selecteren wat er is geregistreerd.

### <a name="writing-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module schrijven

1. Voeg het kenmerk RunInstallerAttribute toe.

2. Maak een open bare klasse die is afgeleid van de klasse [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .

    In dit voor beeld is de naam van de klasse ' GetProcPSSnapIn01 '.

3. Voeg een open bare eigenschap toe voor de naam van de module (vereist). Gebruik bij het benoemen van modules geen van de volgende tekens: `#` , `.` , `,` , `(` , `)` ,,,,,, `{` ,, `}` `[` `]` `&` `-` `/` `\` , `$` , `;` , `:` , `"` ,,, `'` `<` ,, `>` `|` `?` , `@` , `` ` `` ,,,,,,,,,,`*`

    In dit voor beeld is de naam van de module ' GetProcPSSnapIn01 '.

4. Voeg een open bare eigenschap toe voor de leverancier van de module (vereist).

    In dit voor beeld is de leverancier ' micro soft '.

5. Een open bare eigenschap voor de leveranciers resource van de module toevoegen (optioneel).

    In dit voor beeld is de resource van de leverancier "GetProcPSSnapIn01, micro soft".

6. Voeg een open bare eigenschap toe voor de beschrijving van de module (vereist).

    In dit voor beeld is de beschrijving "Dit is een Windows Power shell-module die de cmdlet Get-proc" registreert.

7. Voeg een open bare eigenschap voor de beschrijvings resource van de module toe (optioneel).

    In dit voor beeld is de resource van de leverancier ' GetProcPSSnapIn01, dit is een Windows Power shell-module die de Get-proc-cmdlet registreert '.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u een Windows Power shell-module schrijft die kan worden gebruikt om de cmdlet Get-proc te registreren in de Windows Power shell-shell. Houd er rekening mee dat in dit voor beeld de volledige assembly alleen de module GetProcPSSnapIn01 en de `Get-Proc` klasse cmdlet bevat.

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

## <a name="see-also"></a>Zie ook

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Windows Power shell shell SDK](../windows-powershell-reference.md)
