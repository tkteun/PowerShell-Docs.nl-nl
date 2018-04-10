---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: pswaauthorizationrule ophalen
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Retourneert een set met autorisatieregels van de Windows PowerShell® Web Access.

## <a name="syntax"></a>Syntaxis

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Naam
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Get-PswaAuthorizationRule** cmdlet retourneert een set met autorisatieregels van de Windows PowerShell® Web Access.
Als noch de **Id** parameter noch de **RuleName** parameter wordt opgegeven, wordt deze cmdlet geeft een lijst van alle regels. De **Id** parameter kan worden gebruikt om de resultaten te filteren.

## <a name="parameters"></a>PARAMETERS

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Hiermee geeft u de id's van de regels die deze cmdlet moet ontvangen. Als er geen id's zijn opgegeven, retourneert deze cmdlet alle autorisatieregels.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue, ByPropertyName)       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

Hiermee worden de namen van autorisatieregels om op te halen. Deze parameter retourneert alle regels waarmee exact overeenkomen met de namen van de regel van de tekenreeksen in deze matrix.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue, ByPropertyName)       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.
Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INVOER

### <a name="int"></a>int\[\]

Deze cmdlet accepteert een matrix van gehele getallen of een matrix van tekenreekswaarden als invoer.

### <a name="string"></a>Tekenreeks\[\]

Deze cmdlet accepteert een matrix van gehele getallen of een matrix van tekenreekswaarden als invoer.

## <a name="outputs"></a>OUTPUTS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Deze cmdlet produceert een PswaAuthorizationRule-object als uitvoer.


## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld haalt alle regels.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld wordt een regel met een ID van *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>Voorbeeld 3 {#example-3 .subHeading}

In dit voorbeeld ziet u hoe de cmdlet accepteert een waarde van de pijplijn.
Een regel-id en de naam van een regel worden doorgegeven in deze cmdlet.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)