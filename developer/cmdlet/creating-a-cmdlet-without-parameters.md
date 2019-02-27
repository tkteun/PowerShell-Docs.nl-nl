---
title: Het maken van een Cmdlet zonder Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850062"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Een cmdlet maken zonder parameters

In deze sectie wordt beschreven hoe u een cmdlet die wordt informatie opgehaald uit de lokale computer zonder het gebruik van parameters en vervolgens schrijft de informatie in de pijplijn te maken. De cmdlet die hier worden beschreven, is een cmdlet Get-Proc die haalt informatie op over de processen van de lokale computer en vervolgens informatie wordt weergegeven op de opdrachtregel.

Onderwerpen in deze sectie bevatten het volgende:

- [Naamgeving van de Cmdlet](#Naming-the-Cmdlet)

- [De Cmdlet-klasse definiëren](#Defining-the-Cmdlet-Class)

- [Invoer verwerken methode te overschrijven](#Overriding-an-Input-Processing-Method)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak](#Defining-Object-Types-and-Formatting)

- [Het bouwen van de Cmdlet](#Building-the-Cmdlet)

- [Testen van de Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> Let erop dat bij het schrijven van cmdlets, de Windows PowerShell®-verwijzingsassembly's worden gedownload naar schijf (standaard op C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Ze zijn niet geïnstalleerd in de Global Assembly Cache (GAC).

## <a name="naming-the-cmdlet"></a>Naamgeving van de Cmdlet

De naam van een cmdlet bestaat uit een term die geeft aan dat de actie van de cmdlet wordt en een zelfstandig naamwoord die aangeeft van de items die de cmdlet reageert. Omdat deze voorbeeld-cmdlet Get-Proc proces objecten worden opgehaald, wordt de term 'Ophalen', gedefinieerd door de [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) inventarisatie en het zelfstandig naamwoord 'Proc' om aan te geven dat de cmdlet op proces-items werkt.

Bij het benoemen van cmdlets gebruik niet een van de volgende tekens bevatten: #, () {} [] & - / \ $;: ' ' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Een zelfstandig naamwoord kiezen

Een zelfstandig naamwoord die specifiek is, moet u kiezen. Het is raadzaam om te gebruiken van een enkelvoudige zelfstandig naamwoord voorafgegaan door een verkorte versie van de naam van het product. De cmdlet-naam van een voorbeeld van dit type is '`Get-SQLServer`'.

### <a name="choosing-a-verb"></a>Een term kiezen

U moet een term uit de set van goedgekeurde cmdlet term namen gebruiken. Zie voor meer informatie over de goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>De Cmdlet-klasse definiëren

Nadat u de naam van een cmdlet hebt gekozen, definieert u een .NET-klasse voor het implementeren van de cmdlet. Hier volgt de definitie van de klasse voor dit voorbeeld-cmdlet Get-Proc:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

U ziet dat voor de klassendefinitie van de de [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk met de syntaxis van de `[Cmdlet(verb, noun, ...)]`, wordt gebruikt voor het identificeren van deze klasse als een cmdlet. Dit is de enige vereiste kenmerk voor alle cmdlets en hierdoor kan de Windows PowerShell-runtime ze correct aanroept. U kunt instellen dat kenmerk trefwoorden voor de klasse verder declareren indien nodig. Let erop dat de kenmerkdeclaratie voor onze GetProcCommand voorbeeldklasse alleen het zelfstandig naamwoord en werkwoord namen voor de cmdlet Get-Proc declareert.

> [!NOTE]
> Voor alle Windows PowerShell-klassen in kenmerk overeenkomen de trefwoorden die u kunt instellen met eigenschappen van de kenmerkklasse.

Naam van de klasse van de cmdlet, is het raadzaam in overeenstemming met de cmdletnaam van de in de naam van de klasse. Om dit te doen, gebruikt u de indeling "VerbNounCommand" en 'Bewerking' en "Zelfstandig naamwoord" vervangen door het werkwoord en een zelfstandig naamwoord gebruikt in de cmdletnaam. Zoals wordt weergegeven in de vorige klassedefinitie, de voorbeeld-cmdlet Get-Proc definieert een klasse genaamd GetProcCommand, die is afgeleid van de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basisklasse.

> [!IMPORTANT]
> Als u wilt voor het definiëren van een cmdlet die rechtstreeks toegang heeft tot de Windows PowerShell-runtime, uw .NET-klasse moet zijn afgeleid van de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse. Zie voor meer informatie over deze klasse [het maken van een Cmdlet die parametersets definieert](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> De klasse voor een cmdlet moet expliciet gemarkeerd als openbaar. Klassen die niet zijn gemarkeerd als openbare standaard ingesteld op interne en zal niet worden gevonden door de Windows PowerShell-runtime.

Windows PowerShell gebruikt de [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) naamruimte voor de cmdlet-klassen. Het verdient aanbeveling uw cmdlet-klassen in een naamruimte opdrachten van uw API-naamruimte, bijvoorbeeld xxx.PS.Commands plaatsen.

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

De [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse biedt drie verwerkingsmethoden van de belangrijkste invoer, ten minste een van die de cmdlet moet overschrijven. Zie voor meer informatie over hoe Windows PowerShell records verwerkt [hoe Windows PowerShell werkt](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Voor alle soorten invoer, de Windows PowerShell-runtime roept [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) om in te schakelen van verwerking. Als de cmdlet sommige voorverwerking of setup uitvoert moet, kunt deze dit doen door deze methode te overschrijven.

> [!NOTE]
> Windows PowerShell wordt de term 'record' gebruikt om te beschrijven van de set met parameterwaarden die zijn opgegeven als een cmdlet wordt aangeroepen.

Als de cmdlet pijpleidinginvoer accepteert, overschrijven deze de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, en (optioneel) de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)methode. Bijvoorbeeld, een cmdlet beide methoden kan overschrijven als het verzamelt alle invoer met behulp van [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en wordt vervolgens toegepast op de invoer als geheel in plaats van één element tegelijk, als de `Sort-Object` cmdlet is.

Als uw cmdlet pijpleidinginvoer neemt, overschrijven deze de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode. Houd er rekening mee dat deze methode vaak in plaats van gebruikt wordt [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wanneer de cmdlet kan niet worden uitgevoerd op één element op een tijdstip, zoals het geval van een cmdlet sorteren.

Omdat deze voorbeeld-cmdlet Get-Proc pijpleidinginvoer ontvangen moet, dit vervangt de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode en maakt gebruik van de standaard-implementaties voor [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) en [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). De [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) onderdrukking processen worden opgehaald en schrijft deze naar de opdrachtregel met behulp van de [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Om te onthouden over de verwerking van invoer

- De standaardbron voor invoer is een expliciete object (bijvoorbeeld een tekenreeks) opgegeven door de gebruiker op de opdrachtregel. Zie voor meer informatie, [het maken van een Cmdlet voor het proces vanaf de opdrachtregelinvoer](./adding-parameters-that-process-command-line-input.md).

- Invoer verwerken methode kan ook invoer ontvangen van het uitvoerobject van een upstream-cmdlet op de pijplijn. Zie voor meer informatie, [het maken van een Cmdlet voor het proces Pijpleidinginvoer](./adding-parameters-that-process-pipeline-input.md). Houd er rekening mee dat de cmdlet kunt invoer van een combinatie van de opdrachtregel ontvangen en pipeline-gegevensbronnen.

- De downstream-cmdlet kan niet worden geretourneerd gedurende een lange periode of helemaal niet. Om die reden, de verwerking van de methode in uw cmdlet invoer moet niet vergrendelingen hebben tijdens het aanroepen van [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), met name vergrendelingen waarvoor het bereik het cmdlet-exemplaar overschrijdt.

> [!IMPORTANT]
> Cmdlets moet nooit aanroepen [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) of een equivalent daarvan.

- Uw cmdlet hebt objectvariabelen opschonen na afloop verwerken (bijvoorbeeld, als het openen van de schuifknop van een bestand van de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode en houdt de ingang voor gebruik door openen.[ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Het is belangrijk te onthouden dat de Windows PowerShell-runtime niet altijd aanroepen de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode, waarmee de object-opschoning moet uitvoeren.

Bijvoorbeeld, [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan niet worden aangeroepen als de cmdlet halverwege wordt geannuleerd of als een afsluitende fout in een deel van de cmdlet optreedt. Daarom een cmdlet waarvoor de object-opschoning moet implementeren de volledige [System.Idisposable](/dotnet/api/System.IDisposable) patroon, waaronder de finalizer, zodat de runtime beide aanroepen kan [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) en [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking.

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [GetProcessSample01 voorbeeld](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten. Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. De code voor onze voorbeeld-cmdlet Get-Proc is klein, maar nog steeds maakt gebruik van de Windows PowerShell-runtime en een bestaande .NET-object, wat voldoende is om nuttig. Laten we het testen om beter te begrijpen wat Get-Proc kan doen en hoe de uitvoer kan worden gebruikt. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Start Windows PowerShell en ophalen van de huidige processen die worden uitgevoerd op de computer.

    ```powershell
    get-proc
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Een variabele toewijzen aan de cmdlet-resultaten voor het eenvoudiger bewerken.

    ```powershell
    $p=get-proc
    ```

3. Het aantal processen ophalen.

    ```powershell
    $p.length
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    63
    ```

4. Een specifiek proces worden opgehaald.

    ```powershell
    $p[6]
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Haal de begintijd van dit proces.

    ```powershell
    $p[6].starttime
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. De processen die het aantal ingangen groter dan 500 is ophalen en het resultaat te sorteren.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Gebruik de `Get-Member` cmdlet om de eigenschappen die beschikbaar zijn voor elk proces weer te geven.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    De volgende uitvoer wordt weergegeven.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Zie ook

[Het maken van een Cmdlet voor het verwerken van invoer van de opdrachtregel](./adding-parameters-that-process-command-line-input.md)

[Het maken van een Cmdlet voor het verwerken van invoer van de pijplijn](./adding-parameters-that-process-pipeline-input.md)

[Over het maken van een Windows PowerShell-Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referentie](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)