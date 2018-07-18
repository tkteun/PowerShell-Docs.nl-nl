---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094225"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SAMENVATTING

Voegt een nieuwe autorisatieregel toe aan de set met autorisatieregels Windows PowerShell® Web Access.

## <a name="syntax"></a>Syntaxis

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Add-PswaAuthorizationRule** cmdlet voegt een nieuwe autorisatieregel toe aan de set met autorisatieregels Windows PowerShell® Web Access.

U moet de gebruikers, computers en Windows PowerShell-eindpunten voor deze regel opgeven. U kunt gebruikers en computers door afzonderlijke gebruikersaccounts en computernamen of door op te geven groepen opgeven.

Voor een computer die lid van een Active Directory-domein is, wordt de cmdlet de beveiligings-id (SID) van de computer gebruikt om de regel te maken.
Hiermee kunt u gebruikmaken van een korte naam, een volledig gekwalificeerde domeinnaam (FQDN) of een IP-adres voor de **computernaam** op de aanmeldingspagina.

De cmdlet maakt voor een computer die niet is gekoppeld aan een Active Directory-domein, de regel met behulp van de computernaam die is opgegeven door de beheerder. Als u wilt verbinding maken met deze machine, moet de eindgebruiker de computernaam opgeven precies zoals deze wordt weergegeven in de regel.

Als er meerdere computers met dezelfde naam in het netwerk, kan korte naam omzetten in meer dan één computer. Dit kan leiden tot verwarring bij het maken van een verbinding. Bijvoorbeeld, als een regel bestaat voor de werkgroepcomputer met de naam '*Server1*' en een nieuwe computer met de naam *server1.contoso.com* is gekoppeld met het netwerk met behulp van regels voor de validatie is geslaagd en Windows PowerShell-webtoegang wil een verbinding met de computer met de naam '*Server1*'. Is er geen garantie dat de verbinding tot stand is gebracht met de opgegeven werkgroepcomputer. de poging kan worden gemaakt op de werkgroep of het domeincomputer met de naam '*Server1*'. Als u wilt verkleinen dubbelzinnigheid, wordt het aanbevolen dat u de FQDN-naam voor de doelcomputer wanneer dit mogelijk gebruiken te maken van een autorisatieregel.

Regels voor het evalueren van de primaire aanmelden referentie van de Windows PowerShell Web Access-gebruikers, niet de alternatieve referenties (de tweede set referenties die zijn gevonden in de **optionele verbindingsinstellingen** sectie van de aanmeldingspagina). Zie voor een voorbeeld van dit voorbeeld 6.

## <a name="parameters"></a>Parameters

### <a name="-computergroupname-string"></a>-ComputerGroupName \<tekenreeks\>

Hiermee geeft u de naam van een computergroep in Active Directory Domain Services (AD DS) of het lokale groepen waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | True                                 |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-computername-string"></a>-ComputerName \<tekenreeks\>

Hiermee geeft u de naam van de computer waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | True                                 |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-configurationname-string"></a>-ConfigurationName \<tekenreeks\>

Hiermee geeft u de naam van de configuratie van Windows PowerShell-sessie, ook wel bekend als runspace, waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | True                                 |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u wilt gebruiken voor het wijzigen van de Windows PowerShell-webtoegang autorisatieregels. Als u deze parameter niet toevoegt, gebruikt de cmdlet het gebruikersaccount momenteel is aangemeld. Om op te halen een **PSCredential** object, dat vereist voor het op afstand autorisatieregels toevoegen is, voert u de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-force"></a>-Force

Hiermee wordt de opdracht uitgevoerd zonder gebruikersbevestiging. \
Daarnaast wordt ook gevraagd om bevestiging bij het invoeren van een eenvoudige of korte computernaam (zoals een naam die niet de naam van een domein of is niet volledig gekwalificeerd). Bevestiging is aangevraagd voor opmaaktalen wordt om beveiligingsredenen, zodat u de naam van de eenvoudige gebruiken kunt om toe te voegen een computer als de computer in een werkgroep.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-rulename-string"></a>-RuleName \<tekenreeks\>

Hiermee geeft u de beschrijvende naam voor deze regel.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<tekenreeks\[\]\>

Hiermee geeft u de naam van een of meer gebruikersgroepen in AD DS of lokale groepen waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | True                                 |
| Positie?                            | met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-username-string"></a>-UserName \<tekenreeks\[\]\>

Hiermee geeft u een of meer gebruikers waarop deze regel toegang verleent. Naam van de gebruiker kan een lokale gebruikersaccount op de computer met de gateway of een gebruiker in AD DS zijn.
De indeling is `domain\user` of `computer\user`.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | True                                 |
| Positie?                            | 1                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue, ByPropertyName)       |
| Jokertekens accepteren?          | onjuist                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Deze cmdlet worden de gangbare parameters ondersteund:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.
Zie voor meer informatie, [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>INVOER

### <a name="string"></a>Tekenreeks

Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.

### <a name="string"></a>Tekenreeks\[\]

Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.

## <a name="outputs"></a>Resultaten

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Deze cmdlet retourneert de autorisatie-regelobject.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld verleent toegang tot de sessieconfiguratie _Pswaeindpunt_, een beperkte runspace op _srv2_ voor gebruikers in de _SMAdmins_ groep.

> [!NOTE]
> Naam van de computer moet een volledig gekwalificeerde domeinnaam (FQDN). Beheerders definiëren voor een beperkte sessieconfiguratie of een runspace, dit is een beperkt aantal cmdlets en taken die eindgebruikers kunnen worden uitgevoerd. Een beperkte runspace te definiëren kan voorkomen dat gebruikers toegang tot andere computers die niet in de toegestane Windows PowerShell® runspace, dus firewallopties voor een beter beveiligde verbinding. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) of de [installeren en gebruik Windows PowerShell-webtoegang](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld verleent toegang tot de Windows PowerShell-sessie standaardconfiguratie `Microsoft.PowerShell`op *srv2* voor gebruikers in de gebruikers met de naam `contoso\user1`, `contoso\user2`, en `contoso\user3`. Met deze cmdlet maakt drie regels (1 per persoon).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>VOORBEELD 3

In dit voorbeeld ziet u hoe u voor het invoeren van waarden van de naam van gebruiker via de pijplijn.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>VOORBEELD 4

In dit voorbeeld laat zien hoe alle parameters, nemen de waarden van de pijplijn door de naam van eigenschap.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>VOORBEELD 5

In dit voorbeeld wordt een regel voor het toestaan van de lokale gebruiker met de naam `PswaServer\ChrisLocal` toegang tot de server met de naam **srv1.contoso.com**.

In dit voorbeeld wordt een scenario waarin de gateway zich in een werkgroep en de doelcomputer zich in een domein. De autorisatieregel is van toepassing op de lokale gebruikers op de gateway. Op de Windows PowerShell-webtoegang aanmelden pagina als u wilt verifiëren, moet de gebruiker leveren een tweede set referenties in de **optionele verbindingsinstellingen** gebied. De gateway-server gebruikt de aanvullende set referenties voor het verifiëren van de gebruiker op de doelcomputer, een server met de naam *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>VOORBEELD 6

In dit voorbeeld kan alle gebruikers toegang tot alle eindpunten op alle computers.
Dit wordt in feite uitgeschakeld autorisatieregels.

> [!NOTE]
> Het gebruik van de `*` jokerteken wordt niet aanbevolen voor implementaties van de beveiliging van gevoelige en moet alleen worden beschouwd voor testomgevingen of wordt gebruikt in implementaties waarbij de beveiliging kan worden verminderd.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Zie ook

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Add Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)