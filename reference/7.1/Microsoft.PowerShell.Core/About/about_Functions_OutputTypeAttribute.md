---
description: Beschrijft een kenmerk dat het type object rapporteert dat door de functie wordt geretourneerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 7cd7f04941077d823bb15d0fa393ca241f38ae3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252046"
---
# <a name="about-functions-outputtypeattribute"></a>Over functies OutputTypeAttribute

## <a name="short-description"></a>KORTE BESCHRIJVING
Beschrijft een kenmerk dat het type object rapporteert dat door de functie wordt geretourneerd.

## <a name="long-description"></a>LANGE BESCHRIJVING

Het kenmerk output type geeft de .NET-typen objecten weer die door de functies worden geretourneerd. U kunt de optionele ParameterSetName-para meter gebruiken om verschillende uitvoer typen voor elke parameterset weer te geven.

Het kenmerk output type wordt ondersteund voor eenvoudige en geavanceerde functies. Het is onafhankelijk van het kenmerk CmdletBinding.

Het kenmerk output type levert de waarde van de eigenschap output type van het object **System. Management. Automation. FunctionInfo** dat door de `Get-Command` cmdlet wordt geretourneerd.

De waarde van het kenmerk output type is alleen een documentatie opmerking. Het is niet afgeleid van de functie code of vergeleken met de daad werkelijke functie-uitvoer. De waarde kan als zodanig onjuist zijn.

## <a name="syntax"></a>SYNTAXIS

Het kenmerk output type van functions heeft de volgende syntaxis:

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

De para meter **ParameterSetName** is optioneel.

U kunt meerdere typen in het kenmerk output type vermelden.

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

U kunt de para meter **ParameterSetName** gebruiken om aan te geven dat verschillende parameter sets verschillende typen retour neren.

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

Plaats de instructies output type-kenmerk in de lijst met kenmerken die voorafgaat aan de `Param` instructie.

In het volgende voor beeld wordt de plaatsing van het kenmerk output type in een eenvoudige functie weer gegeven.

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

In het volgende voor beeld wordt de plaatsing van het kenmerk output type in geavanceerde functies weer gegeven.

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>Voor beeld 1: een functie maken die het output type van de teken reeks bevat

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

Als u de resulterende eigenschap van het uitvoer type wilt zien, gebruikt u de `Get-Command` cmdlet.

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>Voor beeld 2: het uitvoer kenmerk gebruiken om dynamische uitvoer typen aan te duiden

De volgende geavanceerde functie maakt gebruik van het kenmerk output type om aan te geven dat de functie verschillende typen retourneert, afhankelijk van de ingestelde para meters in de functie opdracht.

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>Voor beeld 3: toont wanneer een werkelijke uitvoer afwijkt van het output type

In het volgende voor beeld ziet u dat de waarde van de eigenschap uitvoer type de waarde van het kenmerk output item weergeeft, zelfs wanneer deze onjuist is.

De `Get-Time` functie retourneert een teken reeks die de korte vorm van de tijd in een datetime-object bevat. Met het kenmerk output type wordt echter gerapporteerd dat er een **System. datetime** -object wordt geretourneerd.

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

De- `GetType()` methode bevestigt dat de functie een teken reeks retourneert.

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

De eigenschap output type, die de waarde van het kenmerk output type krijgt, rapporteert dat de functie een **DateTime** -object retourneert.

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>Voor beeld 4: een functie die geen uitvoer mag hebben

In het volgende voor beeld ziet u een aangepaste functie die moet worden uitgevoerd, maar die geen actie retourneert.

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>OPMERKINGEN

De waarde van de eigenschap output type van een **FunctionInfo** -object is een matrix van **System. Management. Automation. PSTypeName** -objecten, die elk de eigenschappen name en type hebben.

Als u alleen de naam van elk uitvoer type wilt ophalen, gebruikt u een opdracht met de volgende notatie.

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

De waarde van de eigenschap output type kan null zijn. Gebruik een null-waarde wanneer de uitvoer geen .NET-type is, zoals een **WMI-** object of een opmaak weergave van een object.

## <a name="see-also"></a>ZIE OOK

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

