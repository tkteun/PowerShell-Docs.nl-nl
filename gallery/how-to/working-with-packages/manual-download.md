---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery
title: Pakket handmatig downloaden
ms.openlocfilehash: af628f99befe50c16c2c0c60f1a352647af34ff4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054867"
---
# <a name="manual-package-download"></a>Pakket handmatig downloaden

De PowerShell Gallery biedt ondersteuning voor downloaden van een pakket van de website rechtstreeks, zonder gebruik van de PowerShellGet-cmdlets. U kunt een pakket downloaden als een NuGet-pakket (.nupkg)-bestand, dat u vervolgens naar een interne opslagplaats kopiëren kunt.

> [!NOTE]
> Handmatige pakket downloaden is **niet** bedoeld als vervanging voor de cmdlet Install-Module.
> Downloaden van het pakket wordt niet geïnstalleerd voor de module of het script. Afhankelijkheden zijn niet opgenomen in het NuGet-pakket gedownload. De volgende instructies zijn alleen bedoeld ter referentie opgegeven.

## <a name="using-manual-download-to-acquire-a-package"></a>Gebruik van handmatig worden gedownload voor het verkrijgen van een pakket

Elke pagina bevat een koppeling voor het handmatig downloaden, zoals hier wordt weergegeven:

![Handmatig worden gedownload](../../Images/packagedisplaypagewithpseditions.png)

Handmatig downloaden, klikt u op **downloaden van het bestand onbewerkte nupkg**. Een kopie van het pakket gekopieerd naar de downloadmap voor uw browser met de naam van de `<name>.<version>.nupkg`.

Een NuGet-pakket is een ZIP-archief met extra bestanden met informatie over de inhoud van het pakket. Sommige browsers, zoals Internet Explorer automatisch vervangen door de `.nupkg` bestandsextensie met `.zip`. Wijzig om uit te breiden het pakket, de naam van de `.nupkg` van het bestand in `.zip`, indien nodig, klikt u vervolgens de inhoud uitpakken naar een lokale map.

Een NuGet-pakket-bestand bevat de volgende NuGet-specifieke elementen die geen deel uitmaken van de oorspronkelijke verpakte code:

- Een map met de naam `_rels` -bevat een `.rels` bestand de afhankelijkheden bevat
- Een map met de naam `package` -bevat de NuGet-specifieke gegevens
- Een bestand met de naam `[Content_Types].xml` -beschrijving van de werking van extensies als PowerShellGet met NuGet
- Een bestand met de naam `<name>.nuspec` -het grootste deel van de metagegevens bevat

## <a name="installing-powershell-modules-from-a-nuget-package"></a>PowerShell-Modules installeren vanaf een NuGet-pakket

> [!NOTE]
> Deze instructies **niet** krijgt u hetzelfde resultaat als het uitvoeren `Install-Module`. Deze instructies te voldoen aan de minimale vereisten voldoet. Ze zijn niet bedoeld als vervanging voor `Install-Module`. Sommige stappen die worden uitgevoerd door `Install-Module` zijn niet opgenomen.

De beste aanpak is het verwijderen van de NuGet-specifieke elementen uit de map. Hierdoor blijft de PowerShell-code die zijn gemaakt door de auteur van het pakket. De stappen zijn:

1. Pak de inhoud van het NuGet-pakket naar een lokale map.
2. NuGet-specifieke elementen verwijderen uit de map.
3. Wijzig de naam van de map. De standaardnaam van de map is meestal `<name>.<version>`. De versie kan bevatten "-prerelease ' als de module is gemarkeerd als een prerelease-versie. Wijzig de naam van de map tot alleen de modulenaam. Bijvoorbeeld, wordt 'azurerm.storage.5.0.4-preview' 'azurerm.storage'.
4. Kopieer de map naar een van de mappen in de `$env:PSModulePath value`. `$env:PSModulePath` is een door puntkomma's gescheiden reeks paden waarin PowerShell er voor modules ziet.

> [!IMPORTANT]
> Bevat geen eventuele afhankelijkheden vereist door de module voor het handmatig worden gedownload. Als het pakket afhankelijkheden heeft, moeten ze worden geïnstalleerd op het systeem voor deze module correct te laten werken. De PowerShell-galerie bevat alle afhankelijkheden die zijn vereist voor het pakket.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>PowerShell-Scripts van een NuGet-pakket installeren

> [!NOTE]
> Deze instructies **niet** krijgt u hetzelfde resultaat als het uitvoeren `Install-Script`. Deze instructies te voldoen aan de minimale vereisten voldoet. Ze zijn niet bedoeld als vervanging voor `Install-Script`.

De eenvoudigste methode is rechtstreeks en gebruik het script vervolgens uitpakken het NuGet-pakket. De stappen zijn:

1. Pak de inhoud van het NuGet-pakket.
2. De `.PS1` bestand in de map rechtstreeks vanaf deze locatie kan worden gebruikt.
3. U kunt de NuGet-specifieke elementen in de map verwijderen.

> [!IMPORTANT]
> Bevat geen eventuele afhankelijkheden vereist door de module voor het handmatig worden gedownload. Als het pakket afhankelijkheden heeft, moeten ze worden geïnstalleerd op het systeem voor deze module correct te laten werken. De PowerShell-galerie bevat alle afhankelijkheden die zijn vereist voor het pakket.
