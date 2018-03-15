---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Een PowerShell-galerie-Account maken
ms.openlocfilehash: 5af38884d819cb9c600a061109233614bd33666f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="14bf0-103">Een PowerShell-galerie-Account maken</span><span class="sxs-lookup"><span data-stu-id="14bf0-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="14bf0-104">Een PowerShell-galerie-account moet worden ingesteld voordat u verder niets te publiceren naar de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="14bf0-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span> <span data-ttu-id="14bf0-105">De PowerShell Gallery-accounts moeten worden gekoppeld aan een account voor het e-functionaliteit van Azure Active Directory of een Microsoft-account voor e-mail (met een domein van outlook.com, hotmail.com, enz.)</span><span class="sxs-lookup"><span data-stu-id="14bf0-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="14bf0-106">Voor het maken van een PowerShell-galerie-account, gaat u naar https://PowerShellGallery.com en klik op 'Register' (Zie de onderstaande afbeelding).</span><span class="sxs-lookup"><span data-stu-id="14bf0-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span> 

![Registreren van nieuwe account](./images/CreatingAccount-Register.png)

<span data-ttu-id="14bf0-108">In de volgende pagina voor het gebruik van Azure Active Directory-account, selecteer 'Werk of School-Account' en meld u aan met uw account.</span><span class="sxs-lookup"><span data-stu-id="14bf0-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span> <span data-ttu-id="14bf0-109">Voor het gebruik van een Microsoft-account - bijvoorbeeld in een domein Hotmail.com of Outlook.com - Kies 'Persoonlijke Account' en aanmelden.</span><span class="sxs-lookup"><span data-stu-id="14bf0-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span> 

<span data-ttu-id="14bf0-110">Zodra u zich hebt aangemeld, wordt u gevraagd een gebruikersnaam voor de PowerShell-galerie maken.</span><span class="sxs-lookup"><span data-stu-id="14bf0-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="14bf0-111">Raadpleeg de gebruiksrechtovereenkomst en privacybeleid die zijn gekoppeld in, voer een gebruikersnaam en klik op registreren.</span><span class="sxs-lookup"><span data-stu-id="14bf0-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="14bf0-112">Opmerking: De accountnaam van dit kan niet worden gewijzigd zodra deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="14bf0-112">Note: This account name cannot be changed once it is created.</span></span>  
<span data-ttu-id="14bf0-113">Zie [beheren Item eigenaars](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) voor meer informatie hierover.</span><span class="sxs-lookup"><span data-stu-id="14bf0-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="14bf0-114">Aanbevolen procedures voor PowerShell Gallery Accounts</span><span class="sxs-lookup"><span data-stu-id="14bf0-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="14bf0-115">Het is belangrijk dat het e-mailaccount gebruikt met uw account PowerShell Gallery actief worden bewaakt.</span><span class="sxs-lookup"><span data-stu-id="14bf0-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="14bf0-116">Alle communiction met eigenaren van PowerShell-galerie-items is via het e-mailbericht met het adres dat is gekoppeld aan uw account PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="14bf0-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="14bf0-117">Als er kan geen verbinding met de eigenaar van een item, kan het operationele team worden vereist om een item onder bepaalde omstandigheden te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="14bf0-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="14bf0-118">Organisaties die vaak naar de PowerShell-galerie publiceren maken een uniek account daarvoor in Outlook.com of een ander domein voor Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="14bf0-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="14bf0-119">In veel gevallen wordt dat account niet regelmatig gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="14bf0-119">In many cases that account is not regularly monitored.</span></span> <span data-ttu-id="14bf0-120">In dat geval is een best practice doorsturen van Outlook gebruiken om e-mail te verzenden naar een ander account, meestal een binnen de organisatie, die wordt bewaakt door de eigenaar van het item.</span><span class="sxs-lookup"><span data-stu-id="14bf0-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="14bf0-121">Als er meerdere eigenaren van een item is gekoppeld, gaan alle communicatie die afkomstig van de PowerShell-galerie zijn naar alle eigenaren.</span><span class="sxs-lookup"><span data-stu-id="14bf0-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="14bf0-122">Zie [beheren Item eigenaars](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) voor meer informatie over het toevoegen van eigenaren aan een item.</span><span class="sxs-lookup"><span data-stu-id="14bf0-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span> 

