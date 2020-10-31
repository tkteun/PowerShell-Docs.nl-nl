---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-bestands resource
description: DSC-bestands resource
ms.openlocfilehash: b62b9b80beb1f433715b32b41445dd0a8bb19d84
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142936"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="dd5d9-103">DSC-bestands resource</span><span class="sxs-lookup"><span data-stu-id="dd5d9-103">DSC File Resource</span></span>

> <span data-ttu-id="dd5d9-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="dd5d9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="dd5d9-105">De bron van het **bestand** in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="dd5d9-106">**Doelpad** en **bronpad** moeten beide toegankelijk zijn voor het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="dd5d9-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd5d9-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dd5d9-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dd5d9-108">Properties</span></span>

|<span data-ttu-id="dd5d9-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dd5d9-109">Property</span></span> |<span data-ttu-id="dd5d9-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dd5d9-110">Description</span></span> |
|---|---|
|<span data-ttu-id="dd5d9-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="dd5d9-111">DestinationPath</span></span> |<span data-ttu-id="dd5d9-112">De locatie, op het doel knooppunt, wilt **ervoor zorgen dat** **deze aanwezig** is of **ontbreekt** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure** .</span></span> |
|<span data-ttu-id="dd5d9-113">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dd5d9-113">Attributes</span></span> |<span data-ttu-id="dd5d9-114">De gewenste status van de kenmerken voor het betreffende bestand of de doel directory.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="dd5d9-115">Geldige waarden zijn _Archief_ , _verborgen_ , _alleen-lezen_ en _systeem_ .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-115">Valid values are _Archive_ , _Hidden_ , _ReadOnly_ , and _System_ .</span></span> |
|<span data-ttu-id="dd5d9-116">Controlesom</span><span class="sxs-lookup"><span data-stu-id="dd5d9-116">Checksum</span></span> |<span data-ttu-id="dd5d9-117">Het type controlesom dat moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="dd5d9-118">Geldige waarden zijn: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-118">Valid values include: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span></span> |
|<span data-ttu-id="dd5d9-119">Inhoud</span><span class="sxs-lookup"><span data-stu-id="dd5d9-119">Contents</span></span> |<span data-ttu-id="dd5d9-120">Alleen geldig als deze wordt gebruikt met het **type** **bestand** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-120">Only valid when used with **Type** **File** .</span></span> <span data-ttu-id="dd5d9-121">Hiermee wordt **aangegeven dat de** inhoud **aanwezig** is of **ontbreekt** in het doel bestand.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="dd5d9-122">Referentie</span><span class="sxs-lookup"><span data-stu-id="dd5d9-122">Credential</span></span> |<span data-ttu-id="dd5d9-123">De referenties die nodig zijn voor toegang tot bronnen, zoals bron bestanden.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="dd5d9-124">Force</span><span class="sxs-lookup"><span data-stu-id="dd5d9-124">Force</span></span> |<span data-ttu-id="dd5d9-125">Onderdrukt de toegangs bewerkingen die resulteren in een fout (bijvoorbeeld het overschrijven van een bestand of het verwijderen van een niet-lege map).</span><span class="sxs-lookup"><span data-stu-id="dd5d9-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="dd5d9-126">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="dd5d9-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="dd5d9-127">Recurse</span></span> |<span data-ttu-id="dd5d9-128">Alleen geldig als deze wordt gebruikt met het **type** **Directory** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-128">Only valid when used with **Type** **Directory** .</span></span> <span data-ttu-id="dd5d9-129">Hiermee wordt de status bewerking recursief uitgevoerd voor alle directory-inhoud, submappen en submappen.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-129">Performs the state operation recursively to all directory content, subdirectories, and subdirectory content.</span></span> <span data-ttu-id="dd5d9-130">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="dd5d9-131">Bronpad</span><span class="sxs-lookup"><span data-stu-id="dd5d9-131">SourcePath</span></span> |<span data-ttu-id="dd5d9-132">Het pad waaruit de bron van het bestand of de map moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="dd5d9-133">Type</span><span class="sxs-lookup"><span data-stu-id="dd5d9-133">Type</span></span> |<span data-ttu-id="dd5d9-134">Het type resource dat wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-134">The type of resource being configured.</span></span> <span data-ttu-id="dd5d9-135">Geldige waarden zijn **map** en **bestand** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-135">Valid values are **Directory** and **File** .</span></span> <span data-ttu-id="dd5d9-136">De standaard waarde is een **bestand** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-136">Default value is **File** .</span></span> |
|<span data-ttu-id="dd5d9-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="dd5d9-137">MatchSource</span></span> |<span data-ttu-id="dd5d9-138">Hiermee wordt bepaald of de resource moet controleren op nieuwe bestanden die worden toegevoegd aan de bron directory na de eerste kopie.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="dd5d9-139">Een waarde van `$true` geeft aan dat na de eerste kopie nieuwe bron bestanden moeten worden gekopieerd naar de bestemming.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="dd5d9-140">Als `$false` deze is ingesteld op, wordt de inhoud van de bronmap in cache opgeslagen en worden alle bestanden die na de eerste kopie worden toegevoegd, genegeerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="dd5d9-141">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="dd5d9-142">Als u geen waarde opgeeft voor **referentie** -of **PSRunAsCredential** , gebruikt de resource het computer account van het doel knooppunt om toegang te krijgen tot het **bronpad** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-142">If you do not specify a value for **Credential** or **PSRunAsCredential** , the resource will use the computer account of the target node to access the **SourcePath** .</span></span> <span data-ttu-id="dd5d9-143">Wanneer het **bronpad** een UNC-share is, kan dit resulteren in een fout ' toegang geweigerd '.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="dd5d9-144">Zorg ervoor dat uw machtigingen dienovereenkomstig zijn ingesteld, of gebruik de eigenschappen **Credential** of **PSRunAsCredential** om het account op te geven dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="dd5d9-145">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dd5d9-145">Common properties</span></span>

|<span data-ttu-id="dd5d9-146">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dd5d9-146">Property</span></span> |<span data-ttu-id="dd5d9-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dd5d9-147">Description</span></span> |
|---|---|
|<span data-ttu-id="dd5d9-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dd5d9-148">DependsOn</span></span> |<span data-ttu-id="dd5d9-149">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dd5d9-150">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dd5d9-151">Zo</span><span class="sxs-lookup"><span data-stu-id="dd5d9-151">Ensure</span></span> |<span data-ttu-id="dd5d9-152">Hiermee wordt bepaald of het bestand en de **inhoud** op de **bestemming** bestaan of niet.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="dd5d9-153">Stel deze eigenschap in op **presen teren** om te controleren of het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="dd5d9-154">Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="dd5d9-155">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-155">The default value is **Present** .</span></span> |
|<span data-ttu-id="dd5d9-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dd5d9-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="dd5d9-157">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dd5d9-158">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dd5d9-159">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="dd5d9-160">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="dd5d9-160">Additional information</span></span>

- <span data-ttu-id="dd5d9-161">Wanneer u alleen een **doelpad** opgeeft, zorgt de bron ervoor dat het pad bestaat, indien het **aanwezig** is of niet bestaat als het **ontbreekt** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-161">When you only specify a **DestinationPath** , the resource ensures that the path exists if **Present** or does not exist if **Absent** .</span></span>
- <span data-ttu-id="dd5d9-162">Wanneer u een **bronpad** en een **doelpad** met de **type** waarde **Directory** opgeeft, wordt de bron Directory gekopieerd naar het doelpad.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory** , the resource copies source directory to the destination path.</span></span> <span data-ttu-id="dd5d9-163">Met de **Eigenschappen wordt** het type Kopieer bewerking dat wordt uitgevoerd, gewijzigd, **geforceerd** en **MatchSource** , terwijl de **referentie** bepaalt welk account moet worden gebruikt om toegang te krijgen tot de bron directory.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-163">The properties **Recurse** , **Force** , and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="dd5d9-164">Als u de eigenschap **recursief** niet instelt op bij het `$true` kopiëren van een map, wordt geen van de inhoud van de bestaande map gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-164">If you do not set the **Recurse** property to `$true` when copying a directory, none of the contents of the existing directory will be copied.</span></span> <span data-ttu-id="dd5d9-165">Alleen de opgegeven map wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-165">Only the directory specified will be copied.</span></span>
- <span data-ttu-id="dd5d9-166">Als u voor de eigenschap **Attributes** naast een **doelpad** de waarde **ReadOnly** hebt opgegeven **, moet u** **ervoor zorgen dat** het opgegeven pad wordt gemaakt, terwijl de **inhoud** van het bestand is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-166">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath** , **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="dd5d9-167">Als u **ervoor zorgt dat** de instelling niet **aanwezig** is, wordt de eigenschap **Attributes** volledig genegeerd en worden alle bestanden verwijderd uit het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-167">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="dd5d9-168">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="dd5d9-168">Example</span></span>

<span data-ttu-id="dd5d9-169">In het volgende voor beeld wordt een map en de bijbehorende submappen gekopieerd van een pull-server naar een doel knooppunt met behulp van de bestands resource.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-169">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="dd5d9-170">Als de bewerking is geslaagd, schrijft de logboek bron een bevestigings bericht naar het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-170">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="dd5d9-171">De bron directory is een UNC-pad () dat wordt `\\PullServer\DemoSource` gedeeld vanaf de pull-server.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-171">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="dd5d9-172">Met de **recursieve** eigenschap zorgt u ervoor dat alle submappen ook worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-172">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd5d9-173">De LCM op het doel knooppunt wordt standaard uitgevoerd in de context van het lokale systeem account.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-173">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="dd5d9-174">Als u toegang wilt verlenen tot het **bronpad** , geeft u het computer account van het doel knooppunt de juiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-174">To grant access to the **SourcePath** , give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="dd5d9-175">De **referentie** -en **PSDSCRunAsCredential** wijzigen de context die de LCM gebruikt om toegang te krijgen tot het **bronpad** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-175">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath** .</span></span> <span data-ttu-id="dd5d9-176">U moet nog steeds toegang verlenen tot het account dat wordt gebruikt voor toegang tot het **bronpad** .</span><span class="sxs-lookup"><span data-stu-id="dd5d9-176">You still need to grant access to the account that will be used to access the **SourcePath** .</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="dd5d9-177">Zie [uitvoeren als gebruiker](../../../configurations/runAsUser.md) of [configuratie gegevens referenties](../../../configurations/configDataCredentials.md)voor meer informatie over het gebruik van **referenties** in DSC.</span><span class="sxs-lookup"><span data-stu-id="dd5d9-177">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
