---
ms.date: 09/12/2016
ms.topic: reference
title: Naamgeving van Help-bestanden
description: Naamgeving van Help-bestanden
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667586"
---
# <a name="naming-help-files"></a>Naamgeving van Help-bestanden

In dit onderwerp wordt uitgelegd hoe u een XML-gebaseerd Help-bestand kunt benoemen, zodat de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) het kan vinden. De naam vereisten verschillen per opdracht type.

## <a name="cmdlet-help-files"></a>Help-bestanden voor cmdlets

Het Help-bestand voor een C#-cmdlet moet een naam hebben voor de assembly waarin de cmdlet is gedefinieerd. Gebruik de volgende bestands indeling:

```
<AssemblyName>.dll-help.xml
```

De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.

De cmdlet [Get-Wine vent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) wordt bijvoorbeeld gedefinieerd in de assembly Microsoft.PowerShell.Diagnostics.dll. De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de `Get-WinEvent` cmdlet in het `Microsoft.PowerShell.Diagnostics.dll-help.xml` bestand in de module directory.

## <a name="provider-help-files"></a>Help-bestanden voor providers

Het Help-bestand voor een Power shell-provider moet een naam hebben voor de assembly waarin de provider is gedefinieerd. Gebruik de volgende bestands indeling:

`<AssemblyName>.dll-help.xml`

De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.

Bijvoorbeeld, de certificaat provider wordt gedefinieerd in de `Microsoft.PowerShell.Security.dll` Assembly. De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de certificaat provider in het `Microsoft.PowerShell.Security.dll-help.xml` bestand in de module directory.

## <a name="function-help-files"></a>Help-bestanden voor functies

Functies kunnen worden gedocumenteerd met behulp van [Help op basis van opmerkingen](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of gedocumenteerd in een XML-Help-bestand. Wanneer de functie is gedocumenteerd in een XML-bestand, moet de functie een `.ExternalHelp` Opmerking bevatten die de functie koppelt aan het XML-bestand. Anders kan het `Get-Help` Help-bestand niet worden gevonden met de cmdlet.

Er zijn geen technische vereisten voor de naam van een functie Help-bestand. Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de functie is gedefinieerd. De volgende functie is bijvoorbeeld gedefinieerd in het `MyModule.psm1` bestand.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Help-bestanden voor de CIM-opdracht

Het Help-bestand voor een CIM-opdracht moet een naam hebben voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd. Gebruik de volgende bestands indeling:

`<FileName>.cdxml-help.xml`

CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules. Wanneer de CIM-opdracht in de sessie als een functie wordt geïmporteerd, voegt Power shell een `.ExternalHelp` tref woord opmerking toe aan de functie definitie die de functie koppelt aan een XML Help-bestand met de naam van het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.

## <a name="script-workflow-help-files"></a>Help-bestanden voor de script werk stroom

Script werk stromen die zijn opgenomen in modules kunnen worden gedocumenteerd in Help-bestanden op basis van XML. Er zijn geen technische vereisten voor de naam van het Help-bestand. Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de werk stroom van het script is gedefinieerd. Bijvoorbeeld:

`<ScriptModule>.psm1-help.xml`

In tegens telling tot andere script opdrachten, is voor de script werk stromen geen `.ExternalHelp` tref woord opmerking vereist om ze te koppelen aan een Help-bestand. In plaats daarvan doorzoekt Power shell de specifieke submappen voor de gebruikers interface van de module directory voor Help-bestanden op basis van XML en zoekt u hulp voor de script werk stroom in alle bestanden. `.ExternalHelp` tref woord opmerking wordt genegeerd.

Omdat het `.ExternalHelp` tref woord opmerking wordt genegeerd, `Get-Help` kan de cmdlet alleen hulp voor script werk stromen vinden als deze zijn opgenomen in modules.
