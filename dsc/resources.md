---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-Resources
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219807"
---
# <a name="dsc-resources"></a><span data-ttu-id="42082-103">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="42082-103">DSC Resources</span></span>

><span data-ttu-id="42082-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="42082-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="42082-105">Desired dat State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="42082-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="42082-106">Een bron beschrijft eigenschappen die kunnen worden geconfigureerd (schema) en bevat de functies van de PowerShell-script die de lokale Configuration Manager (LCM) ' om deze te maken zodat' aanroept.</span><span class="sxs-lookup"><span data-stu-id="42082-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="42082-107">Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.</span><span class="sxs-lookup"><span data-stu-id="42082-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="42082-108">Groepen van zoals bronnen worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die overdraagbaar en bevat metagegevens om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="42082-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="42082-109">De volgende onderwerpen beschrijven DSC-resources:</span><span class="sxs-lookup"><span data-stu-id="42082-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="42082-110">Ingebouwde DSC-resources</span><span class="sxs-lookup"><span data-stu-id="42082-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="42082-111">Maken van aangepaste DSC-resources</span><span class="sxs-lookup"><span data-stu-id="42082-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="42082-112">Ingebouwde DSC-resources voor Linux</span><span class="sxs-lookup"><span data-stu-id="42082-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)