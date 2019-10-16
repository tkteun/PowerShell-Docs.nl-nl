---
title: Toegestane bestands typen in een Help CAB-bestand dat kan worden bijgewerkt | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357503"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="aee65-102">Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="aee65-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="aee65-103">In deze onderwerpen vindt u een overzicht van de inhouds vereisten voor CAB-bestanden die kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="aee65-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="aee65-104">Bijwerk bare CAB-bestands vereisten voor Help</span><span class="sxs-lookup"><span data-stu-id="aee65-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="aee65-105">Inhoud van niet-gecomprimeerd CAB-bestand is standaard beperkt tot 1 GB.</span><span class="sxs-lookup"><span data-stu-id="aee65-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="aee65-106">Als u deze limiet wilt overs Laan, moeten gebruikers de para meter **Force** van de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aee65-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="aee65-107">Om de beveiliging te waarborgen van de Help-bestanden die worden gedownload van Internet, kan een Help CAB-bestand dat kan worden bijgewerkt, alleen de onderstaande bestands typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="aee65-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="aee65-108">Met de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) worden alle bestanden gevalideerd op basis van de schema's van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="aee65-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="aee65-109">Als de `Update-Help`-cmdlet een bestand tegen komt dat ongeldig is of niet het toegestane type heeft, wordt het ongeldige bestand niet geïnstalleerd en worden er geen bestanden meer geïnstalleerd van de CAB op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aee65-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="aee65-110">Help-onderwerpen over XML voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="aee65-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="aee65-111">Help-onderwerpen over XML voor scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="aee65-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="aee65-112">Help-onderwerpen over XML voor Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="aee65-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="aee65-113">Help-onderwerpen op basis van tekst, zoals over onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="aee65-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="aee65-114">De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) de inhoud van het CAB-bestand te controleren wanneer het CAB-bestand wordt uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="aee65-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="aee65-115">Als `Update-Help` niet-compatibele bestands typen vindt in een Help CAB-bestand dat kan worden bijgewerkt, wordt er een afsluit fout gegenereerd en wordt de bewerking gestopt.</span><span class="sxs-lookup"><span data-stu-id="aee65-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="aee65-116">Er worden geen Help-bestanden van het CAB-bestand geïnstalleerd, zelfs van de bestands typen die voldoen aan het beleid.</span><span class="sxs-lookup"><span data-stu-id="aee65-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>