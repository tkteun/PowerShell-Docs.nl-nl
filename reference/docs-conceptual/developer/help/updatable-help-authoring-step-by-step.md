---
ms.date: 09/13/2016
ms.topic: reference
title: Bij te werken hulp bij het ontwerpen-stap voor stap
description: Bij te werken hulp bij het ontwerpen-stap voor stap
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658814"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="e6948-103">Ontwerpen van Help die kan worden bijgewerkt: stap voor stap</span><span class="sxs-lookup"><span data-stu-id="e6948-103">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="e6948-104">Dit document bevat een lijst met de stappen in het proces van het maken van een Beschrijf bare Help.</span><span class="sxs-lookup"><span data-stu-id="e6948-104">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="e6948-105">Beschrijf bare Help voor ontwerpen: stapsgewijs</span><span class="sxs-lookup"><span data-stu-id="e6948-105">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="e6948-106">De Help die kan worden bijgewerkt, is ontworpen voor eind gebruikers, maar biedt ook aanzienlijke voor delen van module auteurs en Help-schrijvers, met inbegrip van de mogelijkheid om inhoud toe te voegen, fouten op te lossen, te leveren in meerdere GEBRUIKERSINTERFACE culturen en te reageren op opmerkingen en aanvragen van gebruikers, lang nadat de module is verzonden.</span><span class="sxs-lookup"><span data-stu-id="e6948-106">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="e6948-107">In dit onderwerp wordt uitgelegd hoe u Help-bestanden inpakt en uploadt, zodat gebruikers deze kunnen downloaden en installeren met behulp van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en cmdlets voor [opslaan-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="e6948-107">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="e6948-108">De volgende stappen bieden een overzicht van het proces van het ondersteunen van de Help-informatie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e6948-108">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="e6948-109">Stap 1: een Internet site voor uw Help-bestanden zoeken</span><span class="sxs-lookup"><span data-stu-id="e6948-109">Step 1: Find an internet site for your help files</span></span>

<span data-ttu-id="e6948-110">De eerste stap bij het maken van een Help-informatie is het vinden van een Internet locatie voor de Help-bestanden van uw module.</span><span class="sxs-lookup"><span data-stu-id="e6948-110">The first step in creating updatable help is to find an internet location for your module's help files.</span></span> <span data-ttu-id="e6948-111">U kunt ook twee verschillende locaties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e6948-111">Actually, you can use two different locations.</span></span> <span data-ttu-id="e6948-112">U kunt het bestand met Help-informatie voor de module (HelpInfo XML-hieronder) op één Internet locatie en de CAB-bestanden van de Help-inhoud op een andere Internet locatie houden.</span><span class="sxs-lookup"><span data-stu-id="e6948-112">You can keep your module's help information file (HelpInfo XML - described below) at one internet location and the help content CAB files at another internet location.</span></span> <span data-ttu-id="e6948-113">Alle CAB-bestanden van de Help-inhoud voor een module moeten zich op dezelfde locatie bezoeken.</span><span class="sxs-lookup"><span data-stu-id="e6948-113">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="e6948-114">U kunt CAB-bestanden voor Help-inhoud voor verschillende modules op dezelfde locatie plaatsen.</span><span class="sxs-lookup"><span data-stu-id="e6948-114">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="e6948-115">Stap 2: een HelpInfoURI-sleutel toevoegen aan het module manifest</span><span class="sxs-lookup"><span data-stu-id="e6948-115">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="e6948-116">Voeg een **HelpInfoURI** -sleutel toe aan het module manifest.</span><span class="sxs-lookup"><span data-stu-id="e6948-116">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="e6948-117">De waarde van de sleutel is de Uniform Resource Identifier (URI) van de locatie van het HelpInfo XML-gegevens bestand voor uw module.</span><span class="sxs-lookup"><span data-stu-id="e6948-117">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="e6948-118">Voor beveiliging moet het adres beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="e6948-118">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="e6948-119">De URI moet een Internet locatie opgeven, maar mag de HelpInfo XML-bestands naam niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="e6948-119">The URI should specify an internet location, but must not include the HelpInfo XML filename.</span></span>

<span data-ttu-id="e6948-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e6948-120">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="e6948-121">Stap 3: een HelpInfo XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="e6948-121">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="e6948-122">Het HelpInfo XML-informatie bestand bevat de URI van de Internet locatie van uw Help-bestanden en de versie nummers van de nieuwste Help-bestanden voor uw module in elke ondersteunde UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="e6948-122">The HelpInfo XML information file contains the URI of the internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="e6948-123">Elke Windows Power shell-module heeft één HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="e6948-123">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="e6948-124">Wanneer u de Help-bestanden bijwerkt, moet u het HelpInfo XML-bestand bewerken of vervangen. u kunt geen andere toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e6948-124">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="e6948-125">Zie [How to Create a HELPINFO XML file](./how-to-create-a-helpinfo-xml-file.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e6948-125">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-create-cab-files"></a><span data-ttu-id="e6948-126">Stap 4: CAB-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="e6948-126">Step 4: Create CAB files</span></span>

<span data-ttu-id="e6948-127">Gebruik een hulp programma waarmee u Cabinet ( `.cab` )-bestanden maakt, zoals `MakeCab.exe` , om een CAB-bestand te maken dat de Help-bestanden voor uw module bevat.</span><span class="sxs-lookup"><span data-stu-id="e6948-127">Use a tool that creates cabinet (`.cab`) files, such as `MakeCab.exe`, to create a CAB file that contains the help files for your module.</span></span> <span data-ttu-id="e6948-128">Maak een afzonderlijk CAB-bestand voor de Help-bestanden in elke ondersteunde UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="e6948-128">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="e6948-129">Zie voor meer informatie voor [bereiding voor het voorbereiden van bijwerk bare Help cab-bestanden](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="e6948-129">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-5-upload-your-files"></a><span data-ttu-id="e6948-130">Stap 5: uw bestanden uploaden</span><span class="sxs-lookup"><span data-stu-id="e6948-130">Step 5: Upload your files</span></span>

<span data-ttu-id="e6948-131">Als u nieuwe of bijgewerkte Help-bestanden wilt publiceren, uploadt u de CAB-bestanden naar de Internet locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="e6948-131">To publish new or updated help files, upload the CAB files to the internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="e6948-132">Upload vervolgens het HelpInfo XML-bestand naar de Internet locatie die is opgegeven door de waarde van de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="e6948-132">Then, upload the HelpInfo XML file to the internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
