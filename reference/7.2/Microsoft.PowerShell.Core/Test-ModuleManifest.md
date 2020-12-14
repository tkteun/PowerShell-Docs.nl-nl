---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: c86a7253335b91011d2eb225bc53d1c5cc671aff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705495"
---
# <span data-ttu-id="2b967-102">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="2b967-102">Test-ModuleManifest</span></span>

## <span data-ttu-id="2b967-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2b967-103">SYNOPSIS</span></span>
<span data-ttu-id="2b967-104">Verifieert of een module manifest bestand nauw keurig de inhoud van een module beschrijft.</span><span class="sxs-lookup"><span data-stu-id="2b967-104">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="2b967-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2b967-105">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="2b967-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2b967-106">DESCRIPTION</span></span>

<span data-ttu-id="2b967-107">Met de cmdlet **test-ModuleManifest** wordt gecontroleerd of de bestanden die worden vermeld in het module manifest bestand (. psd1) zich in werkelijkheid in de opgegeven paden bevinden.</span><span class="sxs-lookup"><span data-stu-id="2b967-107">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="2b967-108">Deze cmdlet is ontworpen om module auteurs te helpen hun manifest bestanden te testen.</span><span class="sxs-lookup"><span data-stu-id="2b967-108">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="2b967-109">Module gebruikers kunnen deze cmdlet ook gebruiken in scripts en opdrachten om fouten te detecteren voordat ze scripts uitvoeren die afhankelijk zijn van de module.</span><span class="sxs-lookup"><span data-stu-id="2b967-109">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="2b967-110">**Test-ModuleManifest** retourneert een object dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2b967-110">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="2b967-111">Dit is hetzelfde type object dat Get-Module retourneert.</span><span class="sxs-lookup"><span data-stu-id="2b967-111">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="2b967-112">Als bestanden zich niet op de opgegeven locaties in het manifest bevinden, genereert de cmdlet ook een fout voor elk ontbrekend bestand.</span><span class="sxs-lookup"><span data-stu-id="2b967-112">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="2b967-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2b967-113">EXAMPLES</span></span>

### <span data-ttu-id="2b967-114">Voor beeld 1: een manifest testen</span><span class="sxs-lookup"><span data-stu-id="2b967-114">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="2b967-115">Met deze opdracht wordt het module manifest TestModule.psd1 getest.</span><span class="sxs-lookup"><span data-stu-id="2b967-115">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="2b967-116">Voor beeld 2: een manifest testen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="2b967-116">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="2b967-117">Met deze opdracht wordt een pijplijn operator (|) gebruikt voor het verzenden van een padtekenreeks naar **test-ModuleManifest**.</span><span class="sxs-lookup"><span data-stu-id="2b967-117">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="2b967-118">De uitvoer van de opdracht geeft aan dat de test is mislukt, omdat het TestTypes.ps1XML-bestand, dat in het manifest is vermeld, niet is gevonden.</span><span class="sxs-lookup"><span data-stu-id="2b967-118">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="2b967-119">Voor beeld 3: een functie schrijven om een module manifest te testen</span><span class="sxs-lookup"><span data-stu-id="2b967-119">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="2b967-120">Deze functie is vergelijkbaar met **test-ModuleManifest**, maar retourneert een Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="2b967-120">This function is like **Test-ModuleManifest**, but it returns a Boolean value.</span></span>
<span data-ttu-id="2b967-121">De functie retourneert $True als het manifest is door gegeven aan de test en $False anderszins.</span><span class="sxs-lookup"><span data-stu-id="2b967-121">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="2b967-122">De functie maakt gebruik van de Get-ChildItem cmdlet, alias = dir, om het module manifest op te halen dat is opgegeven door de $path-variabele.</span><span class="sxs-lookup"><span data-stu-id="2b967-122">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="2b967-123">De opdracht maakt gebruik van een pijplijn operator (|) om het File-object door te geven aan **test-ModuleManifest**.</span><span class="sxs-lookup"><span data-stu-id="2b967-123">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest**.</span></span>

<span data-ttu-id="2b967-124">**Test-ModuleManifest** gebruikt de gemeen schappelijke para meter *Error Action* met de waarde SilentlyContinue om de weer gave te onderdrukken van fouten die door de opdracht worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2b967-124">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="2b967-125">Ook wordt het **PSModuleInfo** -object opgeslagen dat door **test-ModuleManifest** wordt geretourneerd in de variabele $a.</span><span class="sxs-lookup"><span data-stu-id="2b967-125">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="2b967-126">Daarom wordt het object niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2b967-126">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="2b967-127">Vervolgens wordt in een afzonderlijke opdracht de waarde van de $? weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2b967-127">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="2b967-128">Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="2b967-128">automatic variable.</span></span>
<span data-ttu-id="2b967-129">Als er geen fout wordt gegenereerd door de vorige opdracht, wordt de opdracht $True weer gegeven en $False anders.</span><span class="sxs-lookup"><span data-stu-id="2b967-129">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="2b967-130">U kunt deze functie gebruiken in voorwaardelijke instructies, zoals die voor een opdracht van een **import module** of een opdracht die gebruikmaakt van de module.</span><span class="sxs-lookup"><span data-stu-id="2b967-130">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="2b967-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b967-131">PARAMETERS</span></span>

### <span data-ttu-id="2b967-132">-Path</span><span class="sxs-lookup"><span data-stu-id="2b967-132">-Path</span></span>

<span data-ttu-id="2b967-133">Hiermee geeft u een pad en een bestands naam op voor het manifest bestand.</span><span class="sxs-lookup"><span data-stu-id="2b967-133">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="2b967-134">Voer een optioneel pad en de naam in van het manifest bestand van de module met de bestandsnaam extensie. psd1.</span><span class="sxs-lookup"><span data-stu-id="2b967-134">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="2b967-135">De standaard locatie is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="2b967-135">The default location is the current directory.</span></span>
<span data-ttu-id="2b967-136">Joker tekens worden ondersteund, maar moeten worden omgezet in een manifest bestand met één module.</span><span class="sxs-lookup"><span data-stu-id="2b967-136">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="2b967-137">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="2b967-137">This parameter is required.</span></span>
<span data-ttu-id="2b967-138">U kunt ook een pad naar **test-ModuleManifest** sluizen.</span><span class="sxs-lookup"><span data-stu-id="2b967-138">You can also pipe a path to **Test-ModuleManifest**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2b967-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b967-139">CommonParameters</span></span>

<span data-ttu-id="2b967-140">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2b967-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b967-141">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2b967-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b967-142">INVOER</span><span class="sxs-lookup"><span data-stu-id="2b967-142">INPUTS</span></span>

### <span data-ttu-id="2b967-143">System. String</span><span class="sxs-lookup"><span data-stu-id="2b967-143">System.String</span></span>

<span data-ttu-id="2b967-144">U kunt het pad naar een module manifest door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b967-144">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="2b967-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2b967-145">OUTPUTS</span></span>

### <span data-ttu-id="2b967-146">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="2b967-146">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="2b967-147">Met deze cmdlet wordt een **PSModuleInfo** -object geretourneerd dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2b967-147">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="2b967-148">Dit object wordt als resultaat gegeven, zelfs als het manifest fouten bevat.</span><span class="sxs-lookup"><span data-stu-id="2b967-148">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="2b967-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2b967-149">NOTES</span></span>

## <span data-ttu-id="2b967-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2b967-150">RELATED LINKS</span></span>

[<span data-ttu-id="2b967-151">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="2b967-151">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="2b967-152">Get-module</span><span class="sxs-lookup"><span data-stu-id="2b967-152">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="2b967-153">Import-module</span><span class="sxs-lookup"><span data-stu-id="2b967-153">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="2b967-154">New-module</span><span class="sxs-lookup"><span data-stu-id="2b967-154">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="2b967-155">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="2b967-155">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="2b967-156">Remove-module</span><span class="sxs-lookup"><span data-stu-id="2b967-156">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="2b967-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="2b967-157">about_Modules</span></span>](About/about_Modules.md)

