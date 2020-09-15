---
title: Alles wat u wilt weten over PSCustomObject
description: PSCustomObject is een eenvoudige manier om gestructureerde gegevens te maken.
ms.date: 07/29/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 9a5cab7e662ef89b6565a29079ce1d5a657f94d0
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410135"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>Alles wat u wilt weten over PSCustomObject

`PSCustomObject`s zijn een uitstekend hulp programma om toe te voegen aan de band van uw Power shell-tool. Laten we beginnen met de basis principes en werken op onze manier in de meer geavanceerde functies. Het idee van het gebruik van a `PSCustomObject` is een eenvoudige manier om gestructureerde gegevens te maken. Bekijk het eerste voor beeld en u hebt een beter idee van wat dat betekent.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="creating-a-pscustomobject"></a>Een PSCustomObject maken

Ik ben gek `[PSCustomObject]` op het gebruik van Power shell. Het maken van een bruikbaar object is nog nooit zo eenvoudig geweest.
Daarom ga ik over op alle andere manieren om een object te maken, maar ik moet vermelden dat de meeste van deze voor beelden Power shell v 3.0 en hoger zijn.

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

Deze methode werkt goed voor mij omdat ik hashtabellen gebruik voor vrijwel alles. Er zijn echter momenten waarop Power shell hashtabellen meer lijkt te behandelen als een object. De eerste plaats die u ziet, is het verschil wanneer u wilt gebruiken `Format-Table` of `Export-CSV` en u beseft dat een hashtabel alleen een verzameling sleutel-waardeparen is.

U kunt de waarden vervolgens openen en gebruiken, net zoals u een normaal object zou doen.

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>Een hashtabel converteren

Wist u dat u het onderwerp hebt, maar u hebt wel de volgende handelingen uitgevoerd:

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

Ik wil het object nu vanuit het begin maken, maar er zijn tijden dat u eerst met een hashtabel moet werken. Dit voor beeld werkt omdat de constructor een hashtabel voor de object eigenschappen gebruikt. Een belang rijke opmerking is dat hoewel deze methode werkt, het geen exacte equivalent is. Het grootste verschil is dat de volg orde van de eigenschappen niet wordt behouden.

### <a name="legacy-approach"></a>Verouderde aanpak

U hebt misschien gezien dat mensen `New-Object` aangepaste objecten kunnen maken.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

Op deze manier is het heel wat langzamer, maar dit is mogelijk de beste optie voor vroege versies van Power shell.

### <a name="saving-to-a-file"></a>Opslaan naar een bestand

Ik vind de beste manier om een hashtabel op te slaan in een bestand om het op te slaan als JSON. U kunt deze weer importeren in een `[PSCustomObject]`

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

Ik vind meer manieren voor het opslaan van objecten in een bestand in mijn artikel op [de vele manieren om bestanden te lezen en te schrijven][].

## <a name="working-with-properties"></a>Werken met eigenschappen

### <a name="adding-properties"></a>Eigenschappen toevoegen

U kunt nog steeds nieuwe eigenschappen toevoegen aan uw `PSCustomObject` met `Add-Member` .

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>Eigenschappen verwijderen

U kunt de eigenschappen van een object ook verwijderen.

```powershell
$myObject.psobject.properties.remove('ID')
```

De `psobject` is een verborgen eigenschap waarmee u toegang krijgt tot de meta gegevens van het basis object.

### <a name="enumerating-property-names"></a>Eigenschaps namen opsommen

Soms hebt u een lijst nodig van alle eigenschapnamen van een object.

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

Deze lijst kan ook worden opgehaald van de `psobject` eigenschap.

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>Eigenschappen dynamisch gebruiken

Ik heb al aangegeven dat u rechtstreeks toegang hebt tot eigenschaps waarden.

```powershell
$myObject.Name
```

U kunt een teken reeks gebruiken voor de naam van de eigenschap. deze blijft echter wel werken.

```powershell
$myObject.'Name'
```

We kunnen een extra stap uitvoeren en een variabele voor de naam van de eigenschap gebruiken.

```powershell
$property = 'Name'
$myObject.$property
```

Ik weet dat dat vreemd lijkt, maar het werkt.

### <a name="convert-pscustombobject-into-a-hashtable"></a>PSCustombObject naar een hashtabel converteren

Als u wilt door gaan met de laatste sectie, kunt u de eigenschappen dynamisch door lopen en een hashtabel maken.

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>Testen op Eigenschappen

Als u wilt weten of een eigenschap bestaat, kunt u gewoon controleren of de eigenschap een waarde heeft.

```powershell
if( $null -ne $myObject.ID )
```

Maar als de waarde zou kunnen zijn `$null` en u deze nog steeds moet controleren, kunt u de `psobject.properties` voor IT controleren.

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a>Object methoden toevoegen

Als u een script methode moet toevoegen aan een object, kunt u dit doen met `Add-Member` en een `ScriptBlock` . U moet de `this` automatische variabelen referentie het huidige object gebruiken. Hier is een `scriptblock` om een object in een hashtabel in te scha kelen. (dezelfde code vormen het laatste voor beeld)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

Vervolgens voegen we het toe aan ons object als een script eigenschap.

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

Vervolgens kunnen we onze functie als volgt aanroepen:

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>Objecten versus waardetypen

Met objecten en waardetypen worden variabelen toewijzingen niet op dezelfde manier afgehandeld. Als u waardetypen aan elkaar toewijst, wordt alleen de waarde opgehaald die wordt gekopieerd naar de nieuwe variabele.

```powershell
$first = 1
$second = $first
$second = 2
```

In dit geval `$first` is 1 en `$second` 2.

Object variabelen bevatten een verwijzing naar het daad werkelijke object. Wanneer u één object toewijst aan een nieuwe variabele, verwijzen ze nog steeds naar hetzelfde object.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

Omdat `$third` en `$fourth` naar hetzelfde exemplaar van een object verwijst, `$third.key` zijn beide en `$fourth.Key` 4.

### <a name="psobjectcopy"></a>psobject. Copy ()

Als u een echt exemplaar van een object nodig hebt, kunt u dit klonen.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

Met de kloon maakt u een bestaand exemplaar van het object. Ze hebben nu verschillende exemplaren en zijn `$third.key` 3 en `$fourth.Key` 4 in dit voor beeld.

Ik roep dit een inkomend exemplaar aan omdat als u geneste objecten hebt. (waarbij de eigenschappen andere objecten bevatten). Alleen de waarden op het hoogste niveau worden gekopieerd. De onderliggende objecten verwijzen naar elkaar.

### <a name="pstypename-for-custom-object-types"></a>PSTypeName voor aangepaste object typen

Nu we een object hebben, zijn er nog enkele dingen die u kunt doen. Dit kan bijna niet zo duidelijk zijn. Het eerste wat u moet doen, is een `PSTypeName` . Dit is de meest voorkomende manier waarop ik mensen kan zien:

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

Ik heb onlangs een andere manier ontdekt om dit te doen vanuit dit [bericht door/u/markekraus][]. Ik heb een beetje Blijf spitten en meer posts over het idee van [Adam Bertram][] en [Mike Shepard][] , waar ze over deze aanpak praten, zodat u deze inline kunt definiëren.

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

Ik ben geweldig hoe mooi dit precies in de taal past. Nu we een object met de juiste type naam hebben, kunnen we meer dingen doen.

> [!NOTE]
> U kunt ook aangepaste Power shell-typen maken met behulp van Power shell-klassen. Zie [overzicht van Power shell-klassen](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes)voor meer informatie.

## <a name="using-defaultpropertyset-the-long-way"></a>DefaultPropertySet gebruiken (de lange manier)

Power Shell heeft voor ons besloten welke eigenschappen standaard moeten worden weer gegeven. Veel van de systeem eigen opdrachten hebben een `.ps1xml` [Opmaak bestand][] dat het hoge aantal opheffen. Vanuit dit [bericht van BOE-proxy][]is het een andere manier om dit te doen voor ons aangepaste object met behulp van alleen Power shell. We kunnen het een voor stel geven `MemberSet` om het te gebruiken.

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

Nu wanneer mijn object net in de shell is ingedeeld, worden deze eigenschappen standaard alleen weer gegeven.

### <a name="update-typedata-with-defaultpropertyset"></a>Update-TypeData met DefaultPropertySet

Dit is leuk, maar ik heb onlangs een betere manier gezien wanneer [Power shell is ontkoppeld 2016 met Jeffrey Snover & Daan Jansen][psunplugged]. Jeffrey heeft [Update-TypeData][] gebruikt om de standaard eigenschappen op te geven.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

Dat is zo eenvoudig dat ik dit niet kan onthouden als ik dit bericht niet had als snelle verwijzing. Ik kan nu eenvoudig objecten met veel eigenschappen maken en deze toch een fraaie, overzichtelijke weer gave geven bij het bekijken van de shell. Als ik de andere eigenschappen moet openen of bekijken, zijn ze nog steeds beschikbaar.

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>Update-TypeData met ScriptProperty

Iets anders heb ik van deze video bezig met het maken van script eigenschappen voor objecten. Dit is een goed moment om te wijzen dat dit ook voor bestaande objecten werkt.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

U kunt dit doen voordat het object wordt gemaakt of wanneer het nog steeds wordt uitgevoerd. Zo maakt u dit anders met `Add-Member` een script eigenschap. Wanneer u `Add-Member` de verwijzing eerder gebruikt, bestaat deze alleen op die specifieke instantie van het object. Dit geldt voor alle objecten met deze naam `TypeName` .

## <a name="function-parameters"></a>Functie parameters

U kunt deze aangepaste typen nu gebruiken voor para meters in uw functies en scripts. U kunt deze aangepaste objecten met één functie maken en vervolgens door geven aan andere functies.

```powershell
param( [PSTypeName('My.Object')]$Data )
```

Voor Power shell is vereist dat het object het type is dat u hebt opgegeven. Er wordt een validatie fout gegenereerd als het type niet automatisch overeenkomt met het opslaan van de stap van de test in uw code. Een goed voor beeld van Power shell om te laten zien wat het beste werkt.

### <a name="function-outputtype"></a>Functie output type

U kunt ook een `OutputType` voor uw geavanceerde functies definiëren.

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

De waarde van het kenmerk **output** type is alleen een documentatie opmerking. Het is niet afgeleid van de functie code of vergeleken met de daad werkelijke functie-uitvoer.

De belangrijkste reden voor het gebruik van een uitvoer type is dat meta gegevens over uw functie uw bedoelingen kunnen weer spie gelen. Wat `Get-Command` `Get-Help` u kunt doen met uw ontwikkel omgeving. Als u meer informatie wilt, raadpleegt u de Help voor IT: [about_Functions_OutputTypeAttribute][].

Als u een functie voor het testen van uw functies gebruikt, is het een goed idee om de uitvoer objecten te valideren die overeenkomen met uw **output**type. Dit kan ertoe leiden dat variabelen die net tot de pipe vallen, worden onderschept wanneer dat niet het geval is.

## <a name="closing-thoughts"></a>Afsluitende ideeën

De context van dit was alles `[PSCustomObject]` , maar een groot aantal van deze informatie is van toepassing op objecten in het algemeen.

Ik heb de meeste van deze functies in de door gave gezien, maar u hebt deze nooit gezien als een verzameling gegevens over `PSCustomObject` . Alleen deze afgelopen week heb ik stumbled bij een ander abonnement en was het verbaasd dat ik het nog niet had gezien. Ik wilde al deze ideeën samen stellen, zodat u de foto groter kunt zien en weet wanneer u de mogelijkheid hebt om ze te gebruiken. Ik hoop dat u iets hebt geleerd en een manier kunt vinden om dit in uw scripts te gebruiken.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[post by BOE-proxy]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Opmaak bestand]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[De vele manieren om bestanden te lezen en te schrijven]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[post by/u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam-Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
