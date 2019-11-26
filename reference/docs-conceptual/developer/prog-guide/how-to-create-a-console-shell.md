---
title: Een console-shell maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352603"
---
# <a name="how-to-create-a-console-shell"></a>Een console-shell maken

Windows Power shell biedt een hulp programma voor het maken van Shell, ook wel ' maken-Kit ' genoemd. dit wordt gebruikt voor het maken van een console shell die niet uitbreidbaar is. Shells die zijn gemaakt met dit nieuwe hulp programma kunnen niet later worden uitgebreid via een Windows Power shell-module.

## <a name="syntax"></a>Syntaxis

Hier volgt de syntaxis die wordt gebruikt voor het uitvoeren van een make-shell vanuit een bestand.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parameters

Hier volgt een korte beschrijving van de para meters van make-shell.

> [!CAUTION]
> UNC-paden naar assembly's worden niet ondersteund door make-shell.

|Parameter|Beschrijving|
|---------------|-----------------|
|-uitgaand n. exe|Vereist. De naam van de shell die moet worden geproduceerd. Het pad is opgegeven als deel van deze para meter.<br /><br /> Make-shell voegt '. exe ' toe aan deze waarde als deze niet is opgegeven. **Let op:**  Maak geen uitvoer bestand met dezelfde naam als het dll-bestand waarnaar wordt verwezen. Als u dit probeert, maakt het hulp programma maken-shell een. CS-bestand met dezelfde naam, waardoor het. CS-bestand met de bron code van de cmdlet wordt overschreven.|
|-naam ruimte NS|Vereist. De naam ruimte die moet worden gebruikt voor de afgeleide klasse [System. Management. Automation. Runspaces. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) die de set-Kit genereert en compileert.|
|-lib libdirectory1 [, libdirectory2,..]|De mappen die worden gezocht naar .NET-assembly's, inclusief de Windows Power shell-assembly's, assembly's die zijn opgegeven met de para meter `reference`, assembly's indirect waarnaar wordt verwezen door een andere assembly en de .NET-systeem-assembly's.|
|-Reference Ca1. dll [, Ca2. dll,...]|Een door komma's gescheiden lijst met de assembly's die in de shell moeten worden meegenomen. Deze assembly's omvatten alle cmdlets en provider-assembly's, evenals bron-assembly's die moeten worden geladen. Als deze para meter niet is opgegeven, wordt er een shell geproduceerd met alleen de kern-cmdlets en providers van Windows Power shell.<br /><br /> De assembly's kunnen worden opgegeven met behulp van het volledige pad, anders wordt gezocht naar het pad dat is opgegeven met de para meter `lib`.|
|-formatdata FD1. Format. ps1xml [, FD2. Format. ps1xml,...]|Een door komma's gescheiden lijst met indelings gegevens die u wilt opnemen in de shell. Als deze para meter niet is opgegeven, wordt er een shell gemaakt die alleen de indelings gegevens bevat die worden geleverd door Windows Power shell.|
|-typedata Td1. type. ps1xml [, Td2. type. ps1xml,...]|Een door komma's gescheiden lijst met type gegevens die u wilt opnemen in de shell. Als deze para meter niet is opgegeven, wordt er een shell geproduceerd die alleen de type gegevens bevat die door Windows Power shell worden verstrekt.|
|-source c1.cs [, c2.cs,...]|De naam van een bestand dat door de shell-ontwikkelaar wordt verschaft en dat een bron code bevat die nodig is om de shell te bouwen.<br /><br /> Het bron code bestand kan een van de volgende bron code bevatten:<br /><br /> -De autorisatie beheer-implementatie die de standaard autorisatie beheerder overschrijft. (Dit kan ook worden opgegeven in een assembly.)<br />-Declaraties van assembly-kenmerk gegevens: zoals AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute en AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Het type dat de autorisatie beheer-implementatie bevat. Dit kan worden gedefinieerd in de bron code of gecompileerd in een assembly (opgegeven door de para meter `reference`). Als deze para meter niet wordt opgegeven, wordt de standaard beveiligings beheerder gebruikt. De waarde moet de volledige type naam zijn, met inbegrip van naam ruimten.|
|-win32icon i. ico|Het pictogram voor het exe-bestand voor de shell. Als dat niet is opgegeven, heeft de shell het pictogram dat de c#-compiler bevat (indien aanwezig).|
|-initscript p. ps1|Het opstart profiel voor de shell. Het bestand is opgenomen in de as-is. Er wordt geen geldigheids controle uitgevoerd door make-shell.|
|-builtinscript S1. ps1 [, S2. ps1,...]|Een lijst met ingebouwde scripts voor de shell. Deze scripts worden gedetecteerd vóór scripts in het pad en de inhoud kan niet worden gewijzigd nadat de shell is gebouwd.<br /><br /> De bestanden zijn opgenomen in de as-is. Er wordt geen geldigheids controle uitgevoerd door make-shell.|
|-resource resource file. txt|Het txt-bestand met Help-en banner resources voor de shell. De eerste resource heeft de naam ShellHelp en bevat de tekst die wordt weer gegeven als de shell wordt aangeroepen met de para meter `help`. De tweede resource heeft de naam ShellBanner en bevat de tekst en copyright gegevens die worden weer gegeven wanneer de shell wordt gestart in de interactieve modus.<br /><br /> Als deze para meter niet wordt opgegeven of als deze resources niet aanwezig zijn, worden er een algemene Help en banner gebruikt.|
|-cscflags cscFlags|Vlaggen die moeten worden door gegeven aan C# de compiler (CSC. exe). Deze worden door gegeven ongewijzigd. Als deze para meter spaties bevat, moet deze tussen dubbele aanhalings tekens worden geplaatst.|
|-?<br /><br /> -Help|Hiermee worden de opdracht regel opties copyright bericht en shell gemaakt.|
|-verbose|Geeft gedetailleerde informatie weer terwijl de shell wordt gemaakt.|

## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)