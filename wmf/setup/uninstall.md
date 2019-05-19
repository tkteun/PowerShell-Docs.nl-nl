---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verwijderen van WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856187"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="0f650-103">Verwijderen van de installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="0f650-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="0f650-104">Met behulp van de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="0f650-104">Using Command Prompt</span></span>

1. <span data-ttu-id="0f650-105">Open **opdrachtprompt.**</span><span class="sxs-lookup"><span data-stu-id="0f650-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="0f650-106">Voer de [startprogramma voor de zelfstandige versie van de Windows Update](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="0f650-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="0f650-107">Op Windows Server 2012 R2 en Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="0f650-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="0f650-108">On Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="0f650-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="0f650-109">Op Windows Server 2008 R2 SP1 en Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="0f650-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="0f650-110">Via het Configuratiescherm</span><span class="sxs-lookup"><span data-stu-id="0f650-110">Using Control Panel</span></span>

1. <span data-ttu-id="0f650-111">Open **het Configuratiescherm.**</span><span class="sxs-lookup"><span data-stu-id="0f650-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="0f650-112">Open **programma's**en open vervolgens **een programma verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="0f650-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="0f650-113">Klik op **geïnstalleerde updates weergeven.**</span><span class="sxs-lookup"><span data-stu-id="0f650-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="0f650-114">Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates.</span><span class="sxs-lookup"><span data-stu-id="0f650-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="0f650-115">Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="0f650-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="0f650-116">Klik op **verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="0f650-116">Click **Uninstall.**</span></span>
