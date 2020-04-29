---
title: PowerShell gebruiken in Docker
description: Power shell gebruiken die vooraf is geïnstalleerd in een docker-installatie kopie.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646376"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="b920c-103">PowerShell gebruiken in Docker</span><span class="sxs-lookup"><span data-stu-id="b920c-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="b920c-104">Docker-installatie kopieën worden gepubliceerd met vooraf geïnstalleerde Power shell.</span><span class="sxs-lookup"><span data-stu-id="b920c-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="b920c-105">In dit artikel wordt beschreven hoe u Power shell in de docker-container kunt gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b920c-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="b920c-106">Beschik bare installatie kopieën zoeken</span><span class="sxs-lookup"><span data-stu-id="b920c-106">Finding available images</span></span>

<span data-ttu-id="b920c-107">De uitgebrachte installatie kopieën vereisen docker 17,05 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="b920c-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="b920c-108">Er wordt ook verwacht dat u docker kunt uitvoeren zonder `sudo` lokale beheerders rechten.</span><span class="sxs-lookup"><span data-stu-id="b920c-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="b920c-109">Volg de officiële [instructies][install] van de docker om `docker` correct te installeren.</span><span class="sxs-lookup"><span data-stu-id="b920c-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="b920c-110">De release containers zijn afgeleid van de officiële distributie kopie, zoals `centos:7`, vervolgens afhankelijkheden installeren en tot slot het Power shell-pakket installeren.</span><span class="sxs-lookup"><span data-stu-id="b920c-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="b920c-111">Deze containers zijn live op [hub.docker.com/r/Microsoft/PowerShell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="b920c-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="b920c-112">Ga naar de [Power shell-docker-][PowerShell-Docker] opslag plaats op github voor meer informatie over deze docker-installatie kopieën.</span><span class="sxs-lookup"><span data-stu-id="b920c-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="b920c-113">Power shell in een container gebruiken</span><span class="sxs-lookup"><span data-stu-id="b920c-113">Using PowerShell in a container</span></span>

<span data-ttu-id="b920c-114">In de volgende stappen ziet u de docker-opdrachten die vereist zijn om de installatie kopie te downloaden en een interactieve Power shell-sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="b920c-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="b920c-115">De installatie kopie verwijderen wanneer deze niet meer nodig is</span><span class="sxs-lookup"><span data-stu-id="b920c-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="b920c-116">De volgende opdracht wordt gebruikt om de docker-installatie kopie te verwijderen wanneer u deze niet meer nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="b920c-116">The following command is used to delete the Docker image when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="b920c-117">Juridisch en licentie verlening</span><span class="sxs-lookup"><span data-stu-id="b920c-117">Legal and Licensing</span></span>

<span data-ttu-id="b920c-118">Power shell is gelicentieerd onder de [MIT-licentie][].</span><span class="sxs-lookup"><span data-stu-id="b920c-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="b920c-119">Windows docker-bestands-en installatie kopie licenties</span><span class="sxs-lookup"><span data-stu-id="b920c-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="b920c-120">Door de container besturingssysteem installatie kopie voor Windows-containers te vragen en te gebruiken, erkent, begrijpt en toestemming voor de aanvullende licentie voorwaarden die beschikbaar zijn op docker hub:</span><span class="sxs-lookup"><span data-stu-id="b920c-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="b920c-121">[Windows Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="b920c-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="b920c-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="b920c-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="b920c-123">Telemetrie</span><span class="sxs-lookup"><span data-stu-id="b920c-123">Telemetry</span></span>

<span data-ttu-id="b920c-124">Power shell verzamelt standaard beperkte telemetrie zonder persoons gegevens om hulp te bieden aan de ontwikkeling van toekomstige versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="b920c-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="b920c-125">Als u geen telemetrie wilt verzenden, maakt u een omgevings `POWERSHELL_TELEMETRY_OPTOUT` variabele met de naam ingesteld `1` op een waarde van voordat Power shell vanaf de geïnstalleerde locatie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="b920c-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="b920c-126">De telemetrie die we verzamelen, valt onder de [privacyverklaring van micro soft][privacy].</span><span class="sxs-lookup"><span data-stu-id="b920c-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

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
