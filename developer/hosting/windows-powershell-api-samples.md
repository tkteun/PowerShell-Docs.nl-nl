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
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="7a424-102">Voorbeelden van Windows PowerShell-API's</span><span class="sxs-lookup"><span data-stu-id="7a424-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="7a424-103">In deze sectie bevat voorbeelden van code die laat zien over het maken van runspaces met functionaliteit beperkte en het asynchroon uitvoeren van opdrachten met behulp van een groep runspace om op te geven van de runspaces.</span><span class="sxs-lookup"><span data-stu-id="7a424-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="7a424-104">Microsoft Visual Studio kunt u een consoletoepassing maken en kopieer vervolgens de code van de onderwerpen in deze sectie in uw hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="7a424-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7a424-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="7a424-105">In This Section</span></span>

<span data-ttu-id="7a424-106">[Voorbeeld van PowerShell01](./windows-powershell01-sample.md) in dit voorbeeld laat zien hoe u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object om de functionaliteit van een runspace te beperken.</span><span class="sxs-lookup"><span data-stu-id="7a424-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="7a424-107">De uitvoer van dit voorbeeld ziet u hoe u beperken van de taalmodus van de runspace, het markeren van een cmdlet als privégegevens, toevoegen en verwijderen-cmdlets en providers, het toevoegen van een proxy-opdracht, en meer.</span><span class="sxs-lookup"><span data-stu-id="7a424-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="7a424-108">[Voorbeeld van PowerShell02](./windows-powershell02-sample.md) in dit voorbeeld laat zien hoe u opdrachten asynchroon uitvoeren met behulp van de runspaces van een groep runspace.</span><span class="sxs-lookup"><span data-stu-id="7a424-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="7a424-109">Het voorbeeld genereert een lijst met opdrachten en vervolgens deze opdrachten worden uitgevoerd terwijl de Windows PowerShell-engine wordt een runspace geopend uit de pool wanneer dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="7a424-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>