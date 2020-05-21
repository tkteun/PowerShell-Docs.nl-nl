---
title: Uw Windows Power shell-provider ontwerpen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 6112e64a4a15d9dc8ac28ba51259b6647db4c064
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560046"
---
# <a name="designing-your-windows-powershell-provider"></a>Uw Windows PowerShell-provider ontwerpen

U moet een Windows Power shell-provider implementeren als uw product of configuratie een set opgeslagen gegevens bevat, zoals een Data Base die de gebruiker wil navigeren of bladeren. Als uw product daarnaast een container bevat, is het zinvol om een Windows Power shell-provider te implementeren, zelfs als deze geen container met meerdere niveaus is. U kunt bijvoorbeeld een Windows Power shell-container provider implementeren als de opdracht voor het schrijven, verplaatsen, wijzigen, nieuw of verwijderen van de cmdlet wordt uitgevoerd als een bewerking voor uw product of configuratie gegevens.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows Power shell-paden identificeren uw provider

De Windows Power shell-runtime maakt gebruik van Windows Power shell-paden om toegang te krijgen tot de juiste Windows Power shell-provider. Wanneer een cmdlet een van deze paden opgeeft, weet de runtime welke provider moet worden gebruikt om toegang te krijgen tot de bijbehorende gegevens opslag. Deze paden bevatten Stationspaden, paden die zijn gemachtigd voor de provider, de provider-directe paden en de interne paden van de provider. Elke Windows Power shell-provider moet een of meer van deze paden ondersteunen.

Zie How Windows Power shell (Engelstalig) voor meer informatie over Windows Power shell-paden.

### <a name="defining-a-drive-qualified-path"></a>Een pad naar een station definiëren

Als u wilt dat de gebruiker toegang kan krijgen tot gegevens die zich op een fysiek station bevinden, moet uw Windows Power shell-provider een pad naar het station ondersteunen. Dit pad begint met de stationsnaam gevolgd door een dubbele punt (:) bijvoorbeeld mydrive: \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Een pad naar een provider definiëren

Om ervoor te zorgen dat de Windows Power shell-runtime de provider kan initialiseren en ongedaan maken, moet uw Windows Power shell-provider een door de provider gekwalificeerd pad ondersteunen. Bestands systeem:: \\ \uncshare\abc\bar is bijvoorbeeld het pad naar de provider voor de bestandssysteem provider die is geleverd door Windows Power shell.

### <a name="defining-a-provider-direct-path"></a>Een provider-direct pad definiëren

Als u externe toegang tot uw Windows Power shell-provider wilt toestaan, moet het een provider-direct-pad ondersteunen om rechtstreeks door te geven aan de Windows Power shell-provider voor de huidige locatie. De Windows Power shell-provider van het REGI ster kan bijvoorbeeld \\ \server\regkeypath gebruiken als een provider-direct-pad.

### <a name="defining-a-provider-internal-path"></a>Een provider definiëren-intern pad

Uw Windows Power shell-provider moet een provider-intern pad ondersteunen om de provider-cmdlet toegang te geven tot gegevens met behulp van niet-Windows Power shell-Api's (Application Programming Interfaces). Dit pad wordt aangegeven na ':: ' in het provider-pad. Bijvoorbeeld: het interne pad van de provider voor de Windows Power shell-provider van het bestands systeem is \\ \uncshare\abc\bar.

## <a name="changing-stored-data"></a>Opgeslagen gegevens wijzigen

Wanneer u methoden overschrijft die het onderliggende gegevens archief wijzigen, moet u altijd de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) aanroepen met de meest recente versie van het item dat door deze methode is gewijzigd. De provider infrastructuur bepaalt of het object item moet worden door gegeven aan de pijp lijn, bijvoorbeeld wanneer de gebruiker de para meter-PassThru opgeeft. Als het meest recente item wordt opgehaald, kunt u de eigenschap context. PassThru testen om te bepalen of u het resulterende item daad werkelijk moet schrijven, bijvoorbeeld voor de prestaties.

## <a name="choose-a-base-class-for-your-provider"></a>Kies een basis klasse voor uw provider

Windows Power shell biedt een aantal basis klassen die u kunt gebruiken voor het implementeren van uw eigen Windows Power shell-provider. Bij het ontwerpen van een provider kiest u de basis klasse, zoals beschreven in deze sectie, die het meest geschikt is voor uw vereisten.

Elke basis klasse van een Windows Power shell-provider maakt een set cmdlets beschikbaar. In deze sectie worden de cmdlets beschreven, maar worden de para meters niet beschreven.

Met de sessie status maakt de Windows Power shell-runtime verschillende locatie-cmdlets beschikbaar voor bepaalde Windows Power shell-providers, zoals de-,- `Get-Location` `Set-Location` en- `Pop-Location` `Push-Location` cmdlets. U kunt de `Get-Help` cmdlet gebruiken om informatie over deze locatie-cmdlets te verkrijgen.

### <a name="cmdletprovider-base-class"></a>Basis klasse CmdletProvider

De klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) definieert een basis provider van Windows Power shell. Deze klasse ondersteunt de provider declaratie en levert een aantal eigenschappen en methoden die beschikbaar zijn voor alle Windows Power shell-providers.
De-klasse wordt aangeroepen door de `Get-PSProvider` cmdlet om alle beschik bare providers voor een sessie weer te geven.
De implementatie van deze cmdlet wordt geleverd door de sessie status.

> [!NOTE]
> Windows Power shell-providers zijn beschikbaar voor alle Windows Power shell-taal bereik.

### <a name="drivecmdletprovider-base-class"></a>Basis klasse DriveCmdletProvider

De klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) definieert een Windows Power shell-schijf provider die ondersteuning biedt voor bewerkingen voor het toevoegen van nieuwe stations, het verwijderen van bestaande stations en het initialiseren van de standaard stations. De bestandssysteem provider die wordt meegeleverd met Windows Power shell initialiseert bijvoorbeeld stations voor alle volumes die zijn gekoppeld, zoals harde schijven en CD/DVD-stations.

Deze klasse is afgeleid van de basis klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . De volgende tabel geeft een lijst van de cmdlets die door deze klasse worden weer gegeven. Naast de vermelde items `Get-PSDrive` is de cmdlet (weer gegeven door sessie status) een gerelateerde cmdlet die wordt gebruikt voor het ophalen van beschik bare stations.

|      Cmdlet      |                             Definitie                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | Hiermee maakt u een nieuw station voor de sessie en streamt u stationgegevens. |
| `Remove-PSDrive` | Hiermee verwijdert u een station uit de sessie.                                   |

### <a name="itemcmdletprovider-base-class"></a>Basis klasse ItemCmdletProvider

De klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) definieert een Windows Power shell-item provider waarmee bewerkingen worden uitgevoerd op de afzonderlijke items van het gegevens archief en er worden geen containers of navigatie mogelijkheden door gegeven. Deze klasse is afgeleid van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . De volgende tabel geeft een lijst van de cmdlets die door deze klasse worden weer gegeven.

|     Cmdlet     |                                                                                                                                                            Definitie                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | Hiermee wordt de huidige inhoud van items op de opgegeven locatie gewist en vervangen door de waarde ' Clear ' die is opgegeven door de provider. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.                                                                                   |
| `Get-Item`     | Hiermee worden items opgehaald van de opgegeven locatie en worden de resulterende objecten gestreamd.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | Hiermee wordt de standaard actie voor het item op het opgegeven pad aangeroepen.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | Hiermee stelt u een item op de opgegeven locatie met de opgegeven waarde. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.                                                                                                                                                   |
| `Resolve-Path` | Hiermee worden de joker tekens voor een Windows Power shell-pad en gegevens van het pad streamen omgezet.                                                                                                                                                                                                                                              |
| `Test-Path`    | Testen voor het opgegeven pad en retour neren `true` als dit bestaat en `false` anders. Deze cmdlet wordt geïmplementeerd ter ondersteuning `IsContainer` van de para meter voor de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) . |

### <a name="containercmdletprovider-base-class"></a>Basis klasse ContainerCmdletProvider

De klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) definieert een Windows Power shell-container provider waarmee een container, voor gegevens archiefbestanden, aan de gebruiker wordt getoond. Houd er rekening mee dat een Windows Power shell-container provider alleen kan worden gebruikt als er één container (geen geneste containers) met items bevat. Als er geneste containers zijn, moet u een Windows Power shell-navigatie provider implementeren.

Deze klasse is afgeleid van de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . In de volgende tabel worden de cmdlets gedefinieerd die door deze klasse worden geïmplementeerd.

|     Cmdlet      |                                                                        Definitie                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | Hiermee worden items van de ene locatie naar de andere gekopieerd. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |
| `Get-Childitem` | Hiermee worden de onderliggende items op de opgegeven locatie opgehaald en als objecten gestreamd.                                                                        |
| `New-Item`      | Hiermee worden nieuwe items gemaakt op de opgegeven locatie en wordt het resulterende object gestreamd.                                                                           |
| `Remove-Item`   | Hiermee verwijdert u items van de opgegeven locatie.                                                                                                               |
| `Rename-Item`   | De naam van een item op de opgegeven locatie wordt gewijzigd. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |

### <a name="navigationcmdletprovider-base-class"></a>Basis klasse NavigationCmdletProvider

De klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) definieert een Windows Power shell-navigatie provider waarmee bewerkingen worden uitgevoerd voor items die gebruikmaken van meer dan één container. Deze klasse is afgeleid van de basis klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . De volgende tabel vermeldt de cmdlets die door deze klasse worden weer gegeven.

|    Cmdlet    |                                                                      Definitie                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combine-pad | Combineert twee paden in één pad, met behulp van een provider-specifiek scheidings teken tussen paden. Deze cmdlet streamt teken reeksen.                               |
| `Move-Item`  | Hiermee verplaatst u items naar de opgegeven locatie. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |

Een gerelateerde cmdlet is de elementaire parser-pad-cmdlet die wordt geleverd door Windows Power shell. Deze cmdlet kan worden gebruikt voor het parseren van een Windows Power shell-pad voor de ondersteuning van de `Parent` para meter. Hiermee wordt de teken reeks voor het bovenliggende pad gestreamd.

## <a name="select-provider-interfaces-to-support"></a>Provider interfaces selecteren voor ondersteuning

Naast het afleiden van een van de Windows Power shell-basis klassen kan uw Windows Power shell-provider andere functionaliteit ondersteunen door een of meer van de volgende provider interfaces te verkrijgen. In deze sectie worden de interfaces en de cmdlets gedefinieerd die door elke interface worden ondersteund. De para meters voor de met interface ondersteunde cmdlets worden niet beschreven. Cmdlet-parameter informatie is online beschikbaar met `Get-Command` de `Get-Help` cmdlets en.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

De interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) definieert een inhouds provider die bewerkingen uitvoert op de inhoud van een gegevens item. De volgende tabel geeft een lijst van de cmdlets die door deze interface worden weer gegeven.

|     Cmdlet      |                                                                                        Definitie                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | Hiermee worden de opgegeven lengten van waarden toegevoegd aan de inhoud van het opgegeven item. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |
| `Clear-Content` | Hiermee stelt u de inhoud van het opgegeven item in op de waarde ' Clear '. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.               |
| `Get-Content`   | Hiermee wordt de inhoud van de opgegeven items opgehaald en worden de resulterende objecten gestreamd.                                                                                                         |
| `Set-Content`   | Vervangt de bestaande inhoud voor de opgegeven items. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

De interface [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) definieert een eigenschap Windows Power shell-provider waarmee bewerkingen worden uitgevoerd op de eigenschappen van items in het gegevens archief. De volgende tabel geeft een lijst van de cmdlets die door deze interface worden weer gegeven.

> [!NOTE]
> De `Path` para meter voor deze cmdlets geeft een pad naar een item aan in plaats van een eigenschap te identificeren.

|        Cmdlet        |                                                                                   Definitie                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | Hiermee stelt u de eigenschappen van de opgegeven items in op de waarde wissen. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.      |
| `Get-ItemProperty`   | Hiermee worden eigenschappen opgehaald uit de opgegeven items en worden de resulterende objecten gestreamd.                                                                                                |
| `Set-ItemProperty`   | Hiermee stelt u de eigenschappen in van de opgegeven items met de aangegeven waarden. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

De interface [System. Management. Automation. provider. Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) , die is afgeleid van [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definieert een provider die dynamische para meters voor de ondersteunde cmdlets opgeeft. Dit type provider verwerkt bewerkingen waarvoor eigenschappen tijdens runtime kunnen worden gedefinieerd, bijvoorbeeld een nieuwe eigenschaps bewerking. Dergelijke bewerkingen zijn niet mogelijk voor items die statisch gedefinieerde eigenschappen hebben.
De volgende tabel geeft een lijst van de cmdlets die door deze interface worden weer gegeven.

|        Cmdlet         |                                                                                Definitie                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | Hiermee wordt een eigenschap van het opgegeven item naar een ander item gekopieerd. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven. |
| `Move-ItemProperty`   | Hiermee wordt een eigenschap van het opgegeven item verplaatst naar een ander item. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.  |
| `New-ItemProperty`    | Hiermee maakt u een eigenschap voor de opgegeven items en worden de resulterende objecten gestreamd.                                                                                             |
| `Remove-ItemProperty` | Hiermee verwijdert u een eigenschap voor de opgegeven items.                                                                                                                              |
| `Rename-ItemProperty` | De naam van een eigenschap van de opgegeven items wordt gewijzigd. Met deze cmdlet wordt geen uitvoer object door middel van de pijp lijn door gegeven, tenzij de `PassThru` para meter is opgegeven.                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

De interface [System. Management. Automation. provider. Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) voegt security descriptor functionaliteit aan een provider toe. Met deze interface kan de gebruiker security descriptor informatie ophalen en instellen voor een item in het gegevens archief. De volgende tabel geeft een lijst van de cmdlets die door deze interface worden weer gegeven.

|  Cmdlet   |                                                                                                                                                                                                          Definitie                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | Hiermee haalt u de gegevens op die zijn opgenomen in een toegangs beheer lijst (ACL), die deel uitmaakt van een security descriptor die wordt gebruikt voor het beveiligen van besturingssysteem bronnen, bijvoorbeeld een bestand of een object.                                                                                                                                                                                                                                      |
| `Set-Acl` | Hiermee stelt u de gegevens voor een ACL in. Het is in de vorm van een exemplaar van [System. Security. accesscontrol. objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) op de item (s) die zijn toegewezen voor het opgegeven pad. Met deze cmdlet kunt u informatie instellen over bestanden, sleutels en subsleutels in het REGI ster, of een ander provider item, als de Windows Power shell-provider de instelling van beveiligings informatie ondersteunt. |

## <a name="see-also"></a>Zie ook

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Hoe Windows Power shell werkt](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
