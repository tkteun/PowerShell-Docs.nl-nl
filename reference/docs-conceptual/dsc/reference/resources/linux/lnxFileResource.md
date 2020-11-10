---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxFile-resource
description: DSC voor Linux nxFile-resource
ms.openlocfilehash: 14a8174a92f1bbde9b1f16cf814ef7c83309c737
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389025"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="83767-103">DSC voor Linux nxFile-resource</span><span class="sxs-lookup"><span data-stu-id="83767-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="83767-104">De **nxFile** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="83767-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="83767-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="83767-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="83767-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="83767-106">Properties</span></span>

|<span data-ttu-id="83767-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="83767-107">Property</span></span> |<span data-ttu-id="83767-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83767-108">Description</span></span> |
|---|---|
|<span data-ttu-id="83767-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="83767-109">DestinationPath</span></span> |<span data-ttu-id="83767-110">Hiermee geeft u de locatie op waar u de status van een bestand of map wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="83767-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="83767-111">Bronpad</span><span class="sxs-lookup"><span data-stu-id="83767-111">SourcePath</span></span> |<span data-ttu-id="83767-112">Hiermee geeft u het pad op waaruit het bestand of de bron van de map moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="83767-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="83767-113">Dit pad mag een lokaal pad of een URL zijn `http/https/ftp` .</span><span class="sxs-lookup"><span data-stu-id="83767-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="83767-114">Externe `http/https/ftp` url's worden alleen ondersteund wanneer de waarde van de eigenschap **type** **File** is.</span><span class="sxs-lookup"><span data-stu-id="83767-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="83767-115">Type</span><span class="sxs-lookup"><span data-stu-id="83767-115">Type</span></span> |<span data-ttu-id="83767-116">Hiermee geeft u op of de resource die wordt geconfigureerd een map of een bestand is.</span><span class="sxs-lookup"><span data-stu-id="83767-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="83767-117">Stel deze eigenschap in op **Directory** om aan te geven dat de resource een directory is.</span><span class="sxs-lookup"><span data-stu-id="83767-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="83767-118">Stel deze in op **bestand** om aan te geven dat de resource een bestand is.</span><span class="sxs-lookup"><span data-stu-id="83767-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="83767-119">De standaard waarde is **File**.</span><span class="sxs-lookup"><span data-stu-id="83767-119">The default value is **file**.</span></span> |
|<span data-ttu-id="83767-120">Inhoud</span><span class="sxs-lookup"><span data-stu-id="83767-120">Contents</span></span> |<span data-ttu-id="83767-121">Hiermee geeft u de inhoud van een bestand, zoals een bepaalde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="83767-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="83767-122">Controlesom</span><span class="sxs-lookup"><span data-stu-id="83767-122">Checksum</span></span> |<span data-ttu-id="83767-123">Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="83767-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="83767-124">Als er geen **controlesom** is opgegeven, wordt alleen de naam van het bestand of de map gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="83767-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="83767-125">Waarden zijn: **ctime** , **mtime** of **MD5**.</span><span class="sxs-lookup"><span data-stu-id="83767-125">Values are: **ctime** , **mtime** , or **md5**.</span></span> |
|<span data-ttu-id="83767-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="83767-126">Recurse</span></span> |<span data-ttu-id="83767-127">Hiermee wordt aangegeven of submappen zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="83767-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="83767-128">Stel deze eigenschap in op `$true` om aan te geven dat u submappen wilt opnemen.</span><span class="sxs-lookup"><span data-stu-id="83767-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="83767-129">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="83767-129">The default is `$false`.</span></span> <span data-ttu-id="83767-130">Deze eigenschap is alleen geldig wanneer de eigenschap **type** is ingesteld op **Directory**.</span><span class="sxs-lookup"><span data-stu-id="83767-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="83767-131">Force</span><span class="sxs-lookup"><span data-stu-id="83767-131">Force</span></span> |<span data-ttu-id="83767-132">Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="83767-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="83767-133">Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd.</span><span class="sxs-lookup"><span data-stu-id="83767-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="83767-134">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="83767-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="83767-135">Koppelingen</span><span class="sxs-lookup"><span data-stu-id="83767-135">Links</span></span> |<span data-ttu-id="83767-136">Hiermee geeft u het gewenste gedrag voor symbolische koppelingen op.</span><span class="sxs-lookup"><span data-stu-id="83767-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="83767-137">Stel deze eigenschap in op **volgen** van symbolische koppelingen volgen en reageren op het doel van de koppelingen.</span><span class="sxs-lookup"><span data-stu-id="83767-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="83767-138">Kopieer bijvoorbeeld het bestand in plaats van de koppeling.</span><span class="sxs-lookup"><span data-stu-id="83767-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="83767-139">Stel deze eigenschap in op **beheren** om op de koppeling te reageren.</span><span class="sxs-lookup"><span data-stu-id="83767-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="83767-140">Kopieer bijvoorbeeld de koppeling zelf.</span><span class="sxs-lookup"><span data-stu-id="83767-140">For example, copy the link itself.</span></span> <span data-ttu-id="83767-141">Stel deze eigenschap in op **negeren** om symbolische koppelingen te negeren.</span><span class="sxs-lookup"><span data-stu-id="83767-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="83767-142">Groep</span><span class="sxs-lookup"><span data-stu-id="83767-142">Group</span></span> |<span data-ttu-id="83767-143">De naam van de **groep** die machtigingen voor het bestand of de map moet hebben.</span><span class="sxs-lookup"><span data-stu-id="83767-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="83767-144">Modus</span><span class="sxs-lookup"><span data-stu-id="83767-144">Mode</span></span> |<span data-ttu-id="83767-145">Hiermee geeft u de gewenste machtigingen voor de resource op in een octale of symbolische notatie.</span><span class="sxs-lookup"><span data-stu-id="83767-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="83767-146">Bijvoorbeeld **777** of **rwxrwxrwx**.</span><span class="sxs-lookup"><span data-stu-id="83767-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="83767-147">Als u de symbolische notatie gebruikt, geeft u niet het eerste teken op dat map of bestand aangeeft.</span><span class="sxs-lookup"><span data-stu-id="83767-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="83767-148">Eigenaar</span><span class="sxs-lookup"><span data-stu-id="83767-148">Owner</span></span> |<span data-ttu-id="83767-149">De naam van de groep die eigenaar is van het bestand of de map.</span><span class="sxs-lookup"><span data-stu-id="83767-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="83767-150">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="83767-150">Common properties</span></span>

|<span data-ttu-id="83767-151">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="83767-151">Property</span></span> |<span data-ttu-id="83767-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83767-152">Description</span></span> |
|---|---|
|<span data-ttu-id="83767-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="83767-153">DependsOn</span></span> |<span data-ttu-id="83767-154">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="83767-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="83767-155">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="83767-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="83767-156">Zo</span><span class="sxs-lookup"><span data-stu-id="83767-156">Ensure</span></span> |<span data-ttu-id="83767-157">Hiermee wordt bepaald of het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="83767-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="83767-158">Stel deze eigenschap in op **presen teren** om te controleren of het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="83767-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="83767-159">Stel deze in op **afwezig** om te controleren of het bestand niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="83767-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="83767-160">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="83767-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="83767-161">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="83767-161">Additional Information</span></span>

<span data-ttu-id="83767-162">Linux en Windows gebruiken standaard andere regel-afbreek tekens in tekst bestanden. Dit kan leiden tot onverwachte resultaten bij het configureren van een aantal bestanden op een Linux-computer met **nxFile**.</span><span class="sxs-lookup"><span data-stu-id="83767-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="83767-163">Er zijn meerdere manieren om de inhoud van een Linux-bestand te beheren, terwijl er problemen ontstaan die worden veroorzaakt door onverwachte regel einde tekens:</span><span class="sxs-lookup"><span data-stu-id="83767-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="83767-164">Het bestand kopiëren van een externe bron (http, https of FTP)</span><span class="sxs-lookup"><span data-stu-id="83767-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="83767-165">Maak een bestand op Linux met de gewenste inhoud en werk het op een web-of FTP-server toegankelijk voor de knoop punten die u wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="83767-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="83767-166">Definieer de eigenschap **SourcePath** in de **nxFile** -resource met de web-of FTP-URL voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="83767-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="83767-167">Lees de bestands inhoud in het Power shell-script met [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) nadat u de eigenschap **$OFS** hebt ingesteld op het gebruik van het Linux-regel scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="83767-167">Read the file contents in the PowerShell script with [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="83767-168">Gebruik een Power shell-functie om Windows-regel einden te vervangen door Linux-regel einde tekens.</span><span class="sxs-lookup"><span data-stu-id="83767-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="83767-169">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="83767-169">Example</span></span>

<span data-ttu-id="83767-170">In het volgende voor beeld wordt ervoor gezorgd dat de map `/opt/mydir` bestaat en dat er voor een bestand met de opgegeven inhoud deze map bestaat.</span><span class="sxs-lookup"><span data-stu-id="83767-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```
