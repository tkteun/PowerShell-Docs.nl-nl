---
title: Voorbeelden van Windows PowerShell API | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850153"
---
# <a name="windows-powershell-api-samples"></a>Voorbeelden van Windows PowerShell-API's

In deze sectie bevat voorbeelden van code die laat zien over het maken van runspaces met functionaliteit beperkte en het asynchroon uitvoeren van opdrachten met behulp van een groep runspace om op te geven van de runspaces. Microsoft Visual Studio kunt u een consoletoepassing maken en kopieer vervolgens de code van de onderwerpen in deze sectie in uw hosttoepassing.

## <a name="in-this-section"></a>In deze sectie

[Voorbeeld van PowerShell01](./windows-powershell01-sample.md) in dit voorbeeld laat zien hoe u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object om de functionaliteit van een runspace te beperken. De uitvoer van dit voorbeeld ziet u hoe u beperken van de taalmodus van de runspace, het markeren van een cmdlet als privégegevens, toevoegen en verwijderen-cmdlets en providers, het toevoegen van een proxy-opdracht, en meer.

[Voorbeeld van PowerShell02](./windows-powershell02-sample.md) in dit voorbeeld laat zien hoe u opdrachten asynchroon uitvoeren met behulp van de runspaces van een groep runspace. Het voorbeeld genereert een lijst met opdrachten en vervolgens deze opdrachten worden uitgevoerd terwijl de Windows PowerShell-engine wordt een runspace geopend uit de pool wanneer dat nodig is.