---
title: Toevoegen van niet-afsluitfouten die fouten rapporteren aan uw Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851014"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking

Cmdlets afsluitfouten kunt melden door het aanroepen van de [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode en nog steeds kan functioneren op het huidige invoerobject of verdere inkomende pipeline-objecten. In deze sectie wordt uitgelegd hoe u een cmdlet die afsluitfouten uit de invoer verwerkingsmethoden rapporten maken.

Voor afsluitfouten (evenals afsluitende fouten), de cmdlet moet slagen voor een [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identificeren van de fout. Elke foutrecord wordt geïdentificeerd door een unieke tekenreeks met de naam van de 'fout-id." Naast de-id, de categorie van elke fout die is opgegeven door de constanten zijn gedefinieerd door een [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming. De gebruiker kan zien fouten op basis van hun categorie door in te stellen de `$ErrorView` variabele 'CategoryView'.

Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).

Onderwerpen in deze sectie bevatten het volgende:

- [De Cmdlet definiëren](#Defining-the-Cmdlet)

- [Parameters definiëren](#Defining-Parameters)

- [Invoer verwerking van methoden overschrijven](#Overriding-Input-Processing-Methods)

- [Rapportage afsluitfouten](#Reporting-Nonterminating-Errors)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak](#Define-Object-Types-and-Formatting)

- [Het bouwen van de Cmdlet](#Building-the-Cmdlet)

- [Testen van de Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>De Cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'. (Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

Hier volgt de definitie voor deze cmdlet Get-Proc. Details van deze definitie zijn vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Parameters definiëren

Indien nodig, moet de cmdlet-parameters voor het verwerken van invoer definiëren. Deze cmdlet Get-Proc definieert een `Name` parameter zoals beschreven in [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md).

Hier is de parameterdeclaratie voor de `Name` parameter van deze cmdlet Get-Proc.

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

## <a name="overriding-input-processing-methods"></a>Invoer verwerking van methoden overschrijven

Alle cmdlets moet ten minste één van de invoer voor het verwerken van methoden die door overschrijven de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse. Deze methoden worden besproken in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> De cmdlet moet onafhankelijk mogelijk elke record verwerken.

Deze cmdlet Get-Proc overschrijft de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter voor invoer geleverd door de gebruiker of een script. Deze methode krijgt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven. Details van deze overschrijving worden vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

#### <a name="things-to-remember-when-reporting-errors"></a>Om te onthouden wanneer die fouten rapporteren

De [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object dat de cmdlet wordt doorgegeven tijdens het schrijven van een fout is een uitzondering in de kern vereist. Volg de richtlijnen voor .NET bij het bepalen van de uitzondering te gebruiken. In feite, als de fout semantisch gelijk zijn aan een bestaande uitzondering is, de cmdlet moet gebruiken of afgeleid van de uitzondering. Anders moet afleiden een nieuwe uitzondering of uitzonderingen hiërarchie rechtstreeks vanuit de [System.Exception](/dotnet/api/System.Exception) klasse.

Houd er rekening mee met het volgende bij het maken van fout-id's (toegankelijk via de eigenschap FullyQualifiedErrorId van de klasse ErrorRecord).

- Gebruik tekenreeksen die zijn bedoeld voor diagnostische doeleinden zodat bij de inspectie van de volledig gekwalificeerde id kunt u bepalen wat de fout is en waar de fout die afkomstig zijn uit.

- Als volgt kan een juist opgemaakte volledig gekwalificeerde fout-id zijn.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

U ziet dat in het vorige voorbeeld wordt de fout-id (de eerste token) Hiermee wordt aangegeven wat de fout is en het resterende deel geeft aan waar de fout afkomstig zijn uit.

- Voor complexere scenario's, kan de fout-id een punt van elkaar gescheiden-token dat kan worden geparseerd voor controle zijn. Hiermee kunt dat u ook op de onderdelen van de fout-id, evenals de fout-id en de fout categorie vertakking.

De cmdlet moet specifieke fout-id's toewijzen aan andere codepaden. Houd er rekening mee voor de toewijzing van fout-id's de volgende informatie:

- Een fout-id moet ongewijzigd blijft gedurende de levenscyclus van de cmdlet. De semantiek van een fout-id tussen versies van de cmdlet niet wijzigen.

- Gebruik de tekst voor een fout-id die tersely overeenkomt met de fout wordt gerapporteerd. Gebruik geen spaties of leestekens.

- De cmdlet genereert alleen fout-id's die kunnen worden gereproduceerd hebben. Er moet een id die een proces-id bevat bijvoorbeeld niet gegenereerd. Fout-id's zijn handig om een gebruiker alleen als ze overeenkomen met de id's die zijn zichtbaar voor andere gebruikers hetzelfde probleem ondervindt.

Niet-verwerkte uitzonderingen zijn niet opgepikt door Windows PowerShell in de volgende voorwaarden:

- Als een cmdlet maakt een nieuwe thread en code die wordt uitgevoerd in deze thread een niet-verwerkte uitzondering genereert, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd.

- Als een object heeft de code in de destructor of Dispose methoden die ervoor zorgt een niet-verwerkte uitzondering dat, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd.

## <a name="reporting-nonterminating-errors"></a>Rapportage afsluitfouten

Een van de invoer verwerkingsmethoden kan een nonterminating fout rapporteren aan de uitvoer stream met de [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode. Hier volgt een voorbeeld van deze cmdlet Get-procedure die laat zien van de aanroep van [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) uit binnen de onderdrukking van de [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode. In dit geval wordt de aanroep uitgevoerd als de cmdlet kan een proces voor een opgegeven proces-id niet vinden.

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Om te onthouden over het schrijven van afsluitfouten

Voor een nonterminating fout, moet de cmdlet een specifieke fout-id voor elke specifieke invoerobject genereren.

Een cmdlet moet vaak wijzigen van de Windows PowerShell-actie die wordt geproduceerd door een nonterminating fout. Dit kan worden gedaan door te definiëren de `ErrorAction` en `ErrorVariable` parameters. Als u definieert de `ErrorAction` parameter, de cmdlet geeft de gebruikersopties [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), u kunt ook rechtstreeks van invloed zijn op de actie door in te stellen de `$ErrorActionPreference` variabele.

De cmdlet afsluitfouten kunt opslaan naar een variabele met de `ErrorVariable` parameter, die wordt niet beïnvloed door de instelling van `ErrorAction`. Fouten kunnen worden toegevoegd aan een bestaande variabele van de fout door een plusteken (+) toe te voegen aan het begin van de naam van de variabele.

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [GetProcessSample04 voorbeeld](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieer objecttypen en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten. Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. We gaan de voorbeeld-cmdlet Get-Proc om te zien of er een fout gemeld testen:

- Start Windows PowerShell en gebruik de cmdlet Get-procedure voor het ophalen van de processen met de naam 'TEST'.

    ```powershell
    PS> get-proc -name test
    ```

De volgende uitvoer wordt weergegeven.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Zie ook

[Parameters die proces Pipeline ingevoerd toe te voegen](./adding-parameters-that-process-pipeline-input.md)

[Parameters die opdrachtregel verwerken toe te voegen](./adding-parameters-that-process-command-line-input.md)

[Het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referentie](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
