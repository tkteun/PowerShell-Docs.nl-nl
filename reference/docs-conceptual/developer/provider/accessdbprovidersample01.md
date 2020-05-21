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
ms.openlocfilehash: 67c2b6cfd36a805fce25bf0c7c55db56ec14092c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690920"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

In dit voor beeld ziet u hoe u een provider klasse declareert die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Deze is alleen opgenomen voor volledigheid.

## <a name="demonstrates"></a>Demonstreert

> [!IMPORTANT]
> Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:
>
> - Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.

- Een provider klasse definiëren die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u een provider klasse definieert en hoe u het kenmerk declareert `CmdletProvider` .

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

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
