---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-pakket resource
ms.openlocfilehash: ff2eae712b4117da9bca915f52e18caed7c4885d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559927"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="c7322-103">DSC-pakket resource</span><span class="sxs-lookup"><span data-stu-id="c7322-103">DSC Package Resource</span></span>

> <span data-ttu-id="c7322-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="c7322-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c7322-105">De **pakket** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van pakketten, zoals Windows Installer en Setup. exe-pakketten, op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="c7322-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7322-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c7322-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c7322-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c7322-107">Properties</span></span>

|<span data-ttu-id="c7322-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c7322-108">Property</span></span> |<span data-ttu-id="c7322-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7322-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c7322-110">Name</span><span class="sxs-lookup"><span data-stu-id="c7322-110">Name</span></span> |<span data-ttu-id="c7322-111">Hiermee wordt de naam aangegeven van het pakket waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="c7322-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c7322-112">Pad</span><span class="sxs-lookup"><span data-stu-id="c7322-112">Path</span></span> |<span data-ttu-id="c7322-113">Hiermee wordt het pad aangegeven waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="c7322-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="c7322-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="c7322-114">ProductId</span></span> |<span data-ttu-id="c7322-115">Hiermee wordt de product-ID aangegeven waarmee het pakket uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="c7322-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="c7322-116">Argumenten</span><span class="sxs-lookup"><span data-stu-id="c7322-116">Arguments</span></span> |<span data-ttu-id="c7322-117">Een lijst met argumenten die precies zo worden door gegeven aan het pakket.</span><span class="sxs-lookup"><span data-stu-id="c7322-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="c7322-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="c7322-118">Credential</span></span> |<span data-ttu-id="c7322-119">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="c7322-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="c7322-120">Deze eigenschap wordt niet gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="c7322-120">This property is not used to install the package.</span></span> <span data-ttu-id="c7322-121">Het pakket wordt altijd op het lokale systeem geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c7322-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="c7322-122">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="c7322-122">LogPath</span></span> |<span data-ttu-id="c7322-123">Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c7322-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="c7322-124">Return code</span><span class="sxs-lookup"><span data-stu-id="c7322-124">ReturnCode</span></span> |<span data-ttu-id="c7322-125">Geeft de verwachte retour code aan.</span><span class="sxs-lookup"><span data-stu-id="c7322-125">Indicates the expected return code.</span></span> <span data-ttu-id="c7322-126">Als de daad werkelijke retour code niet overeenkomt met de verwachte waarde die hier wordt opgegeven, wordt er een fout geretourneerd door de configuratie.</span><span class="sxs-lookup"><span data-stu-id="c7322-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c7322-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c7322-127">Common properties</span></span>

|<span data-ttu-id="c7322-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c7322-128">Property</span></span> |<span data-ttu-id="c7322-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7322-129">Description</span></span> |
|---|---|
|<span data-ttu-id="c7322-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c7322-130">DependsOn</span></span> |<span data-ttu-id="c7322-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c7322-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c7322-132">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="c7322-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c7322-133">Zo</span><span class="sxs-lookup"><span data-stu-id="c7322-133">Ensure</span></span> |<span data-ttu-id="c7322-134">Hiermee wordt aangegeven of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c7322-134">Indicates if the package is installed.</span></span> <span data-ttu-id="c7322-135">Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="c7322-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="c7322-136">Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c7322-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="c7322-137">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="c7322-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="c7322-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c7322-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="c7322-139">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="c7322-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c7322-140">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="c7322-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c7322-141">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7322-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c7322-142">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c7322-142">Example</span></span>

<span data-ttu-id="c7322-143">In dit voor beeld wordt het MSI-installatie programma uitgevoerd dat zich bevindt in het opgegeven pad en heeft de opgegeven product-ID.</span><span class="sxs-lookup"><span data-stu-id="c7322-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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
