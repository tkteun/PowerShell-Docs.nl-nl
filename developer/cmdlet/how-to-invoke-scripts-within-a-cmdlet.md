---
title: Het aanroepen van Scripts in een Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846695"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Scripts in een cmdlet aanroepen

In dit voorbeeld laat zien hoe een script dat wordt doorgegeven aan een cmdlet aanroepen. Het script is uitgevoerd door de cmdlet en de resultaten worden geretourneerd aan de cmdlet als een verzameling van [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objecten.

## <a name="to-invoke-a-script-block"></a>Om aan te roepen, een scriptblok

1. De opdracht wordt gecontroleerd of een scriptblok is opgegeven aan de cmdlet. Als een scriptblok is opgegeven, roept de opdracht in het scriptblok met de vereiste parameters.

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

2. Vervolgens de resulterende verzameling van het script doorloopt [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objecten en de noodzakelijke bewerkingen uit te voeren.

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
