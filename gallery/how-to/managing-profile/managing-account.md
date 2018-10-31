---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: PowerShell Gallery-accountinstellingen
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002783"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="88897-103">PowerShell Gallery-accountinstellingen</span><span class="sxs-lookup"><span data-stu-id="88897-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="88897-104">Uw account PowerShell Gallery is de naam van een zichtbaar voor iedereen die is gekoppeld aan een identiteit.</span><span class="sxs-lookup"><span data-stu-id="88897-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="88897-105">Deze identiteit is ofwel een Microsoft-ID, zoals `user@hotmail.com` of `user@outlook.com`, of een Azure Active Directory (AAD)-account.</span><span class="sxs-lookup"><span data-stu-id="88897-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="88897-106">De PowerShell Gallery bevat de instellingen van het volgende:</span><span class="sxs-lookup"><span data-stu-id="88897-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="88897-107">Het e-mailaccount dat is gekoppeld aan uw account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="88897-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="88897-108">Opties voor e-mailmeldingen verzonden vanuit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="88897-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="88897-109">Het gebruikersaccount dat is gekoppeld aan uw account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="88897-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="88897-110">De afbeelding die is gekoppeld aan uw account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="88897-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="88897-111">E-mailadres</span><span class="sxs-lookup"><span data-stu-id="88897-111">Email address</span></span>

<span data-ttu-id="88897-112">Het e-mailadres is het doel voor meldingen van de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="88897-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="88897-113">Dit heeft geen zodat deze overeenkomt met het account voor aanmelding.</span><span class="sxs-lookup"><span data-stu-id="88897-113">It does not have to match the login account.</span></span> <span data-ttu-id="88897-114">U kunt een e-mailaccount dat u toegang tot hebt.</span><span class="sxs-lookup"><span data-stu-id="88897-114">You may use any email account you have access to.</span></span> <span data-ttu-id="88897-115">Uw e-mailadres wordt nooit rechtstreeks geleverd door de PowerShell Gallery aan andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="88897-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![E-mailadres wijzigen](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="88897-117">Wanneer u een nieuw e-mailadres opgeeft, verzendt de PowerShell Gallery een verificatie-e-mailbericht het desbetreffende adres.</span><span class="sxs-lookup"><span data-stu-id="88897-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="88897-118">Het verificatie-e-mailbericht bevat een koppeling terug naar de PowerShell Gallery om de wijzigingsproces te voltooien.</span><span class="sxs-lookup"><span data-stu-id="88897-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="88897-119">Totdat u het verificatieproces, worden alle meldingen worden verzonden naar het vorige adres.</span><span class="sxs-lookup"><span data-stu-id="88897-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="88897-120">E-mailmeldingen</span><span class="sxs-lookup"><span data-stu-id="88897-120">Email notifications</span></span>

<span data-ttu-id="88897-121">PowerShell Gallery bevat de volgende meldingsopties:</span><span class="sxs-lookup"><span data-stu-id="88897-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="88897-122">Gebruikers contact met mij kunnen via de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="88897-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="88897-123">Een melding ontvangen wanneer een pakket wordt doorgestuurd naar de PowerShell-galerie met behulp van mijn account</span><span class="sxs-lookup"><span data-stu-id="88897-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![E-mailadres wijzigen](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="88897-125">Als op de pagina die u hebt genoteerd, kunnen niet kritieke meldingen vanuit de PowerShell Gallery worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="88897-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="88897-126">Deze omvatten:</span><span class="sxs-lookup"><span data-stu-id="88897-126">These include:</span></span>

- <span data-ttu-id="88897-127">Meldingen</span><span class="sxs-lookup"><span data-stu-id="88897-127">Security notifications</span></span>
- <span data-ttu-id="88897-128">Account management meldingen van de PowerShell Gallery-beheerders</span><span class="sxs-lookup"><span data-stu-id="88897-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="88897-129">Meldingen over de tests uitgevoerd door de PowerShell Gallery voor inzendingen die u hebt gemaakt</span><span class="sxs-lookup"><span data-stu-id="88897-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="88897-130">Uw account voor aanmelding wijzigen</span><span class="sxs-lookup"><span data-stu-id="88897-130">Change your login account</span></span>

<span data-ttu-id="88897-131">De aanmeldings-serviceaccount wilt wijzigen, moet u zijn aangemeld met het huidige account.</span><span class="sxs-lookup"><span data-stu-id="88897-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="88897-132">Gebruik de volgende stappen uit om de wijziging te voltooien.</span><span class="sxs-lookup"><span data-stu-id="88897-132">Use the following steps to complete the change.</span></span>

![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="88897-134">Klik op **Account wijzigen**.</span><span class="sxs-lookup"><span data-stu-id="88897-134">Click on **Change Account**.</span></span> <span data-ttu-id="88897-135">Een pop-upvenster wordt uitgelegd dat de aanmeldingsaccount wijzigen wordt toegepast op al het gebruik van dat account in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="88897-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="88897-136">Lees de informatie en klik vervolgens op **OK** om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="88897-136">Review the information, then click **OK** to continue.</span></span>

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="88897-138">U wordt gevraagd zich aanmelden met de _nieuw account_.</span><span class="sxs-lookup"><span data-stu-id="88897-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="88897-140">Wanneer u klikt op **volgende**, ziet u een bericht dat u bent aangemeld met behulp van het huidige account.</span><span class="sxs-lookup"><span data-stu-id="88897-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="88897-141">Klik op **zich out en meld u aan met een ander account**.</span><span class="sxs-lookup"><span data-stu-id="88897-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Aanmeldings-Accountinstellingen](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="88897-143">Voer het wachtwoord van het nieuwe account.</span><span class="sxs-lookup"><span data-stu-id="88897-143">Enter the password of the new account.</span></span> <span data-ttu-id="88897-144">Na het invoeren van het wachtwoord, keert u terug naar de pagina met Accountinstellingen weergegeven dat de aanmeldingsaccount is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="88897-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="88897-145">Tweeledige verificatie (2FA) inschakelen</span><span class="sxs-lookup"><span data-stu-id="88897-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="88897-146">Verificatie met twee factoren wordt aanbevolen voor alle gebruikers die handmatig naar de PowerShell Gallery publiceren.</span><span class="sxs-lookup"><span data-stu-id="88897-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="88897-147">Aanmeldingsaccount van het moet ten minste twee soorten verificatie geregistreerd hebben zodat tweeledige verificatie.</span><span class="sxs-lookup"><span data-stu-id="88897-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="88897-148">Een wachtwoord en de andere formulieren kunnen worden:</span><span class="sxs-lookup"><span data-stu-id="88897-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="88897-149">Een telefoonnummer op dat de SMS-berichten kunt ontvangen</span><span class="sxs-lookup"><span data-stu-id="88897-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="88897-150">Een geregistreerde authenticator-toepassing, zoals Microsoft Authenticator voor uw mobiele telefoon</span><span class="sxs-lookup"><span data-stu-id="88897-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="88897-151">Deze soorten verificatie moeten worden geconfigureerd in de gegevens van uw AAD-account of in de beveiligingsinstellingen van Microsoft-ID-Account.</span><span class="sxs-lookup"><span data-stu-id="88897-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="88897-152">Zodra de 2FA is ingeschakeld, moet u verifiëren met behulp van de geconfigureerde authenticatiemethoden telkens wanneer u zich aanmeldt bij de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="88897-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88897-153">Inschakelen van tweeledige verificatie voor de PowerShell Gallery-site vereist niet dat u om in te schakelen 2FA voor al het gebruik van uw account voor aanmelding.</span><span class="sxs-lookup"><span data-stu-id="88897-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="88897-154">Zie voor meer informatie, [over verificatie in twee stappen](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="88897-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="88897-155">Uw eigen profielfoto wijzigen</span><span class="sxs-lookup"><span data-stu-id="88897-155">Change your profile picture</span></span>

<span data-ttu-id="88897-156">De PowerShell Gallery, is afhankelijk van Gravatar opslaan en weergeven van de afbeelding die is gekoppeld aan uw profiel.</span><span class="sxs-lookup"><span data-stu-id="88897-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="88897-157">Voor het bijwerken van uw profielafbeelding, gaat u naar [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="88897-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
