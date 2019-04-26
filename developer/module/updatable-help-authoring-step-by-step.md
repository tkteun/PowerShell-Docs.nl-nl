---
title: 'Ontwerpen van Help die kan worden bijgewerkt: Stapsgewijze | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082121"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="35553-102">Ontwerpen van Help die kan worden bijgewerkt: stap voor stap</span><span class="sxs-lookup"><span data-stu-id="35553-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="35553-103">Deze documenten worden de stappen van het ontwerpen van bij te werken Help.</span><span class="sxs-lookup"><span data-stu-id="35553-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="35553-104">Bij te werken Help ontwerpen: stap voor stap</span><span class="sxs-lookup"><span data-stu-id="35553-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="35553-105">Help bij te werken is ontworpen voor eindgebruikers, maar ook biedt aanzienlijke voordelen voor auteurs en schrijvers van Help-informatie, inclusief de mogelijkheid om toe te voegen inhoud, fouten, leveren in meerdere UI culturen en reageren op aanvragen, en gebruikersopmerkingen lang na de module heeft verzonden.</span><span class="sxs-lookup"><span data-stu-id="35553-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="35553-106">Dit onderwerp wordt uitgelegd hoe u een pakket en help voor uploaden van bestanden, zodat gebruikers kunnen downloaden en te met behulp van installeren de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="35553-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="35553-107">De volgende stappen bevatten een overzicht van het proces van ondersteunende bij te werken Help.</span><span class="sxs-lookup"><span data-stu-id="35553-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="35553-108">Stap 1: Een internetsite vinden voor de help-bestanden</span><span class="sxs-lookup"><span data-stu-id="35553-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="35553-109">De eerste stap bij het maken van bij te werken Help-informatie is te vinden van een internetlocatie op voor help-bestanden van uw module.</span><span class="sxs-lookup"><span data-stu-id="35553-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="35553-110">Daadwerkelijk, kunt u twee verschillende locaties.</span><span class="sxs-lookup"><span data-stu-id="35553-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="35553-111">U kunt van uw module help-informatiebestand (HelpInfo XML - hieronder beschreven) op één locatie van het Internet en de help-inhoud CAB-bestanden op een andere internetlocatie.</span><span class="sxs-lookup"><span data-stu-id="35553-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="35553-112">Alle help-inhoud CAB-bestanden voor een module moeten zich in dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="35553-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="35553-113">U kunt de help-inhoud CAB-bestanden voor andere modules op dezelfde locatie plaatsen.</span><span class="sxs-lookup"><span data-stu-id="35553-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="35553-114">Stap 2: Een sleutel HelpInfoURI toevoegen aan uw module-manifest</span><span class="sxs-lookup"><span data-stu-id="35553-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="35553-115">Voeg een **HelpInfoURI** sleutel op uw module-manifest.</span><span class="sxs-lookup"><span data-stu-id="35553-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="35553-116">De waarde van de sleutel is de Uniform Resource Identifier (URI) van de locatie van het bestand met HelpInfo XML voor de module.</span><span class="sxs-lookup"><span data-stu-id="35553-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="35553-117">Voor beveiliging, moet het adres beginnen met 'http' of 'https'.</span><span class="sxs-lookup"><span data-stu-id="35553-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="35553-118">De URI moet een Internet-locatie opgeven, maar niet de naam van het HelpInfo XML-bestand moet bevatten.</span><span class="sxs-lookup"><span data-stu-id="35553-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="35553-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="35553-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="35553-120">Stap 3: Een HelpInfo XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="35553-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="35553-121">Het bestand met HelpInfo XML bevat de URI van de Internet-locatie van de help-bestanden en het versienummer van de meest recente help-bestanden voor de module in elke ondersteunde gebruikersinterfacecultuur.</span><span class="sxs-lookup"><span data-stu-id="35553-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="35553-122">Elke Windows PowerShell-module heeft een HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="35553-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="35553-123">Wanneer u de helpbestanden niet bijwerken, u kunt bewerken of vervangen door het HelpInfo XML-bestand. Voeg geen een andere naam.</span><span class="sxs-lookup"><span data-stu-id="35553-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="35553-124">Zie voor meer informatie, [over het maken van een XML-bestand HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="35553-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="35553-125">Stap 4: Meld u aan uw help-bestanden</span><span class="sxs-lookup"><span data-stu-id="35553-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="35553-126">Digitale handtekeningen zijn niet vereist, maar ze zijn een best practice-aanbeveling wanneer u bestanden delen.</span><span class="sxs-lookup"><span data-stu-id="35553-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="35553-127">Stap 5: CAB-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="35553-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="35553-128">Gebruik een hulpprogramma waarmee u cab-bestanden, zoals MakeCab.exe maken maakt een. CAB-bestand met de help-bestanden voor de module.</span><span class="sxs-lookup"><span data-stu-id="35553-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="35553-129">Maak een afzonderlijk cabinetbestand voor de help-bestanden in elke ondersteunde gebruikersinterfacecultuur.</span><span class="sxs-lookup"><span data-stu-id="35553-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="35553-130">Zie voor meer informatie, [over het voorbereiden bij te werken Help CAB-bestanden](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="35553-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="35553-131">Stap 6: Uw bestanden uploaden</span><span class="sxs-lookup"><span data-stu-id="35553-131">Step 6: Upload your files</span></span>

<span data-ttu-id="35553-132">Voor het publiceren van nieuwe of bijgewerkte help-bestanden, kunt u de CAB-bestanden uploaden naar de locatie van het Internet die is opgegeven door de **HelpContentUri** -element in het HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="35553-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="35553-133">Vervolgens kunt u het HelpInfo XML-bestand uploaden naar de locatie van het Internet die is opgegeven door de waarde van de **HelpInfoUri** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="35553-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
