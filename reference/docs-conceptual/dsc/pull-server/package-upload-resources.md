---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Resources verpakken en uploaden naar een pull-server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942242"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="8a54a-103">Resources verpakken en uploaden naar een pull-server</span><span class="sxs-lookup"><span data-stu-id="8a54a-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="8a54a-104">In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="8a54a-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="8a54a-105">Als u uw pull-server niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="8a54a-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="8a54a-106">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="8a54a-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8a54a-107">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="8a54a-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8a54a-108">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="8a54a-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8a54a-109">In dit artikel wordt uitgelegd hoe u bronnen uploadt, zodat ze beschikbaar zijn om te worden gedownload en clients zodanig configureren dat bronnen automatisch worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="8a54a-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="8a54a-110">Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** -of **Push** (V5), downloadt het automatisch alle resources die vereist zijn voor de configuratie van de locatie die is opgegeven in de LCM.</span><span class="sxs-lookup"><span data-stu-id="8a54a-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="8a54a-111">Pakket resource modules</span><span class="sxs-lookup"><span data-stu-id="8a54a-111">Package Resource Modules</span></span>

<span data-ttu-id="8a54a-112">Elke resource die beschikbaar is voor een client die kan worden gedownload, moet worden opgeslagen in een zip-bestand.</span><span class="sxs-lookup"><span data-stu-id="8a54a-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="8a54a-113">In het onderstaande voor beeld ziet u de vereiste stappen met behulp van de [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resource.</span><span class="sxs-lookup"><span data-stu-id="8a54a-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="8a54a-114">Als u een client hebt die Power Shell 4,0 gebruikt, moet u de structuur van de resource mappen plat maken en alle versie mappen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8a54a-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="8a54a-115">Zie [meerdere resource versies](../configurations/import-dscresource.md#multiple-resource-versions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8a54a-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="8a54a-116">U kunt de resource directory comprimeren met elk hulp programma, script of methode die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8a54a-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="8a54a-117">In Windows kunt u met de rechter muisknop op de map ' xPSDesiredStateConfiguration ' *klikken* en ' verzenden naar ' en ' gecomprimeerde map ' selecteren.</span><span class="sxs-lookup"><span data-stu-id="8a54a-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Met de rechter muisknop](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="8a54a-119">De naam van het Resource Archief benoemen</span><span class="sxs-lookup"><span data-stu-id="8a54a-119">Naming the Resource Archive</span></span>

<span data-ttu-id="8a54a-120">Het bron archief moet een naam hebben met de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="8a54a-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="8a54a-121">In het bovenstaande voor beeld moet ' xPSDesiredStateConfiguration. zip ' de naam ' xPSDesiredStateConfiguration_ 8.4.4.0. zip ' hebben.</span><span class="sxs-lookup"><span data-stu-id="8a54a-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="8a54a-122">Controle sommen maken</span><span class="sxs-lookup"><span data-stu-id="8a54a-122">Create CheckSums</span></span>

<span data-ttu-id="8a54a-123">Zodra de resource module is gecomprimeerd en de naam ervan is gewijzigd, moet u een **controlesom**maken.</span><span class="sxs-lookup"><span data-stu-id="8a54a-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="8a54a-124">De **controlesom** wordt door de LCM op de client gebruikt om te bepalen of de resource is gewijzigd en moet opnieuw worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="8a54a-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="8a54a-125">U kunt een **controlesom** maken met de cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , zoals wordt weer gegeven in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="8a54a-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="8a54a-126">Er wordt geen uitvoer weer gegeven, maar u ziet nu een ' xPSDesiredStateConfiguration_ 8.4.4.0. zip. checksum '.</span><span class="sxs-lookup"><span data-stu-id="8a54a-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="8a54a-127">U kunt ook `New-DSCCheckSum` uitvoeren voor een map met bestanden met behulp van de para meter `-Path`.</span><span class="sxs-lookup"><span data-stu-id="8a54a-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="8a54a-128">Als er al een controlesom bestaat, kunt u afdwingen dat deze opnieuw wordt gemaakt met de para meter `-Force`.</span><span class="sxs-lookup"><span data-stu-id="8a54a-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="8a54a-129">Locatie voor het opslaan van resource archieven</span><span class="sxs-lookup"><span data-stu-id="8a54a-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="8a54a-130">Op een DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="8a54a-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="8a54a-131">Wanneer u de HTTP-pull-server instelt, zoals wordt uitgelegd in [een DSC HTTP-pull-server instellen](pullServer.md), geeft u directory's op voor de sleutels **para modulepath in** en **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="8a54a-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="8a54a-132">De **ConfigurationPath** -sleutel geeft aan waar de MOF-bestanden moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8a54a-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="8a54a-133">De **para modulepath in** geeft aan waar eventuele DSC-resource modules moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8a54a-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="8a54a-134">Op een SMB-share</span><span class="sxs-lookup"><span data-stu-id="8a54a-134">On an SMB Share</span></span>

<span data-ttu-id="8a54a-135">Als u een **ResourceRepositoryShare**hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ResourceRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="8a54a-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="8a54a-136">Als u alleen een **ConfigurationRepositoryShare**hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ConfigurationRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="8a54a-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="8a54a-137">Resources bijwerken</span><span class="sxs-lookup"><span data-stu-id="8a54a-137">Updating resources</span></span>

<span data-ttu-id="8a54a-138">U kunt afdwingen dat een knoop punt de resources bijwerkt door het versie nummer in de naam van het archief te wijzigen of door een nieuwe controlesom te maken.</span><span class="sxs-lookup"><span data-stu-id="8a54a-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="8a54a-139">De pull-client controleert op nieuwere versies van de vereiste resources, evenals bijgewerkte controle sommen wanneer de LCM wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="8a54a-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a54a-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8a54a-140">See also</span></span>

- [<span data-ttu-id="8a54a-141">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="8a54a-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8a54a-142">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="8a54a-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
