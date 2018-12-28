---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Publiceren naar een Pull-Server met behulp van configuratie-ID's (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403940"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="ac7fc-103">Publiceren naar een Pull-Server met behulp van configuratie-ID's (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="ac7fc-104">De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="ac7fc-105">Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="ac7fc-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="ac7fc-106">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ac7fc-107">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="ac7fc-108">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="ac7fc-109">In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="ac7fc-110">Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="ac7fc-111">Configuraties compileren</span><span class="sxs-lookup"><span data-stu-id="ac7fc-111">Compile Configurations</span></span>

<span data-ttu-id="ac7fc-112">De eerste stap bij het opslaan van [configuraties](../configurations/configurations.md) is gecompileerd in MOF-bestanden op een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="ac7fc-113">Als u een configuratie algemene en van toepassing op meer clients bevatten, gebruikt u `localhost` in het knooppunt-blok.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="ac7fc-114">Het volgende voorbeeld ziet u een configuratie-shell die gebruikmaakt van `localhost` in plaats van de naam van een specifieke client.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="ac7fc-115">Nadat u hebt de configuratie van uw algemene gecompileerd, moet u een bestand 'localhost.mof' hebben.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="ac7fc-116">Naam van het MOF-bestand</span><span class="sxs-lookup"><span data-stu-id="ac7fc-116">Renaming the MOF file</span></span>

<span data-ttu-id="ac7fc-117">U kunt opslaan '.mof' configuratiebestanden op een Pull-Server door **ConfigurationName** of **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="ac7fc-118">Afhankelijk van hoe u van plan bent voor het instellen van uw pull-clients, kunt u een sectie hieronder goed uw gecompileerde ".mof" om bestandsnamen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="ac7fc-119">Configuratie-ID's (GUID)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="ac7fc-120">U moet de naam van uw bestand 'localhost.mof' naar '<GUID>.mof "bestand.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="ac7fc-121">U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder of met behulp van de [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="ac7fc-122">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="ac7fc-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="ac7fc-123">Vervolgens kunt u uw 'MOF'-bestand met behulp van een acceptabele methode wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="ac7fc-124">Het onderstaande voorbeeld wordt de [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="ac7fc-125">Voor meer informatie over het gebruik van **GUID's** in uw omgeving, Zie [plannen voor GUID's](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="ac7fc-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="ac7fc-126">Configuratienamen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-126">Configuration Names</span></span>

<span data-ttu-id="ac7fc-127">U moet de naam van uw bestand 'localhost.mof' naar '<Configuration Name>.mof "bestand.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="ac7fc-128">In het volgende voorbeeld wordt wordt de naam van de configuratie van de vorige sectie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="ac7fc-129">Vervolgens kunt u uw 'MOF'-bestand met behulp van een acceptabele methode wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="ac7fc-130">Het onderstaande voorbeeld wordt de [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="ac7fc-131">De controlesom maken</span><span class="sxs-lookup"><span data-stu-id="ac7fc-131">Create the CheckSum</span></span>

<span data-ttu-id="ac7fc-132">Elk bestand '.mof' die is opgeslagen op een Pull-Server of SMB-share moet een bijbehorende ".checksum"-bestand hebt.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="ac7fc-133">Dit bestand kiest, kunnen clients weten wanneer het bestand gekoppeld ".mof" is gewijzigd en moet opnieuw worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="ac7fc-134">U kunt maken een **controlesom** met de [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="ac7fc-135">U kunt ook uitvoeren `New-DSCCheckSum` op basis van een map met bestanden met behulp van de `-Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="ac7fc-136">Als een controlesom al bestaat, kunt u zorgen dat niet opnieuw worden gemaakt met de `-Force` parameter.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="ac7fc-137">Het volgende voorbeeld opgegeven van een map met het bestand '.mof' uit de vorige sectie en maakt gebruik van de `-Force` parameter.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="ac7fc-138">Er is geen uitvoer wordt weergegeven, maar u ziet nu een '<GUID or Configuration Name>. mof.checksum "bestand.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="ac7fc-139">Waar om op te slaan en controlesommen van het MOF-bestanden</span><span class="sxs-lookup"><span data-stu-id="ac7fc-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="ac7fc-140">Op een DSC-HTTP-Pull-Server</span><span class="sxs-lookup"><span data-stu-id="ac7fc-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="ac7fc-141">Bij het instellen van uw HTTP-Pull-Server, zoals uitgelegd in [instellen van een DSC HTTP-Pull-Server](pullServer.md), geeft u de mappen voor de **ModulePath** en **ConfigurationPath** sleutels.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="ac7fc-142">De **ConfigurationPath** sleutel geeft aan waar alle bestanden ".mof" moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="ac7fc-143">De **ConfigurationPath** geeft aan waar een MOF-bestanden en ".checksum" bestanden moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="ac7fc-144">Op een SMB-Share</span><span class="sxs-lookup"><span data-stu-id="ac7fc-144">On an SMB Share</span></span>

<span data-ttu-id="ac7fc-145">Bij het instellen van een Pull-Client een SMB-share te gebruiken, geeft u een **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="ac7fc-146">Alle bestanden van ".mof" en ".checksum" bestanden moeten vervolgens worden opgeslagen in de **bronpad** map van de **ConfigurationRepositoryShare** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="ac7fc-147">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-147">Next Steps</span></span>

<span data-ttu-id="ac7fc-148">Vervolgens wilt u Pull-Clients om op te halen van de opgegeven configuratie configureren.</span><span class="sxs-lookup"><span data-stu-id="ac7fc-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="ac7fc-149">Zie voor meer informatie, een van de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="ac7fc-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="ac7fc-150">Instellen van een Pull-Client met behulp van configuratie-ID's (v4)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="ac7fc-151">Instellen van een Pull-Client met behulp van configuratie-ID's (v5)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="ac7fc-152">Instellen van een Pull-Client met behulp van configuratienamen (v5)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="ac7fc-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac7fc-153">See also</span></span>

- [<span data-ttu-id="ac7fc-154">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ac7fc-155">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="ac7fc-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="ac7fc-156">Pakket- en Resources uploaden naar een Pull-Server</span><span class="sxs-lookup"><span data-stu-id="ac7fc-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
