---
description: Geeft een korte inleiding tot de Power shell-werk stroom functie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252391"
---
# <a name="about-workflows"></a>Over werk stromen

## <a name="short-description"></a>Korte beschrijving

Geeft een korte inleiding tot de Power shell-werk stroom functie.

## <a name="long-description"></a>Lange beschrijving

Power shell workflow biedt de voor delen van de [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) naar Power shell en biedt u de mogelijkheid om werk stromen te schrijven en uit te voeren.

Power shell-werk stroom is geïntroduceerd in Power Shell 3,0 en de module is beschikbaar tot Power shell 5,1. Voor meer informatie over de Power shell-werk stroom raadpleegt u de werk [stromen Guide](/previous-versions/powershell/scripting/components/workflows-guide) en [schrijft u een Windows Power shell-werk stroom](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).

## <a name="about-workflows"></a>Over werk stromen

Werk stromen zijn opdrachten die bestaan uit een geordende reeks gerelateerde activiteiten. Normaal gesp roken worden ze gedurende lange tijd uitgevoerd, waarbij gegevens worden verzameld uit en gewijzigd in honderden computers, vaak in heterogene omgevingen.

Werk stromen kunnen worden geschreven in XAML, de taal die wordt gebruikt in Windows Workflow Foundation of in de Power shell-taal. Werk stromen worden meestal verpakt in modules en bevatten Help-onderwerpen. Zie [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf)voor meer informatie.

Werk stromen zijn kritiek in een IT-omgeving, omdat ze niet meer opnieuw kunnen worden opgestart en automatisch moeten worden hersteld van veelvoorkomende fouten. U kunt de verbinding verbreken en opnieuw verbinden met sessies en computers waarop werk stromen worden uitgevoerd zonder de werk stroom verwerking te onderbreken, en werk stromen transparant te onderbreken en uit te scha kelen zonder gegevens verlies. Elke activiteit in een werk stroom kan worden vastgelegd en gecontroleerd ter referentie.
Werk stromen kunnen worden uitgevoerd als taken en kunnen worden gepland met behulp van de functie voor geplande taken van Power shell.

De status en de gegevens in een werk stroom worden opgeslagen of bewaard aan het begin en het einde van de werk stroom en op de punten die u opgeeft. Persistentie punten van werk stromen werken zoals moment opnamen van data bases of Program ma's voor programma controle om de werk stroom te beschermen tegen de gevolgen van onderbrekingen en storingen. Als de werk stroom niet kan worden hersteld na een storing, kunt u de permanente gegevens gebruiken en hervatten vanaf het laatste persistentie punt, in plaats van een uitgebreide werk stroom vanaf het begin opnieuw uit te voeren.

## <a name="workflow-requirements-and-configuration"></a>Werk stroom vereisten en configuratie

Een Power shell-werk stroom configuratie bestaat uit de volgende elementen:

- Een client computer waarop de werk stroom wordt uitgevoerd.
- Een werk stroom sessie, **PSSession** , op de client computer of op een externe computer.
- Beheerde knoop punten, de doel computers die worden beïnvloed door de werk stroom activiteiten.

De werk stroom sessie is niet vereist, maar wordt aanbevolen. **PSSessions** kan profiteren van de functies van de robuuste herstel-en verbroken sessies van Power shell om niet-verbonden werk stroom sessies te herstellen. Zie [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md) voor meer informatie.

Omdat de client computer en de computer waarop de werk stroom sessie wordt uitgevoerd, beheerde knoop punten kunnen zijn, kunt u een werk stroom uitvoeren op één computer die voldoet aan alle rollen.

Op de client computer en de computer waarop de werk stroom sessie wordt uitgevoerd, moet Power Shell 3,0 worden uitgevoerd. Alle in aanmerking komende systemen worden ondersteund, met inbegrip van de Server Core-installatie opties van Windows Server-besturings systemen.

Voor het uitvoeren van werk stromen die cmdlets bevatten, moeten de beheerde knoop punten beschikken over Windows Power Shell 2,0 of hoger. Voor beheerde knoop punten is Power shell niet vereist, tenzij de werk stroom cmdlets bevat. U kunt werk stromen uitvoeren met Windows Management Instrumentation (WMI) en Common Information Model (CIM)-opdrachten op computers die geen Power shell bevatten.

## <a name="how-to-get-workflows"></a>Werk stromen ophalen

Werk stromen worden meestal verpakt in modules. Als u de module wilt importeren die een werk stroom bevat, gebruikt u een wille keurige opdracht in de module of gebruikt u de `Import-Module` cmdlet.
Modules worden automatisch geïmporteerd bij het eerste gebruik van een opdracht in de module.

Gebruik de `Get-Command` **CommandType** -para meter van de cmdlet om de werk stromen te vinden in modules die op uw computer zijn geïnstalleerd.

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a>Werk stromen uitvoeren

Gebruik de volgende procedure om een werk stroom uit te voeren.

1. Wanneer het beheerde knoop punt de lokale computer is, is deze stap niet vereist.
   Als dat niet het geval is, start u Power shell op de client computer met de optie **als administrator uitvoeren** .

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. Schakel externe communicatie van Power shell in op de computer waarop de werk stroom sessie wordt uitgevoerd en op beheerde knoop punten die worden beïnvloed door werk stromen die cmdlets bevatten.

   U hoeft deze stap maar één keer op elke deelnemende computer uit te voeren.

   Deze stap is alleen vereist bij het uitvoeren van werk stromen die cmdlets bevatten. U hoeft externe toegang niet in te scha kelen op de client computer, tenzij de werk stroom sessie wordt uitgevoerd op de client computer of op alle beheerde knoop punten waarop Power Shell 3,0 wordt uitgevoerd.

   Als u externe toegang wilt inschakelen, gebruikt u de `Enable-PSRemoting` cmdlet.

   ```powershell
   Enable-PSRemoting -Force
   ```

   U kunt externe toegang inschakelen met de instelling **script uitvoering inschakelen** Groepsbeleid. Zie [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) en [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie.

1. Gebruik de `New-PSWorkflowSession` `New-PSSession` cmdlets of om de werk stroom sessie te maken.

   De `New-PSWorkflowSession` cmdlet start een sessie die gebruikmaakt van de ingebouwde **micro soft. Power shell. werk stroom** sessie configuratie op de doel computer. Deze sessie configuratie bevat scripts, bestands typen en Format teren, en opties die zijn ontworpen voor werk stromen.

   U kunt ook de `New-PSSession` cmdlet gebruiken. Gebruik de para meter **configuratiepad** om de configuratie van **micro soft. Power shell. werk stroom** sessie op te geven. Deze opdracht is hetzelfde als het gebruik van de `New-PSWorkflowSession` cmdlet.

   U kunt ook de cmdlet gebruiken `New-PSSession` . Gebruik de para meter **configuratiepad** om de configuratie van **micro soft. Power shell. werk stroom** sessie op te geven.

   Op de lokale computer:

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   Op een externe computer:

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   Als u een beheerder bent van de werk stroom sessie computer, kunt u de `New-PSWorkflowExecutionOption` cmdlet gebruiken om aangepaste optie-instellingen te maken voor de werk stroom sessie configuratie. En gebruik de `Set-PSSessionConfiguration` cmdlet om de sessie configuratie te wijzigen.

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. Voer de werk stroom uit in de werk stroom sessie. Als u de namen van de beheerde knoop punten, doel computers wilt opgeven, gebruikt u de algemene para meter **PSComputerName** workflow.

   In de volgende voor beelden wordt de werk stroom met de naam **test-werk stroom** uitgevoerd.

   Waarbij het beheerde knoop punt de computer is die als host fungeert voor de werk stroom sessie:

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   Waar de beheerde knoop punten externe computers zijn.

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   In het volgende voor beeld wordt de **test werk stroom** op honderden computers uitgevoerd. De `Get-Content` cmdlet haalt de computer namen op uit een tekst bestand en slaat ze op in de `$Servers` variabele op de lokale computer.

   `Invoke-Command` gebruikt de `$Using` aanpassings functie van het bereik om de `$Servers` variabele in de lokale sessie te definiëren. Zie about_Remote_Variables voor meer informatie over de `$Using` aanpassing van het [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)bereik.

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a>Algemene werk stroom parameters gebruiken

De algemene werk stroom parameters zijn een set para meters die door Power shell automatisch aan alle werk stromen worden toegevoegd. Power shell voegt de algemene cmdlet-para meters toe aan alle werk stromen, zelfs als de werk stroom geen gebruik maakt van het kenmerk **CmdletBinding** .

Met de volgende werk stroom worden bijvoorbeeld geen para meters gedefinieerd. Wanneer u de werk stroom uitvoert, heeft deze echter zowel de **CommonParameters** als de **WorkflowCommonParameters**.

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

De algemene werk stroom parameters bevatten verschillende para meters die essentieel zijn voor het uitvoeren van werk stromen. De gemeen schappelijke para meter **PSComputerName** geeft bijvoorbeeld de beheerde knoop punten waarop de werk stroom invloed heeft.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

De algemene para meter **PSPersist** workflow bepaalt wanneer werk stroom gegevens worden bewaard. U kunt hiermee het persistentie punt tussen activiteiten toevoegen aan werk stromen die geen persistentie punten definiëren.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

Met andere algemene werk stroom parameters kunt u de kenmerken van de externe verbinding met de beheerde knoop punten opgeven. Hun namen en functionaliteit zijn vergelijkbaar met de para meters van externe cmdlets, waaronder `Invoke-Command` .

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

Zorg ervoor dat u de externe para meters die de verbinding voor de werk stroom sessie definieert **,** onderscheidt van de algemene para meters voor de vaste workflow die de verbinding met de beheerde knoop punten definiëren.

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

Sommige algemene werk stroom parameters zijn uniek voor werk stromen, zoals de **PSParameterCollection** -para meter waarmee u verschillende algemene parameter waarden van werk stromen kunt opgeven voor verschillende externe knoop punten. Zie [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)voor een lijst en een beschrijving van de algemene werk stroom parameters.

## <a name="see-also"></a>Zie ook

[Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[PSWorkflow](xref:PSWorkflow) -cmdlets

[Handleiding voor werkstromen](/previous-versions/powershell/scripting/components/workflows-guide)

[Een Windows PowerShell-werkstroom schrijven](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
