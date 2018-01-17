---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Hiermee wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.

## <a name="syntax"></a>SYNTAXIS

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Test-PswaAuthorizationRule** cmdlet wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.
Deze cmdlet kan ook worden gebruikt voor het testen van autorisatieregels om te valideren dat een bepaalde gebruiker, computer of eindpunt toegangsaanvraag is geautoriseerd.
Deze cmdlet evalueert standaard alle regels in het bestand met autorisatieregels.
U kunt echter een subset van regels voor het testen van opgeven.

U kunt deze cmdlet gebruiken om op te lossen verificatiefouten.

De parameters voor deze cmdlet overeen met velden op de pagina van de aanmelding Windows PowerShell® Web Access.

## <a name="parameters"></a>PARAMETERS

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;tekenreeks&gt;

Hiermee geeft u de naam van de computer om te testen.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;tekenreeks&gt;

Geeft de naam van de Windows PowerShell-sessieconfiguratie, ook wel bekend als eindpunt of runspace om te testen.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | 3                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Hiermee geeft u de URI voor het testen van verbinding.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 2                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u gebruiken wilt voor het testen van Windows PowerShell-webtoegang autorisatieregels. Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker. Ophalen van een **PSCredential** -object, dat vereist is voor het testen van autorisatieregels op afstand, voert u de [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regel &lt;PswaAuthorizationRule\[\]&gt;

Hiermee geeft u een subset van regels om te testen. Als deze parameter niet is opgegeven, zijn deze cmdlet van test tegen alle autorisatieregels.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue)                       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;tekenreeks&gt;

Hiermee geeft u de naam van de gebruiker om te testen.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 1                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.
Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INVOER

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Deze cmdlet accepteert een matrix met objecten PswaAuthorizationRule als invoer.

## <a name="outputs"></a>OUTPUTS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Deze cmdlet produceert een matrix met objecten PswaAuthorizationRule als uitvoer.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld alle autorisatieregels gecontroleerd om de regels waarmee de gebruiker weer te geven *contoso\\mhanson* verbinding maken met de computer *srv2* en een Windows PowerShell-sessie gebruiken configuratie met de naam *testen*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld tests alle autorisatieregels om te controleren welke autorisatieregels gelden voor de gebruiker *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
