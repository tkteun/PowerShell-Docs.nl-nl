---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Uninstall-pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Hiermee verwijdert u de webtoepassing Windows PowerShell®.

## <a name="syntax"></a>SYNTAXIS

### <a name="default"></a>Standaardinstelling
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Uninstall-PswaWebApplication** cmdlet verwijdert u de Windows PowerShell-webtoepassing en verwijdert u de website in IIS. De cmdlet worden niet verwijderd IIS of andere onderdelen geïnstalleerd, omdat ze zijn vereist voor Windows PowerShell om uit te voeren.

## <a name="parameters"></a>PARAMETERS

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Geeft aan dat de testcertificaten gemaakt door de **installeren\_PswaWebApplication** cmdlet (met de **UseTestCertificate** parameter) is verwijderd.
Het testcertificaat met dezelfde naam als het account dat is gemaakt door de **Install-PswaWebApplication** cmdlet wordt verwijderd.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | De waarde True                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;tekenreeks&gt;

Hiermee geeft u de naam van de webtoepassing te verwijderen.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | 1                                    |
| Standaardwaarde                        | pswa                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

Geeft de naam van de website waarop de webtoepassing is geïnstalleerd.

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

Deze cmdlet retourneert geen uitvoer.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

Deze opdracht verwijdert u de Windows PowerShell-webtoepassing.
Deze cmdlet kunt u de Windows PowerShell-webtoepassing verwijderen als u met behulp van de standaardwaarden hebt geïnstalleerd.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>VOORBEELD 2

Deze opdracht verwijdert de Windows PowerShell-webtoepassing en Hiermee verwijdert u de testcertificaat dat is gekoppeld aan de toepassing.
Deze cmdlet kunt u de Windows PowerShell-webtoepassing verwijderen als u met behulp van de standaardwaarden zijn geïnstalleerd en een testcertificaat gemaakt.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>Voorbeeld 3 {#example-3 .subHeading}

Deze opdracht verwijdert u de Windows PowerShell-webtoepassing wanneer een aangepaste website en de toepassing tijdens de installatie zijn opgegeven.
De opdracht verwijdert u de website met de naam *persoonlijke site* en de toepassing met de naam *testtoepassing* en specificeert de testcertificaten die zijn gekoppeld aan de toepassing worden ook verwijderd.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Verwante onderwerpen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)