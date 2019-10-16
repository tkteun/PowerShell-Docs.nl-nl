---
title: Windows Power shell-API-voor beelden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353002"
---
# <a name="windows-powershell-api-samples"></a>Voorbeelden van Windows PowerShell-API's

Deze sectie bevat voorbeeld code die laat zien hoe u runspaces maakt die de functionaliteit beperkt en hoe u opdrachten asynchroon uitvoert met behulp van een runs Pace-groep om de runspaces op te geven. U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.

## <a name="in-this-section"></a>In deze sectie

[PowerShell01](./windows-powershell01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een object [System. Management. Automation. Runspaces. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) kunt gebruiken om de functionaliteit van een runs Pace te beperken. De uitvoer van dit voor beeld laat zien hoe u de taal modus van de runs Pace kunt beperken, hoe u een cmdlet als privé markeert, hoe u cmdlets en providers toevoegt en verwijdert, hoe u een proxy opdracht toevoegt, en meer.

[PowerShell02](./windows-powershell02-sample.md) -voor beeld In dit voor beeld ziet u hoe u opdrachten asynchroon uitvoert met behulp van de runspaces van een runs Pace-groep. Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.