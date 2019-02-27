---
title: Over het maken van een Console-Shell | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845057"
---
# <a name="how-to-create-a-console-shell"></a>Een console-shell maken

Windows PowerShell biedt een merk-Shell-hulpprogramma, ook wel de 'maken-kit', die wordt gebruikt voor het maken van een console-shell die kan niet worden uitgebreid. De houders die zijn gemaakt met dit nieuwe hulpprogramma kunnen niet later worden uitgebreid via een Windows PowerShell-module.

## <a name="syntax"></a>Syntaxis

Hier volgt de syntaxis die is gebruikt voor het uitvoeren van maken-Shell uit in een bestand maken.

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

Hier volgt een korte beschrijving van de parameters van maken-Shell.

> [!CAUTION]
> UNC-paden naar assembly's worden niet ondersteund door maken-Shell.

|Parameter|Description|
|---------------|-----------------|
|-out n.exe|Vereist. De naam van de shell te produceren. Het pad is opgegeven als onderdeel van deze parameter.<br /><br /> Merk-shell worden '.exe' toegevoegd aan deze waarde als deze niet is opgegeven. **Let op:**  Maak een uitvoerbestand niet met dezelfde naam als het waarnaar wordt verwezen, dll-bestand. Als u dit probeert, maakt het hulpprogramma maken-Shell een .cs-bestand met dezelfde naam, die het .cs-bestand met de cmdlet-broncode wordt overschreven.|
|ns - naamruimte|Vereist. De naamruimte moet worden gebruikt voor het afgeleide [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) klasse die de maken-kit compileert en genereert.|
|-lib libdirectory1[,libdirectory2,..]|De mappen waarin wordt gezocht naar .NET-assembly's, met inbegrip van de Windows PowerShell-assembly's, assembly's die zijn opgegeven door de `reference` parameter, assembly's waarnaar indirect wordt verwezen door een ander assembly en het systeem .NET-assembly's.|
|-verwijzen naar ca1.dll[,ca2.dll,...]|Een door komma's gescheiden lijst van de assembly's om op te nemen in de shell. Deze assembly's bevat alle cmdlet en provider assembly's, evenals resource-assembly's die moeten worden geladen. Als deze parameter niet is opgegeven, wordt klikt u vervolgens een shell geproduceerd dat alleen de essentiële cmdlets en providers die worden geleverd door Windows PowerShell bevat.<br /><br /> De assembly's kunnen worden opgegeven met behulp van het volledige pad, anders wordt gezocht voor het gebruik van het pad dat is opgegeven door de `lib` parameter.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Een door komma's gescheiden lijst van de gegevens opmaken om op te nemen in de shell. Als deze parameter niet is opgegeven, wordt klikt u vervolgens een shell geproduceerd die alleen de indeling gegevens geleverd door Windows PowerShell bevat.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Een door komma's gescheiden lijst van het typegegevens u wilt opnemen in de shell. Als deze parameter niet is opgegeven, wordt klikt u vervolgens een shell geproduceerd die alleen het typegegevens geleverd door Windows PowerShell bevat.|
|-bron c1.cs [, c2.cs,...]|De naam van een bestand, geleverd door de ontwikkelaar van de shell, dat alle broncode die nodig zijn voor het bouwen van de shell bevat.<br /><br /> Het bronbestand van de code kan bevatten van de volgende code:<br /><br /> -De implementatie van de autorisatie manager die de standaard-Autorisatiebeheer overschrijft. (Dit kan ook worden opgegeven in een assembly gecompileerd.)<br />-De informatieve kenmerkdeclaraties assembly:, zoals de AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, en AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Het type dat de autorisatie manager-implementatie bevat. Dit kan worden gedefinieerd in de broncode, of in een assembly gecompileerd (opgegeven door de `reference` parameter). Als deze parameter niet is opgegeven, wordt de standaard security manager gebruikt. De waarde moet de volledige naam, met inbegrip van naamruimten.|
|-win32icon i.ico|Het pictogram voor het .exe-bestand voor de shell. Als niet is opgegeven, wordt het pictogram met de c# compiler (indien aanwezig) hebben op de shell.|
|-initscript p.ps1|Het van opstartprofiel voor de shell. Het bestand wordt geleverd ' as-is '; Er is geen geldig controle wordt uitgevoerd door maken-Shell.|
|-builtinscript s1.ps1[,s2.ps1,...]|Een lijst met ingebouwde scripts voor de shell. Deze scripts worden gedetecteerd voordat de scripts in het pad en de inhoud kunnen niet worden gewijzigd als de shell is gemaakt.<br /><br /> De bestanden zijn opgenomen "as-is '; Er is geen geldig controle wordt uitgevoerd door maken-Shell.|
|-resource resourcefile.txt|De txt-bestand met help en banner resources voor de shell. De eerste resource ShellHelp heet, en bevat de tekst die wordt weergegeven als de shell is aangeroepen met de `help` parameter. De tweede resource met de naam ShellBanner en bevat de tekst en copyrightgegevens weergegeven wanneer de shell wordt gestart in de interactieve modus.<br /><br /> Als deze parameter niet is opgegeven, of deze resources niet aanwezig zijn, wordt een algemene hulp en een banner gebruikt.|
|-cscflags cscFlags|Vlaggen die moeten worden doorgegeven aan de C# compiler (csc.exe). Deze worden doorgegeven via ongewijzigd. Als deze parameter spaties bevat, moeten tussen dubbele aanhalingstekens worden geplaatst.|
|-?<br /><br /> -help|Geeft de copyright bericht en de opdrachtregelopties maken-Shell.|
|-verbose|Geeft gedetailleerde informatie, terwijl de shell wordt gemaakt.|

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)