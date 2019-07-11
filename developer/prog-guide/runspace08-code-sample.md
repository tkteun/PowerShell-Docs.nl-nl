---
title: Codevoorbeeld RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734910"
---
# <a name="runspace08-code-sample"></a>Runspace08-codevoorbeeld

Hier volgt de broncode voor het voorbeeld Runspace08 die zijn beschreven [het maken van een toepassing die wordt toegevoegd Consoleparameters aan een opdracht](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Deze voorbeeldtoepassing maakt een runspace, wordt een pijplijn gemaakt, worden twee opdrachten toegevoegd aan de pijplijn, voegt u twee parameters toe aan de tweede opdracht en voert de pijplijn. De opdrachten die worden toegevoegd aan de pijplijn zijn de `Get-Process` en `Sort-Object` cmdlets.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)