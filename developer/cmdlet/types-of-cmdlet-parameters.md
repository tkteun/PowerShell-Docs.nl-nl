---
title: Typen van de Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059572"
---
# <a name="types-of-cmdlet-parameters"></a>Typen cmdlet-parameters

Dit onderwerp beschrijft de verschillende typen parameters die u in de cmdlets aangeven kunt. Cmdlet-parameters worden positionele, met de naam, vereist, optioneel of verwissel de parameters.

## <a name="positional-and-named-parameters"></a>Positionele en benoemde Parameters

Alle cmdlet-parameters zijn benoemde of positionele parameters. Een benoemde parameter is vereist dat u de parameternaam en argument invoeren bij het aanroepen van de cmdlet. Een positionele parameter is alleen vereist dat u de argumenten in de juiste volgorde typen. Het systeem wordt het eerste argument naamloze vervolgens toegewezen aan de eerste positionele parameter. Het systeem het tweede argument naamloze toegewezen aan de tweede naamloze parameter, enzovoort. Standaard worden alle parameters van de cmdlet benoemde parameters.

Voor het definiëren van een benoemde parameter, laat de `Position` sleutelwoord in de **Parameter** declaratie van het kenmerk zoals wordt weergegeven in de volgende parameterdeclaratie.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Voor het definiëren van een positionele parameter toevoegen de `Position` sleutelwoord in de Parameter declaratie van het kenmerk en geef vervolgens een positie. In het volgende voorbeeld wordt de `UserName` parameter is gedeclareerd als een positionele parameter met de positie 0. Dit betekent dat het eerste argument van de aanroep automatisch worden gekoppeld aan deze parameter.

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
> Goede cmdlet ontwerp raadt aan dat de meest gebruikte parameters worden gedeclareerd als positionele parameters, zodat de gebruiker heeft geen naam van de parameter invoeren wanneer de cmdlet wordt uitgevoerd.

Positionele en benoemde parameters accepteren één argumenten of meerdere argumenten gescheiden door komma's. Meerdere argumenten zijn alleen toegestaan als de parameter een verzameling, zoals een matrix met tekenreeksen accepteert. Positionele en benoemde parameters in dezelfde cmdlet kan worden gecombineerd. In dit geval wordt de benoemde argumenten eerst opgehaald en vervolgens probeert toe te wijzen de resterende benoemde argumenten aan de positionele parameters.

De volgende opdrachten tonen de verschillende manieren waarop u en één of meerdere argumenten voor de parameters van opgeven kunt de `Get-Command` cmdlet. U ziet dat in de laatste twee bewakingen, **-naam** hoeft niet te worden opgegeven omdat de `Name` parameter wordt gedefinieerd als een positionele parameter.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Verplichte en optionele Parameters

U kunt ook de cmdlet-parameters definiëren als verplicht of optioneel parameters. (Een verplichte parameter moet worden opgegeven voordat de runtime van de Windows PowerShell de cmdlet aanroept.)  Parameters worden gedefinieerd als optionele standaard.

Toevoegen voor het definiëren van een verplichte parameter, de `Mandatory` sleutelwoord in de Parameter declaratie van het kenmerk en stel deze in op `true`, zoals weergegeven in de volgende parameterdeclaratie.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Voor het definiëren van een optionele parameter, laat de `Mandatory` sleutelwoord in de **Parameter** declaratie van het kenmerk zoals wordt weergegeven in de volgende parameterdeclaratie.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Verwissel de Parameters

Windows PowerShell biedt een [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type waarmee u een parameter definiëren waarvan de waarde automatisch is ingesteld op `false` als de parameter niet wordt opgegeven wanneer de cmdlet is met de naam. Gebruik indien mogelijk de switch-parameters in plaats van Booleaanse parameters.

Houd rekening met het volgende voorbeeld. Standaard worden een object op in de pijplijn in verschillende Windows PowerShell-cmdlets niet geslaagd. Deze cmdlets hebben echter een `PassThru` switch-parameter die het standaardgedrag overschrijft. Als de `PassThru` parameter is opgegeven wanneer deze cmdlets worden aangeroepen, wordt de cmdlet retourneert een uitvoerobject aan de pijplijn.

Als u de parameter een standaardwaarde van `true` als de parameter niet is opgegeven in de aanroep, houd rekening met het gevoel van de parameter omkeren. Voor het voorbeeld in plaats van de parameterkenmerk instelt op een Booleaanse waarde `true`, de eigenschap declareert de [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typt, en stel de standaardwaarde van de parameter `false`.

Voor het definiëren van een switch-parameter, de eigenschap als declareren de [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typt, zoals wordt weergegeven in het volgende voorbeeld.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Als u de cmdlet reageren op de parameter wanneer deze is opgegeven, gebruik de volgende structuur binnen een van de invoer verwerkingsmethoden.

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
