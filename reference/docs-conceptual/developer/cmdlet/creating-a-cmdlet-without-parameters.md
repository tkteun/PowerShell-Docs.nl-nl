---
title: Een cmdlet zonder para meters maken | Microsoft Docs
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
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359429"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Een cmdlet maken zonder parameters

In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee informatie wordt opgehaald van de lokale computer zonder het gebruik van para meters, en vervolgens de informatie naar de pijp lijn schrijft. De cmdlet die hier wordt beschreven, is een Get-proc-cmdlet waarmee informatie wordt opgehaald over de processen van de lokale computer en die informatie vervolgens wordt weer gegeven op de opdracht regel.

> [!NOTE]
> Houd er rekening mee dat bij het schrijven van cmdlets de referentie-assembly's van Windows Power shell® worden gedownload naar schijf (standaard in C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Ze zijn niet geïnstalleerd in de GAC (Global assembly cache).

## <a name="naming-the-cmdlet"></a>De cmdlet een naam geven

De naam van een cmdlet bestaat uit een werk woord waarmee de actie wordt aangegeven die de cmdlet uitvoert en een zelfstandig naam woord dat de items aangeeft waarop de cmdlet op betrekking heeft. Omdat in deze voor beeld-cmdlet Get-proc proces objecten worden opgehaald, wordt de term Get gebruikt, die is gedefinieerd door [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -inventarisatie en het zelfstandig naam woord ' proc ' om aan te geven dat de cmdlet werkt voor het verwerken van items.

Gebruik bij het benoemen van cmdlets geen van de volgende tekens: #, () {} [] &-/\ $; : "' < > &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Een zelfstandig naam woord kiezen

Kies een specifiek zelfstandig naam woord. U kunt het beste een enkelvoudig zelfstandig naam woord gebruiken, met een kortere versie van de product naam. Een voor beeld van een cmdlet-naam van dit type is "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Een werk woord kiezen

U moet een verb gebruiken uit de set met goedgekeurde opdracht namen voor cmdlets. Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over de goedgekeurde cmdlet-termen.

## <a name="defining-the-cmdlet-class"></a>De cmdlet-klasse definiëren

Nadat u de naam van een cmdlet hebt gekozen, definieert u een .NET-klasse voor het implementeren van de cmdlet. Dit is de klassedefinitie voor deze voor beeld van de cmdlet Get-proc:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

U ziet dat er eerder aan de klassedefinitie, het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) met de syntaxis `[Cmdlet(verb, noun, ...)]`, wordt gebruikt om deze klasse te identificeren als een cmdlet. Dit is het enige vereiste kenmerk voor alle cmdlets en de Windows Power shell-runtime kan ze op de juiste wijze aanroepen. U kunt kenmerk trefwoorden instellen om de klasse zo nodig verder te declareren. Houd er rekening mee dat de kenmerk declaratie voor onze voor beeld-GetProcCommand-klasse alleen de namen van de zelfstandig naam woord en de verb declareert voor de cmdlet Get-proc.

> [!NOTE]
> Voor alle Windows Power shell-kenmerk klassen moeten de tref woorden die u kunt instellen overeenkomen met de eigenschappen van de kenmerk klasse.

Wanneer u de klasse van de cmdlet een naam geeft, is het een goed idee om de naam van de cmdlet in de naam van de klasse weer te geven. U doet dit door het formulier "VerbNounCommand" te gebruiken en "verb" en "zelfstandig naam" te vervangen door het werk woord en het zelfstandig naam woord dat wordt gebruikt in de cmdletnaam. Zoals wordt weer gegeven in de vorige klassedefinitie, definieert de voor beeld-cmdlet Get-proc een klasse met de naam GetProcCommand, die is afgeleid van de basis klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .

> [!IMPORTANT]
> Als u een cmdlet wilt definiëren die rechtstreeks toegang heeft tot de Windows Power shell-runtime, moet uw .NET-klasse worden afgeleid van de basis klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Zie [een cmdlet maken die parameter sets definieert](./adding-parameter-sets-to-a-cmdlet.md)voor meer informatie over deze klasse.

> [!NOTE]
> De klasse voor een cmdlet moet expliciet als openbaar worden gemarkeerd. Klassen die niet zijn gemarkeerd als openbaar, worden standaard intern en worden niet gevonden door de Windows Power shell-runtime.

Windows Power Shell maakt gebruik van de naam ruimte [micro soft. Power shell. commands](/dotnet/api/Microsoft.PowerShell.Commands) voor de bijbehorende cmdlet-klassen. Het is raadzaam om uw cmdlet-klassen in een opdrachten naam ruimte van uw API-naam ruimte te plaatsen, bijvoorbeeld xxx. PS. commands.

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

De klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) biedt drie belang rijke invoer methoden, ten minste één van de cmdlets die moeten worden overschreven. Zie [How Windows Power shell](/previous-versions//ms714658(v=vs.85))(Engelstalig) voor meer informatie over het verwerken van records in Windows Power shell.

Voor alle typen invoer roept Windows Power shell runtime [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) aan om de verwerking in te scha kelen. Als uw cmdlet een aantal voor verwerkingen of Setup moet uitvoeren, kan dit door deze methode te overschrijven.

> [!NOTE]
> Windows Power shell gebruikt de term ' record ' om de set parameter waarden te beschrijven die worden opgegeven wanneer een cmdlet wordt aangeroepen.

Als uw cmdlet pijplijn invoer accepteert, moet deze de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) negeren en optioneel de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Zo kan een cmdlet beide methoden overschrijven als alle invoer wordt verzameld met [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en vervolgens op de invoer als geheel wordt uitgevoerd in plaats van één element per keer, omdat de cmdlet `Sort-Object` doet.

Als uw cmdlet geen pijplijn invoer heeft, moet deze de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) overschrijven. Houd er rekening mee dat deze methode veelvuldig wordt gebruikt in plaats van [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wanneer de cmdlet op één element per keer niet kan worden uitgevoerd, zoals in het geval van een sorteer-cmdlet.

Omdat deze voor beeld-cmdlet Get-proc de pijplijn invoer moet ontvangen, overschrijft deze de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en gebruikt de standaard implementaties voor [System. Management. Automation. cmdlet. BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)en [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Met [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override worden processen opgehaald en naar de opdracht regel geschreven met behulp van de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

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

#### <a name="things-to-remember-about-input-processing"></a>Wat u moet weten over invoer verwerking

- De standaard bron voor invoer is een expliciet object (bijvoorbeeld een teken reeks) dat door de gebruiker is opgegeven op de opdracht regel. Zie [een cmdlet maken voor het verwerken van opdracht regel invoer](./adding-parameters-that-process-command-line-input.md)voor meer informatie.

- Een invoer verwerkings methode kan ook invoer ontvangen van het uitvoer object van een upstream-cmdlet in de pijp lijn. Zie [een cmdlet maken voor het verwerken van pijplijn invoer](./adding-parameters-that-process-pipeline-input.md)voor meer informatie. Houd er rekening mee dat uw cmdlet invoer kan ontvangen van een combi natie van opdracht regel-en pijplijn bronnen.

- De downstream-cmdlet kan niet lang worden geretourneerd of helemaal niet. Om die reden mag de invoer verwerkings methode in uw cmdlet geen vergren delingen bevatten tijdens aanroepen naar [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), met name de vergren delingen waarvoor de scope zich buiten het cmdlet-exemplaar bevindt.

> [!IMPORTANT]
> Cmdlets moeten nooit [System. console. WriteLine *](/dotnet/api/System.Console.WriteLine) of gelijkwaardige aanroepen.

- Uw cmdlet kan object variabelen bevatten om op te schonen wanneer de verwerking is voltooid (bijvoorbeeld als er een bestands ingang in de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wordt geopend en de ingang geopend is voor gebruik door [ System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Het is belang rijk te weten dat de Windows Power shell-runtime de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) niet altijd aanroept, waardoor het opschonen van objecten moet worden uitgevoerd.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan bijvoorbeeld niet worden aangeroepen als de cmdlet halverwege is geannuleerd of als er een afsluit fout optreedt in een deel van de cmdlet. Daarom moet een cmdlet die het opschonen van objecten vereist, het volledige [System. IDisposable](/dotnet/api/System.IDisposable) -patroon implementeren, met inbegrip van de FINALIZE, zodat de runtime beide [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan aanroepen en [ System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking.

## <a name="code-sample"></a>Code voorbeeld

Zie GetProcessSample01- C# voor [beeld](./getprocesssample01-sample.md)voor de volledige voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. De code voor de voor beeld-cmdlet Get-proc is klein, maar maakt nog steeds gebruik van de Windows Power shell-runtime en een bestaand .NET-object. Dit is voldoende om het handig te maken. Laten we dit testen om beter te begrijpen wat Get-proc kan doen en hoe de uitvoer ervan kan worden gebruikt. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

1. Start Windows Power shell en ontvang de huidige processen die op de computer worden uitgevoerd.

    ```powershell
    get-proc
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Wijs een variabele toe aan de cmdlet-resultaten voor eenvoudiger manipulatie.

    ```powershell
    $p=get-proc
    ```

3. Het aantal processen ophalen.

    ```powershell
    $p.length
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    63
    ```

4. Haal een specifiek proces op.

    ```powershell
    $p[6]
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. De begin tijd van dit proces ophalen.

    ```powershell
    $p[6].starttime
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Haal de processen op waarvoor het aantal ingangen groter is dan 500 en sorteer het resultaat.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Gebruik de `Get-Member`-cmdlet om de eigenschappen weer te geven die beschikbaar zijn voor elk proces.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Zie ook

[Een cmdlet maken voor het verwerken van de invoer van de opdracht regel](./adding-parameters-that-process-command-line-input.md)

[Een cmdlet maken om de invoer van de pijp lijn te verwerken](./adding-parameters-that-process-pipeline-input.md)

[Een Windows Power shell-cmdlet maken](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Hoe Windows Power shell werkt](/previous-versions//ms714658(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Naslag informatie voor Windows Power shell](../windows-powershell-reference.md)

[Voor beelden van cmdlets](./cmdlet-samples.md)