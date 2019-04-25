---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: PowerShell Gallery-accountinstellingen
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084471"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell Gallery-accountinstellingen

Uw account PowerShell Gallery is de naam van een zichtbaar voor iedereen die is gekoppeld aan een identiteit. Deze identiteit is ofwel een Microsoft-ID, zoals `user@hotmail.com` of `user@outlook.com`, of een Azure Active Directory (AAD)-account.

De PowerShell Gallery bevat de instellingen van het volgende:

- Het e-mailaccount dat is gekoppeld aan uw account PowerShell Gallery
- Opties voor e-mailmeldingen verzonden vanuit de PowerShell Gallery
- Het gebruikersaccount dat is gekoppeld aan uw account PowerShell Gallery
- De afbeelding die is gekoppeld aan uw account PowerShell Gallery

## <a name="email-address"></a>E-mailadres

Het e-mailadres is het doel voor meldingen van de PowerShell Gallery. Dit heeft geen zodat deze overeenkomt met het account voor aanmelding. U kunt een e-mailaccount dat u toegang tot hebt. Uw e-mailadres wordt nooit rechtstreeks geleverd door de PowerShell Gallery aan andere gebruikers.

![E-mailadres wijzigen](../../Images/PSGallery_AcccountEmailAddress.png)

Wanneer u een nieuw e-mailadres opgeeft, verzendt de PowerShell Gallery een verificatie-e-mailbericht het desbetreffende adres. Het verificatie-e-mailbericht bevat een koppeling terug naar de PowerShell Gallery om de wijzigingsproces te voltooien. Totdat u het verificatieproces, worden alle meldingen worden verzonden naar het vorige adres.

## <a name="email-notifications"></a>E-mailmeldingen

PowerShell Gallery bevat de volgende meldingsopties:

- Gebruikers contact met mij kunnen via de PowerShell Gallery
- Een melding ontvangen wanneer een pakket wordt doorgestuurd naar de PowerShell-galerie met behulp van mijn account

![E-mailadres wijzigen](../../Images/PSGallery_AccountEmailOptions.png)

Als op de pagina die u hebt genoteerd, kunnen niet kritieke meldingen vanuit de PowerShell Gallery worden uitgeschakeld.
Deze omvatten:

- Meldingen
- Account management meldingen van de PowerShell Gallery-beheerders
- Meldingen over de tests uitgevoerd door de PowerShell Gallery voor inzendingen die u hebt gemaakt

## <a name="change-your-login-account"></a>Uw account voor aanmelding wijzigen

De aanmeldings-serviceaccount wilt wijzigen, moet u zijn aangemeld met het huidige account. Gebruik de volgende stappen uit om de wijziging te voltooien.

![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountSettings.png)

1. Klik op **Account wijzigen**. Een pop-upvenster wordt uitgelegd dat de aanmeldingsaccount wijzigen wordt toegepast op al het gebruik van dat account in de PowerShell Gallery. Lees de informatie en klik vervolgens op **OK** om door te gaan.

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-1.png)

2. U wordt gevraagd zich aanmelden met de _nieuw account_.

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-2.png)

3. Wanneer u klikt op **volgende**, ziet u een bericht dat u bent aangemeld met behulp van het huidige account.
   Klik op **zich out en meld u aan met een ander account**.

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-3.png)

4. Voer het wachtwoord van het nieuwe account. Na het invoeren van het wachtwoord, keert u terug naar de pagina met Accountinstellingen weergegeven dat de aanmeldingsaccount is bijgewerkt.


## <a name="enable-two-factor-authentication-2fa"></a>Tweeledige verificatie (2FA) inschakelen

Verificatie met twee factoren wordt aanbevolen voor alle gebruikers die handmatig naar de PowerShell Gallery publiceren. Aanmeldingsaccount van het moet ten minste twee soorten verificatie geregistreerd hebben zodat tweeledige verificatie. Een wachtwoord en de andere formulieren kunnen worden:

- Een telefoonnummer op dat de SMS-berichten kunt ontvangen
- Een geregistreerde authenticator-toepassing, zoals Microsoft Authenticator voor uw mobiele telefoon

Deze soorten verificatie moeten worden geconfigureerd in de gegevens van uw AAD-account of in de beveiligingsinstellingen van Microsoft-ID-Account.

Zodra de 2FA is ingeschakeld, moet u verifiëren met behulp van de geconfigureerde authenticatiemethoden telkens wanneer u zich aanmeldt bij de PowerShell Gallery.

> [!IMPORTANT]
> Inschakelen van tweeledige verificatie voor de PowerShell Gallery-site vereist niet dat u om in te schakelen 2FA voor al het gebruik van uw account voor aanmelding. Zie voor meer informatie, [over verificatie in twee stappen](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Uw eigen profielfoto wijzigen

De PowerShell Gallery, is afhankelijk van Gravatar opslaan en weergeven van de afbeelding die is gekoppeld aan uw profiel. Voor het bijwerken van uw profielafbeelding, gaat u naar [Gravatar.com](http://www.gravatar.com/).
