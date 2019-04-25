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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082173"
---
# <a name="naming-help-files"></a>Naamgeving van Help-bestanden

In dit onderwerp wordt uitgelegd hoe u om de naam van een help op basis van een XML-bestand zodat het [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kunt vinden. De vereisten voor de naam verschillen voor elk opdrachttype.

## <a name="cmdlet-help-files"></a>Cmdlet Help-bestanden

Het help-bestand voor een C# cmdlet moet de naam voor de assembly waarin de cmdlet is gedefinieerd. Gebruik de volgende bestandsindeling: naam:

```
<AssemblyName>.dll-help.xml
```

De indeling van de assembly-naam is vereist, zelfs wanneer de assembly een geneste module is.

Bijvoorbeeld, de [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly Microsoft.PowerShell.Diagnostics.dll. De `Get-Help` cmdlet zoekt een help-onderwerp voor de `Get-WinEvent` cmdlet alleen in het bestand Microsoft.PowerShell.Diagnostics.dll help.xml in de modulemap.

## <a name="provider-help-files"></a>Provider van Help-bestanden

Het help-bestand voor een Windows PowerShell-provider moet de naam voor de assembly waarin de provider is gedefinieerd. Gebruik de volgende bestandsindeling: naam:

```
<AssemblyName>.dll-help.xml
```

De indeling van de assembly-naam is vereist, zelfs wanneer de assembly een geneste module is.

Bijvoorbeeld, is de certificaat-provider gedefinieerd in de assembly Microsoft.PowerShell.Security.dll. De `Get-Help` cmdlet zoekt een help-onderwerp in voor de provider certificaat alleen in het bestand Microsoft.PowerShell.Security.dll help.xml in de modulemap.

## <a name="function-help-files"></a>Functie Help-bestanden

Functions kunnen worden vastgelegd met behulp van [help op basis van een opmerking](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of in een XML-help-bestand wordt vermeld. Als de functie wordt gedocumenteerd in een XML-bestand, de functie moet beschikken over een `.ExternalHelp` Opmerking trefwoord dat u de functie aan het XML-bestand koppelt. Anders wordt de `Get-Help` cmdlet kan het help-bestand niet vinden.

Er zijn geen technische vereisten voor de naam van een help-bestand. Er is echter een best practice om de naam van het help-bestand voor de scriptmodule waarin de functie is gedefinieerd. Bijvoorbeeld, is de volgende functie gedefinieerd in het bestand MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM-opdracht Help-bestanden

Het help-bestand voor een CIM-opdracht moet de naam voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd. Gebruik de volgende bestandsindeling: naam:

```
<FileName>.cdxml-help.xml
```

CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules. Wanneer de CIM-opdracht wordt geïmporteerd in de sessie als een functie, Windows PowerShell wordt toegevoegd een `.ExternalHelp` Opmerking trefwoord dat u wilt de functiedefinitie van de die wordt gekoppeld aan de functie aan de hand van een XML-bestand dat de naam voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.

## <a name="script-workflow-help-files"></a>Script werkstroom Help-bestanden

Scriptwerkstromen die zijn opgenomen in modules kunnen worden beschreven in de help op basis van een XML-bestanden. Er zijn geen technische vereisten voor de naam van het help-bestand. Er is echter een best practice om de naam van het help-bestand voor de scriptmodule waarin de scriptwerkstroom is gedefinieerd. Bijvoorbeeld:

```
<ScriptModule>.psm1-help.xml
```

In tegenstelling tot andere scripts opdrachten scriptwerkstromen hoeven niet een `.ExternalHelp` Opmerking trefwoord om deze te koppelen met een help-bestand. In plaats daarvan Windows PowerShell zoekt in de UI-cultuur-specifieke submappen van de modulemap voor help op basis van een XML-bestanden en Help-informatie voor de scriptwerkstroom in alle bestanden zoekt. `.ExternalHelp` Opmerking sleutelwoord worden genegeerd.

Omdat de `.ExternalHelp` Opmerking trefwoord wordt genegeerd, de `Get-Help` cmdlet kunt hulp zoeken over scriptwerkstromen alleen wanneer ze zijn opgenomen in modules.