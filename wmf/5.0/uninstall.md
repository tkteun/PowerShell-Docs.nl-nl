---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688523"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="74a45-102">Verwijderen van de installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="74a45-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="74a45-103">Met behulp van de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="74a45-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="74a45-104">Open **opdrachtprompt.**</span><span class="sxs-lookup"><span data-stu-id="74a45-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="74a45-105">Voer de [startprogramma voor de zelfstandige versie van de Windows Update](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="74a45-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="74a45-106">Op Windows Server 2012 R2 en Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="74a45-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="74a45-107">On Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="74a45-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="74a45-108">Op Windows Server 2008 R2 SP1 en Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="74a45-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="74a45-109">Via het Configuratiescherm</span><span class="sxs-lookup"><span data-stu-id="74a45-109">Using Control Panel</span></span>
1.  <span data-ttu-id="74a45-110">Open **het Configuratiescherm.**</span><span class="sxs-lookup"><span data-stu-id="74a45-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="74a45-111">Open **programma's**en open vervolgens **een programma verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="74a45-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="74a45-112">Klik op **geïnstalleerde updates weergeven.**</span><span class="sxs-lookup"><span data-stu-id="74a45-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="74a45-113">Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates.</span><span class="sxs-lookup"><span data-stu-id="74a45-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="74a45-114">Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="74a45-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="74a45-115">Klik op **verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="74a45-115">Click **Uninstall.**</span></span>
