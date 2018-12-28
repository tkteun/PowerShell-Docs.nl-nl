---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Pakket- en Resources uploaden naar een Pull-Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403915"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="ee7ae-103">Pakket- en Resources uploaden naar een Pull-Server</span><span class="sxs-lookup"><span data-stu-id="ee7ae-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="ee7ae-104">De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="ee7ae-105">Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="ee7ae-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="ee7ae-106">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ee7ae-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ee7ae-107">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ee7ae-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="ee7ae-108">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="ee7ae-109">In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="ee7ae-110">Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="ee7ae-111">Pakket Resource Modules</span><span class="sxs-lookup"><span data-stu-id="ee7ae-111">Package Resource Modules</span></span>

<span data-ttu-id="ee7ae-112">Elke resource die beschikbaar zijn voor een client te downloaden moet worden opgeslagen in een 'ZIP'-bestand.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="ee7ae-113">In het volgende voorbeeld ziet u de vereiste stappen met behulp van de [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="ee7ae-114">Als u clients met behulp van PowerShell 4.0 hebt, wordt u moet flaten de mapstructuur van de resource en de versie-mappen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="ee7ae-115">Zie voor meer informatie, [meerdere versies van de Resource](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="ee7ae-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="ee7ae-116">U kunt de resource-map met behulp van een hulpprogramma, script of methode die u wilt comprimeren.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="ee7ae-117">In Windows, kunt u *met de rechtermuisknop op* op de directory 'xPSDesiredStateConfiguration' en selecteer "Verzenden naar" en "Gecomprimeerde map".</span><span class="sxs-lookup"><span data-stu-id="ee7ae-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Klik met de rechtermuisknop](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="ee7ae-119">Naamgeving van de Resource-archief</span><span class="sxs-lookup"><span data-stu-id="ee7ae-119">Naming the Resource Archive</span></span>

<span data-ttu-id="ee7ae-120">Het archief van de Resource moet worden benoemd met de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="ee7ae-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="ee7ae-121">In het bovenstaande voorbeeld moet 'xPSDesiredStateConfiguration.zip' hernoemd 'xPSDesiredStateConfiguration_8.4.4.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="ee7ae-122">Controlesommen maken</span><span class="sxs-lookup"><span data-stu-id="ee7ae-122">Create CheckSums</span></span>

<span data-ttu-id="ee7ae-123">Zodra de Resource-module is gecomprimeerd en gewijzigd, moet u maken een **controlesom**.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="ee7ae-124">De **controlesom** wordt gebruikt om door de LCM op de client om te bepalen of de resource is gewijzigd en moet opnieuw worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="ee7ae-125">U kunt maken een **controlesom** met de [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, zoals weergegeven in het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="ee7ae-126">Er is geen uitvoer wordt weergegeven, maar u ziet nu een 'xPSDesiredStateConfiguration_8.4.4.0.zip.checksum'.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="ee7ae-127">U kunt ook uitvoeren `New-DSCCheckSum` op basis van een map met bestanden met behulp van de `-Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="ee7ae-128">Als een controlesom al bestaat, kunt u zorgen dat niet opnieuw worden gemaakt met de `-Force` parameter.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="ee7ae-129">Waar archieven van de Resource wordt opgeslagen</span><span class="sxs-lookup"><span data-stu-id="ee7ae-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="ee7ae-130">Op een DSC-HTTP-Pull-Server</span><span class="sxs-lookup"><span data-stu-id="ee7ae-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="ee7ae-131">Bij het instellen van uw HTTP-Pull-Server, zoals uitgelegd in [instellen van een DSC HTTP-Pull-Server](pullServer.md), geeft u de mappen voor de **ModulePath** en **ConfigurationPath** sleutels.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="ee7ae-132">De **ConfigurationPath** sleutel geeft aan waar alle bestanden ".mof" moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="ee7ae-133">De **ModulePath** geeft aan waar alle Modules DSC-Resource moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="ee7ae-134">Op een SMB-Share</span><span class="sxs-lookup"><span data-stu-id="ee7ae-134">On an SMB Share</span></span>

<span data-ttu-id="ee7ae-135">Als u hebt opgegeven een **ResourceRepositoryShare**wordt bij het instellen van uw Pull-Client, opslaan-archieven en controlesommen in de **bronpad** map van de **ResourceRepositoryShare** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="ee7ae-136">Als u alleen opgegeven een **ConfigurationRepositoryShare**wordt bij het instellen van uw Pull-Client, opslaan-archieven en controlesommen in de **bronpad** map van de  **ConfigurationRepositoryShare** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="ee7ae-137">De resources worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="ee7ae-137">Updating resources</span></span>

<span data-ttu-id="ee7ae-138">U kunt afdwingen dat een knooppunt de daarbij behorende bronnen bijwerken door het wijzigen van het versienummer in de naam van het archief, of door het maken van een nieuwe controlesom.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="ee7ae-139">De Pull-Client voor nieuwere versies van de vereiste resources wordt gecontroleerd, evenals controlesommen, bijgewerkt wanneer de LCM wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="ee7ae-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee7ae-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ee7ae-140">See also</span></span>

- [<span data-ttu-id="ee7ae-141">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ee7ae-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ee7ae-142">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ee7ae-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
