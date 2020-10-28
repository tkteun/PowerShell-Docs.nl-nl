---
ms.date: 09/13/2016
ms.topic: reference
title: Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking
description: Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking
ms.openlocfilehash: 883ff2d522266495e409fb0d45f29713baa6f047
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648674"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking

Cmdlets kunnen niet-afsluit fouten rapporteren door de methode [System. Management. Automation. cmdlet. WriteError][] aan te roepen en nog steeds te blijven werken op het huidige invoer object of op verdere inkomende pijplijn objecten. In deze sectie wordt uitgelegd hoe u een cmdlet maakt die niet-afsluit fouten in de invoer methoden van het proces rapporteert.

Voor niet-afsluit fouten (en het beëindigen van fouten) moet de cmdlet een [System. Management. Automation. ErrorRecord][] -object door geven om de fout te identificeren. Elke fout record wordt geïdentificeerd door een unieke teken reeks met de naam ' fout-id '. Naast de id wordt de categorie van elke fout opgegeven door constanten die zijn gedefinieerd door een [System. Management. Automation. ErrorCategory][] -inventarisatie. De gebruiker kan fouten op basis van hun categorie weer geven door de `$ErrorView` variabele in te stellen op ' CategoryView '.

Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.

## <a name="defining-the-cmdlet"></a>De cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is. (Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

Hier volgt de definitie voor deze `Get-Proc` cmdlet. Details van deze definitie vindt u in [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Para meters definiëren

Als dat nodig is, moet uw cmdlet para meters definiëren voor het verwerken van invoer. Deze Get-Proc-cmdlet definieert een **naam** parameter zoals beschreven in [para meters toevoegen die Command-Line invoer verwerken](adding-parameters-that-process-command-line-input.md).

Hier volgt de parameter declaratie voor de para meter **name** van deze Get-Proc-cmdlet.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>Invoer verwerkings methoden overschrijven

Alle cmdlets moeten ten minste één van de invoer verwerkings methoden van de klasse [System. Management. Automation. cmdlet][] overschrijven. Deze methoden worden besproken bij [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> De cmdlet moet elke record zo onafhankelijk mogelijk verwerken.

Deze Get-Proc-cmdlet overschrijft de methode [System. Management. Automation. cmdlet. ProcessRecord][] om de para meter **name** te verwerken voor de invoer van de gebruiker of een script. Met deze methode worden de processen voor elke aangevraagde proces naam of alle processen opgehaald als er geen naam is opgegeven. Details van deze onderdrukking zijn gegeven bij [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Dingen die u moet onthouden bij het rapporteren van fouten

Het object [System. Management. Automation. ErrorRecord][] dat door de cmdlet wordt door gegeven tijdens het schrijven van een fout, vereist een uitzonde ring op de kern. Volg de .NET-richt lijnen bij het bepalen van de uitzonde ring die moet worden gebruikt.
Als de fout semantisch hetzelfde is als een bestaande uitzonde ring, moet de cmdlet deze uitzonde ring gebruiken of afleiden. Anders moet het een nieuwe uitzonde ring of uitzonderings hiërarchie rechtstreeks vanuit de klasse [System. Exception][] worden afgeleid.

Houd bij het maken van fout-id's (toegankelijk via de eigenschap FullyQualifiedErrorId van de klasse ErrorRecord) het volgende in acht.

- Gebruik teken reeksen die zijn gericht op diagnostische doel einden, zodat u bij het controleren van de volledig gekwalificeerde id kunt bepalen wat de fout is en waar de fout vandaan komt.

- Een goed gevormde, volledig gekwalificeerde fout-id kan er als volgt uitzien.

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

In het vorige voor beeld wordt met de fout-id (het eerste token) aangegeven wat de fout is en het resterende deel geeft aan waar de fout vandaan komt.

- Voor complexere scenario's kan de fout-id een token gescheiden door een punt zijn dat bij inspectie kan worden geparseerd. Hierdoor kunt u de onderdelen van de fout-id en de fout-id en fout categorie als vertakking hebben.

De cmdlet moet specifieke fout-id's toewijzen aan verschillende code paden. Houd de volgende informatie in acht voor het toewijzen van fout-id's:

- Een fout-id moet constant blijven gedurende de levens cyclus van de cmdlet. Wijzig de semantiek van een fout-id tussen de cmdlet-versies niet.
- Gebruik tekst voor een fout-id die tersely overeenkomt met de fout die wordt gerapporteerd. Gebruik geen spaties of lees tekens.
- Laat uw cmdlet alleen fout-id's genereren die kunnen worden gereproduceerd. Er mag bijvoorbeeld geen id worden gegenereerd die een proces-id bevat. Fout-id's zijn alleen nuttig voor gebruikers wanneer ze overeenkomen met id's die worden gezien door andere gebruikers die hetzelfde probleem ondervinden.

Niet-verwerkte uitzonde ringen worden niet in de volgende omstandigheden door Power shell gedetecteerd:

- Als een cmdlet een nieuwe thread maakt en de code die in die thread wordt uitgevoerd, een onverwerkte uitzonde ring genereert, wordt de fout niet onderschept door Power shell en wordt het proces beëindigd.
- Als een object code bevat in de Destruct-of Dispose-methoden die een niet-verwerkte uitzonde ring veroorzaakt, wordt de fout niet onderschept door Power shell en wordt het proces beëindigd.

## <a name="reporting-nonterminating-errors"></a>Niet-afsluit fouten rapporteren

Een van de invoer verwerkings methoden kan een niet-afsluit fout melden aan de uitvoer stroom met behulp van de methode [System. Management. Automation. cmdlet. WriteError][] .

Hier volgt een code voorbeeld van deze Get-Proc-cmdlet die de aanroep van [System. Management. Automation. cmdlet. WriteError][] in de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord][] illustreert. In dit geval wordt de aanroep gedaan als de cmdlet geen proces voor een opgegeven proces-id kan vinden.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Wat u moet weten over het schrijven van niet-afsluit fouten

Voor een niet-afsluit fout moet de cmdlet een specifieke fout-id genereren voor elk specifiek invoer object.

Een cmdlet moet regel matig de Power shell-actie wijzigen die is geproduceerd door een niet-afsluit fout. U kunt dit doen door de `ErrorAction` `ErrorVariable` para meters en te definiëren. Bij het definiëren `ErrorAction` van de para meter geeft de cmdlet de gebruikers opties [System. Management. Automation. ActionPreference][], kunt u ook rechtstreeks van invloed zijn op de actie door de variabele in te stellen `$ErrorActionPreference` .

Met de-cmdlet kunnen niet-afsluit fouten worden opgeslagen in een variabele met behulp `ErrorVariable` van de para meter, die niet wordt beïnvloed door de instelling van `ErrorAction` . Fouten kunnen worden toegevoegd aan een bestaande fout variabele door een plus teken (+) toe te voegen aan het begin van de naam van de variabele.

## <a name="code-sample"></a>Code voorbeeld

Zie GetProcessSample04-voor [beeld](./getprocesssample04-sample.md)voor de volledige C#-voorbeeld code.

## <a name="define-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Power shell geeft informatie door over cmdlets met behulp van .NET-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. We gaan de voor beeld-Get-Proc-cmdlet testen om te zien of er een fout melding wordt weer gegeven:

- Start Power shell en gebruik de cmdlet Get-Proc om de processen met de naam TEST op te halen.

  ```powershell
  get-proc -name test
  ```

  De volgende uitvoer wordt weer gegeven.

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>Zie ook

[Parameters toevoegen die pijplijninvoer verwerken](./adding-parameters-that-process-pipeline-input.md)

[Para meters toevoegen die Command-Line invoer verwerken](./adding-parameters-that-process-command-line-input.md)

[Uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)

[Object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Naslaginformatie over Windows PowerShell](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System. Management. Automation. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
