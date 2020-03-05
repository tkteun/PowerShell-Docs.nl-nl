---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: API-sleutels beheren
ms.openlocfilehash: 0f44a080415f1acf13680771b6e9db5b805f8f45
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278283"
---
# <a name="managing-api-keys"></a>API-sleutels beheren

De PowerShell Gallery biedt ondersteuning voor het maken van meerdere API-sleutels ter ondersteuning van een reeks publicatie vereisten. Een API-sleutel kan worden toegepast op een of meer pakketten, verleent specifieke bevoegdheden en heeft een verval datum.

> [!IMPORTANT]
> Gebruikers die zijn gepubliceerd in de PowerShell Gallery voorafgaand aan de introductie van API-sleutels met een bereik, hebben een volledige Access API-sleutel. De volledige toegangs sleutels hebben geen beveiligings verbeteringen die zijn ingebouwd in de API-sleutels met een bereik. De volledige toegangs sleutels verlopen nooit en zijn van toepassing op alle items die eigendom zijn van de gebruiker. Als u deze sleutel verwijdert, kan deze niet opnieuw worden gemaakt.

In de volgende afbeelding ziet u de beschik bare opties bij het maken van een scoped API-sleutel.

![API-sleutels maken](media/creating-APIkeys/PSGallery_KeyScoped.png)

In dit voor beeld hebben we een API-sleutel met de naam **AzureRMDataFactory**gemaakt. Deze sleutel waarde kan worden gebruikt om pakketten te pushen met namen die beginnen met ' AzureRM. DataFactory ' en die 365 dagen geldig zijn. Dit is een typisch scenario wanneer verschillende teams binnen dezelfde organisatie op verschillende pakketten werken. De leden van het team beschikken over een sleutel waarmee ze bevoegdheden worden verleend voor het specifieke pakket waaraan ze werken.
De verloop waarde voor komt het gebruik van verouderde of verg eten sleutels.

## <a name="using-glob-patterns"></a>Globs-patronen gebruiken

Als u op meerdere pakketten werkt, kunt u globbing-patronen gebruiken om meerdere pakketten als groep te vergelijken. API-sleutel machtigingen zijn van toepassing op alle nieuwe pakketten die overeenkomen met het Globs-patroon. In het vorige voor beeld wordt bijvoorbeeld de **Globs-patroon** waarde ' AzureRM. DataFactory * ' gebruikt. U kunt een pakket met de naam ' AzureRm. DataFactoryV2. NetCore ' pushen met behulp van deze sleutel, aangezien het pakket overeenkomt met het Globs-patroon.

## <a name="create-api-keys-securely"></a>De API-sleutels veilig maken

Ter beveiliging wordt een nieuwe sleutel waarde nooit op het scherm weer gegeven en is deze alleen beschikbaar met de Kopieer knop, zoals hieronder wordt weer gegeven.

![Nieuwe API-sleutel waarde verkrijgen](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> U kunt de waarde van de API-sleutel alleen direct na het maken of vernieuwen kopiëren. Deze wordt niet weer gegeven en is niet meer toegankelijk nadat de pagina is vernieuwd. Als u de sleutel waarde kwijtraakt, moet u Regenerate gebruiken en de sleutel kopiëren nadat deze opnieuw is gegenereerd.

## <a name="key-permissions-and-expiration"></a>Sleutel machtigingen en verloop tijd

Scoped API-sleutels kunnen een van de volgende machtigingen toewijzen:

- Nieuwe pakketten pushen
- Nieuwe of bijgewerkte pakketten pushen
- Pakketten in lijst opnemen

Elke nieuwe sleutel heeft een verval datum. De verloop waarde wordt gemeten in dagen. De mogelijke verval waarden zijn:

- 1 dag
- 90 dagen
- 180 dagen
- 270 dagen
- 365 dagen (standaard)

Deze instellingen kunnen niet worden gewijzigd nadat de sleutel is gemaakt. U kunt geen nieuwe sleutel maken die nooit verloopt.

## <a name="editing-and-deleting-existing-api-keys"></a>Bestaande API-sleutels bewerken en verwijderen

U kunt sommige instellingen van een bestaande sleutel wijzigen. Zoals eerder is vermeld, kunt u het beveiligings bereik voor een bestaande API-sleutel niet wijzigen of de verval datum wijzigen. De opties die u kunt wijzigen, worden weer gegeven in de volgende scherm afbeelding:

![Nieuwe API-sleutel waarde verkrijgen](media/creating-APIkeys/PSGallery_EditAPIKey.png)

Als u de pakketten wilt wijzigen die worden beheerd door een sleutel, kunt u afzonderlijke pakketten kiezen in de lijst of het Globs-patroon wijzigen.

Als u op **opnieuw genereren** klikt, wordt een nieuwe sleutel waarde gemaakt. Net als bij de eerste keer dat u de sleutel hebt gemaakt, moet u de sleutel waarde direct na het bijwerken **kopiëren** . De **Kopieer** optie is niet beschikbaar wanneer u deze pagina verlaat.

Als u op **verwijderen** klikt, wordt een bevestigings bericht weer gegeven. Wanneer een sleutel eenmaal is verwijderd, kan deze niet meer worden gebruikt.

## <a name="key-expiration"></a>Verval datum van de sleutel

Tien dagen voor het verlopen van de PowerShell Gallery wordt een waarschuwing verzonden met de account houder van de API-sleutel. Na verloop van tijd is de sleutel onbruikbaar. Boven aan de pagina API-sleutel beheer wordt een waarschuwings bericht weer gegeven met de sleutels die niet meer geldig zijn. U kunt een nieuwe sleutel waarde genereren.
