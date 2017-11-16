---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="5ba7f-102">Instructies voor het verwijderen</span><span class="sxs-lookup"><span data-stu-id="5ba7f-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="5ba7f-103">Vanaf een opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="5ba7f-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="5ba7f-104">Open **opdrachtprompt.**</span><span class="sxs-lookup"><span data-stu-id="5ba7f-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="5ba7f-105">Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="5ba7f-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="5ba7f-106">Op Windows Server 2012 R2 en Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="5ba7f-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="5ba7f-107">In WindowsServer 2012:</span><span class="sxs-lookup"><span data-stu-id="5ba7f-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="5ba7f-108">Op Windows Server 2008 R2 SP1 en Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="5ba7f-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="5ba7f-109">Via het Configuratiescherm</span><span class="sxs-lookup"><span data-stu-id="5ba7f-109">Using Control Panel</span></span>
1.  <span data-ttu-id="5ba7f-110">Open **het Configuratiescherm.**</span><span class="sxs-lookup"><span data-stu-id="5ba7f-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="5ba7f-111">Open **programma's**, open vervolgens **een programma verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="5ba7f-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="5ba7f-112">Klik op **geïnstalleerde updates weergeven.**</span><span class="sxs-lookup"><span data-stu-id="5ba7f-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="5ba7f-113">Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates.</span><span class="sxs-lookup"><span data-stu-id="5ba7f-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="5ba7f-114">Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="5ba7f-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="5ba7f-115">Klik op **verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="5ba7f-115">Click **Uninstall.**</span></span>

