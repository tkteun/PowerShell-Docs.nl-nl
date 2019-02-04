---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery, GDPR
title: PowerShell Gallery GDPR-naleving
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687816"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell Gallery GDPR-naleving

## <a name="overview"></a>Overzicht

In mei 2018 kracht een Europese wetgeving, de General Data Protection Regulation (GDPR).
De AVG legt een nieuwe regels voor bedrijven, overheidsinstellingen worden gesteld, non-profitorganisaties en andere organisaties die aanbieding goederen en diensten naar mensen in de Europese Unie (EU) of die verzamelen en analyseren van gegevens van inwoners van de EU.
De AVG is van toepassing, ongeacht waar u zich bevinden.

> [!NOTE]
> In dit artikel bevat stappen voor het verwijderen van persoonlijke gegevens van de PowerShell Gallery en kan worden gebruikt voor de ondersteuning van uw verplichtingen onder de AVG. Als u algemene informatie over GDPR zoekt, raadpleegt u de [GDPR-sectie van de Service Trust-portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Persoonlijke gegevens verzenden

De PowerShell Gallery slaat de volgende informatie die kan worden geleverd door gebruikers die mogelijk persoonlijke gegevens bevatten:

- PowerShell Gallery-account
- Pakketten die zijn gepubliceerd naar de PowerShell-galerie
- E-mailcorrespondentie met het team van PowerShell Gallery

De meeste gebruikers maken geen een PowerShell Gallery-account.
Een account is niet vereist, tenzij u gaat publiceren van een pakket of de functie 'Neem contact op met eigenaar' in de PowerShell Gallery.
De PowerShell Gallery slaat dan e-mailcorrespondentie gestart door de gebruiker, geen persoonlijke gegevens voor gebruikers die geen een account hebt gemaakt.

Gebruikers die een PowerShell Gallery-account maken kunnen pakketten publiceren naar de PowerShell Gallery.
Die pakketten naar verwachting wordt PowerShell-code, maar andere gegevens, waaronder persoonlijke gegevens kunnen bevatten.
De informatie hieronder ziet u hoe u krijgt alle pakketten u hebt gepubliceerd naar de PowerShell Gallery.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-exporteren van gegevens van de PowerShell Gallery

De volgende secties beschrijven hoe de PowerShell Gallery onderwerp gegevensaanvragen (DSR), ondersteunt door waarin wordt uitgelegd hoe u kunt exporteren die zijn opgeslagen in de PowerShell Gallery en het verwijderen van deze informatie aanvragen.

### <a name="email"></a>E-mail

E-mailcorrespondentie, kan het volgende omvatten:

- E-mailbericht verzonden naar de eigenaars van de PowerShell Gallery pakketten als de analyse code scant is een probleem opgetreden met ze hebt gepubliceerd naar de PowerShell Gallery pakketten
- E-mailbericht verzonden door iemand die naar de PowerShell Gallery-team met behulp van het e-mailadres op de pagina 'Contact opnemen' [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Geregistreerde gebruikers die de functie 'Neem contact op met eigenaar' in de PowerShell Gallery gebruiken om e-mail te verzenden naar de eigenaar van een pakket in de PowerShell Gallery

E-mailberichten verzonden naar de PowerShell Gallery of door hebben een bewaarbeleid van 90 dagen voor de ondersteuning van onderzoeken van mogelijke beveiliging moet schadelijke code worden gedetecteerd in de PowerShell Gallery.
E-mailberichten worden na 90 dagen verwijderd door het beleid.

U kunt kopieën van alle e-mailberichten verzonden naar of van uw e-mailadres en de PowerShell Gallery in de afgelopen 90 dagen aanvragen.
Om aan te vragen van deze overeenkomst, stuur een e-mail naar [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), met de titel: 'DSR aanvragen voor e-mailberichten met betrekking tot dit account'.
In de hoofdtekst van het bericht, staat welke gegevens u aanvraagt (bijvoorbeeld: Stuur alle e-mailberichten verzonden naar of ontvangen van dit e-mailadres.) Alle e-mailberichten met betrekking tot uw e-mailadres binnen 90 dagen na de aanvraag wordt verzonden binnen 7 dagen.

### <a name="powershell-gallery-account-information"></a>PowerShell Gallery-accountgegevens

Als u een PowerShell Gallery-account hebt gemaakt, vindt u alle persoonlijke gegevens die zijn opgeslagen in de PowerShell Gallery door de volgende stappen uit:

1. Aanmelden bij de PowerShell Gallery, en klik vervolgens op uw gebruikersnaam
2. De volgende pagina wordt weergegeven is de Account-pagina, waarin het e-mailadres dat is gebruikt voor het account van de PowerShell Gallery

Als u meer dan één account hebt gemaakt in de PowerShell Gallery, moet u deze stappen herhalen voor elk account.

### <a name="packages-in-the-powershell-gallery"></a>Pakketten in de PowerShell Gallery

Om te kunnen exporteren pakketten die zijn gepubliceerd naar de PowerShell Gallery, hebben we het script "GetPSGalleryItemsForAuthor" gepubliceerd naar de PowerShell Gallery.
Met dit script wordt een kopie van elke versie van elk pakket in de PowerShell Gallery op basis van de van auteurgegevens die zijn opgeslagen in het pakket geëxporteerd.

> [!NOTE]
> De auteur wordt opgeslagen in het manifest van het pakket wanneer u het pakket publiceert.
> Er is geen garantie dat de auteur van de dezelfde id als het account dat u in de PowerShell Gallery gebruikt is.
> Als u een andere waarde in het veld ' auteur ' gebruikt, moet u die waarde leveren wanneer dit script te gebruiken.

U kunt het script downloaden met behulp van de volgende PowerShell-opdracht:

```powershell
Save-Script Get-repository psgallery
```

U kunt het script vervolgens rechtstreeks door het uitvoeren van de volgende PowerShell-opdrachten uitvoeren:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

U wordt gevraagd om op te geven van de auteur en een map op uw systeem waar u de pakketten worden opgeslagen.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Verwijderen van persoonlijke gegevens uit de PowerShell Gallery

Als u wilt verwijderen van de PowerShell Gallery-account of een pakket dat u in de PowerShell Gallery eigenaar bent, e-mailbericht verzendt cgadmin@microsoft.com met de titel: 'AVG de aanvraag voor artikelen met betrekking tot dit account'.
In de hoofdtekst van het bericht staat welke gegevens u wilt verwijderen. Bijvoorbeeld:

- Verwijder versie x.y.z van mijn pakket "pakketnaam"
- Verwijder alle versies van mijn pakket "pakketnaam"
- Verwijder op mijn account PowerShell Gallery

De PowerShell Gallery-beheerders wordt binnen 7 werkdagen beantwoorden.
De pakketten die zijn opgegeven worden, verwijderd binnen 30 dagen nadat de aanvraag is verzonden.
