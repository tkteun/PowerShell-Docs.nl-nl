---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081118"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

In dit voorbeeld laat zien hoe u een providerklasse die is afgeleid rechtstreeks van declareert de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse. Het is hier opgenomen voor de volledigheid.

## <a name="demonstrates"></a>Ziet u

> [!IMPORTANT]
> Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class. Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class. Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).

In dit voorbeeld ziet u het volgende:

- Declareren de `CmdletProvider` kenmerk.

- Het definiëren van een klasse in de provider die is afgeleid rechtstreeks vanuit de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse.

## <a name="example"></a>Voorbeeld

Dit voorbeeld laat zien hoe u een providerklasse definieert en hoe u declareert de `CmdletProvider` kenmerk.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md)