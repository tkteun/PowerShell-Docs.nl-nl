---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189030"
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SAMENVATTING

Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell® Web Access.

## <a name="syntax"></a>SYNTAXIS

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regel
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell Web Access.

## <a name="parameters"></a>PARAMETERS

### <a name="-force"></a>-Force

De cmdlet uitvoert zonder dat om bevestiging wordt gevraagd. Standaard wordt de cmdlet gevraagd om bevestiging voordat u doorgaat.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Hiermee geeft u de id's van een of meer regels te verwijderen.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue, ByPropertyName)       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regel &lt;PswaAuthorizationRule\[\]&gt;

Hiermee geeft u de regels te verwijderen.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue)                       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-confirm"></a>-Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

|||
|-|-|
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | onjuist                                |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-whatif"></a>-WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

|||
|-|-|
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | onjuist                                |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.
Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INVOER

### <a name="int"></a>int\[\]

Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.

## <a name="outputs"></a>UITVOER

Deze cmdlet produceert geen uitvoer.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld verwijdert u de autorisatieregel met een ID van *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>Voorbeeld 2 {.subHeading #example-2}

In dit voorbeeld verwijdert alle autorisatieregels en bevestiging van de gebruiker is ook vereist.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)