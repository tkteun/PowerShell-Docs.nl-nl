---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: De PowerShell-galerie
ms.openlocfilehash: 9fe341e4b297764321f3b3f07caca8ef4b8b40e0
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
# <a name="the-powershell-gallery"></a>De PowerShell-galerie

De PowerShell-galerie is de centrale opslagplaats voor PowerShell-inhoud. U vindt nieuwe PowerShell-opdrachten of Desired State Configuration (DSC) resources in de galerie.

## <a name="powershellget-overview"></a>Overzicht van PowerShellGet

De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van PowerShell-artefacten, zoals Modules, DSC-Resources, rol mogelijkheden en -Scripts uit de [PowerShell Gallery](https://www.PowerShellGallery.com) en andere persoonlijke opslagplaatsen.

## <a name="getting-started-with-the-gallery"></a>Aan de slag met de galerie

Installeren van items uit de galerie, is de meest recente versie van de module PowerShellGet, die beschikbaar is in Windows 10, in Windows Management Framework (WMF) 5.0 of in het installatieprogramma (MSI) gebaseerde (voor PowerShell 3 en 4) vereist.

- [**Ophalen van Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Ophalen van WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), of
- [**MSI-Installer ophalen**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Met de meest recente [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) -module, kunt u:

-   Zoekopdracht in de items in de galerie met [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) en [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Items opslaan in uw systeem uit de galerie met [opslaan-Module](https://go.microsoft.com/fwlink/?LinkId=821669) en [opslaan-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Installeren van items uit de galerie met [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) en [Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Items uploaden naar de galerie met [publiceren-Module](https://go.microsoft.com/fwlink/?LinkId=821666) en [publiceren-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Toevoegen van uw eigen aangepaste opslagplaats met [registreren PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Bekijk de [aan de slag](psgallery/psgallery_gettingstarted.md) pagina voor meer informatie over het gebruik van PowerShellGet opdrachten in de galerie. U kunt ook uitvoeren *Update-Help-Module PowerShellGet* om lokale help voor deze opdrachten te installeren.

## <a name="supported-operating-systems"></a>Ondersteunde besturingssystemen

De **PowerShellGet** module vereist **PowerShell 3.0 of hoger**.

Daarom **PowerShellGet** moet een van de volgende besturingssystemen:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** vereist ook .NET Framework 4.5 of hoger. U kunt installeren .NET Framework 4.5 of hoger van [hier](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Hebt u een vraag? Hebt u feedback?

Meer informatie over de PowerShell-galerie en PowerShellGet vindt u in de [aan de slag](psgallery/psgallery_gettingstarted.md) pagina. Geef feedback en rapport problemen met [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

