---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Het maken van een account met PowerShell Gallery
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004046"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="d1e4f-103">Het maken van een account met PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d1e4f-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="d1e4f-104">U moet een PowerShell Gallery-account maken voordat u iets publiceert naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="d1e4f-105">PowerShell Gallery-accounts moeten worden gekoppeld aan een aanmeldingsaccount van e-mail kunnen ontvangen.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="d1e4f-106">Dit account kan worden een Azure Active Directory-account of een Microsoft-ID, zoals een e-mailaccount van outlook.com of hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="d1e4f-107">Voor het maken van een PowerShell Gallery-account, gaat u naar [ https://PowerShellGallery.com ](https://PowerShellGallery.com) en klikt u op **aanmelden** zoals wordt weergegeven in de volgende afbeelding.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

<span data-ttu-id="d1e4f-109">Voor het gebruik van Azure Active Directory-account, selecteert u **werk- of Schoolaccount**, en meld u aan met uw account.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="d1e4f-110">Kies voor het gebruik van een Microsoft-ID, **persoonlijk Account** en meld u aan.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="d1e4f-111">U wordt vervolgens gevraagd om te maken van een gebruikersnaam voor de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="d1e4f-112">Raadpleeg de gebruiksrechtovereenkomst en privacybeleid, voer een gebruikersnaam in en klik vervolgens op **registreren**.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="d1e4f-113">De accountnaam kan niet worden gewijzigd nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="d1e4f-114">Zie voor meer informatie, [beheren pakket eigenaren](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="d1e4f-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="d1e4f-115">Aanbevolen procedures voor PowerShell Gallery-accounts</span><span class="sxs-lookup"><span data-stu-id="d1e4f-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="d1e4f-116">Het is belangrijk voor het bewaken van het e-mailaccount gebruikt in combinatie met de PowerShell Gallery-account actief.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="d1e4f-117">Alle communicatie met eigenaren van pakketten van de PowerShell Gallery is via dit e-mailadres.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="d1e4f-118">Als het team van de PowerShell Gallery-bewerkingen kan geen verbinding met de eigenaar van een pakket, kunnen we zijn vereist voor het verwijderen van een pakket.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="d1e4f-119">Organisaties die vaak naar de PowerShell Gallery publiceren maken een unieke externe account voor dat doel.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="d1e4f-120">U wordt aangeraden dat u e-mailbericht doorsturen gebruiken voor het doorsturen van meldingen naar een adres binnen uw organisatie.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="d1e4f-121">Wanneer meerdere eigenaren gekoppeld aan een pakket zijn, worden alle PowerShell Gallery-meldingen worden verzonden naar alle eigenaren.</span><span class="sxs-lookup"><span data-stu-id="d1e4f-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="d1e4f-122">Zie voor meer informatie, [beheren pakket eigenaren](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="d1e4f-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
