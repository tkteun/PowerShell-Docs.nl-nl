---
title: 'Bijwerk bare Help-ontwerpen: Step-by-Step | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357314"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="ebc99-102">Ontwerpen van Help die kan worden bijgewerkt: stap voor stap</span><span class="sxs-lookup"><span data-stu-id="ebc99-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="ebc99-103">Dit document bevat een lijst met de stappen in het proces van het maken van een Beschrijf bare Help.</span><span class="sxs-lookup"><span data-stu-id="ebc99-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="ebc99-104">Beschrijf bare Help voor ontwerpen: stapsgewijs</span><span class="sxs-lookup"><span data-stu-id="ebc99-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="ebc99-105">De Help-informatie die kan worden bijgewerkt, is ontworpen voor eind gebruikers, maar biedt ook aanzienlijke voor delen van module auteurs en Help schrijvers, met inbegrip van de mogelijkheid om inhoud toe te voegen, fouten op te lossen, te leveren in meerdere GEBRUIKERSINTERFACE culturen en te reageren op opmerkingen en aanvragen van gebruikers, lang nadat de de module is verzonden.</span><span class="sxs-lookup"><span data-stu-id="ebc99-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="ebc99-106">In dit onderwerp wordt uitgelegd hoe u Help-bestanden inpakt en uploadt, zodat gebruikers deze kunnen downloaden en installeren met behulp van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en cmdlets voor [opslaan-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="ebc99-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="ebc99-107">De volgende stappen bieden een overzicht van het proces van het ondersteunen van de Help-informatie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="ebc99-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="ebc99-108">Stap 1: een Internet site voor uw Help-bestanden zoeken</span><span class="sxs-lookup"><span data-stu-id="ebc99-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="ebc99-109">De eerste stap bij het maken van een Help-informatie is het vinden van een Internet locatie voor de Help-bestanden van uw module.</span><span class="sxs-lookup"><span data-stu-id="ebc99-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="ebc99-110">U kunt ook twee verschillende locaties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ebc99-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="ebc99-111">U kunt het bestand met Help-informatie voor de module (HelpInfo XML-hieronder) op één Internet locatie en de CAB-bestanden van de Help-inhoud op een andere Internet locatie houden.</span><span class="sxs-lookup"><span data-stu-id="ebc99-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="ebc99-112">Alle CAB-bestanden van de Help-inhoud voor een module moeten zich op dezelfde locatie bezoeken.</span><span class="sxs-lookup"><span data-stu-id="ebc99-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="ebc99-113">U kunt CAB-bestanden voor Help-inhoud voor verschillende modules op dezelfde locatie plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ebc99-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="ebc99-114">Stap 2: een HelpInfoURI-sleutel toevoegen aan het module manifest</span><span class="sxs-lookup"><span data-stu-id="ebc99-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="ebc99-115">Voeg een **HelpInfoURI** -sleutel toe aan het module manifest.</span><span class="sxs-lookup"><span data-stu-id="ebc99-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="ebc99-116">De waarde van de sleutel is de Uniform Resource Identifier (URI) van de locatie van het HelpInfo XML-gegevens bestand voor uw module.</span><span class="sxs-lookup"><span data-stu-id="ebc99-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="ebc99-117">Voor beveiliging moet het adres beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="ebc99-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="ebc99-118">De URI moet een Internet locatie opgeven, maar mag de HelpInfo XML-bestands naam niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="ebc99-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="ebc99-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ebc99-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="ebc99-120">Stap 3: een HelpInfo XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="ebc99-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="ebc99-121">Het HelpInfo XML-informatie bestand bevat de URI van de Internet locatie van uw Help-bestanden en de versie nummers van de nieuwste Help-bestanden voor uw module in elke ondersteunde UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="ebc99-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="ebc99-122">Elke Windows Power shell-module heeft één HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="ebc99-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="ebc99-123">Wanneer u de Help-bestanden bijwerkt, moet u het HelpInfo XML-bestand bewerken of vervangen. u kunt geen andere toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ebc99-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="ebc99-124">Zie [How to Create a HELPINFO XML file](./how-to-create-a-helpinfo-xml-file.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ebc99-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="ebc99-125">Stap 4: uw Help-bestanden ondertekenen</span><span class="sxs-lookup"><span data-stu-id="ebc99-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="ebc99-126">Digitale hand tekeningen zijn niet vereist, maar het is een aanbevolen aanbeveling wanneer u bestanden deelt.</span><span class="sxs-lookup"><span data-stu-id="ebc99-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="ebc99-127">Stap 5: CAB-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="ebc99-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="ebc99-128">Gebruik een hulp programma dat cab-bestanden (. cab) maakt, zoals MakeCab. exe, om een te maken. CAB-bestand dat de Help-bestanden voor uw module bevat.</span><span class="sxs-lookup"><span data-stu-id="ebc99-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="ebc99-129">Maak een afzonderlijk CAB-bestand voor de Help-bestanden in elke ondersteunde UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="ebc99-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="ebc99-130">Zie voor meer informatie voor [bereiding voor het voorbereiden van bijwerk bare Help cab-bestanden](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="ebc99-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="ebc99-131">Stap 6: uw bestanden uploaden</span><span class="sxs-lookup"><span data-stu-id="ebc99-131">Step 6: Upload your files</span></span>

<span data-ttu-id="ebc99-132">Als u nieuwe of bijgewerkte Help-bestanden wilt publiceren, uploadt u de CAB-bestanden naar de Internet locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="ebc99-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="ebc99-133">Upload vervolgens het HelpInfo XML-bestand naar de Internet locatie die is opgegeven door de waarde van de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="ebc99-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
