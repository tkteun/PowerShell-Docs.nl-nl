---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a>Rapportage over JEA
Om te rapporteren over de status van de configuratie van uw JEA, kunt u het volgende gebruiken:
1.  **Get-PSSessionConfiguration** geregistreerd om te retourneren van een lijst met alle eindpunten op een bepaalde computer.
2.  **Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker op een specifieke eindpunt heeft.

Hier volgt een voorbeeld van **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Om te rapporteren over de _acties_ gebruikers tijdens een sessie JEA duurde, kunt u:
1. Schakel de transcripties 'failover-de-schouder' voor dat eindpunt JEA en raadpleegt u de map met de tekst voor een volledige logboek van acties van elke gebruiker
2. PowerShell-module logboekregistratie inschakelen en controleren van de PowerShell-gebeurtenislogboeken.

