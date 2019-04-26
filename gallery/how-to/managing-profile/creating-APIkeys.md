---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: API-sleutels beheren
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084339"
---
# <a name="managing-api-keys"></a>API-sleutels beheren

De PowerShell Gallery biedt ondersteuning voor het maken van meerdere API-sleutels ter ondersteuning van een bereik van de publicatie van vereisten. Een API-sleutel kan worden toegepast op een of meer pakketten, verleent u specifieke bevoegdheden en heeft een vervaldatum.

> [!IMPORTANT]
> Gebruikers die gepubliceerd naar de PowerShell Gallery vóór de introductie van binnen het bereik API-sleutels heeft een 'volledige toegang tot de API key'. De volledige toegangssleutel beschikt niet over de verbeteringen in de beveiliging die is ingebouwd in binnen het bereik API-sleutels. De volledige toegang tot de sleutels nooit verloopt en toepassen op Alles eigendom zijn van de gebruiker. Als u deze sleutel verwijdert, kan niet opnieuw gemaakt.

De volgende afbeelding toont de beschikbare opties bij het maken van een bereik API-sleutel.

![Het maken van API-sleutels](../../Images/PSGallery_KeyScoped.png)

In dit voorbeeld hebben we een API-sleutel met de naam gemaakt **AzureRMDataFactory**. De waarde van deze sleutel kan worden gebruikt om pakketten met namen die beginnen met 'AzureRM.DataFactory' en is geldig tot 365 dagen. Dit is een typisch scenario bij verschillende teams binnen dezelfde organisatie aan verschillende pakketten werken. De leden van het team hebben een sleutel die deze machtigingen voor het specifieke pakket dat ze werken verleent op.
De vervaltijd wordt voorkomen dat het gebruik van verouderde of vergeten sleutels.

## <a name="using-glob-patterns"></a>Met behulp van glob patronen

Als u op meerdere pakketten werkt, kunt u bij globbing patronen zodat deze overeenkomen met meerdere pakketten als een groep. API-sleutel machtigingen toepassen op alle nieuwe pakketten die overeenkomt met het patroon glob. Het vorige voorbeeld gebruikt bijvoorbeeld een **Glob patroon** waarde van 'AzureRM.DataFactory*'. U kunt een pakket met de naam met behulp van deze sleutel omdat het pakket overeenkomt met het patroon glob AzureRm.DataFactoryV2.Netcore pushen.

## <a name="create-api-keys-securely"></a>API-sleutels veilig maken

Voor beveiliging, de waarde van een nieuwe sleutel nooit op het scherm wordt weergegeven en is alleen beschikbaar met de knop kopiëren, zoals hieronder wordt weergegeven.

![Het ophalen van de nieuwe API-sleutelwaarde](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> U kunt alleen de waarde van de API-sleutel kopiëren onmiddellijk na het maken of vernieuwen. Deze worden niet weergegeven en wordt niet meer toegankelijk opnieuw nadat de pagina wordt vernieuwd. Als u de waarde van de sleutel verliest, moet u gebruik van de sleutel opnieuw genereren en kopieer de sleutel nadat deze is opnieuw gegenereerd.

## <a name="key-permissions-and-expiration"></a>Machtigingen en de vervaldatum

Scoped API-sleutels kunnen een van de volgende machtigingen toewijzen:

- Nieuwe push-pakketten
- Nieuwe push of pakketten bijwerken
- Unlist pakketten

Elke nieuwe sleutel heeft een vervaldatum. De vervaltijd wordt gemeten in dagen. De vervaldatum voor de mogelijke waarden zijn:

- 1 dag
- 90 dagen
- 180 dagen
- 270 dagen
- 365 dagen (standaard)

Deze instellingen kunnen niet worden gewijzigd nadat de sleutel is gemaakt. U kunt een nieuwe sleutel nooit verloopt kan niet maken.

## <a name="editing-and-deleting-existing-api-keys"></a>Bewerken en verwijderen van bestaande API-sleutels

U kunt bepaalde instellingen van een bestaande sleutel wijzigen. Zoals eerder vermeld, kan u wijzigen van het beveiligingsbereik voor een bestaande API-sleutel of wijzigen van de vervaldatum. De instelbare opties worden weergegeven in de volgende schermafbeelding:

![Het ophalen van de nieuwe API-sleutelwaarde](../../Images/PSGallery_EditAPIKey.png)

Als u wilt wijzigen van de pakketten die wordt beheerd door een sleutel, kunt u afzonderlijke pakketten in de lijst kiezen of het patroon glob wijzigen.

Te klikken op **opnieuw genereren** wordt de waarde van een nieuwe sleutel gemaakt. Net zoals wanneer u de sleutel in eerste instantie hebt gemaakt, u moet **kopie** de waarde van de sleutel onmiddellijk na het bijwerken van het. De **kopie** optie is niet beschikbaar wanneer u deze pagina verlaat.

Te klikken op **verwijderen** verschijnt een bevestigingsbericht. Zodra een sleutel is verwijderd, wordt het onbruikbaar zijn.

## <a name="key-expiration"></a>Vervaldatum van de sleutel

Tien dagen vóór de vervaldatum, verzendt de PowerShell Gallery een waarschuwing e-mailbericht de accounteigenaar van de API-sleutel. De sleutel is na de verloopdatum onbruikbaar. Een waarschuwingsbericht wordt weergegeven aan de bovenkant van de API-Sleutelbeheer-pagina met welke sleutels zijn niet langer geldig. U kunt de waarde van een nieuwe sleutel genereren.
