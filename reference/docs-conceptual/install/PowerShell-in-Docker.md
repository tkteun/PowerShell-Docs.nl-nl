---
title: Power shell gebruiken in docker
description: Power shell gebruiken die vooraf is geïnstalleerd in een docker-installatie kopie.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279948"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="8d030-103">Power shell gebruiken in docker</span><span class="sxs-lookup"><span data-stu-id="8d030-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="8d030-104">Docker-installatie kopieën worden gepubliceerd met vooraf geïnstalleerde Power shell.</span><span class="sxs-lookup"><span data-stu-id="8d030-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="8d030-105">In dit artikel wordt beschreven hoe u Power shell in de docker-container kunt gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8d030-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="8d030-106">Beschik bare installatie kopieën zoeken</span><span class="sxs-lookup"><span data-stu-id="8d030-106">Finding available images</span></span>

<span data-ttu-id="8d030-107">De uitgebrachte installatie kopieën vereisen docker 17,05 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="8d030-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="8d030-108">Er wordt ook verwacht dat u docker kunt uitvoeren zonder `sudo` of lokale beheerders rechten.</span><span class="sxs-lookup"><span data-stu-id="8d030-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="8d030-109">Volg de officiële [instructies][install] van de docker om `docker` correct te installeren.</span><span class="sxs-lookup"><span data-stu-id="8d030-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="8d030-110">De release containers zijn afgeleid van de officiële distributie kopie, zoals `centos:7`, vervolgens afhankelijkheden installeren en tot slot het Power shell-pakket installeren.</span><span class="sxs-lookup"><span data-stu-id="8d030-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="8d030-111">Deze containers zijn live op [hub.docker.com/r/Microsoft/PowerShell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="8d030-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="8d030-112">Ga naar de [Power shell-docker-][PowerShell-Docker] opslag plaats op github voor meer informatie over deze docker-installatie kopieën.</span><span class="sxs-lookup"><span data-stu-id="8d030-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="8d030-113">Power shell in een container gebruiken</span><span class="sxs-lookup"><span data-stu-id="8d030-113">Using PowerShell in a container</span></span>

<span data-ttu-id="8d030-114">In de volgende stappen ziet u de docker-opdrachten die vereist zijn om de installatie kopie te downloaden en een interactieve Power shell-sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="8d030-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="8d030-115">De installatie kopie verwijderen wanneer deze niet meer nodig is</span><span class="sxs-lookup"><span data-stu-id="8d030-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="8d030-116">De volgende opdracht wordt gebruikt om de docker-container te verwijderen wanneer u deze niet meer nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="8d030-116">The following command is used to delete the Docker container when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="8d030-117">Juridisch en licentie verlening</span><span class="sxs-lookup"><span data-stu-id="8d030-117">Legal and Licensing</span></span>

<span data-ttu-id="8d030-118">Power shell is gelicentieerd onder de [MIT-licentie][].</span><span class="sxs-lookup"><span data-stu-id="8d030-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="8d030-119">Windows docker-bestands-en installatie kopie licenties</span><span class="sxs-lookup"><span data-stu-id="8d030-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="8d030-120">Door de container besturingssysteem installatie kopie voor Windows-containers te vragen en te gebruiken, erkent, begrijpt en toestemming voor de aanvullende licentie voorwaarden die beschikbaar zijn op docker hub:</span><span class="sxs-lookup"><span data-stu-id="8d030-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="8d030-121">[Windows Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="8d030-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="8d030-122">[Nano server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="8d030-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="8d030-123">Telemetrie</span><span class="sxs-lookup"><span data-stu-id="8d030-123">Telemetry</span></span>

<span data-ttu-id="8d030-124">Power shell verzamelt standaard beperkte telemetrie zonder persoons gegevens om hulp te bieden aan de ontwikkeling van toekomstige versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8d030-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="8d030-125">Als u geen telemetrie wilt verzenden, maakt u een omgevings variabele met de naam `POWERSHELL_TELEMETRY_OPTOUT` ingesteld op een waarde van `1` voordat Power shell vanaf de geïnstalleerde locatie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="8d030-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="8d030-126">De telemetrie die we verzamelen, valt onder de [privacyverklaring van micro soft][privacy].</span><span class="sxs-lookup"><span data-stu-id="8d030-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-licentie]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
