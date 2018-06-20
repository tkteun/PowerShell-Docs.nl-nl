---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217988"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="56d84-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="56d84-102">New-TemporaryFile</span></span>
<span data-ttu-id="56d84-103">Soms moet u in uw scripts, een tijdelijk bestand maken.</span><span class="sxs-lookup"><span data-stu-id="56d84-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="56d84-104">U kunt eenvoudig doen met de **nieuw TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="56d84-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="56d84-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="56d84-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="56d84-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="56d84-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="56d84-107">C:\\gebruikers\\slee\\AppData\\lokale\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="56d84-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
