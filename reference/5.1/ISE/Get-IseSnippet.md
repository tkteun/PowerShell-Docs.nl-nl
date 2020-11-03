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
# Get-IseSnippet

## SAMENVATTING
Hiermee worden de fragmenten opgehaald die de gebruiker heeft gemaakt.

## SYNTAXIS

```
Get-IseSnippet [<CommonParameters>]
```

## BESCHRIJVING

De `Get-IseSnippet` cmdlet haalt de PS1XML-bestanden op die herbruikbare tekst fragmenten bevatten die de gebruiker heeft gemaakt. Het werkt alleen in Windows Power shell Integrated Scripting Environment (ISE).

Wanneer u de `New-IseSnippet` cmdlet gebruikt om een fragment te maken, `New-IseSnippet` maakt u een `<SnippetTitle>.Snippets.ps1xml` bestand in de `$home\Documents\WindowsPowerShell\Snippets` map.
`Get-IseSnippet` Hiermee worden de fragment bestanden in de map fragmenten opgehaald.

Deze cmdlet krijgt geen ingebouwde fragmenten of fragmenten die vanuit modules worden geïmporteerd via de- `Import-IseSnippet` cmdlet.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: alle door de gebruiker gedefinieerde fragmenten ophalen

In dit voor beeld worden alle door de gebruiker gedefinieerde fragmenten opgehaald in de map fragmenten.

```powershell
Get-IseSnippet
```

### Voor beeld 2: alle door de gebruiker gedefinieerde fragmenten kopiëren van externe computers naar een gedeelde map

In dit voor beeld worden alle door de gebruiker gemaakte fragmenten gekopieerd van een groep externe computers naar een map met gedeelde fragmenten.

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

`Invoke-Command` wordt uitgevoerd `Get-IseSnippet` op de computers in het `Servers.txt` bestand. Met een pijplijn operator ( `|` ) worden de fragment bestanden naar de `Copy-Item` cmdlet verzonden. deze worden gekopieerd naar de map die is opgegeven door de para meter **Destination** .

### Voor beeld 3: de titel en tekst van elk fragment op een lokale computer weer geven

In dit voor beeld worden de- `Get-IseSnippet` en- `Select-Xml` cmdlets gebruikt om de titel en tekst van elk fragment op de lokale computer weer te geven.

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

### Voor beeld 4: de titel en beschrijving van alle fragmenten in de sessie weer geven

In dit voor beeld worden de titel en beschrijving weer gegeven van alle fragmenten in de sessie, met inbegrip van ingebouwde fragmenten, door de gebruiker gedefinieerde fragmenten en geïmporteerde fragmenten.

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

De `$PSISE` variabele vertegenwoordigt het Windows PowerShell ISE host-programma. De eigenschap **CurrentPowerShellTab** van de `$PSISE` variabele vertegenwoordigt de huidige sessie. De eigenschap **fragmenten** bevat fragmenten in de huidige sessie.

De `$PSISE.CurrentPowerShellTab.Snippets` opdracht retourneert een **micro soft. Power shell. host. ISE. ISESnippet** -object dat een fragment vertegenwoordigt, in tegens telling tot de `Get-IseSnippet` cmdlet. `Get-IseSnippet` retourneert een File-object (System. io. file info) dat een fragment bestand vertegenwoordigt.

`Format-Table`Met de cmdlet worden de eigenschappen **DisplayTitle** en **Description** van de fragmenten in een tabel weer gegeven.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### System. IO. file info

Met deze cmdlet wordt een File-object geretourneerd dat het fragment bestand vertegenwoordigt.

## OPMERKINGEN

* De `New-IseSnippet` cmdlet slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden. Windows Power shell kan deze niet toevoegen aan een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is. In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.

  Als u niet-ondertekende door de gebruiker gemaakte fragmenten wilt gebruiken die `Get-IseSnippet` door de cmdlet worden geretourneerd, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.

  Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie over het uitvoerings beleid van Windows Power shell.

## GERELATEERDE KOPPELINGEN

[New-IseSnippet](New-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
