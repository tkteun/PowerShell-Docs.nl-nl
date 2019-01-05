---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Bestandsresource
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048314"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="c1340-103">DSC-Bestandsresource</span><span class="sxs-lookup"><span data-stu-id="c1340-103">DSC File Resource</span></span>

> <span data-ttu-id="c1340-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c1340-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c1340-105">De resource van het bestand in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="c1340-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="c1340-106">**Opmerking:** Als de **MatchSource** eigenschap is ingesteld op **$false** (dit is de standaardwaarde), de inhoud wordt gekopieerd in de cache opgeslagen de eerste keer dat de configuratie is toegepast.</span><span class="sxs-lookup"><span data-stu-id="c1340-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="c1340-107">Volgende aanvragen van de configuratie wordt niet gecontroleerd op bijgewerkte bestanden en/of mappen in het pad dat is opgegeven door **bronpad**.</span><span class="sxs-lookup"><span data-stu-id="c1340-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="c1340-108">Als u wilt controleren op updates voor de bestanden en/of mappen in **bronpad** telkens wanneer de configuratie is toegepast, stel **MatchSource** naar **$true**.</span><span class="sxs-lookup"><span data-stu-id="c1340-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1340-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c1340-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="c1340-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c1340-110">Properties</span></span>

|  <span data-ttu-id="c1340-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c1340-111">Property</span></span>  |  <span data-ttu-id="c1340-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1340-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="c1340-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="c1340-113">DestinationPath</span></span>| <span data-ttu-id="c1340-114">Geeft de locatie waar u om te controleren of de status van een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="c1340-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c1340-115">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c1340-115">Attributes</span></span>| <span data-ttu-id="c1340-116">Hiermee geeft u de gewenste status van de kenmerken voor het betreffende bestand of map.</span><span class="sxs-lookup"><span data-stu-id="c1340-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="c1340-117">Controlesom</span><span class="sxs-lookup"><span data-stu-id="c1340-117">Checksum</span></span>| <span data-ttu-id="c1340-118">Geeft het type controlesom te gebruiken bij het bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="c1340-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="c1340-119">Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="c1340-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="c1340-120">Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="c1340-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="c1340-121">Inhoud</span><span class="sxs-lookup"><span data-stu-id="c1340-121">Contents</span></span>| <span data-ttu-id="c1340-122">Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="c1340-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="c1340-123">Referentie</span><span class="sxs-lookup"><span data-stu-id="c1340-123">Credential</span></span>| <span data-ttu-id="c1340-124">Geeft aan dat de referenties die vereist voor toegang tot resources, zoals de bronbestanden bevat zijn, als deze toegang vereist is.</span><span class="sxs-lookup"><span data-stu-id="c1340-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="c1340-125">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="c1340-125">Ensure</span></span>| <span data-ttu-id="c1340-126">Geeft aan of het bestand of map bestaat.</span><span class="sxs-lookup"><span data-stu-id="c1340-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="c1340-127">Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat het bestand of map niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="c1340-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="c1340-128">Stel deze in op 'Aanwezig' om ervoor te zorgen dat het bestand of map bestaat.</span><span class="sxs-lookup"><span data-stu-id="c1340-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="c1340-129">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="c1340-129">The default is "Present".</span></span>|
| <span data-ttu-id="c1340-130">Force</span><span class="sxs-lookup"><span data-stu-id="c1340-130">Force</span></span>| <span data-ttu-id="c1340-131">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt.</span><span class="sxs-lookup"><span data-stu-id="c1340-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c1340-132">Met behulp van de Force-eigenschap heeft voorrang op dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="c1340-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="c1340-133">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="c1340-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="c1340-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="c1340-134">Recurse</span></span>| <span data-ttu-id="c1340-135">Hiermee wordt aangegeven als submappen opgenomen worden.</span><span class="sxs-lookup"><span data-stu-id="c1340-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="c1340-136">Deze eigenschap instellen op __$true__ om aan te geven dat u wilt dat de submappen moeten worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c1340-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="c1340-137">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="c1340-137">The default is __$false__.</span></span> <span data-ttu-id="c1340-138">**Houd er rekening mee**: Deze eigenschap is alleen geldig wanneer de eigenschap Type is ingesteld op de Directory.</span><span class="sxs-lookup"><span data-stu-id="c1340-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="c1340-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c1340-139">DependsOn</span></span> | <span data-ttu-id="c1340-140">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c1340-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c1340-141">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c1340-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c1340-142">Bronpad</span><span class="sxs-lookup"><span data-stu-id="c1340-142">SourcePath</span></span>| <span data-ttu-id="c1340-143">Geeft het pad van waaruit de resource van het bestand of map kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c1340-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="c1340-144">Type</span><span class="sxs-lookup"><span data-stu-id="c1340-144">Type</span></span>| <span data-ttu-id="c1340-145">Geeft aan of de resource wordt geconfigureerd een map of een bestand is.</span><span class="sxs-lookup"><span data-stu-id="c1340-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="c1340-146">Deze eigenschap instellen op 'Directory' om aan te geven dat de resource een map is.</span><span class="sxs-lookup"><span data-stu-id="c1340-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="c1340-147">Stel deze in op 'File' om aan te geven dat de resource een bestand is.</span><span class="sxs-lookup"><span data-stu-id="c1340-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="c1340-148">De standaardwaarde is 'File'.</span><span class="sxs-lookup"><span data-stu-id="c1340-148">The default value is “File”.</span></span>|
| <span data-ttu-id="c1340-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="c1340-149">MatchSource</span></span>| <span data-ttu-id="c1340-150">Indien ingesteld op de standaardwaarde van __$false__, en vervolgens alle bestanden op de bron (bijvoorbeeld bestanden A, B en C) wordt toegevoegd aan het doel de eerste keer dat de configuratie is toegepast.</span><span class="sxs-lookup"><span data-stu-id="c1340-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="c1340-151">Als een nieuw bestand (D) is toegevoegd aan de bron, wordt deze niet toegevoegd aan de bestemming, zelfs wanneer de configuratie wordt later opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="c1340-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="c1340-152">Als de waarde __$true__, en vervolgens elke keer dat de configuratie is toegepast, nieuwe bestanden vervolgens gevonden op de bron (zoals bestand D in dit voorbeeld) worden toegevoegd aan de bestemming.</span><span class="sxs-lookup"><span data-stu-id="c1340-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="c1340-153">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="c1340-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="c1340-154">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c1340-154">Example</span></span>

<span data-ttu-id="c1340-155">Het volgende voorbeeld ziet u hoe u de resource van het bestand om ervoor te zorgen dat een map met het pad `C:\Users\Public\Documents\DSCDemo\DemoSource` op een computer (zoals de server 'pull') is ook aanwezig zijn (samen met alle submappen) op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="c1340-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="c1340-156">Ook een bevestiging bericht wordt geschreven naar het logboek voor als u klaar bent en bevat een instructie om ervoor te zorgen dat de bestandscontrole bewerking wordt uitgevoerd voordat de bewerking voor logboekregistratie.</span><span class="sxs-lookup"><span data-stu-id="c1340-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```