---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250593"
---
# New-WebServiceProxy

## SAMENVATTING
Hiermee maakt u een Web Service proxy-object waarmee u de webservice in Power shell kunt gebruiken en beheren.

## SYNTAXIS

### Referenties (standaard)

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### Referentie

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### UseDefaultCredential

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## BESCHRIJVING

`New-WebServiceProxy`Met de cmdlet kunt u een webservice in Power shell gebruiken. Met de cmdlet maakt u verbinding met een webservice en maakt u een Web Service proxy-object in Power shell. U kunt het proxy-object gebruiken om de webservice te beheren.

Een webservice is een XML-programma waarmee gegevens via een netwerk worden uitgewisseld, met name via internet. Het Microsoft .NET Framework biedt Web Service proxy-objecten die de webservice vertegenwoordigen als een .NET Framework-object.

## VOORBEELDEN

### Voor beeld 1: een proxy maken voor een webservice

In dit voor beeld wordt een .NET Framework proxy van de rekenmachine-webservice gemaakt in Windows Power shell.

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### Voor beeld 2: een proxy maken voor een webservice en naam ruimte en klasse opgeven

In dit voor beeld wordt de `New-WebServiceProxy` cmdlet gebruikt om een .NET Framework proxy van de rekenmachine-webservice te maken.

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

De opdracht gebruikt de **URI** -para meter om de URI en de para meters van de **naam ruimte** en **klasse** op te geven om de naam ruimte en klasse van het object op te geven.

### Voor beeld 3: methoden van een webserviceproxy weer geven

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

In dit voor beeld wordt de `Get-Member` cmdlet gebruikt om de methoden van het object Web Service proxy in de variabele weer te geven `$calc` . We gebruiken deze methoden in het volgende voor beeld.

U ziet dat de **TypeName** van het proxy-object, WebServiceProxy, de naam ruimte en klassen namen weerspiegelt die in het vorige voor beeld zijn opgegeven.

### Voor beeld 4: een webserviceproxy gebruiken

```powershell
PS> $calc.Multiply(6,7)
42
```

In dit voor beeld wordt de webserviceproxy gebruikt die is opgeslagen in de `$calc` variabele. De opdracht maakt gebruik van de **vermenigvuldigings** methode van de proxy.

## PARAMETERS

### -Klasse

Hiermee geeft u een naam op voor de proxy klasse die door de cmdlet wordt gemaakt voor de webservice. De waarde van deze para meter wordt samen met de **naam ruimte** parameter gebruikt om een volledig gekwalificeerde naam voor de klasse op te geven. De standaard waarde wordt gegenereerd op basis van de URI (Uniform Resource Identifier).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker. Dit is een alternatief voor het gebruik van de para meter **UseDefaultCredential** .

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u een naam ruimte voor de nieuwe klasse op.

De waarde van deze para meter wordt samen met de waarde van de para meter **Class** gebruikt om een volledig gekwalificeerde naam voor de klasse te genereren. De standaard waarde is **micro soft. Power shell. commands. NewWebserviceProxy. AutogeneratedTypes** plus een type dat is gegenereerd op basis van de URI.

U kunt de waarde van de **naam ruimte** parameter instellen, zodat u toegang hebt tot meerdere webservices die dezelfde naam hebben.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -URI

Hiermee geeft u de URI van de webservice. Voer een URI of het pad en de bestands naam in van een bestand dat een service beschrijving bevat.

De URI moet een `.asmx` pagina of een pagina retour neren die een service beschrijving retourneert. Als u een service beschrijving wilt retour neren van een webservice die is gemaakt met behulp van ASP.NET, voegt u '? ' toe? WSDL ' naar de URL van de webservice (bijvoorbeeld `http://www.contoso.com/MyWebService.asmx?WSDL` ).

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredential

Geeft aan dat deze cmdlet de standaard referentie gebruikt. Met deze cmdlet wordt de eigenschap **UseDefaultCredential** in het resulterende proxy-object ingesteld op True. Dit is een alternatief voor het gebruik van de para meter **Credential** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Een Web Service proxy-object

Met deze cmdlet wordt een object van een webservice-proxy geretourneerd. De naam ruimte en klasse van het object worden bepaald door de para meters van de opdracht. De standaard waarde wordt gegenereerd op basis van de invoer-URI.

## OPMERKINGEN

`New-WebServiceProxy` maakt gebruik van de klasse **System .net. webclient** om de opgegeven webservice te laden.

## GERELATEERDE KOPPELINGEN

[New-Service](New-Service.md)
