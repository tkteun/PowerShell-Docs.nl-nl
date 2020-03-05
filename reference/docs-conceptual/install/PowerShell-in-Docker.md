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
# <a name="using-powershell-in-docker"></a>Power shell gebruiken in docker

Docker-installatie kopieën worden gepubliceerd met vooraf geïnstalleerde Power shell. In dit artikel wordt beschreven hoe u Power shell in de docker-container kunt gaan gebruiken.

## <a name="finding-available-images"></a>Beschik bare installatie kopieën zoeken

De uitgebrachte installatie kopieën vereisen docker 17,05 of nieuwer. Er wordt ook verwacht dat u docker kunt uitvoeren zonder `sudo` of lokale beheerders rechten. Volg de officiële [instructies][install] van de docker om `docker` correct te installeren.

De release containers zijn afgeleid van de officiële distributie kopie, zoals `centos:7`, vervolgens afhankelijkheden installeren en tot slot het Power shell-pakket installeren.

Deze containers zijn live op [hub.docker.com/r/Microsoft/PowerShell][docker-release].

Ga naar de [Power shell-docker-][PowerShell-Docker] opslag plaats op github voor meer informatie over deze docker-installatie kopieën.

## <a name="using-powershell-in-a-container"></a>Power shell in een container gebruiken

In de volgende stappen ziet u de docker-opdrachten die vereist zijn om de installatie kopie te downloaden en een interactieve Power shell-sessie te starten.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>De installatie kopie verwijderen wanneer deze niet meer nodig is

De volgende opdracht wordt gebruikt om de docker-container te verwijderen wanneer u deze niet meer nodig hebt.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>Juridisch en licentie verlening

Power shell is gelicentieerd onder de [MIT-licentie][].

### <a name="windows-docker-file-and-image-licenses"></a>Windows docker-bestands-en installatie kopie licenties

Door de container besturingssysteem installatie kopie voor Windows-containers te vragen en te gebruiken, erkent, begrijpt en toestemming voor de aanvullende licentie voorwaarden die beschikbaar zijn op docker hub:

- [Windows Server Core][Window Server Core]
- [Nano server][Nano Server]

### <a name="telemetry"></a>Telemetrie

Power shell verzamelt standaard beperkte telemetrie zonder persoons gegevens om hulp te bieden aan de ontwikkeling van toekomstige versies van Power shell. Als u geen telemetrie wilt verzenden, maakt u een omgevings variabele met de naam `POWERSHELL_TELEMETRY_OPTOUT` ingesteld op een waarde van `1` voordat Power shell vanaf de geïnstalleerde locatie wordt gestart. De telemetrie die we verzamelen, valt onder de [privacyverklaring van micro soft][privacy].

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-licentie]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
