---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Maken van een account PowerShell Gallery
ms.openlocfilehash: 4a44b51967ea8acdd331f6b3c682fc5884bd2f54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219562"
---
## <a name="creating-a-powershell-gallery-account"></a>Maken van een account PowerShell Gallery

Een PowerShell-galerie-account moet worden ingesteld voordat u verder niets te publiceren naar de PowerShell-galerie.
De PowerShell Gallery-accounts moeten worden gekoppeld aan een account voor het e-functionaliteit van Azure Active Directory of een Microsoft-account voor e-mail (met een domein van outlook.com, hotmail.com, enz.)

Voor het maken van een PowerShell-galerie-account, gaat u naar https://PowerShellGallery.com en klik op 'Register' (Zie de onderstaande afbeelding).

![Registreren van nieuwe account](../../Images/CreatingAccount-Register.png)

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