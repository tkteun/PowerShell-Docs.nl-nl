---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Een PowerShell-galerie-Account maken
ms.openlocfilehash: c9c263a1926957cbdf059e062326b1903c117f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Een PowerShell-galerie-Account maken

Een PowerShell-galerie-account moet worden ingesteld voordat u verder niets te publiceren naar de PowerShell-galerie.
De PowerShell Gallery-accounts moeten worden gekoppeld aan een account voor het e-functionaliteit van Azure Active Directory of een Microsoft-account voor e-mail (met een domein van outlook.com, hotmail.com, enz.)

Voor het maken van een PowerShell-galerie-account, gaat u naar https://PowerShellGallery.com en klik op 'Register' (Zie de onderstaande afbeelding).

![Registreren van nieuwe account](./images/CreatingAccount-Register.png)

In de volgende pagina voor het gebruik van Azure Active Directory-account, selecteer 'Werk of School-Account' en meld u aan met uw account.
Voor het gebruik van een Microsoft-account - bijvoorbeeld in een domein Hotmail.com of Outlook.com - Kies 'Persoonlijke Account' en aanmelden.

Zodra u zich hebt aangemeld, wordt u gevraagd een gebruikersnaam voor de PowerShell-galerie maken.
Raadpleeg de gebruiksrechtovereenkomst en privacybeleid die zijn gekoppeld in, voer een gebruikersnaam en klik op registreren.

Opmerking: De accountnaam van dit kan niet worden gewijzigd zodra deze is gemaakt.
Zie [beheren Item eigenaars](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) voor meer informatie hierover.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Aanbevolen procedures voor PowerShell Gallery Accounts

Het is belangrijk dat het e-mailaccount gebruikt met uw account PowerShell Gallery actief worden bewaakt.
Alle communiction met eigenaren van PowerShell-galerie-items is via het e-mailbericht met het adres dat is gekoppeld aan uw account PowerShell Gallery.
Als er kan geen verbinding met de eigenaar van een item, kan het operationele team worden vereist om een item onder bepaalde omstandigheden te verwijderen.

Organisaties die vaak naar de PowerShell-galerie publiceren maken een uniek account daarvoor in Outlook.com of een ander domein voor Microsoft-account.
In veel gevallen wordt dat account niet regelmatig gecontroleerd.
In dat geval is een best practice doorsturen van Outlook gebruiken om e-mail te verzenden naar een ander account, meestal een binnen de organisatie, die wordt bewaakt door de eigenaar van het item.

Als er meerdere eigenaren van een item is gekoppeld, gaan alle communicatie die afkomstig van de PowerShell-galerie zijn naar alle eigenaren.
Zie [beheren Item eigenaars](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) voor meer informatie over het toevoegen van eigenaren aan een item.