---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Het maken van een account met PowerShell Gallery
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522823"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="b90ff-103">Het maken van een account met PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b90ff-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="b90ff-104">U moet een PowerShell Gallery-account maken voordat u iets publiceert naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b90ff-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="b90ff-105">PowerShell Gallery-accounts moeten worden gekoppeld aan een aanmeldingsaccount van e-mail kunnen ontvangen.</span><span class="sxs-lookup"><span data-stu-id="b90ff-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="b90ff-106">Dit account kan worden een Azure Active Directory-account of een Microsoft-ID, zoals een e-mailaccount van outlook.com of hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="b90ff-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="b90ff-107">Voor het maken van een PowerShell Gallery-account, gaat u naar [ https://PowerShellGallery.com ](https://PowerShellGallery.com) en klikt u op **aanmelden** zoals wordt weergegeven in de volgende afbeelding.</span><span class="sxs-lookup"><span data-stu-id="b90ff-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Nieuw account registreren](../../Images/CreateAccount-Register.png)

<span data-ttu-id="b90ff-109">Voor het gebruik van Azure Active Directory-account, selecteert u **werk- of Schoolaccount**, en meld u aan met uw account.</span><span class="sxs-lookup"><span data-stu-id="b90ff-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="b90ff-110">Kies voor het gebruik van een Microsoft-ID, **persoonlijk Account** en meld u aan.</span><span class="sxs-lookup"><span data-stu-id="b90ff-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="b90ff-111">U wordt vervolgens gevraagd om te maken van een gebruikersnaam voor de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b90ff-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="b90ff-112">Raadpleeg de gebruiksrechtovereenkomst en privacybeleid, voer een gebruikersnaam in en klik vervolgens op **registreren**.</span><span class="sxs-lookup"><span data-stu-id="b90ff-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="b90ff-113">De accountnaam kan niet worden gewijzigd nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b90ff-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="b90ff-114">Zie voor meer informatie, [Itemeigenaars beheren](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="b90ff-114">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="b90ff-115">Aanbevolen procedures voor PowerShell Gallery-accounts</span><span class="sxs-lookup"><span data-stu-id="b90ff-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="b90ff-116">Het is belangrijk voor het bewaken van het e-mailaccount gebruikt in combinatie met de PowerShell Gallery-account actief.</span><span class="sxs-lookup"><span data-stu-id="b90ff-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="b90ff-117">Alle communicatie met eigenaren van PowerShell-galerie-items, verloopt via dit e-mailadres.</span><span class="sxs-lookup"><span data-stu-id="b90ff-117">All communication with owners of PowerShell Gallery items is through this email address.</span></span> <span data-ttu-id="b90ff-118">Als het team van de PowerShell Gallery-bewerkingen kan geen verbinding met de eigenaar van een item, kunnen we vereist om een item te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b90ff-118">If the PowerShell Gallery Operations team is unable to contact an item owner, we may be required to delete an item.</span></span>

<span data-ttu-id="b90ff-119">Organisaties die vaak naar de PowerShell Gallery publiceren maken een unieke externe account voor dat doel.</span><span class="sxs-lookup"><span data-stu-id="b90ff-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="b90ff-120">U wordt aangeraden dat u e-mailbericht doorsturen gebruiken voor het doorsturen van meldingen naar een adres binnen uw organisatie.</span><span class="sxs-lookup"><span data-stu-id="b90ff-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="b90ff-121">Wanneer meerdere eigenaren gekoppeld aan een item zijn, worden alle PowerShell Gallery-meldingen worden verzonden naar alle eigenaren.</span><span class="sxs-lookup"><span data-stu-id="b90ff-121">When multiple owners are associated with an item, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="b90ff-122">Zie voor meer informatie, [Itemeigenaars beheren](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="b90ff-122">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>
