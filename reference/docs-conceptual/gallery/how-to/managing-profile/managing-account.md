---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: PowerShell Gallery-accountinstellingen
ms.openlocfilehash: b71c7f0658c24ec2eeddb050e48b777a37c11917
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771784"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell Gallery-accountinstellingen

Uw PowerShell Gallery account is een openbaar zicht bare naam die is gekoppeld aan een identiteit. Deze identiteit is een micro soft-ID, zoals `user@hotmail.com` of of `user@outlook.com` een Aad-account (Azure Active Directory).

De PowerShell Gallery biedt de volgende account instellingen:

- Het e-mail account dat is gekoppeld aan uw PowerShell Gallery-account
- Opties voor e-mail meldingen die vanuit de PowerShell Gallery worden verzonden
- Het gebruikers account dat is gekoppeld aan uw PowerShell Gallery-account
- De afbeelding die aan uw PowerShell Gallery-account is gekoppeld

## <a name="email-address"></a>E-mailadres

Het e-mail adres is het doel voor PowerShell Gallery meldingen. Het hoeft niet overeen te komen met het aanmeldings account. U kunt elk e-mail account gebruiken waarmee u toegang hebt. Uw e-mail adres wordt nooit rechtstreeks door de PowerShell Gallery door gegeven aan andere gebruikers.

![E-mail adres wijzigen](media/managing-account/PSGallery_AcccountEmailAddress.png)

Wanneer u een nieuw e-mail adres invoert, stuurt de PowerShell Gallery een verificatie bericht naar dat adres. De e-mail verificatie bevat een koppeling terug naar de PowerShell Gallery om het wijzigings proces te volt ooien. Totdat u het verificatie proces hebt voltooid, worden alle meldingen naar het vorige adres verzonden.

## <a name="email-notifications"></a>E-mailmeldingen

PowerShell Gallery biedt de volgende meldings opties:

- Gebruikers kunnen contact met mij opnemen via de PowerShell Gallery
- Ik wil een melding ontvangen wanneer een pakket wordt gepusht naar de PowerShell Gallery met mijn account

![E-mail adres opties selecteren](media/managing-account/PSGallery_AccountEmailOptions.png)

Zoals op de pagina is aangegeven, kunnen essentiële meldingen van de PowerShell Gallery niet worden uitgeschakeld.
Deze omvatten:

- Beveiligings meldingen
- Account beheer meldingen van PowerShell Gallery beheerders
- Meldingen over de tests die worden uitgevoerd door de PowerShell Gallery voor inzendingen die u hebt gemaakt

## <a name="change-your-login-account"></a>Uw aanmeldings account wijzigen

Als u het aanmeldings account wilt wijzigen, moet u zijn aangemeld met het huidige account. Gebruik de volgende stappen om de wijziging te volt ooien.

![Instellingen voor aanmeldings account wijzigen](media/managing-account/PSGallery_LoginAccountSettings.png)

1. Klik op **account wijzigen**. In een pop-upvenster wordt uitgelegd dat het wijzigen van het aanmeldings account van toepassing is op alle toepassingen van dat account in de PowerShell Gallery. Lees de informatie en klik vervolgens op **OK** om door te gaan.

   ![Wijzigings bevestiging: OK/Annuleren](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. U wordt vervolgens gevraagd om u aan te melden met het _nieuwe account_.

   ![Meld u aan met het nieuwe account](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. Wanneer u op **volgende**klikt, wordt er een bericht weer gegeven dat u bent aangemeld met het huidige account.
   Klik op **Afmelden en meld u aan met een ander account**.

   ![Afmelden en aanmelden met een ander account](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. Voer het wacht woord van het nieuwe account in. Nadat u het wacht woord hebt ingevoerd, keert u terug naar de pagina account instellingen, waarin wordt weer gegeven dat het aanmeldings account is bijgewerkt.

## <a name="enable-two-factor-authentication-2fa"></a>Twee ledige verificatie inschakelen (twee ledige)

Verificatie met twee factoren wordt aanbevolen voor alle gebruikers die hand matig naar de PowerShell Gallery publiceren. Als u twee ledige verificatie wilt inschakelen, moet er ten minste twee geregistreerde verificaties zijn geregistreerd voor het aanmeldings account. De ene is een wacht woord en de andere formulieren kunnen de volgende zijn:

- Een telefoon nummer waarmee tekst berichten kunnen worden ontvangen
- Een geregistreerde verificator-toepassing, zoals Microsoft Authenticator voor uw mobiele telefoon

Deze verificatie vormen moeten worden geconfigureerd in de gegevens van uw AAD-account of in de beveiligings instellingen van uw micro soft-ID-account.

Wanneer twee ledige is ingeschakeld, moet u zich bij het PowerShell Gallery verifiëren met behulp van de geconfigureerde verificatie methoden wanneer u zich aanmeldt.

> [!IMPORTANT]
> Als u twee ledige verificatie voor de PowerShell Gallery-site inschakelt, hoeft u twee ledige niet in te scha kelen voor het gebruik van uw aanmeldings account. Zie [about verificatie in twee stappen](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)voor meer informatie.

## <a name="change-your-profile-picture"></a>Uw profielfoto wijzigen

De PowerShell Gallery is afhankelijk van Gravatar om de afbeelding op te slaan en weer te geven die aan uw profiel is gekoppeld. Ga naar [Gravatar.com](http://www.gravatar.com/)om de profiel afbeelding bij te werken.
