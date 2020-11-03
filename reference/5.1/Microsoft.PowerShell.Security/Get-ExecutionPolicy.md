---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: 4a805874c039e97574a78bb3bbc7a4d6e958d2ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250500"
---
# Get-ExecutionPolicy

## SAMENVATTING
Hiermee haalt u het uitvoerings beleid voor de huidige sessie op.

## SYNTAXIS

### Alles

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## BESCHRIJVING

Gebruik om het uitvoerings beleid voor elk bereik weer te geven in de volg orde van prioriteit `Get-ExecutionPolicy -List` . Om het effectief uitvoerings beleid voor uw Power shell-sessie gebruik `Get-ExecutionPolicy` zonder para meters te bekijken.

Het effectief uitvoerings beleid wordt bepaald door uitvoerings beleid dat is ingesteld door `Set-ExecutionPolicy` en Groepsbeleid instellingen.

Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: alle uitvoerings beleidsregels ophalen

Met deze opdracht wordt het uitvoerings beleid voor elk bereik weer gegeven in de volg orde van prioriteit.

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven.

### Voor beeld 2: een uitvoerings beleid instellen

In dit voor beeld ziet u hoe u een uitvoerings beleid instelt voor de lokale computer.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **RemoteSigned** -beleid op te geven. De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**. Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.

### Voor beeld 3: het effectief uitvoerings beleid ophalen

In dit voor beeld ziet u hoe het effectief uitvoerings beleid voor een Power shell-sessie wordt weer gegeven.

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven. De `Get-ExecutionPolicy` cmdlet wordt uitgevoerd zonder para meter om het effectief uitvoerings beleid, **Alles ondertekend** , weer te geven.

### Voor beeld 4: een script blok keren om het uit te voeren zonder het uitvoerings beleid te wijzigen

Dit voor beeld laat zien hoe u met het beleid voor het uitvoeren van **RemoteSigned** geen niet-ondertekende scripts kunt uitvoeren.

Een best practice is de code van het script te lezen en te controleren of het veilig is **voordat** u de `Unblock-File` cmdlet gebruikt. De `Unblock-File` cmdlet verwijdert scripts zodat ze kunnen worden uitgevoerd, maar het uitvoerings beleid wordt niet gewijzigd.

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **RemoteSigned** -beleid op te geven. Het beleid wordt ingesteld voor het standaard bereik **LocalMachine**.

De `Get-ExecutionPolicy` cmdlet geeft aan dat **RemoteSigned** het effectief uitvoerings beleid voor de huidige Power shell-sessie is.

Het **Start-ActivityTracker.ps1** script wordt uitgevoerd vanuit de huidige map. Het script wordt geblokkeerd door **RemoteSigned** omdat het script geen digitale hand tekening heeft.

Voor dit voor beeld is de code van het script beoordeeld en geverifieerd als veilig om uit te voeren. De `Unblock-File` cmdlet gebruikt de para meter **Path** om het script uit te blok keren.

Als u wilt controleren of `Unblock-File` het uitvoerings beleid niet is gewijzigd, `Get-ExecutionPolicy` wordt het effectief uitvoerings beleid, **RemoteSigned** , weer gegeven.

Het script **Start-ActivityTracker.ps1** wordt uitgevoerd vanuit de huidige map. Het script wordt uitgevoerd, omdat het is gedeblokkeerd door de `Unblock-File` cmdlet.

## PARAMETERS

### -Lijst

Hiermee worden alle uitvoerings beleids waarden opgehaald voor de sessie die in volg orde van prioriteit wordt vermeld. `Get-ExecutionPolicy`Hiermee wordt standaard alleen het effectief uitvoerings beleid opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het bereik op dat wordt beïnvloed door een uitvoerings beleid.

Het effectief uitvoerings beleid wordt als volgt bepaald door de volg orde van prioriteit:

- **MachinePolicy**. Ingesteld door een groepsbeleid voor alle gebruikers van de computer.
- **User Policy**. Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.
- **Proces**. Alleen van invloed op de huidige Power shell-sessie.
- **CurrentUser**. Alleen van invloed op de huidige gebruiker.
- **LocalMachine**. Het standaard bereik dat van invloed is op alle gebruikers van de computer.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

`Get-ExecutionPolicy` invoer van de pijp lijn wordt niet geaccepteerd.

## UITVOER

### Microsoft.PowerShell.ExecutionPolicy

## OPMERKINGEN

Een uitvoerings beleid maakt deel uit van de Power shell-beveiligings strategie. Uitvoerings beleid bepaalt of u configuratie bestanden kunt laden, zoals uw Power shell-profiel, of scripts moet uitvoeren. En, of scripts digitaal moeten worden ondertekend voordat ze worden uitgevoerd.

## GERELATEERDE KOPPELINGEN

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)
