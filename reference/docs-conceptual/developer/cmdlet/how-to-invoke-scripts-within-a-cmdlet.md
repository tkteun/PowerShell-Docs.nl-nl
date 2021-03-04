---
ms.date: 09/13/2016
ms.topic: reference
title: Scripts in een cmdlet aanroepen
description: Scripts in een cmdlet aanroepen
ms.openlocfilehash: 503ecb8913fe61ef3f5ec6fe969c22c2319a4f12
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685342"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Scripts in een cmdlet aanroepen

In dit voor beeld ziet u hoe u een script aanroept dat wordt geleverd aan een cmdlet. Het script wordt uitgevoerd door de cmdlet en de resultaten worden geretourneerd naar de cmdlet als een verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten.

## <a name="to-invoke-a-script-block"></a>Een script blok aanroepen

1. Met deze opdracht wordt gecontroleerd of een script blok is opgegeven bij de cmdlet. Als een script blok is opgegeven, roept de opdracht het script blok aan met de vereiste para meters.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Vervolgens doorloopt het script de geretourneerde verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten en voert u de benodigde bewerkingen uit.

    ```csharp
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
