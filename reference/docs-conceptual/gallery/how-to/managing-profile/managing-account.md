---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: PowerShell Gallery-accountinstellingen
ms.openlocfilehash: 7f67311b42123f247a00a9c7a5bf775685b64d48
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560454"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="b9eca-103">PowerShell Gallery-accountinstellingen</span><span class="sxs-lookup"><span data-stu-id="b9eca-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="b9eca-104">Uw PowerShell Gallery account is een openbaar zicht bare naam die is gekoppeld aan een identiteit.</span><span class="sxs-lookup"><span data-stu-id="b9eca-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="b9eca-105">Deze identiteit is een micro soft-ID, zoals `user@hotmail.com` of of `user@outlook.com` een Aad-account (Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="b9eca-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="b9eca-106">De PowerShell Gallery biedt de volgende account instellingen:</span><span class="sxs-lookup"><span data-stu-id="b9eca-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="b9eca-107">Het e-mail account dat is gekoppeld aan uw PowerShell Gallery-account</span><span class="sxs-lookup"><span data-stu-id="b9eca-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="b9eca-108">Opties voor e-mail meldingen die vanuit de PowerShell Gallery worden verzonden</span><span class="sxs-lookup"><span data-stu-id="b9eca-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="b9eca-109">Het gebruikers account dat is gekoppeld aan uw PowerShell Gallery-account</span><span class="sxs-lookup"><span data-stu-id="b9eca-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="b9eca-110">De afbeelding die aan uw PowerShell Gallery-account is gekoppeld</span><span class="sxs-lookup"><span data-stu-id="b9eca-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="b9eca-111">E-mailadres</span><span class="sxs-lookup"><span data-stu-id="b9eca-111">Email address</span></span>

<span data-ttu-id="b9eca-112">Het e-mail adres is het doel voor PowerShell Gallery meldingen.</span><span class="sxs-lookup"><span data-stu-id="b9eca-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="b9eca-113">Het hoeft niet overeen te komen met het aanmeldings account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-113">It does not have to match the login account.</span></span> <span data-ttu-id="b9eca-114">U kunt elk e-mail account gebruiken waarmee u toegang hebt.</span><span class="sxs-lookup"><span data-stu-id="b9eca-114">You may use any email account you have access to.</span></span> <span data-ttu-id="b9eca-115">Uw e-mail adres wordt nooit rechtstreeks door de PowerShell Gallery door gegeven aan andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b9eca-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![E-mail adres wijzigen](media/managing-account/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="b9eca-117">Wanneer u een nieuw e-mail adres invoert, stuurt de PowerShell Gallery een verificatie bericht naar dat adres.</span><span class="sxs-lookup"><span data-stu-id="b9eca-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="b9eca-118">De e-mail verificatie bevat een koppeling terug naar de PowerShell Gallery om het wijzigings proces te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b9eca-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="b9eca-119">Totdat u het verificatie proces hebt voltooid, worden alle meldingen naar het vorige adres verzonden.</span><span class="sxs-lookup"><span data-stu-id="b9eca-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="b9eca-120">E-mailmeldingen</span><span class="sxs-lookup"><span data-stu-id="b9eca-120">Email notifications</span></span>

<span data-ttu-id="b9eca-121">PowerShell Gallery biedt de volgende meldings opties:</span><span class="sxs-lookup"><span data-stu-id="b9eca-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="b9eca-122">Gebruikers kunnen contact met mij opnemen via de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b9eca-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="b9eca-123">Ik wil een melding ontvangen wanneer een pakket wordt gepusht naar de PowerShell Gallery met mijn account</span><span class="sxs-lookup"><span data-stu-id="b9eca-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![E-mail adres wijzigen](media/managing-account/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="b9eca-125">Zoals op de pagina is aangegeven, kunnen essentiële meldingen van de PowerShell Gallery niet worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b9eca-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="b9eca-126">Deze omvatten:</span><span class="sxs-lookup"><span data-stu-id="b9eca-126">These include:</span></span>

- <span data-ttu-id="b9eca-127">Beveiligings meldingen</span><span class="sxs-lookup"><span data-stu-id="b9eca-127">Security notifications</span></span>
- <span data-ttu-id="b9eca-128">Account beheer meldingen van PowerShell Gallery beheerders</span><span class="sxs-lookup"><span data-stu-id="b9eca-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="b9eca-129">Meldingen over de tests die worden uitgevoerd door de PowerShell Gallery voor inzendingen die u hebt gemaakt</span><span class="sxs-lookup"><span data-stu-id="b9eca-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="b9eca-130">Uw aanmeldings account wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9eca-130">Change your login account</span></span>

<span data-ttu-id="b9eca-131">Als u het aanmeldings account wilt wijzigen, moet u zijn aangemeld met het huidige account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="b9eca-132">Gebruik de volgende stappen om de wijziging te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b9eca-132">Use the following steps to complete the change.</span></span>

![Instellingen voor aanmeldings account](media/managing-account/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="b9eca-134">Klik op **account wijzigen**.</span><span class="sxs-lookup"><span data-stu-id="b9eca-134">Click on **Change Account**.</span></span> <span data-ttu-id="b9eca-135">In een pop-upvenster wordt uitgelegd dat het wijzigen van het aanmeldings account van toepassing is op alle toepassingen van dat account in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b9eca-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="b9eca-136">Lees de informatie en klik vervolgens op **OK** om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="b9eca-136">Review the information, then click **OK** to continue.</span></span>

   ![Instellingen voor aanmeldings account](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="b9eca-138">U wordt vervolgens gevraagd om u aan te melden met het _nieuwe account_.</span><span class="sxs-lookup"><span data-stu-id="b9eca-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Instellingen voor aanmeldings account](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="b9eca-140">Wanneer u op **volgende**klikt, wordt er een bericht weer gegeven dat u bent aangemeld met het huidige account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="b9eca-141">Klik op **Afmelden en meld u aan met een ander account**.</span><span class="sxs-lookup"><span data-stu-id="b9eca-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Instellingen voor aanmeldings account](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="b9eca-143">Voer het wacht woord van het nieuwe account in.</span><span class="sxs-lookup"><span data-stu-id="b9eca-143">Enter the password of the new account.</span></span> <span data-ttu-id="b9eca-144">Nadat u het wacht woord hebt ingevoerd, keert u terug naar de pagina account instellingen, waarin wordt weer gegeven dat het aanmeldings account is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="b9eca-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>

## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="b9eca-145">Twee ledige verificatie inschakelen (twee ledige)</span><span class="sxs-lookup"><span data-stu-id="b9eca-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="b9eca-146">Verificatie met twee factoren wordt aanbevolen voor alle gebruikers die hand matig naar de PowerShell Gallery publiceren.</span><span class="sxs-lookup"><span data-stu-id="b9eca-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="b9eca-147">Als u twee ledige verificatie wilt inschakelen, moet er ten minste twee geregistreerde verificaties zijn geregistreerd voor het aanmeldings account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="b9eca-148">De ene is een wacht woord en de andere formulieren kunnen de volgende zijn:</span><span class="sxs-lookup"><span data-stu-id="b9eca-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="b9eca-149">Een telefoon nummer waarmee tekst berichten kunnen worden ontvangen</span><span class="sxs-lookup"><span data-stu-id="b9eca-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="b9eca-150">Een geregistreerde verificator-toepassing, zoals Microsoft Authenticator voor uw mobiele telefoon</span><span class="sxs-lookup"><span data-stu-id="b9eca-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="b9eca-151">Deze verificatie vormen moeten worden geconfigureerd in de gegevens van uw AAD-account of in de beveiligings instellingen van uw micro soft-ID-account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="b9eca-152">Wanneer twee ledige is ingeschakeld, moet u zich bij het PowerShell Gallery verifiëren met behulp van de geconfigureerde verificatie methoden wanneer u zich aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="b9eca-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9eca-153">Als u twee ledige verificatie voor de PowerShell Gallery-site inschakelt, hoeft u twee ledige niet in te scha kelen voor het gebruik van uw aanmeldings account.</span><span class="sxs-lookup"><span data-stu-id="b9eca-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="b9eca-154">Zie [about verificatie in twee stappen](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9eca-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="b9eca-155">Uw profielfoto wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9eca-155">Change your profile picture</span></span>

<span data-ttu-id="b9eca-156">De PowerShell Gallery is afhankelijk van Gravatar om de afbeelding op te slaan en weer te geven die aan uw profiel is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="b9eca-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="b9eca-157">Ga naar [Gravatar.com](http://www.gravatar.com/)om de profiel afbeelding bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b9eca-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
