---
title: Een Power shell-module importeren | Microsoft Docs
ms.date: 02/03/2020
ms.openlocfilehash: 8cd1938d0a7b49b4a594753d8ce5ebe60625025d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784874"
---
# <a name="importing-a-powershell-module"></a>Een PowerShell-module importeren

Wanneer u een module op een systeem hebt geïnstalleerd, wilt u waarschijnlijk de module importeren. Importeren is het proces waarmee de module wordt geladen in actief geheugen, zodat een gebruiker toegang heeft tot die module in hun Power shell-sessie. In Power Shell 2,0 kunt u een nieuw geïnstalleerde Power shell-module importeren met een aanroep van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) . In Power Shell 3,0 kan Power shell een module impliciet importeren als een van de functies of cmdlets in de module wordt aangeroepen door een gebruiker. Houd er rekening mee dat beide versies ervan uitgaan dat u de module installeert op een locatie waar Power shell deze kan vinden. Zie [een Power shell-module installeren](./installing-a-powershell-module.md)voor meer informatie.
U kunt een module manifest gebruiken om te beperken welke onderdelen van uw module worden geëxporteerd en u kunt para meters van de `Import-Module` aanroep gebruiken om te beperken welke onderdelen worden geïmporteerd.

## <a name="importing-a-snap-in-powershell-10"></a>Een module importeren (Power shell 1,0)

Modules zijn niet aanwezig in Power shell 1,0: in plaats daarvan moest u de modules registreren en gebruiken. Het wordt echter niet aanbevolen deze technologie op dit moment te gebruiken, omdat modules doorgaans eenvoudiger te installeren en te importeren zijn. Zie [een Windows Power shell-module maken](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)voor meer informatie.

## <a name="importing-a-module-with-import-module-powershell-20"></a>Een module importeren met import-module (Power Shell 2,0)

Power Shell 2,0 maakt gebruik van de juiste benoemde cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) voor het importeren van modules. Wanneer deze cmdlet wordt uitgevoerd, zoekt Windows Power shell naar de opgegeven module binnen de mappen die zijn opgegeven in de `PSModulePath` variabele. Wanneer de opgegeven map wordt gevonden, zoekt Windows Power shell naar bestanden in de volgende volg orde: module manifest bestanden (. psd1), script module bestanden (. psm1), binaire module bestanden (. dll). Zie voor meer informatie over het toevoegen van mappen aan de zoek opdracht het installatiepad van [PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md).
De volgende code beschrijft hoe een module moet worden geïmporteerd:

```powershell
Import-Module myModule
```

Ervan uitgaande dat myModule zich in Power Shell bevindt `PSModulePath` , wordt myModule in het actieve geheugen geladen. Als myModule zich niet op een pad bevindt `PSModulePath` , kunt u Power shell nog steeds expliciet aanwijzen waar u deze kunt vinden:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

U kunt ook de `-Verbose` para meter gebruiken om te bepalen wat wordt geëxporteerd uit de module en wat wordt geïmporteerd in actief geheugen. Zowel de export als de invoer beperken wat er aan de gebruiker wordt blootgesteld: het verschil is wie de zicht baarheid beheert. In wezen worden exports beheerd door code binnen de module. De invoer wordt daarentegen bepaald door de `Import-Module` aanroep. Zie voor meer informatie **het beperken van leden die hieronder worden geïmporteerd**.

## <a name="implicitly-importing-a-module-powershell-30"></a>Een module impliciet importeren (Power Shell 3,0)

Vanaf Windows Power Shell 3,0 worden modules automatisch geïmporteerd wanneer een cmdlet of functie in de module in een opdracht wordt gebruikt. Deze functie werkt voor elke module in een map die is opgenomen in de waarde van de omgevings variabele **PSModulePath** . Als u de module niet opslaat op een geldig pad, kunt u deze nog steeds laden met de expliciete [import module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) optie, zoals hierboven beschreven.

Met de volgende acties wordt het automatisch importeren van een module geactiveerd, ook wel ' module automatisch laden ' genoemd.

- Een cmdlet gebruiken in een opdracht. Typ bijvoorbeeld `Get-ExecutionPolicy` de module micro soft. Power shell. Security die de cmdlet bevat geïmporteerd `Get-ExecutionPolicy` .

- Gebruik de [Get-opdracht](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet om de opdracht op te halen. Als u bijvoorbeeld typt, wordt `Get-Command Get-JobTrigger` de **PSScheduledJob** -module met de `Get-JobTrigger` cmdlet geïmporteerd. Een `Get-Command` opdracht die joker tekens bevat, wordt beschouwd als detectie en het importeren van een module wordt niet geactiveerd.

- Met de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) kunt u hulp krijgen bij een cmdlet. Typ bijvoorbeeld `Get-Help Get-WinEvent` de module micro soft. Power shell. Diagnostics die de cmdlet bevat geïmporteerd `Get-WinEvent` .

Ter ondersteuning van het automatisch importeren van modules, worden met de `Get-Command` cmdlet alle cmdlets en functies in alle geïnstalleerde modules opgehaald, zelfs als de module niet in de sessie is geïmporteerd. Zie het Help-onderwerp voor de cmdlet [Get-opdracht](/powershell/module/Microsoft.PowerShell.Core/Get-Command) voor meer informatie.

## <a name="the-importing-process"></a>Het import proces

Wanneer een module wordt geïmporteerd, wordt een nieuwe sessie status voor de module gemaakt en wordt er een [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -object in het geheugen gemaakt. Er wordt een sessie status gemaakt voor elke module die wordt geïmporteerd (dit omvat de hoofd module en eventuele geneste modules). De leden die worden geëxporteerd uit de hoofd module, inclusief alle leden die zijn geëxporteerd naar de hoofd module door een geneste modules, worden vervolgens geïmporteerd in de sessie status van de aanroeper.

De meta gegevens van leden die vanuit een module worden geëxporteerd, hebben een eigenschap van de module naam. Deze eigenschap wordt gevuld met de naam van de module die deze heeft geëxporteerd.

> [!WARNING]
> Als de naam van een geëxporteerd lid een niet-goedgekeurde term gebruikt of als de naam van het lid beperkte tekens gebruikt, wordt er een waarschuwing weer gegeven wanneer de [import-module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet wordt uitgevoerd.

De cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) retourneert standaard geen objecten aan de pijp lijn. De cmdlet ondersteunt echter een **PassThru** -para meter die kan worden gebruikt om een [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -object te retour neren voor elke module die wordt geïmporteerd. Gebruikers moeten de [Write-host-](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet uitvoeren om de uitvoer naar de host te verzenden.

## <a name="restricting--the-members-that-are-imported"></a>De leden die worden geïmporteerd beperken

Wanneer een module wordt geïmporteerd met behulp van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , worden alle geëxporteerde module leden standaard in de sessie geïmporteerd, met inbegrip van opdrachten die naar de module worden geëxporteerd door een geneste module. Variabelen en aliassen worden standaard niet geëxporteerd. Als u de geëxporteerde leden wilt beperken, gebruikt u een [module manifest](./how-to-write-a-powershell-module-manifest.md).
Gebruik de volgende para meters van de cmdlet om de leden te beperken die worden geïmporteerd `Import-Module` .

- **Functie**: deze para meter beperkt de functies die worden geëxporteerd. (Als u een module manifest gebruikt, raadpleegt u de sleutel FunctionsToExport.)

- `**Cmdlet**: deze para meter beperkt de cmdlets die worden geëxporteerd (als u een module manifest gebruikt, raadpleegt u de sleutel CmdletsToExport.)

- **Variabele**: met deze para meter worden de variabelen beperkt die worden geëxporteerd (als u een module manifest gebruikt, raadpleegt u de sleutel VariablesToExport.)

- **Alias**: met deze para meter worden de aliassen beperkt die worden geëxporteerd (als u een module manifest gebruikt, raadpleegt u de sleutel AliasesToExport.)

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)
