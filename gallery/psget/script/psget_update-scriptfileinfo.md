---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update-ScriptFileInfo
ms.openlocfilehash: 3fcbf3a32e74b028501094244df38c631ce18a18
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="update-scriptfileinfo"></a><span data-ttu-id="3db15-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="3db15-103">Update-ScriptFileInfo</span></span>

<span data-ttu-id="3db15-104">Update ScriptFileInfo cmdlet kunt u de metagegevens van het bestaande script bestand bijwerken.</span><span class="sxs-lookup"><span data-stu-id="3db15-104">Update-ScriptFileInfo cmdlet lets you to update the existing script file metadata.</span></span>

## <a name="description"></a><span data-ttu-id="3db15-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3db15-105">Description</span></span>

<span data-ttu-id="3db15-106">Informatie voor een script wordt bijgewerkt door de cmdlet Update-ScriptFileInfo.</span><span class="sxs-lookup"><span data-stu-id="3db15-106">The Update-ScriptFileInfo cmdlet updates information for a script.</span></span>
- <span data-ttu-id="3db15-107">De metagegevens van een scriptbestand alleen als deze is gemaakt met de cmdlet New-ScriptFileInfo of met geldige PSScriptInfo Opmerking update ScriptFileInfo cmdlet-updates.</span><span class="sxs-lookup"><span data-stu-id="3db15-107">Update-ScriptFileInfo cmdlet updates the metadata of a script file only if it was created using New-ScriptFileInfo cmdlet or with valid PSScriptInfo comment.</span></span>
- <span data-ttu-id="3db15-108">Ook kunt u de informatie over de script toevoegen aan de bestaande scriptbestanden die niet zijn gemaakt met de cmdlet New-ScriptFileInfo.</span><span class="sxs-lookup"><span data-stu-id="3db15-108">Also allows you to add the script file information to the existing script files which were not created using New-ScriptFileInfo cmdlet.</span></span>
- <span data-ttu-id="3db15-109">Als – Force is opgegeven, probeert u de metagegevens toevoegen aan het bestaande scriptbestand dat niet is gemaakt met de cmdlet New-ScriptFileInfo.</span><span class="sxs-lookup"><span data-stu-id="3db15-109">If –Force is specified, try to add the metadata to the existing script file which was not created using New-ScriptFileInfo cmdlet.</span></span>
- <span data-ttu-id="3db15-110">Als de Test-ScriptFileInfo mislukt met de fouten bij het parseren nadat de metagegevens van het script aan het bestaande bestand prepending een fout gegenereerd dat ongeveer ' kan niet worden de metagegevens toevoegen aan het bestaande bestand, kunt u de nieuwe scriptfileinfo-cmdlet gebruiken om toe te voegen de metagegevens voor het bestaande scriptbestand dat niet is gemaakt met de cmdlet New-ScriptFileInfo."</span><span class="sxs-lookup"><span data-stu-id="3db15-110">If Test-ScriptFileInfo fails with the parsing errors, after prepending the script metadata to the existing file, an error will be thrown saying something like "unable to add the metadata to the existing file, you can use the new-scriptfileinfo cmdlet to add the metadata to the existing script file which was not created using New-ScriptFileInfo cmdlet."</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="3db15-111">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="3db15-111">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Update-ScriptFileInfo -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="3db15-112">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="3db15-112">Cmdlet online help reference</span></span>

[<span data-ttu-id="3db15-113">Update-Script</span><span class="sxs-lookup"><span data-stu-id="3db15-113">Update-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619793)

## <a name="example-commands"></a><span data-ttu-id="3db15-114">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="3db15-114">Example commands</span></span>

```powershell
# Use Update-ScriptFileInfo cmdlet to update the script metadata
Update-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1 -Version 2.0

Test-ScriptFileInfo C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1

Version Name Author Description
------- ---- ------ -----------
2.0 Demo-ScriptWithComplet... manikb my new script file
```


### <a name="adding-the-script-metadata-to-the-existing-script-file"></a><span data-ttu-id="3db15-115">De script-metagegevens toe te voegen aan het bestaande scriptbestand</span><span class="sxs-lookup"><span data-stu-id="3db15-115">Adding the script metadata to the existing script file</span></span>

```powershell
PS C:\WINDOWS\system32> New-ScriptFileInfo -Description "Script file description." -PassThru

<#PSScriptInfo

.VERSION 1.0

.GUID 1cfd45e7-4219-4cd2-af21-d8577476be09

.AUTHOR manikb

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES


#>

<#

.DESCRIPTION
Script file description.

#>
Param()


PS C:\WINDOWS\system32> $content = @'
   Function foo
   {
   "Foo"
   }
>>
   Foo
'@

PS C:\WINDOWS\system32>
PS C:\WINDOWS\system32> Set-Content -Value $content -Path C:\temp\ScriptFileWithoutMetadata.ps1 -Force
PS C:\WINDOWS\system32> Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\temp\ScriptFileWithoutMetadata.ps1', use the Update-ScriptFileInfo with -Force
or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\temp\ScriptFileWithoutMetadata.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

PS C:\WINDOWS\system32> # Should Fail
PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\temp\ScriptFileWithoutMetadata.ps1', use the Update-ScriptFileInfo with -Force
or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:4704 char:29
+ ...      $psscriptInfo = Test-ScriptFileInfo -LiteralPath $scriptFilePath
+                          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\temp\ScriptFileWithoutMetadata.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

PS C:\WINDOWS\system32> # Should Fail
PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force
Update-ScriptFileInfo : Description parameter is missing for adding the metadata to script file. Try again after specifying the description.
At line:1 char:1
+ Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Update-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : DescriptionParameterIsMissingForAddingTheScriptFileInfo,Update-ScriptFileInfo

PS C:\WINDOWS\system32> Update-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1 -Force -Description "Temp script file."
PS C:\WINDOWS\system32> Test-ScriptFileInfo c:\temp\ScriptFileWithoutMetadata.ps1

Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        ScriptFileWithoutMetadata manikb               Temp script file.


PS C:\WINDOWS\system32> Get-Content c:\temp\ScriptFileWithoutMetadata.ps1

<#PSScriptInfo

.VERSION 1.0

.GUID 855821be-811c-4eb1-a7a7-afd6081be175

.AUTHOR manikb

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES


#>

<#

.DESCRIPTION
Temp script file.

#>

Param()


Function foo
{
"Foo"
}

Foo

```