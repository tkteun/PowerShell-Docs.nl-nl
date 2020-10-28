---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Resources verpakken en uploaden naar een pull-server
description: In dit artikel wordt beschreven hoe u bronnen uploadt naar een pull-server, zodat deze kunnen worden gedownload door configuraties op de knoop punten die worden beheerd door DSC.
ms.openlocfilehash: a19d04346a0ae546cfcaf70701fde870d3839f65
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661690"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="62cf4-104">Resources verpakken en uploaden naar een pull-server</span><span class="sxs-lookup"><span data-stu-id="62cf4-104">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="62cf4-105">In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="62cf4-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="62cf4-106">Als u uw pull-server niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="62cf4-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="62cf4-107">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="62cf4-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="62cf4-108">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="62cf4-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="62cf4-109">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="62cf4-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="62cf4-110">In dit artikel wordt uitgelegd hoe u bronnen uploadt, zodat ze beschikbaar zijn om te worden gedownload en clients zodanig configureren dat bronnen automatisch worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="62cf4-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="62cf4-111">Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** -of **Push** (V5), downloadt het automatisch alle resources die vereist zijn voor de configuratie van de locatie die is opgegeven in de LCM.</span><span class="sxs-lookup"><span data-stu-id="62cf4-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="62cf4-112">Pakket resource modules</span><span class="sxs-lookup"><span data-stu-id="62cf4-112">Package Resource Modules</span></span>

<span data-ttu-id="62cf4-113">Elke resource die beschikbaar is voor een client die kan worden gedownload, moet worden opgeslagen in een `.zip` bestand.</span><span class="sxs-lookup"><span data-stu-id="62cf4-113">Each resource available for a client to download must be stored in a `.zip` file.</span></span> <span data-ttu-id="62cf4-114">In het onderstaande voor beeld ziet u de vereiste stappen met behulp van de [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resource.</span><span class="sxs-lookup"><span data-stu-id="62cf4-114">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="62cf4-115">Als u een client hebt die Power Shell 4,0 gebruikt, moet u de structuur van de resource mappen plat maken en alle versie mappen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="62cf4-115">If you have any clients using PowerShell 4.0, you will need to flatten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="62cf4-116">Zie [meerdere resource versies](../configurations/import-dscresource.md#multiple-resource-versions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62cf4-116">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="62cf4-117">U kunt de resource directory comprimeren met elk hulp programma, script of methode die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62cf4-117">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="62cf4-118">In Windows kunt u met de _rechter_ muisknop op de `xPSDesiredStateConfiguration` map klikken en vervolgens **verzenden naar** en **gecomprimeerde map** selecteren.</span><span class="sxs-lookup"><span data-stu-id="62cf4-118">In Windows, you can _right-click_ on the `xPSDesiredStateConfiguration` directory, and select **Send To** , then **Compressed Folder** .</span></span>

![Klik met de rechter muisknop en verzenden naar-gecomprimeerde map](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="62cf4-120">De naam van het Resource Archief benoemen</span><span class="sxs-lookup"><span data-stu-id="62cf4-120">Naming the Resource Archive</span></span>

<span data-ttu-id="62cf4-121">Het bron archief moet een naam hebben met de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="62cf4-121">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="62cf4-122">In het bovenstaande voor beeld `xPSDesiredStateConfiguration.zip` moet de naam worden gewijzigd `xPSDesiredStateConfiguration_8.4.4.0.zip` .</span><span class="sxs-lookup"><span data-stu-id="62cf4-122">In the example above, `xPSDesiredStateConfiguration.zip` should be renamed `xPSDesiredStateConfiguration_8.4.4.0.zip`.</span></span>

### <a name="create-checksums"></a><span data-ttu-id="62cf4-123">Controle sommen maken</span><span class="sxs-lookup"><span data-stu-id="62cf4-123">Create CheckSums</span></span>

<span data-ttu-id="62cf4-124">Zodra de resource module is gecomprimeerd en de naam ervan is gewijzigd, moet u een **controlesom** maken.</span><span class="sxs-lookup"><span data-stu-id="62cf4-124">Once the Resource module has been compressed and renamed, you need to create a **CheckSum** .</span></span> <span data-ttu-id="62cf4-125">De **controlesom** wordt door de LCM op de client gebruikt om te bepalen of de resource is gewijzigd en moet opnieuw worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="62cf4-125">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="62cf4-126">U kunt een **controlesom** maken met de cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , zoals wordt weer gegeven in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="62cf4-126">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="62cf4-127">Er wordt geen uitvoer weer gegeven, maar u ziet nu een ' xPSDesiredStateConfiguration_8.4.4.0.zip. checksum '.</span><span class="sxs-lookup"><span data-stu-id="62cf4-127">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="62cf4-128">U kunt ook uitvoeren `New-DSCCheckSum` op een map met bestanden met behulp van de `-Path` para meter.</span><span class="sxs-lookup"><span data-stu-id="62cf4-128">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="62cf4-129">Als er al een controlesom bestaat, kunt u afdwingen dat deze opnieuw wordt gemaakt met de `-Force` para meter.</span><span class="sxs-lookup"><span data-stu-id="62cf4-129">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="62cf4-130">Locatie voor het opslaan van resource archieven</span><span class="sxs-lookup"><span data-stu-id="62cf4-130">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="62cf4-131">Op een DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="62cf4-131">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="62cf4-132">Wanneer u de HTTP-pull-server instelt, zoals wordt uitgelegd in [een DSC HTTP-pull-server instellen](pullServer.md), geeft u directory's op voor de sleutels **para modulepath in** en **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="62cf4-132">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="62cf4-133">De **ConfigurationPath** -sleutel geeft aan waar de MOF-bestanden moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="62cf4-133">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="62cf4-134">De **para modulepath in** geeft aan waar eventuele DSC-resource modules moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="62cf4-134">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="62cf4-135">Op een SMB-share</span><span class="sxs-lookup"><span data-stu-id="62cf4-135">On an SMB Share</span></span>

<span data-ttu-id="62cf4-136">Als u een **ResourceRepositoryShare** hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ResourceRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="62cf4-136">If you specified a **ResourceRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="62cf4-137">Als u alleen een **ConfigurationRepositoryShare** hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ConfigurationRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="62cf4-137">If you specified only a **ConfigurationRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="62cf4-138">Bijwerken van resources</span><span class="sxs-lookup"><span data-stu-id="62cf4-138">Updating resources</span></span>

<span data-ttu-id="62cf4-139">U kunt afdwingen dat een knoop punt de resources bijwerkt door het versie nummer in de naam van het archief te wijzigen of door een nieuwe controlesom te maken.</span><span class="sxs-lookup"><span data-stu-id="62cf4-139">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="62cf4-140">De pull-client controleert op nieuwere versies van de vereiste resources, evenals bijgewerkte controle sommen wanneer de LCM wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="62cf4-140">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="62cf4-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="62cf4-141">See also</span></span>

- [<span data-ttu-id="62cf4-142">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="62cf4-142">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="62cf4-143">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="62cf4-143">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
