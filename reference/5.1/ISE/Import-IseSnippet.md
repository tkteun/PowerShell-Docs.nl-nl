---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250047"
---
# Import-IseSnippet

## SAMENVATTING
Hiermee worden ISE-fragmenten in de huidige sessie geïmporteerd

## SYNTAXIS

### FromFolder (standaard)

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### FromModule

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## BESCHRIJVING

`Import-IseSnippet`Met de cmdlet worden Herbruikbare tekst fragmenten uit een module of een map in de huidige sessie geïmporteerd. De fragmenten zijn direct beschikbaar voor gebruik in Windows PowerShell ISE. Deze cmdlet werkt alleen in Windows Power shell Integrated Scripting Environment (ISE).

Als u de geïmporteerde fragmenten wilt bekijken en gebruiken, klikt u in het menu Windows PowerShell ISE **bewerken** op **fragmenten starten** of drukt u op <kbd>CTRL</kbd> + <kbd>J</kbd>.

Geïmporteerde fragmenten zijn alleen beschikbaar in de huidige sessie. Als u de fragmenten wilt importeren in alle Windows PowerShell ISE sessies, voegt `Import-IseSnippet` u een opdracht toe aan uw Windows Power shell-profiel of kopieert u de fragment bestanden naar uw lokale map met fragmenten `$home\Documents\WindowsPowershell\Snippets` .

Als u fragmenten wilt importeren, moeten ze juist zijn ingedeeld in het XML-code fragment voor Windows PowerShell ISE fragmenten en worden opgeslagen in Snippet.ps1XML-bestanden. Als u in aanmerking komende fragmenten wilt maken, gebruikt u de `New-IseSnippet` cmdlet. `New-IseSnippet` Hiermee maakt u een `<SnippetTitle>.Snippets.ps1xml` bestand in de `$home\Documents\WindowsPowerShell\Snippets` map. U kunt de fragmenten verplaatsen of kopiëren naar de map fragmenten van een Windows Power shell-module of naar een andere map.

`Get-IseSnippet`Met de cmdlet, waarmee door de gebruiker gemaakte fragmenten worden opgehaald in de map lokale fragmenten, worden geen geïmporteerde fragmenten opgehaald.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: fragmenten uit een Directory importeren

In dit voor beeld worden de fragmenten uit de `\\Server01\Public\Snippets` map in de huidige sessie geïmporteerd. De **recursieve** para meter wordt gebruikt voor het ophalen van fragmenten uit alle submappen van de map fragmenten.

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### Voor beeld 2: fragmenten uit een module importeren

In dit voor beeld worden de fragmenten uit de **SnippetModule** -module geïmporteerd. De opdracht gebruikt de para meter **ListAvailable** om de fragmenten te importeren, zelfs als de module **SnippetModule** niet is geïmporteerd in de sessie van de gebruiker wanneer de opdracht wordt uitgevoerd.

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### Voor beeld 3: fragmenten in modules zoeken

In dit voor beeld worden fragmenten in alle geïnstalleerde modules in de omgevings variabele PSModulePath opgehaald.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### Voor beeld 4: alle module fragmenten importeren

In dit voor beeld worden alle fragmenten van alle geïnstalleerde modules in de huidige sessie geïmporteerd. Normaal gesp roken hoeft u geen opdracht als volgt uit te voeren, omdat modules met fragmenten de cmdlet gebruiken `Import-IseSnippet` om ze te importeren wanneer de module wordt geïmporteerd.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### Voor beeld 5: alle module fragmenten kopiëren

In dit voor beeld worden de fragment bestanden van alle geïnstalleerde modules gekopieerd naar de map fragmenten van de huidige gebruiker. In tegens telling tot geïmporteerde fragmenten die alleen van invloed zijn op de huidige sessie, zijn gekopieerde fragmenten beschikbaar in elke Windows PowerShell ISE sessie.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## PARAMETERS

### -ListAvailable

Hiermee wordt aangegeven dat met deze cmdlet fragmenten worden opgehaald uit modules die zijn geïnstalleerd op de computer, zelfs als de modules niet in de huidige sessie worden geïmporteerd. Als deze para meter wordt wegge laten en de module die is opgegeven door de **module** para meter, niet in de huidige sessie wordt geïmporteerd, mislukt de poging om de fragmenten uit de module op te halen.

Deze para meter is alleen geldig wanneer de **module** parameter in de opdracht wordt gebruikt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Hiermee worden fragmenten uit de opgegeven module geïmporteerd in de huidige sessie. Joker tekens worden niet ondersteund.

Met deze para meter worden fragmenten geïmporteerd uit Snippet.ps1XML-bestanden in de submap fragmenten in het pad van de module, zoals `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .

Deze para meter is ontworpen om te worden gebruikt door module auteurs in een opstart script, zoals een script dat is opgegeven in de **ScriptsToProcess** -sleutel van een module manifest. Fragmenten in een module worden niet automatisch met de module geïmporteerd, maar u kunt een opdracht gebruiken `Import-IseSnippet` om ze te importeren.

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar de map met fragmenten waarin met deze cmdlet fragmenten worden geïmporteerd.

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Recursief

Geeft aan dat met deze cmdlet fragmenten worden geïmporteerd uit alle submappen van de waarde van de para meter **Path** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet neemt geen invoer van de pijp lijn.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- U kunt de cmdlet niet gebruiken `Get-IseSnippet` om geïmporteerde fragmenten op te halen. `Get-IseSnippet` haalt alleen fragmenten op in de `$home\Documents\WindowsPowerShell\Snippets` map.
- `Import-IseSnippet` maakt gebruik van de statische methode **Load** van **micro soft. Power shell. host. ISE. ISESnippetCollection** -objecten. U kunt ook de methode voor het **laden** van fragmenten in het object model van Windows PowerShell ISE gebruiken: `$psISE.CurrentPowerShellTab.Snippets.Load()`
- De `New-IseSnippet` cmdlet slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden. Windows Power shell kan deze niet laden in een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is. In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.

  Als u niet-ondertekende door de gebruiker gemaakte fragmenten wilt gebruiken die `Import-IseSnippet` door de cmdlet worden geretourneerd, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.

  Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie over het uitvoerings beleid van Windows Power shell.

## GERELATEERDE KOPPELINGEN

[Get-IseSnippet](Get-IseSnippet.md)

[New-IseSnippet](New-IseSnippet.md)
