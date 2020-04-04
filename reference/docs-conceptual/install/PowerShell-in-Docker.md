---
title: PowerShell gebruiken in Docker
description: Power shell gebruiken die vooraf is geïnstalleerd in een docker-installatie kopie.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: f55da6dea4b58a2cd13c7be7c24c07341f177b71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80646376"
---
# <a name="using-powershell-in-docker"></a>PowerShell gebruiken in Docker

Docker-installatie kopieën worden gepubliceerd met vooraf geïnstalleerde Power shell. In dit artikel wordt beschreven hoe u Power shell in de docker-container kunt gaan gebruiken.

## <a name="finding-available-images"></a>Beschikbare installatiekopieën zoeken

De uitgebrachte installatiekopieën hebben Docker 17.05 of hoger nodig. Er wordt ook verwacht dat u Docker kunt uitvoeren zonder `sudo` of lokale beheerdersrechten. Volg de officiële [instructies][install] van Docker om `docker` juist te installeren.

De release containers zijn afgeleid van de officiële distributie kopie, zoals `centos:7`, vervolgens afhankelijkheden installeren en tot slot het Power shell-pakket installeren.

Deze containers zijn live op [hub.docker.com/r/Microsoft/PowerShell][docker-release].

Ga naar de [Power shell-docker-][PowerShell-Docker] opslag plaats op github voor meer informatie over deze docker-installatie kopieën.

## <a name="using-powershell-in-a-container"></a>Power shell in een container gebruiken

In de volgende stappen worden de Docker-opdrachten laten zien die nodig zijn om de installatiekopie te downloaden en een interactieve PowerShell-sessie te starten.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>Verwijder de installatiekopie als deze niet langer nodig is.

De volgende opdracht wordt gebruikt om de docker-installatie kopie te verwijderen wanneer u deze niet meer nodig hebt.

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
