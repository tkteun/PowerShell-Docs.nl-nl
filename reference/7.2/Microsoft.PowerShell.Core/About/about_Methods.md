---
description: Hierin wordt beschreven hoe u methoden gebruikt om acties uit te voeren voor objecten in Power shell.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 35eaafcec5d645be6fe88f506bc0971344406273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705971"
---
# <a name="about-methods"></a>Over methoden

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u methoden gebruikt om acties uit te voeren voor objecten in Power shell.

## <a name="long-description"></a>Lange beschrijving

Power shell gebruikt objecten om de items in de gegevens archieven of de status van de computer weer te geven. File info-objecten vertegenwoordigen bijvoorbeeld de bestanden in bestandssysteem stations en ProcessInfo-objecten die de processen op de computer vertegenwoordigen.

Objecten hebben eigenschappen die gegevens over het object opslaan en methoden waarmee u het object kunt wijzigen.

Een ' methode ' is een set instructies waarmee u een actie opgeeft die u op het object kunt uitvoeren. Het `FileInfo` object bevat bijvoorbeeld de `CopyTo` methode waarmee het bestand dat het object vertegenwoordigt, wordt gekopieerd `FileInfo` .

Als u de methoden van een object wilt ophalen, gebruikt u de- `Get-Member` cmdlet. Gebruik de eigenschap **member type** met de waarde ' method '. Met de volgende opdracht worden de methoden van proces objecten opgehaald.

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

Als u een methode van een object wilt uitvoeren of ' invoke ', typt u een punt (.), de naam van de methode en een verzameling van haakjes "()". Als de methode argumenten heeft, plaatst u de argument waarden tussen de haakjes. De haakjes zijn vereist voor elke methode aanroep, zelfs wanneer er geen argumenten zijn. Als de methode meerdere argumenten heeft, moeten ze worden gescheiden door komma's.

Met de volgende opdracht wordt bijvoorbeeld de methode Kill van processen aangeroepen om het klad blok-proces op de computer te beëindigen.

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

Dit voor beeld kan worden inge kort door de bovenstaande instructies te combi neren.

```powershell
(Get-Process Notepad).Kill()
```

De `Get-Process` opdracht bevindt zich tussen haakjes om ervoor te zorgen dat deze wordt uitgevoerd voordat de Kill-methode wordt aangeroepen. De `Kill` methode wordt vervolgens aangeroepen voor het geretourneerde `Process` object.

Een andere zeer nuttige methode is de `Replace` methode van teken reeksen. De `Replace` -methode vervangt tekst in een teken reeks. In het onderstaande voor beeld kan de punt (.) direct na het einde van de teken reeks worden geplaatst.

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

Zoals in de vorige voor beelden wordt weer gegeven, kunt u een methode aanroepen voor een object dat u krijgt met behulp van een opdracht, een object in een variabele of alles wat resulteert in een object (bijvoorbeeld een teken reeks tussen aanhalings tekens).

Vanaf Power Shell 4,0 wordt de methode aanroep met behulp van dynamische methode namen ondersteund.

### <a name="learning-about-methods"></a>Leren over methoden

Als u definities van de methoden van een object wilt vinden, gaat u naar Help-onderwerp voor het object type en zoekt u de pagina methoden. De volgende pagina beschrijft bijvoorbeeld de methoden van proces objecten [System. Diagnostics. process](/dotnet/api/system.diagnostics.process#methods).

U kunt de argumenten van een methode bepalen door de methode definitie te bekijken, zoals het syntaxis diagram van een Power shell-cmdlet.

Een methode definitie kan een of meer methode-hand tekeningen hebben, zoals de parameter sets van Power shell-cmdlets. De hand tekeningen bevatten alle geldige indelingen van opdrachten om de methode aan te roepen.

De `CopyTo` methode van de `FileInfo` klasse bevat bijvoorbeeld de volgende twee hand tekeningen voor de methode:

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

Bij de eerste hand tekening van de methode wordt de naam van het doel bestand (en een pad) gebruikt. In het volgende voor beeld wordt de eerste `CopyTo` methode gebruikt om het `Final.txt` bestand naar de map te kopiëren `C:\Bin` .

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> In tegens telling tot de _argument_ modus van Power shell, worden object methoden uitgevoerd in de _expressie_ modus, een Pass-Through-bewerking naar het .NET Framework waarin Power shell is gebouwd. In _expressie_ modus **bareword** argumenten (teken reeksen zonder aanhalings tekens) zijn niet toegestaan. U kunt dit verschil zien wanneer u een pad gebruikt als een para meter, vergeleken met het pad als een argument. Meer informatie over het parseren van modi vindt u in [about_Parsing](about_Parsing.md)

De tweede methode handtekening neemt de naam van het doel bestand en een Booleaanse waarde die bepaalt of het doel bestand moet worden overschreven als het al bestaat.

In het volgende voor beeld wordt de tweede `CopyTo` methode gebruikt om het `Final.txt` bestand naar de map te kopiëren `C:\Bin` en om bestaande bestanden te overschrijven.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a>Methoden van scalaire objecten en verzamelingen

De methoden van een object (' scalair ') van een bepaald type zijn vaak anders dan de methoden van een verzameling objecten van hetzelfde type.

Elk proces heeft bijvoorbeeld een `Kill` methode, maar een verzameling processen heeft geen Kill-methode.

Vanaf Power Shell 3,0 probeert Power shell script fouten te voor komen die het resultaat zijn van de verschillende methoden van scalaire objecten en verzamelingen.

Als u een verzameling verzendt, maar een methode aanvraagt die alleen voor één (' scalaire ') objecten bestaat, roept Power shell de methode aan voor elk object in de verzameling.

Als de methode bestaat voor de afzonderlijke objecten en op de verzameling, wordt alleen de methode van de verzameling aangeroepen.

Deze functie werkt ook voor eigenschappen van scalaire objecten en verzamelingen. Zie [about_Properties](about_Properties.md)voor meer informatie.

### <a name="examples"></a>Voorbeelden

In het volgende voor beeld wordt de methode **Kill** van afzonderlijke proces objecten in een verzameling objecten uitgevoerd.

Met de eerste opdracht worden drie exemplaren van het klad blok-proces gestart. `Get-Process` Hiermee haalt u alle drie de exemplaren van het klad blok-proces en slaat u deze op in de `$p` variabele.

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

Met de volgende opdracht wordt de methode **Kill** uitgevoerd voor alle drie de processen in de `$p` variabele. Deze opdracht werkt ook als een verzameling processen geen `Kill` methode heeft.

```powershell
$p.Kill()
Get-Process Notepad
```

De `Get-Process` opdracht bevestigt dat de `Kill` methode heeft gewerkt.

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

Dit voor beeld is functioneel equivalent aan het gebruik `Foreach-Object` van de cmdlet om de methode uit te voeren voor elk object in de verzameling.

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>ForEach en where-methoden

Vanaf Power Shell 4,0 wordt verzamelings filtering met behulp van een methode syntaxis ondersteund. Hierdoor kunnen twee nieuwe methoden worden gebruikt voor het verwerken van verzamelingen `ForEach` en `Where` .

Meer informatie over deze methoden vindt u in [about_arrays](about_arrays.md)

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>Aanroepen van een specifieke methode wanneer meerdere Overloads bestaan

Houd rekening met het volgende scenario bij het aanroepen van .NET-methoden. Als een methode een object aanneemt, maar een overbelasting heeft via een interface die een meer specifiek type heeft, kiest Power shell de methode die het object accepteert, tenzij u het expliciet naar die interface hebt gecast.

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

In dit voor beeld is de minder specifieke `object` overbelasting van de **balk** methode gekozen.

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

In dit voor beeld geven we de methode voor de interface **IFoo** om de meer specifieke overbelasting van de methode **Bar** te selecteren.

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a>Zie ook

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)

