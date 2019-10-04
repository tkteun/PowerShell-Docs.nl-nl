---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Een PowerShell Gallery-account maken
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329034"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="28589-103">Een PowerShell Gallery-account maken</span><span class="sxs-lookup"><span data-stu-id="28589-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="28589-104">U moet een PowerShell Gallery account maken voordat u iets publiceert naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="28589-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="28589-105">PowerShell Gallery accounts moeten worden gekoppeld aan een aanmeldings account waarvoor een e-mail is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="28589-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="28589-106">Dit account kan een Azure Active Directory account of een micro soft-ID zijn, zoals een e-mail account van outlook.com of hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="28589-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="28589-107">Als u een PowerShell Gallery account wilt maken, [https://PowerShellGallery.com](https://PowerShellGallery.com) gaat u naar en klikt u op **Aanmelden** , zoals wordt weer gegeven in de volgende afbeelding.</span><span class="sxs-lookup"><span data-stu-id="28589-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

<span data-ttu-id="28589-109">Als u een Azure Active Directory account wilt gebruiken, selecteert u **werk-of school account**en meldt u zich aan met uw account.</span><span class="sxs-lookup"><span data-stu-id="28589-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="28589-110">Als u een micro soft-ID wilt gebruiken, kiest u **persoonlijk account** en meldt u zich aan.</span><span class="sxs-lookup"><span data-stu-id="28589-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="28589-111">Vervolgens wordt u gevraagd om een gebruikers naam voor de PowerShell Gallery te maken.</span><span class="sxs-lookup"><span data-stu-id="28589-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="28589-112">Lees de gebruiks voorwaarden en het privacybeleid, voer een gebruikers naam in en klik vervolgens op **registreren**.</span><span class="sxs-lookup"><span data-stu-id="28589-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="28589-113">De account naam kan niet worden gewijzigd nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="28589-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="28589-114">Zie [package Owners beheren](managing-package-owners.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="28589-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="28589-115">Aanbevolen procedures voor het PowerShell Gallery accounts</span><span class="sxs-lookup"><span data-stu-id="28589-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="28589-116">Het is belang rijk om het e-mail account dat met uw PowerShell Gallery-account wordt gebruikt, actief te controleren.</span><span class="sxs-lookup"><span data-stu-id="28589-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="28589-117">Alle communicatie met eigen aars van PowerShell Gallery pakketten is via dit e-mail adres.</span><span class="sxs-lookup"><span data-stu-id="28589-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="28589-118">Als het PowerShell Gallery Operations-team geen contact kan maken met een pakket eigenaar, moeten we mogelijk een pakket verwijderen.</span><span class="sxs-lookup"><span data-stu-id="28589-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="28589-119">Organisaties die naar het PowerShell Gallery publiceren, maken vaak een uniek extern account voor dat doel.</span><span class="sxs-lookup"><span data-stu-id="28589-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="28589-120">U wordt aangeraden e-mail door sturen te gebruiken om meldingen door te sturen naar een adres binnen uw organisatie.</span><span class="sxs-lookup"><span data-stu-id="28589-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="28589-121">Wanneer meerdere eigen aren zijn gekoppeld aan een pakket, worden alle PowerShell Gallery meldingen verzonden naar alle eigen aren.</span><span class="sxs-lookup"><span data-stu-id="28589-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="28589-122">Zie [package Owners beheren](managing-package-owners.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="28589-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>