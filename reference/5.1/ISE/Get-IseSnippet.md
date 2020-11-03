---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251459"
---
# <span data-ttu-id="33442-103">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="33442-103">Get-IseSnippet</span></span>

## <span data-ttu-id="33442-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="33442-104">SYNOPSIS</span></span>
<span data-ttu-id="33442-105">Hiermee worden de fragmenten opgehaald die de gebruiker heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="33442-105">Gets snippets that the user created.</span></span>

## <span data-ttu-id="33442-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="33442-106">SYNTAX</span></span>

```
Get-IseSnippet [<CommonParameters>]
```

## <span data-ttu-id="33442-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="33442-107">DESCRIPTION</span></span>

<span data-ttu-id="33442-108">De `Get-IseSnippet` cmdlet haalt de PS1XML-bestanden op die herbruikbare tekst fragmenten bevatten die de gebruiker heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="33442-108">The `Get-IseSnippet` cmdlet gets the PS1XML files that contain reusable text snippets that the user created.</span></span> <span data-ttu-id="33442-109">Het werkt alleen in Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="33442-109">It works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="33442-110">Wanneer u de `New-IseSnippet` cmdlet gebruikt om een fragment te maken, `New-IseSnippet` maakt u een `<SnippetTitle>.Snippets.ps1xml` bestand in de `$home\Documents\WindowsPowerShell\Snippets` map.</span><span class="sxs-lookup"><span data-stu-id="33442-110">When you use the `New-IseSnippet` cmdlet to create a snippet, `New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
<span data-ttu-id="33442-111">`Get-IseSnippet` Hiermee worden de fragment bestanden in de map fragmenten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="33442-111">`Get-IseSnippet` gets the snippet files in the Snippets directory.</span></span>

<span data-ttu-id="33442-112">Deze cmdlet krijgt geen ingebouwde fragmenten of fragmenten die vanuit modules worden geïmporteerd via de- `Import-IseSnippet` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33442-112">This cmdlet does not get built-in snippets or snippets that are imported from modules through the `Import-IseSnippet` cmdlet.</span></span>

<span data-ttu-id="33442-113">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="33442-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="33442-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="33442-114">EXAMPLES</span></span>

### <span data-ttu-id="33442-115">Voor beeld 1: alle door de gebruiker gedefinieerde fragmenten ophalen</span><span class="sxs-lookup"><span data-stu-id="33442-115">Example 1: Get all user-defined snippets</span></span>

<span data-ttu-id="33442-116">In dit voor beeld worden alle door de gebruiker gedefinieerde fragmenten opgehaald in de map fragmenten.</span><span class="sxs-lookup"><span data-stu-id="33442-116">This example gets all user-define snippets in the Snippets directory.</span></span>

```powershell
Get-IseSnippet
```

### <span data-ttu-id="33442-117">Voor beeld 2: alle door de gebruiker gedefinieerde fragmenten kopiëren van externe computers naar een gedeelde map</span><span class="sxs-lookup"><span data-stu-id="33442-117">Example 2: Copy all user-defined snippets from remote computers to a shared directory</span></span>

<span data-ttu-id="33442-118">In dit voor beeld worden alle door de gebruiker gemaakte fragmenten gekopieerd van een groep externe computers naar een map met gedeelde fragmenten.</span><span class="sxs-lookup"><span data-stu-id="33442-118">This example copies all of the user-created snippets from a group of remote computers to a shared Snippets directory.</span></span>

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

<span data-ttu-id="33442-119">`Invoke-Command` wordt uitgevoerd `Get-IseSnippet` op de computers in het `Servers.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="33442-119">`Invoke-Command` runs `Get-IseSnippet` on the computers in the `Servers.txt` file.</span></span> <span data-ttu-id="33442-120">Met een pijplijn operator ( `|` ) worden de fragment bestanden naar de `Copy-Item` cmdlet verzonden. deze worden gekopieerd naar de map die is opgegeven door de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="33442-120">A pipeline operator (`|`) sends the snippet files to the `Copy-Item` cmdlet, which copies them to the directory that is specified by the **Destination** parameter.</span></span>

### <span data-ttu-id="33442-121">Voor beeld 3: de titel en tekst van elk fragment op een lokale computer weer geven</span><span class="sxs-lookup"><span data-stu-id="33442-121">Example 3: Display the title and text of each snippet on a local computer</span></span>

<span data-ttu-id="33442-122">In dit voor beeld worden de- `Get-IseSnippet` en- `Select-Xml` cmdlets gebruikt om de titel en tekst van elk fragment op de lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="33442-122">This example uses the `Get-IseSnippet` and `Select-Xml` cmdlets to display the title and text of each snippet on the local computer.</span></span>

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### <span data-ttu-id="33442-123">Voor beeld 4: de titel en beschrijving van alle fragmenten in de sessie weer geven</span><span class="sxs-lookup"><span data-stu-id="33442-123">Example 4: Display the title and description of all snippets in the session</span></span>

<span data-ttu-id="33442-124">In dit voor beeld worden de titel en beschrijving weer gegeven van alle fragmenten in de sessie, met inbegrip van ingebouwde fragmenten, door de gebruiker gedefinieerde fragmenten en geïmporteerde fragmenten.</span><span class="sxs-lookup"><span data-stu-id="33442-124">This example displays the title and description of all snippets in the session, including built-in snippets, user-defined snippets, and imported snippets.</span></span>

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

<span data-ttu-id="33442-125">De `$PSISE` variabele vertegenwoordigt het Windows PowerShell ISE host-programma.</span><span class="sxs-lookup"><span data-stu-id="33442-125">The `$PSISE` variable represents the Windows PowerShell ISE host program.</span></span> <span data-ttu-id="33442-126">De eigenschap **CurrentPowerShellTab** van de `$PSISE` variabele vertegenwoordigt de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="33442-126">The **CurrentPowerShellTab** property of the `$PSISE` variable represent the current session.</span></span> <span data-ttu-id="33442-127">De eigenschap **fragmenten** bevat fragmenten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="33442-127">The **Snippets** property represents snippets in the current session.</span></span>

<span data-ttu-id="33442-128">De `$PSISE.CurrentPowerShellTab.Snippets` opdracht retourneert een **micro soft. Power shell. host. ISE. ISESnippet** -object dat een fragment vertegenwoordigt, in tegens telling tot de `Get-IseSnippet` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33442-128">The `$PSISE.CurrentPowerShellTab.Snippets` command returns a **Microsoft.PowerShell.Host.ISE.ISESnippet** object that represents a snippet, unlike the `Get-IseSnippet` cmdlet.</span></span> <span data-ttu-id="33442-129">`Get-IseSnippet` retourneert een File-object (System. io. file info) dat een fragment bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="33442-129">`Get-IseSnippet` returns a file object (System.Io.FileInfo) that represents a snippet file.</span></span>

<span data-ttu-id="33442-130">`Format-Table`Met de cmdlet worden de eigenschappen **DisplayTitle** en **Description** van de fragmenten in een tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="33442-130">The `Format-Table` cmdlet displays the **DisplayTitle** and **Description** properties of the snippets in a table.</span></span>

## <span data-ttu-id="33442-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33442-131">PARAMETERS</span></span>

### <span data-ttu-id="33442-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33442-132">CommonParameters</span></span>

<span data-ttu-id="33442-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33442-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33442-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="33442-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33442-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="33442-135">INPUTS</span></span>

## <span data-ttu-id="33442-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="33442-136">OUTPUTS</span></span>

### <span data-ttu-id="33442-137">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="33442-137">System.IO.FileInfo</span></span>

<span data-ttu-id="33442-138">Met deze cmdlet wordt een File-object geretourneerd dat het fragment bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="33442-138">This cmdlet returns a file object that represents the snippet file.</span></span>

## <span data-ttu-id="33442-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="33442-139">NOTES</span></span>

* <span data-ttu-id="33442-140">De `New-IseSnippet` cmdlet slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden.</span><span class="sxs-lookup"><span data-stu-id="33442-140">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="33442-141">Windows Power shell kan deze niet toevoegen aan een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is.</span><span class="sxs-lookup"><span data-stu-id="33442-141">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="33442-142">In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.</span><span class="sxs-lookup"><span data-stu-id="33442-142">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="33442-143">Als u niet-ondertekende door de gebruiker gemaakte fragmenten wilt gebruiken die `Get-IseSnippet` door de cmdlet worden geretourneerd, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.</span><span class="sxs-lookup"><span data-stu-id="33442-143">To use unsigned user-created snippets that the `Get-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="33442-144">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie over het uitvoerings beleid van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="33442-144">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="33442-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="33442-145">RELATED LINKS</span></span>

[<span data-ttu-id="33442-146">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="33442-146">New-IseSnippet</span></span>](New-IseSnippet.md)

[<span data-ttu-id="33442-147">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="33442-147">Import-IseSnippet</span></span>](Import-IseSnippet.md)
