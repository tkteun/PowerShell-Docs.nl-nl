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
# <a name="writing-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module schrijven

In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die kan worden gebruikt voor het registreren van de cmdlets en providers van Windows PowerShell in een assembly.

Met dit type-module kan selecteert u niet welke cmdlets en providers die u wilt registreren. Zie voor het schrijven van een module die kunt u selecteren wat is geregistreerd, [schrijven van een aangepaste Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module schrijven

1. Het kenmerk RunInstallerAttribute toevoegen.

2. Maak een openbare klasse die is afgeleid van de [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) klasse.

    In dit voorbeeld is de naam van de klasse 'GetProcPSSnapIn01'.

3. Toevoegen van een openbare eigenschap voor de naam van de module (vereist). Als naming-modules, gebruik dan niet een van de volgende tekens bevatten: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    In dit voorbeeld is de naam van de module 'GetProcPSSnapIn01'.

4. Voeg een openbare eigenschap toe voor de leverancier van de module (vereist).

    In dit voorbeeld wordt is de leverancier 'Microsoft'.

5. Toevoegen van een openbare eigenschap van de bron van de leverancier van de module (optioneel).

    In dit voorbeeld is de leverancierresource 'GetProcPSSnapIn01, Microsoft'.

6. Toevoegen van een openbare eigenschap voor de beschrijving van de module (vereist).

    In dit voorbeeld wordt is de beschrijving "Dit is een Windows PowerShell-module die de cmdlet get-proc registreert".

7. Toevoegen van een openbare eigenschap van de bron van de beschrijving van de module (optioneel).

    In dit voorbeeld is de leverancierresource "GetProcPSSnapIn01, dit is een Windows PowerShell-module die de cmdlet get-proc registreert".

## <a name="example"></a>Voorbeeld

In dit voorbeeld laat zien hoe het schrijven van een Windows PowerShell-module die kan worden gebruikt voor het registreren van de cmdlet Get-procedure in de Windows PowerShell-shell. Let erop dat in dit voorbeeld wordt de volledige assembly alleen de GetProcPSSnapIn01-module-klasse en de cmdlet Get-Proc klasse bevatten zou.

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

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
