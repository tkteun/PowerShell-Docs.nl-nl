---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery, GDPR
title: PowerShell-galerie GDPR naleving
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189751"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell-galerie GDPR naleving

## <a name="overview"></a>Overzicht

In mei 2018 wordt Europese privacywetgeving is de algemene gegevens beveiliging regelgeving (GDPR), van kracht.
De GDPR legt nieuwe regels voor bedrijven, overheidsinstanties, non-profitorganisaties en andere organisaties aanbieding goederen en diensten naar mensen in de Europese Unie, of dat verzamelen en analyseren van gegevens die zijn gekoppeld aan de EU inwoners.
De GDPR is van toepassing ongeacht waar u zich bevindt.

> [!NOTE]
> Dit artikel bevat verschillende stappen voor het verwijderen van persoonlijke gegevens van de PowerShell Gallery en kan worden gebruikt ter ondersteuning van uw verplichtingen onder de GDPR. Als u algemene informatie over GDPR zoekt, raadpleegt u de [GDPR sectie van de portal Service vertrouwen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Persoonlijk herleidbare informatie

De PowerShell-galerie slaat de volgende informatie die kan worden geleverd door gebruikers die mogelijk persoonlijke gegevens bevatten:

* Account voor PowerShell Gallery
* Items die zijn gepubliceerd naar de PowerShell-galerie
* E-mailcorrespondentie met het team PowerShell Gallery

De meeste gebruikers doen PowerShell Gallery account niet maken.
Een account is niet vereist tenzij u gaat een item publiceren of de functie 'Eigenaar Neem contact op met' in de PowerShell-galerie.
De PowerShell-galerie slaat dan e-mailcorrespondentie geïnitieerd door de gebruiker, geen persoonlijk herleidbare informatie voor gebruikers die geen account hebt gemaakt.

Gebruikers die een PowerShell-galerie-account maken kunnen u items publiceren naar de PowerShell-galerie.
Deze items moet PowerShell-code worden verwacht, maar andere informatie, inclusief persoonlijke gegevens kunnen bevatten.
De informatie hieronder wordt beschreven hoe u alle items kan krijgen u hebt gepubliceerd naar de PowerShell-galerie.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR exporteren van gegevens van de PowerShell-galerie

De volgende secties wordt beschreven hoe onderwerp gegevensaanvragen (DSR) in de PowerShell-galerie worden ondersteunt door uitleg over het exporteren van gegevens die zijn opgeslagen in de PowerShell-galerie en het aanvragen van deze informatie is verwijderd.

### <a name="email"></a>E-mail

E-mailcorrespondentie kan het volgende omvatten:

* E-mailbericht verzonden naar de eigenaren van PowerShell-galerie-items als de code-analyse scant gedetecteerd een probleem met een ze hebt gepubliceerd naar de PowerShell-galerie-item
* E-mailbericht verzonden door iemand die naar de PowerShell Gallery team met behulp van het e-mailadres op de pagina 'Contact met ons opnemen' (cgadmin@microsoft.com)
* Gebruikers die de functie 'Eigenaar Neem contact op met' in de galerie met PowerShell gebruiken om e-mail te verzenden naar de eigenaar van een item in de PowerShell-galerie geregistreerd

E-mailberichten verzonden naar de galerie met PowerShell of door hebben een bewaarbeleid van 90 dagen voor de ondersteuning van onderzoeken van mogelijke beveiliging moet schadelijke code worden gedetecteerd in de PowerShell-galerie.
E-mailberichten worden na 90 dagen verwijderd door het beleid.

Kopieën van alle e-mailberichten verzonden naar of van uw e-mailadres en de PowerShell-galerie in de voorbije 90 dagen mag worden aangevraagd.
Om aan te vragen deze overeenkomst, een e-mail sturen naar cgadmin@microsoft.com, met de titel: 'DSR aanvraag voor e-mailberichten met betrekking tot dit account'.
In de hoofdtekst van het bericht staat welke informatie die u aanvraagt (bijvoorbeeld: Stuur alle e-mailberichten verzonden naar of ontvangen van dit e-mailadres.) Alle e-mailberichten met betrekking tot uw e-mailadres binnen 90 dagen van de aanvraag wordt verzonden binnen 7 dagen.

### <a name="powershell-gallery-account-information"></a>Accountgegevens PowerShell Gallery

Als u een PowerShell-galerie-account hebt gemaakt, vindt u alle persoonlijke gegevens die zijn opgeslagen in PowerShell Gallery door de volgende stappen:

1. Aanmelden bij de PowerShell-galerie en klik vervolgens op uw gebruikersnaam
2. De volgende pagina weergegeven, is de Account-pagina, waarin het e-mailadres dat is gebruikt voor het account PowerShell Gallery

Als u meer dan één account hebt gemaakt in de PowerShell-galerie, moet u deze stappen herhalen voor elke account.

### <a name="items-in-the-powershell-gallery"></a>Items in de PowerShell-galerie

Te vergemakkelijken uitvoerende items die zijn gepubliceerd naar de PowerShell-galerie, hebben we het script 'GetPSGalleryItemsForAuthor' gepubliceerd naar de PowerShell-galerie.
Dit script exporteert u een kopie van elke versie van elk item in de PowerShell-galerie op basis van de auteur informatie opgeslagen in het item geplaatst.

> [!NOTE]
> De auteur wordt opgeslagen in het manifest item wanneer u uw item publiceren.
> Er is geen garantie dat de auteur is dezelfde id als het account waarmee u in de PowerShell-galerie.
> Als u een andere waarde in het veld Auteur gebruikt, moet u op te geven dat de waarde bij gebruik van dit script.

U kunt het script downloaden met behulp van de volgende PowerShell-opdracht:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

U kunt het script vervolgens rechtstreeks uitvoeren met de volgende PowerShell-opdrachten:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

U wordt gevraagd de auteur en een map op uw systeem waar u de items worden opgeslagen op te geven.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Verwijderen van persoonlijke gegevens van de PowerShell Gallery

Verwijder uw account PowerShell Gallery of een item dat u in de PowerShell-galerie bezit, e-mailbericht verzendt cgadmin@microsoft.com met de titel: 'GDPR aanvraag voor artikelen met betrekking tot dit account'.
In de hoofdtekst van het bericht staat welke gegevens u wilt verwijderen. Bijvoorbeeld:

* Verwijder versie x.y.z van mijn 'item name'-item
* Verwijder alle versies van het item 'item name'
* Verwijder op mijn account PowerShell Gallery

De beheerders PowerShell Gallery moeten reageren binnen 7 dagen.
De opgegeven items worden verwijderd binnen 30 dagen nadat de aanvraag is verzonden.
