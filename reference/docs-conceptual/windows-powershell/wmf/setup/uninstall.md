---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: WMF 5.0 verwijderen
ms.openlocfilehash: fa76bacb4b62025d0d2350b9a0e072068ca83ab1
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236302"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="b4590-103">Instructies voor verwijderen</span><span class="sxs-lookup"><span data-stu-id="b4590-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="b4590-104">Opdracht prompt gebruiken</span><span class="sxs-lookup"><span data-stu-id="b4590-104">Using Command Prompt</span></span>

1. <span data-ttu-id="b4590-105">Open de **opdracht prompt.**</span><span class="sxs-lookup"><span data-stu-id="b4590-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="b4590-106">Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/kb/934307) uit, zoals hieronder wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="b4590-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/kb/934307) as shown below:</span></span>

<span data-ttu-id="b4590-107">In Windows Server 2012 R2 en Windows 8,1:</span><span class="sxs-lookup"><span data-stu-id="b4590-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="b4590-108">On Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="b4590-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="b4590-109">Op Windows Server 2008 R2 SP1 en Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="b4590-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="b4590-110">Configuratie scherm gebruiken</span><span class="sxs-lookup"><span data-stu-id="b4590-110">Using Control Panel</span></span>

1. <span data-ttu-id="b4590-111">Open **het configuratie scherm.**</span><span class="sxs-lookup"><span data-stu-id="b4590-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="b4590-112">Open **Program ma's**en open vervolgens **een programma verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="b4590-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="b4590-113">Klik op **geïnstalleerde updates weer geven.**</span><span class="sxs-lookup"><span data-stu-id="b4590-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="b4590-114">Selecteer **Windows Management Framework 5,0** in de lijst met geïnstalleerde updates.</span><span class="sxs-lookup"><span data-stu-id="b4590-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="b4590-115">Dit komt overeen met *KB3134758*, *KB3134759*of *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="b4590-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="b4590-116">Klik op **verwijderen.**</span><span class="sxs-lookup"><span data-stu-id="b4590-116">Click **Uninstall.**</span></span>
