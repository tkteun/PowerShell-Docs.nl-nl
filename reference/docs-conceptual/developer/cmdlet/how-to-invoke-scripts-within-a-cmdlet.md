---
ms.date: 09/13/2016
ms.topic: reference
title: Scripts in een cmdlet aanroepen
description: Scripts in een cmdlet aanroepen
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667025"
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

    ```c
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
