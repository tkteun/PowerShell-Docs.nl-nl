---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Het maken van een account met PowerShell Gallery
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084203"
---
# <a name="creating-a-powershell-gallery-account"></a>Het maken van een account met PowerShell Gallery

U moet een PowerShell Gallery-account maken voordat u iets publiceert naar de PowerShell Gallery.
PowerShell Gallery-accounts moeten worden gekoppeld aan een aanmeldingsaccount van e-mail kunnen ontvangen. Dit account kan worden een Azure Active Directory-account of een Microsoft-ID, zoals een e-mailaccount van outlook.com of hotmail.com.

Voor het maken van een PowerShell Gallery-account, gaat u naar [ https://PowerShellGallery.com ](https://PowerShellGallery.com) en klikt u op **aanmelden** zoals wordt weergegeven in de volgende afbeelding.

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

Voor het gebruik van Azure Active Directory-account, selecteert u **werk- of Schoolaccount**, en meld u aan met uw account. Kies voor het gebruik van een Microsoft-ID, **persoonlijk Account** en meld u aan.

U wordt vervolgens gevraagd om te maken van een gebruikersnaam voor de PowerShell Gallery. Raadpleeg de gebruiksrechtovereenkomst en privacybeleid, voer een gebruikersnaam in en klik vervolgens op **registreren**.

> [!NOTE]
> De accountnaam kan niet worden gewijzigd nadat deze is gemaakt. Zie voor meer informatie, [beheren pakket eigenaren](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Aanbevolen procedures voor PowerShell Gallery-accounts

Het is belangrijk voor het bewaken van het e-mailaccount gebruikt in combinatie met de PowerShell Gallery-account actief. Alle communicatie met eigenaren van pakketten van de PowerShell Gallery is via dit e-mailadres. Als het team van de PowerShell Gallery-bewerkingen kan geen verbinding met de eigenaar van een pakket, kunnen we zijn vereist voor het verwijderen van een pakket.

Organisaties die vaak naar de PowerShell Gallery publiceren maken een unieke externe account voor dat doel. U wordt aangeraden dat u e-mailbericht doorsturen gebruiken voor het doorsturen van meldingen naar een adres binnen uw organisatie.

Wanneer meerdere eigenaren gekoppeld aan een pakket zijn, worden alle PowerShell Gallery-meldingen worden verzonden naar alle eigenaren. Zie voor meer informatie, [beheren pakket eigenaren](managing-package-owners.md).
