---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="1b920-102">Instructies voor het verwijderen</span><span class="sxs-lookup"><span data-stu-id="1b920-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="1b920-103">Vanaf een opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="1b920-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="1b920-104">Open **opdrachtprompt.**</span><span class="sxs-lookup"><span data-stu-id="1b920-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="1b920-105">Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="1b920-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="1b920-106">Op Windows Server 2012 R2 en Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="1b920-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="1b920-107">On Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="1b920-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="1b920-108">Op Windows Server 2008 R2 SP1 en Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="1b920-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="1b920-109">Via het Configuratiescherm</span><span class="sxs-lookup"><span data-stu-id="1b920-109">Using Control Panel</span></span>
1.  <span data-ttu-id="1b920-110">Open **het Configuratiescherm.**</span><span class="sxs-lookup"><span data-stu-id="1b920-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="1b920-111">Open **programma's**, open vervolgens **een programma verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="1b920-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="1b920-112">Klik op **geïnstalleerde updates weergeven.**</span><span class="sxs-lookup"><span data-stu-id="1b920-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="1b920-113">Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates.</span><span class="sxs-lookup"><span data-stu-id="1b920-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="1b920-114">Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="1b920-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="1b920-115">Klik op **verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="1b920-115">Click **Uninstall.**</span></span>