---
title: Bestandstypen die zijn toegestaan in een bij te werken Help CAB-bestand | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082444"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="81498-102">Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="81498-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="81498-103">In dit onderwerp geeft een lijst van en beschrijft de vereisten voor bijwerkbare Help CAB-bestanden.</span><span class="sxs-lookup"><span data-stu-id="81498-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="81498-104">Vereisten voor bijwerkbare Help CAB-bestand</span><span class="sxs-lookup"><span data-stu-id="81498-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="81498-105">Niet-gecomprimeerde inhoud van de CAB-bestand is standaard beperkt tot 1 GB.</span><span class="sxs-lookup"><span data-stu-id="81498-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="81498-106">Als u wilt deze beperking omzeilen, gebruikers moeten gebruiken de **Force** parameter van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="81498-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="81498-107">Om ervoor te zorgen de beveiliging van help-bestanden die worden gedownload vanaf het Internet, kan een bij te werken Help CAB-bestand bevatten alleen de hieronder vermelde bestandstypen.</span><span class="sxs-lookup"><span data-stu-id="81498-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="81498-108">De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valideert alle bestanden op basis van de help-onderwerp schema's.</span><span class="sxs-lookup"><span data-stu-id="81498-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="81498-109">Als de `Update-Help` cmdlet wordt een bestand dat is ongeldig of is geen toegestane type aangetroffen, de ongeldig bestand kan niet worden geïnstalleerd en stopt met het installeren van bestanden uit het CAB-bestand op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="81498-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="81498-110">XML-indeling help-onderwerpen over cmdlets.</span><span class="sxs-lookup"><span data-stu-id="81498-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="81498-111">XML-indeling help-onderwerpen voor scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="81498-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="81498-112">XML-indeling help-onderwerpen voor Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="81498-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="81498-113">Op basis van tekst help-onderwerpen, zoals over onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="81498-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="81498-114">De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) controleert of de inhoud van het CAB-bestand wanneer dit het CAB-bestand hebt uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="81498-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="81498-115">Als `Update-Help` vindt niet-compatibele bestandstypen in een bij te werken Help CAB-bestand, wordt een afsluitende fout gegenereerd en stopt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="81498-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="81498-116">Wordt een help-bestanden van het CAB-bestand, zelfs als die van compatibele bestandstypen niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="81498-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>