---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-pakket resource
ms.openlocfilehash: efac07b4b051564cadd5aa1542a6afda6cd453ad
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324297"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="665d5-103">DSC-pakket resource</span><span class="sxs-lookup"><span data-stu-id="665d5-103">DSC Package Resource</span></span>

> <span data-ttu-id="665d5-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="665d5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="665d5-105">De **pakket** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van pakketten, zoals Windows Installer en Setup. exe-pakketten, op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="665d5-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="665d5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="665d5-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="665d5-107">properties</span><span class="sxs-lookup"><span data-stu-id="665d5-107">Properties</span></span>

|<span data-ttu-id="665d5-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="665d5-108">Property</span></span> |<span data-ttu-id="665d5-109">Description</span><span class="sxs-lookup"><span data-stu-id="665d5-109">Description</span></span> |
|---|---|
|<span data-ttu-id="665d5-110">Name</span><span class="sxs-lookup"><span data-stu-id="665d5-110">Name</span></span> |<span data-ttu-id="665d5-111">Hiermee wordt de naam aangegeven van het pakket waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="665d5-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="665d5-112">Path</span><span class="sxs-lookup"><span data-stu-id="665d5-112">Path</span></span> |<span data-ttu-id="665d5-113">Hiermee wordt het pad aangegeven waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="665d5-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="665d5-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="665d5-114">ProductId</span></span> |<span data-ttu-id="665d5-115">Hiermee wordt de product-ID aangegeven waarmee het pakket uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="665d5-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="665d5-116">Argumenten</span><span class="sxs-lookup"><span data-stu-id="665d5-116">Arguments</span></span> |<span data-ttu-id="665d5-117">Een lijst met argumenten die precies zo worden door gegeven aan het pakket.</span><span class="sxs-lookup"><span data-stu-id="665d5-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="665d5-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="665d5-118">Credential</span></span> |<span data-ttu-id="665d5-119">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="665d5-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="665d5-120">Deze eigenschap wordt niet gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="665d5-120">This property is not used to install the package.</span></span> <span data-ttu-id="665d5-121">Het pakket wordt altijd op het lokale systeem geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="665d5-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="665d5-122">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="665d5-122">LogPath</span></span> |<span data-ttu-id="665d5-123">Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="665d5-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="665d5-124">Return code</span><span class="sxs-lookup"><span data-stu-id="665d5-124">ReturnCode</span></span> |<span data-ttu-id="665d5-125">Geeft de verwachte retour code aan.</span><span class="sxs-lookup"><span data-stu-id="665d5-125">Indicates the expected return code.</span></span> <span data-ttu-id="665d5-126">Als de daad werkelijke retour code niet overeenkomt met de verwachte waarde die hier wordt opgegeven, wordt er een fout geretourneerd door de configuratie.</span><span class="sxs-lookup"><span data-stu-id="665d5-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="665d5-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="665d5-127">Common properties</span></span>

|<span data-ttu-id="665d5-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="665d5-128">Property</span></span> |<span data-ttu-id="665d5-129">Description</span><span class="sxs-lookup"><span data-stu-id="665d5-129">Description</span></span> |
|---|---|
|<span data-ttu-id="665d5-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="665d5-130">DependsOn</span></span> |<span data-ttu-id="665d5-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="665d5-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="665d5-132">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="665d5-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="665d5-133">Zo</span><span class="sxs-lookup"><span data-stu-id="665d5-133">Ensure</span></span> |<span data-ttu-id="665d5-134">Hiermee wordt aangegeven of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="665d5-134">Indicates if the package is installed.</span></span> <span data-ttu-id="665d5-135">Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="665d5-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="665d5-136">Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="665d5-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="665d5-137">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="665d5-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="665d5-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="665d5-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="665d5-139">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="665d5-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="665d5-140">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="665d5-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="665d5-141">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="665d5-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="665d5-142">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="665d5-142">Example</span></span>

<span data-ttu-id="665d5-143">In dit voor beeld wordt het MSI-installatie programma uitgevoerd dat zich bevindt in het opgegeven pad en heeft de opgegeven product-ID.</span><span class="sxs-lookup"><span data-stu-id="665d5-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```