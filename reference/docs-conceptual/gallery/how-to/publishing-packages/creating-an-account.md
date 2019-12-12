---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Een PowerShell Gallery-account maken
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329034"
---
# <a name="creating-a-powershell-gallery-account"></a>Een PowerShell Gallery-account maken

U moet een PowerShell Gallery account maken voordat u iets publiceert naar de PowerShell Gallery.
PowerShell Gallery accounts moeten worden gekoppeld aan een aanmeldings account waarvoor een e-mail is ingeschakeld. Dit account kan een Azure Active Directory account of een micro soft-ID zijn, zoals een e-mail account van outlook.com of hotmail.com.

Als u een PowerShell Gallery account wilt maken, gaat u naar [https://PowerShellGallery.com](https://PowerShellGallery.com) en klikt u op **Aanmelden** , zoals wordt weer gegeven in de volgende afbeelding.

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

Als u een Azure Active Directory account wilt gebruiken, selecteert u **werk-of school account**en meldt u zich aan met uw account. Als u een micro soft-ID wilt gebruiken, kiest u **persoonlijk account** en meldt u zich aan.

Vervolgens wordt u gevraagd om een gebruikers naam voor de PowerShell Gallery te maken. Lees de gebruiks voorwaarden en het privacybeleid, voer een gebruikers naam in en klik vervolgens op **registreren**.

> [!NOTE]
> De account naam kan niet worden gewijzigd nadat deze is gemaakt. Zie [package Owners beheren](managing-package-owners.md)voor meer informatie.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Aanbevolen procedures voor het PowerShell Gallery accounts

Het is belang rijk om het e-mail account dat met uw PowerShell Gallery-account wordt gebruikt, actief te controleren. Alle communicatie met eigen aars van PowerShell Gallery pakketten is via dit e-mail adres. Als het PowerShell Gallery Operations-team geen contact kan maken met een pakket eigenaar, moeten we mogelijk een pakket verwijderen.

Organisaties die naar het PowerShell Gallery publiceren, maken vaak een uniek extern account voor dat doel. U wordt aangeraden e-mail door sturen te gebruiken om meldingen door te sturen naar een adres binnen uw organisatie.

Wanneer meerdere eigen aren zijn gekoppeld aan een pakket, worden alle PowerShell Gallery meldingen verzonden naar alle eigen aren. Zie [package Owners beheren](managing-package-owners.md)voor meer informatie.
