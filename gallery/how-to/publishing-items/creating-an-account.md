---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Het maken van een account met PowerShell Gallery
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522823"
---
# <a name="creating-a-powershell-gallery-account"></a>Het maken van een account met PowerShell Gallery

U moet een PowerShell Gallery-account maken voordat u iets publiceert naar de PowerShell Gallery.
PowerShell Gallery-accounts moeten worden gekoppeld aan een aanmeldingsaccount van e-mail kunnen ontvangen. Dit account kan worden een Azure Active Directory-account of een Microsoft-ID, zoals een e-mailaccount van outlook.com of hotmail.com.

Voor het maken van een PowerShell Gallery-account, gaat u naar [ https://PowerShellGallery.com ](https://PowerShellGallery.com) en klikt u op **aanmelden** zoals wordt weergegeven in de volgende afbeelding.

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

Voor het gebruik van Azure Active Directory-account, selecteert u **werk- of Schoolaccount**, en meld u aan met uw account. Kies voor het gebruik van een Microsoft-ID, **persoonlijk Account** en meld u aan.

U wordt vervolgens gevraagd om te maken van een gebruikersnaam voor de PowerShell Gallery. Raadpleeg de gebruiksrechtovereenkomst en privacybeleid, voer een gebruikersnaam in en klik vervolgens op **registreren**.

> [!NOTE]
> De accountnaam kan niet worden gewijzigd nadat deze is gemaakt. Zie voor meer informatie, [Itemeigenaars beheren](managing-item-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Aanbevolen procedures voor PowerShell Gallery-accounts

Het is belangrijk voor het bewaken van het e-mailaccount gebruikt in combinatie met de PowerShell Gallery-account actief. Alle communicatie met eigenaren van PowerShell-galerie-items, verloopt via dit e-mailadres. Als het team van de PowerShell Gallery-bewerkingen kan geen verbinding met de eigenaar van een item, kunnen we vereist om een item te verwijderen.

Organisaties die vaak naar de PowerShell Gallery publiceren maken een unieke externe account voor dat doel. U wordt aangeraden dat u e-mailbericht doorsturen gebruiken voor het doorsturen van meldingen naar een adres binnen uw organisatie.

Wanneer meerdere eigenaren gekoppeld aan een item zijn, worden alle PowerShell Gallery-meldingen worden verzonden naar alle eigenaren. Zie voor meer informatie, [Itemeigenaars beheren](managing-item-owners.md).
