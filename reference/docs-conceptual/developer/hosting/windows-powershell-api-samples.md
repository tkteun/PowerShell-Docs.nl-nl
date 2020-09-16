---
title: Windows Power shell-API-voor beelden | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780165"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="16141-102">Voorbeelden van Windows PowerShell-API's</span><span class="sxs-lookup"><span data-stu-id="16141-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="16141-103">Deze sectie bevat voorbeeld code die laat zien hoe u runspaces maakt die de functionaliteit beperkt en hoe u opdrachten asynchroon uitvoert met behulp van een runs Pace-groep om de runspaces op te geven.</span><span class="sxs-lookup"><span data-stu-id="16141-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="16141-104">U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="16141-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="16141-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="16141-105">In This Section</span></span>

<span data-ttu-id="16141-106">[PowerShell01](./windows-powershell01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gebruikt om de functionaliteit van een runs Pace te beperken.</span><span class="sxs-lookup"><span data-stu-id="16141-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="16141-107">De uitvoer van dit voor beeld laat zien hoe u de taal modus van de runs Pace kunt beperken, hoe u een cmdlet als privé markeert, hoe u cmdlets en providers toevoegt en verwijdert, hoe u een proxy opdracht toevoegt, en meer.</span><span class="sxs-lookup"><span data-stu-id="16141-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="16141-108">[PowerShell02](./windows-powershell02-sample.md) -voor beeld In dit voor beeld ziet u hoe u opdrachten asynchroon uitvoert met behulp van de runspaces van een runs Pace-groep.</span><span class="sxs-lookup"><span data-stu-id="16141-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="16141-109">Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="16141-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>
