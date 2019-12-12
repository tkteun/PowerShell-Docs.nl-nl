---
title: Scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355508"
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

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
