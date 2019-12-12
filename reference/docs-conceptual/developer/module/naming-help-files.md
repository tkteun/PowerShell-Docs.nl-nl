---
title: Naamgeving van Help-bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357328"
---
# <a name="naming-help-files"></a>Naamgeving van Help-bestanden

In dit onderwerp wordt uitgelegd hoe u een XML-gebaseerd Help-bestand kunt benoemen, zodat de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) het kan vinden. De naam vereisten verschillen per opdracht type.

## <a name="cmdlet-help-files"></a>Help-bestanden voor cmdlets

Het Help-bestand voor C# een cmdlet moet een naam hebben voor de assembly waarin de cmdlet is gedefinieerd. Gebruik de volgende indeling voor bestands namen:

```
<AssemblyName>.dll-help.xml
```

De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.

Bijvoorbeeld, de [Get-Wine vent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly micro soft. Power shell. Diagnostics. dll. De cmdlet `Get-Help` zoekt alleen naar een Help-onderwerp voor de cmdlet `Get-WinEvent` in het bestand micro soft. Power shell. Diagnostics. dll-Help. XML in de module directory.

## <a name="provider-help-files"></a>Help-bestanden voor providers

Het Help-bestand voor een Windows Power shell-provider moet een naam hebben voor de assembly waarin de provider is gedefinieerd. Gebruik de volgende indeling voor bestands namen:

```
<AssemblyName>.dll-help.xml
```

De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.

De certificaat provider wordt bijvoorbeeld gedefinieerd in de assembly micro soft. Power shell. Security. dll. De `Get-Help`-cmdlet zoekt alleen naar een Help-onderwerp voor de certificaat provider in het bestand micro soft. Power shell. Security. dll-Help. XML in de module directory.

## <a name="function-help-files"></a>Help-bestanden voor functies

Functies kunnen worden gedocumenteerd met behulp van [Help op basis van opmerkingen](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of gedocumenteerd in een XML-Help-bestand. Wanneer de functie is gedocumenteerd in een XML-bestand, moet de functie een `.ExternalHelp` Opmerking-tref woord hebben dat de functie koppelt aan het XML-bestand. Anders kan het Help-bestand niet worden gevonden met de `Get-Help`-cmdlet.

Er zijn geen technische vereisten voor de naam van een functie Help-bestand. Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de functie is gedefinieerd. De volgende functie wordt bijvoorbeeld gedefinieerd in het bestand MyModule. psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Help-bestanden voor de CIM-opdracht

Het Help-bestand voor een CIM-opdracht moet een naam hebben voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd. Gebruik de volgende indeling voor bestands namen:

```
<FileName>.cdxml-help.xml
```

CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules. Wanneer de CIM-opdracht in de sessie als een functie wordt geïmporteerd, wordt in Windows Power shell een `.ExternalHelp` opmerking toegevoegd als tref woord aan de functie definitie die de functie koppelt aan een XML Help-bestand met de naam van het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.

## <a name="script-workflow-help-files"></a>Help-bestanden voor de script werk stroom

Script werk stromen die zijn opgenomen in modules kunnen worden gedocumenteerd in Help-bestanden op basis van XML. Er zijn geen technische vereisten voor de naam van het Help-bestand. Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de werk stroom van het script is gedefinieerd. Bijvoorbeeld:

```
<ScriptModule>.psm1-help.xml
```

In tegens telling tot andere script opdrachten, is voor script werk stromen geen sleutel woord voor `.ExternalHelp` opmerking vereist om ze te koppelen aan een Help-bestand. In plaats daarvan zoekt Windows Power shell de specifieke submappen voor de gebruikers interface van de module directory voor Help-bestanden op basis van XML en zoekt de hulp voor de script werk stroom in alle bestanden. het tref woord `.ExternalHelp` opmerking wordt genegeerd.

Omdat het sleutel woord `.ExternalHelp` opmerking wordt genegeerd, kan de cmdlet `Get-Help` alleen hulp voor script werk stromen vinden als ze zijn opgenomen in modules.