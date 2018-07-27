---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268296"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SAMENVATTING

Hiermee configureert u de web-App voor Windows PowerShell-webtoegang in IIS.

## <a name="syntax"></a>SYNTAXIS

### <a name="default"></a>Standaardinstelling
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Install-PswaWebApplication** cmdlet web-App voor Windows PowerShell-internettoegang configureert.
Deze cmdlet installeert de webtoepassing, koppelt het aan een website en (optioneel) maakt een test SSL certificaat met de **useTestCertificate** parameter. Voor beveiliging moeten redenen webbeheerders een testcertificaat niet gebruiken voor productieomgevingen.

## <a name="parameters"></a>PARAMETERS

### <a name="-usetestcertificate"></a>-UseTestCertificate

Hiermee geeft u op dat een testcertificaat is gemaakt. Als deze parameter is ingesteld op true, en vervolgens deze cmdlet een testcertificaat maakt en configureert u de web-App voor Windows PowerShell-webtoegang, met het certificaat voor HTTPS-aanvragen. Als deze parameter is ingesteld op false, wordt er geen certificaat of een binding gemaakt. Deze waarde ingesteld op ONWAAR als een ander certificaat wordt gebruikt voor Windows PowerShell-webtoegang.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | True                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Hiermee geeft u de naam voor uw webtoepassing. Dit wordt weergegeven als het laatste deel van de URL van de Windows PowerShell Web Access.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | 1                                    |
| Standaardwaarde                        | pswa                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-websitename"></a>-Websitenaam

Hiermee geeft u de naam van de webserver (IIS) website waarvoor u wilt deze web-App voor Windows PowerShell-webtoegang installeren.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | Standaardwebsite                     |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-confirm"></a>-Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

|||
|-|-|
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | onjuist                                |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-whatif"></a>-WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

|||
|-|-|
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | onjuist                                |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Deze cmdlet worden de gangbare parameters ondersteund:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable. Zie voor meer informatie, [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INVOER

Deze cmdlet gebruikt geen invoer.

## <a name="outputs"></a>UITVOER

Deze cmdlet produceert geen uitvoer.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld installeert de PSWA-webtoepassing met de standaardwaarden voor de **WebApplicationName** (*pswa*) en **Websitenaam** (*standaardwebsite* ) parameters.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld installeert de webtoepassing PSWA met een testcertificaat en met behulp van de standaardwaarden voor de **WebApplicationName** en **Websitenaam** parameters.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)