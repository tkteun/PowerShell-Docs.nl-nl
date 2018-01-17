---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: pswawebapplication installeren
ms.technology: powershell
ms.openlocfilehash: ce4d01fbe8a83924e7023d792c68c903a32e07d4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Hiermee configureert u de Windows PowerShell® Web Access-webtoepassing in IIS.

## <a name="syntax"></a>SYNTAXIS

### <a name="default"></a>Standaardinstelling
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Install-PswaWebApplication** cmdlet Windows PowerShell-webtoegang webtoepassing configureert. Deze cmdlet installeert de webtoepassing, koppelt u deze aan een website en eventueel maakt een test SSL certificaat met de **useTestCertificate** parameter. Voor beveiliging moeten webbeheerders redenen een testcertificaat niet gebruiken voor productieomgevingen.

## <a name="parameters"></a>PARAMETERS

### <a name="-usetestcertificate"></a>-UseTestCertificate

Geeft aan dat een testcertificaat is gemaakt. Als deze parameter is ingesteld op true, wordt deze cmdlet een testcertificaat maakt en configureert u de Windows PowerShell Web Access-webtoepassing met het certificaat voor HTTPS-aanvragen. Als deze parameter is ingesteld op false, wordt er geen certificaat of een binding gemaakt. Deze waarde ingesteld op false als een ander certificaat wordt gebruikt voor Windows PowerShell Web Access.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | De waarde True                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

Geeft de naam voor uw webtoepassing. Dit wordt weergegeven als het laatste deel van de Windows PowerShell Web Access-URL.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | 1                                    |
| Standaardwaarde                        | pswa                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

Hiermee geeft u de naam van de webserver (IIS) website waarop u deze webtoepassing Windows PowerShell-webtoegang installeren.

|||  
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | Standaardwebsite                     |
| Pijplijn-invoer accepteren?               | onjuist                                |
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet heeft geen invoer.

## <a name="outputs"></a>OUTPUTS

Deze cmdlet produceert geen uitvoer.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld installeert de PSWA-webtoepassing met de standaardwaarden voor de **WebApplicationName** (*pswa*) en **Websitenaam** (*standaardwebsite* ) parameters.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld installeert de webtoepassing PSWA met een testcertificaat en het gebruik van de standaardwaarden voor de **WebApplicationName** en **Websitenaam** parameters.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
