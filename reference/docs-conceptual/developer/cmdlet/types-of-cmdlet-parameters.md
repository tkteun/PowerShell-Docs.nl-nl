---
ms.date: 09/13/2016
ms.topic: reference
title: Typen cmdlet-parameters
description: Typen cmdlet-parameters
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660492"
---
# <a name="types-of-cmdlet-parameters"></a>Typen cmdlet-parameters

In dit onderwerp worden de verschillende typen para meters beschreven die u in cmdlets kunt declareren. Cmdlet-para meters kunnen positioneel, benoemde, required, optional of switch-para meters zijn.

## <a name="positional-and-named-parameters"></a>Positionele en benoemde para meters

Alle cmdlet-para meters hebben de naam of positionele para meters. Voor een benoemde para meter moet u de parameter naam en het argument typen bij het aanroepen van de cmdlet. Een positionele para meter vereist alleen dat u de argumenten in relatieve volg orde typt. Het systeem wijst vervolgens het eerste ongenoemde argument toe aan de eerste positie parameter. Het systeem wijst het tweede ongenoemde argument toe aan de tweede niet-genaamde para meter, enzovoort. Standaard zijn alle cmdlet-para meters benoemde para meters.

Als u een benoemde para meter wilt definiëren, laat u het `Position` sleutel woord in de declaratie van het **parameter** kenmerk weg, zoals wordt weer gegeven in de volgende parameter declaratie.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Als u een positionele para meter wilt definiëren, voegt u het `Position` tref woord toe aan de declaratie van het parameter kenmerk en geeft u een positie op. In het volgende voor beeld `UserName` wordt de para meter gedeclareerd als een positionele para meter met positie 0. Dit betekent dat het eerste argument van de aanroep automatisch wordt gebonden aan deze para meter.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Goede cmdlet-ontwerp beveelt aan dat de meest gebruikte para meters worden gedeclareerd als positionele para meters, zodat de gebruiker de naam van de para meter niet hoeft in te voeren wanneer de cmdlet wordt uitgevoerd.

Positionele en benoemde para meters accepteren enkelvoudige argumenten of meerdere argumenten, gescheiden door komma's. Meerdere argumenten zijn alleen toegestaan als de para meter een verzameling accepteert, zoals een matrix met teken reeksen. U kunt positionele en benoemde para meters in dezelfde cmdlet combi neren. In dit geval haalt het systeem eerst de benoemde argumenten op en probeert vervolgens de resterende niet-benoemde argumenten toe te wijzen aan de positionele para meters.

De volgende opdrachten tonen de verschillende manieren waarop u één en meerdere argumenten kunt opgeven voor de para meters van de `Get-Command` cmdlet. U ziet dat in de laatste twee voor beelden **-name** niet moet worden opgegeven omdat de `Name` para meter is gedefinieerd als een positionele para meter.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Verplichte en optionele para meters

U kunt ook cmdlet-para meters definiëren als verplichte of optionele para meters. (Er moet een verplichte para meter worden opgegeven voordat de Windows Power shell-runtime de cmdlet aanroept.)  Standaard worden para meters gedefinieerd als optioneel.

Als u een verplichte para meter wilt definiëren, voegt u het `Mandatory` sleutel woord in de declaratie van het parameter kenmerk toe en stelt u het in op `true` , zoals wordt weer gegeven in de volgende parameter declaratie.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Als u een optionele para meter wilt definiëren, laat u het `Mandatory` sleutel woord in de declaratie van het **parameter** kenmerk weg, zoals wordt weer gegeven in de volgende parameter declaratie.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Switch parameters

Windows Power shell biedt een [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -type waarmee u een para meter kunt definiëren waarvan de waarde automatisch wordt ingesteld `false` als de para meter niet wordt opgegeven wanneer de cmdlet wordt aangeroepen. Als dat mogelijk is, gebruikt u switch-para meters in plaats van Boole-para meters.

Bekijk het volgende voor beeld. Verschillende Windows Power shell-cmdlets geven standaard geen uitvoer object omlaag in de pijp lijn. Deze cmdlets hebben echter een `PassThru` Switch parameter die het standaard gedrag overschrijft. Als de `PassThru` para meter wordt opgegeven wanneer deze cmdlets worden aangeroepen, retourneert de cmdlet een uitvoer object naar de pijp lijn.

Als u de para meter nodig hebt om een standaard waarde te hebben `true` als de para meter niet is opgegeven in de aanroep, overweeg dan om de gevoel van de para meter te omkeren. Voor het voor beeld moet u in plaats van het parameter kenmerk in te stellen op een Booleaanse waarde van `true` , de eigenschap declareren als het type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) en vervolgens de standaard waarde van de para meter in te stellen op `false` .

Als u een para meter switch wilt definiëren, declareert u de eigenschap als het type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , zoals wordt weer gegeven in het volgende voor beeld.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Als u de cmdlet wilt uitvoeren op de para meter wanneer deze is opgegeven, gebruikt u de volgende structuur binnen een van de invoer verwerkings methoden.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
