---
ms.date: 09/13/2016
ms.topic: reference
title: Een cmdlet maken om toegang te krijgen tot een gegevensarchief
description: Een cmdlet maken om toegang te krijgen tot een gegevensarchief
ms.openlocfilehash: d6ae4779a96b0789f11952a1d66bb96a394c3211
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668181"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Een cmdlet maken om toegang te krijgen tot een gegevensarchief

In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee u opgeslagen gegevens kunt openen via een Windows Power shell-provider. Dit type cmdlet maakt gebruik van de Windows Power shell-provider infrastructuur van de Windows Power shell-runtime en de cmdlet-klasse moet daarom worden afgeleid van de basis klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

Met de cmdlet Select-Str die hier wordt beschreven, kunt u teken reeksen in een bestand of object zoeken en selecteren. De patronen die worden gebruikt om de teken reeks te identificeren, kunnen expliciet worden opgegeven via de `Path` para meter van de cmdlet of impliciet door de `Script` para meter.

De cmdlet is ontworpen voor het gebruik van een Windows Power shell-provider die is afgeleid van [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Met de cmdlet kan bijvoorbeeld de bestandssysteem provider worden opgegeven of de provider van de variabele die wordt verschaft door Windows Power shell. Zie [uw Windows Power shell-provider ontwerpen](../prog-guide/designing-your-windows-powershell-provider.md)voor meer informatie AboutWindows Power shell-providers.

## <a name="defining-the-cmdlet-class"></a>De cmdlet-klasse definiëren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Deze cmdlet detecteert bepaalde teken reeksen, dus de naam van de term die u hier kiest, is ' Select ', gedefinieerd door de klasse [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) . De naam van het zelfstandige zelfstandig woord "str" wordt gebruikt omdat de cmdlet op teken reeksen reageert. Houd er rekening mee dat het cmdlet-werk woord en de naam van het zelfstandigen worden weer gegeven in de naam van de cmdlet-klasse. Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

De .NET-klasse voor deze cmdlet moet worden afgeleid van de basis klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , omdat deze de ondersteuning biedt die nodig is voor de Windows Power shell-runtime om de infra structuur van de Windows Power shell-provider beschikbaar te maken. Houd er rekening mee dat deze cmdlet ook gebruikmaakt van de .NET Framework reguliere expressies klassen, zoals [System. Text. RegularExpressions. regex](/dotnet/api/System.Text.RegularExpressions.Regex).

De volgende code is de klassen definitie voor deze Select-Str-cmdlet.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Met deze cmdlet wordt een standaard parameterset gedefinieerd door het `DefaultParameterSetName` sleutel woord kenmerk toe te voegen aan de klassen declaratie. De standaard parameterset `PatternParameterSet` wordt gebruikt wanneer de `Script` para meter niet is opgegeven. Zie de `Pattern` `Script` para meter en in de volgende sectie voor meer informatie over deze para meter.

## <a name="defining-parameters-for-data-access"></a>Para meters definiëren voor gegevens toegang

Met deze cmdlet worden verschillende para meters gedefinieerd waarmee de gebruiker opgeslagen gegevens kan openen en onderzoeken. Deze para meters bevatten een `Path` para meter die de locatie van het gegevens archief aangeeft, een `Pattern` para meter die het patroon opgeeft dat moet worden gebruikt in de zoek opdracht, en verschillende andere para meters die ondersteuning bieden voor de manier waarop de zoek opdracht wordt uitgevoerd.

> [!NOTE]
> Zie [para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md)voor meer informatie over de basis principes van het definiëren van para meters.

### <a name="declaring-the-path-parameter"></a>De para meter Path declareren

Voor het zoeken naar het gegevens archief moet deze cmdlet een Windows Power shell-pad gebruiken om de Windows Power shell-provider te identificeren die is ontworpen voor toegang tot het gegevens archief. Daarom wordt een `Path` para meter van het type teken reeks matrix gedefinieerd om de locatie van de provider aan te geven.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Houd er rekening mee dat deze para meter deel uitmaakt van twee verschillende parameter sets en dat deze een alias heeft.

Twee [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -kenmerken declareren dat de `Path` para meter hoort bij de `ScriptParameterSet` `PatternParameterSet` . Zie [para meter sets toevoegen aan een cmdlet](./adding-parameter-sets-to-a-cmdlet.md)voor meer informatie over parameter sets.

Het kenmerk [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) declareert een `PSPath` alias voor de `Path` para meter. Het declareren van deze alias wordt sterk aanbevolen voor consistentie met andere cmdlets die toegang hebben tot Windows Power shell-providers. Zie voor meer informatie aboutWindows Power shell-paden ' Power shell Path-concepten ' in de werking van [Windows Power shell](/previous-versions//ms714658(v=vs.85)).

### <a name="declaring-the-pattern-parameter"></a>De para meter pattern declareren

Met deze cmdlet `Pattern` wordt een para meter gedeclareerd die bestaat uit een matrix met teken reeksen om de patronen op te geven waarnaar moet worden gezocht. Er wordt een positief resultaat geretourneerd wanneer een van de patronen in de gegevens opslag is gevonden. Houd er rekening mee dat deze patronen kunnen worden gecompileerd in een matrix met gecompileerde reguliere expressies of een matrix met Joker teken patronen die worden gebruikt voor letterlijke Zoek opdrachten.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Als deze para meter is opgegeven, gebruikt de cmdlet de standaard parameterset `PatternParameterSet` . In dit geval gebruikt de cmdlet de patronen die u hier opgeeft om teken reeksen te selecteren. De `Script` para meter daarentegen kan ook worden gebruikt om een script op te geven dat de patronen bevat. `Script`Met de `Pattern` para meters en worden twee afzonderlijke parameter sets gedefinieerd, zodat ze elkaar wederzijds uitsluiten.

### <a name="declaring-search-support-parameters"></a>Zoeken naar ondersteunings parameters declareren

Deze cmdlet definieert de volgende ondersteunings parameters die kunnen worden gebruikt om de zoek mogelijkheden van de cmdlet te wijzigen.

`Script`Met de para meter wordt een script blok opgegeven dat kan worden gebruikt om een alternatief zoek mechanisme voor de cmdlet op te geven. Het script moet de patronen bevatten die worden gebruikt voor het vergelijken en retour neren van een [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -object. Houd er rekening mee dat deze para meter ook de unieke para meter is waarmee de `ScriptParameterSet` parameterset wordt geïdentificeerd. Wanneer de Windows Power shell-runtime deze para meter ziet, worden alleen para meters gebruikt die bij de `ScriptParameterSet` ingestelde para meter horen.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

De `SimpleMatch` para meter is een para meter switch die aangeeft of de cmdlet expliciet overeenkomt met de patronen die worden verstrekt. Wanneer de gebruiker de para meter op de opdracht regel ( `true` ) opgeeft, gebruikt de cmdlet de patronen zoals ze worden opgegeven. Als de para meter niet is opgegeven ( `false` ), gebruikt de cmdlet reguliere expressies. De standaard waarde voor deze para meter is `false` .

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

De `CaseSensitive` para meter is een switch parameter die aangeeft of een hoofdletter gevoelige zoek opdracht wordt uitgevoerd. Wanneer de gebruiker de para meter opgeeft op de opdracht regel ( `true` ), controleert de cmdlet op de hoofd letters en kleine letters van de tekens bij het vergelijken van patronen. Als de para meter niet is opgegeven ( `false` ), maakt de cmdlet geen onderscheid tussen hoofd letters en kleine letters. Bijvoorbeeld "MijnBestand" en "myfile" worden beide geretourneerd als positieve treffers. De standaard waarde voor deze para meter is `false` .

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

`Exclude`Met de `Include` para meters en worden items geïdentificeerd die expliciet zijn uitgesloten van of opgenomen in de zoek opdracht. Standaard doorzoekt de cmdlet alle items in het gegevens archief. Als u echter de zoek opdracht wilt beperken die door de cmdlet wordt uitgevoerd, kunt u deze para meters gebruiken om expliciet items te geven die moeten worden opgenomen in de zoek opdracht of worden wegge laten.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Parameter sets declareren

Deze cmdlet gebruikt twee parameter sets ( `ScriptParameterSet` en `PatternParameterSet` de standaard instelling) als de namen van twee parameter sets die worden gebruikt in gegevens toegang. `PatternParameterSet` is de standaard parameterset en wordt gebruikt wanneer de `Pattern` para meter is opgegeven. `ScriptParameterSet` wordt gebruikt wanneer de gebruiker een alternatief zoek mechanisme opgeeft via de `Script` para meter. Zie [para meter sets toevoegen aan een cmdlet](./adding-parameter-sets-to-a-cmdlet.md)voor meer informatie over parameter sets.

## <a name="overriding-input-processing-methods"></a>Invoer verwerkings methoden overschrijven

Cmdlets moeten een of meer van de invoer verwerkings methoden voor de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) overschrijven. Zie [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)voor meer informatie over de invoer methoden.

Deze cmdlet overschrijft de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) om tijdens het opstarten een matrix van gecompileerde reguliere expressies te maken. Dit verhoogt de prestaties tijdens Zoek opdrachten die geen gebruik maken van eenvoudige overeenkomsten.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Deze cmdlet overschrijft ook de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) om de teken reeks selecties te verwerken die de gebruiker op de opdracht regel maakt. De resultaten van de teken reeks selectie in de vorm van een aangepast object worden geschreven door een persoonlijke **MatchString** -methode aan te roepen.

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Toegang tot inhoud

Uw cmdlet moet de provider openen die is aangegeven door het Windows Power shell-pad, zodat deze toegang heeft tot de gegevens. Het object [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) voor de runs Pace wordt gebruikt voor toegang tot de provider, terwijl de eigenschap [System. Management. Automation. PSCmdlet. Invokeprovider *](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) van de cmdlet wordt gebruikt om de provider te openen. Toegang tot inhoud wordt gegeven door het ophalen van het [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) -object voor de provider die is geopend.

In dit voor beeld Select-Str cmdlet wordt gebruikgemaakt van de eigenschap [System. Management. Automation. Providerintrinsics. content *](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) om de inhoud weer te geven die u wilt scannen. Vervolgens kan de methode [System. Management. Automation. Contentcmdletproviderintrinsics. getreader *](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) worden aangeroepen, waarbij het vereiste Windows Power shell-pad wordt door gegeven.

## <a name="code-sample"></a>Code voorbeeld

De volgende code toont de implementatie van deze versie van deze Select-Str-cmdlet. Houd er rekening mee dat deze code de klasse cmdlet, de persoonlijke methoden die worden gebruikt door de cmdlet en de Windows Power shell-module code die wordt gebruikt voor het registreren van de cmdlet. Zie [buil ding the cmdlet](#defining-the-cmdlet-class)(Engelstalig) voor meer informatie over het registreren van de cmdlet.

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. De volgende procedure kan worden gebruikt om de voor beeld-Select-Str-cmdlet te testen.

1. Start Windows Power shell en zoek in het notitie bestand naar exemplaren van regels met de expressie ".NET". Houd er rekening mee dat de aanhalings tekens rond de naam van het pad alleen vereist zijn als het pad uit meer dan één woord bestaat.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Zoek in het notitie bestand naar exemplaren van regels met het woord ' boven ', gevolgd door andere tekst. De `SimpleMatch` para meter gebruikt de standaard waarde van `false` . De zoek opdracht is hoofdletter gevoelig omdat de `CaseSensitive` para meter is ingesteld op `false` .

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Zoek in het notitie bestand een reguliere expressie als het patroon. De cmdlet zoekt naar alfabetische tekens en spaties tussen haakjes.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Voer een hoofdletter gevoelige zoek opdracht uit voor het notitie bestand voor exemplaren van het woord "para meter".

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Zoek de variabele provider die is geleverd met Windows Power shell voor variabelen met numerieke waarden van 0 tot en met 9.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Gebruik een script blok om in het bestand SelectStrCommandSample.cs te zoeken naar de teken reeks ' pos '. De functie **cmatch** voor het script voert een niet-hoofdletter gevoelige patroon overeenkomst uit.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    De volgende uitvoer wordt weer gegeven.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet maken](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)

[Een cmdlet maken waarmee het systeem wordt gewijzigd](./creating-a-cmdlet-that-modifies-the-system.md)

[Uw Windows Power shell-provider ontwerpen](../prog-guide/designing-your-windows-powershell-provider.md)

[Hoe Windows Power shell werkt](/previous-versions//ms714658(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
