---
description: Hierin worden de Windows Power shell-modules beschreven en wordt uitgelegd hoe u deze kunt gebruiken en beheren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252595"
---
# <a name="about-pssnapins"></a>Over PSSnapins

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de Windows Power shell-modules beschreven en wordt uitgelegd hoe u deze kunt gebruiken en beheren.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een Windows Power shell-module is een Microsoft .NET Framework-assembly die Windows Power shell-providers en- \/ cmdlets bevat. Windows Power shell bevat een set basis modules, maar u kunt de kracht en waarde van Windows Power shell uitbreiden door modules toe te voegen die providers en cmdlets bevatten die u maakt of van anderen haalt.

Wanneer u een module toevoegt, zijn de cmdlets en providers die deze bevat, onmiddellijk beschikbaar voor gebruik in de huidige sessie, maar de wijziging is alleen van invloed op de huidige sessie.

Als u de module wilt toevoegen aan alle toekomstige sessies, slaat u deze op in uw Windows Power shell-profiel. U kunt ook de cmdlet Export-Console gebruiken om de namen van modules op te slaan in een console bestand en deze vervolgens te gebruiken in toekomstige sessies. U kunt zelfs meerdere console bestanden opslaan, elk met een andere set modules.

Opmerking: Windows Power shell-modules (PSSnapins) zijn beschikbaar voor gebruik in Windows Power Shell 3,0 en Windows Power Shell 2,0. Ze zijn mogelijk gewijzigd of niet beschikbaar in latere versies. Gebruik modules om Windows Power shell-cmdlets en-providers te verpakken. Zie [een Windows Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie over het maken van modules en het omzetten van modules in modules.

### <a name="finding-snap-ins"></a>MODULES ZOEKEN

Als u een lijst wilt weer geven van de Windows Power shell-modules op uw computer, typt u:

```powershell
Get-PSSnapin
```

Als u de module voor elke Windows Power shell-provider wilt ophalen, typt u:

```powershell
Get-PSProvider | Format-List name, pssnapin
```

Als u een lijst met de cmdlets in een Windows Power shell-module wilt ophalen, typt u:

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a>EEN MODULE INSTALLEREN

De ingebouwde modules worden geregistreerd in het systeem en toegevoegd aan de standaard sessie wanneer u Windows Power shell start. U moet echter de modules registreren die u maakt of van anderen verkrijgt en vervolgens de modules aan uw sessie toevoegen.

### <a name="registering-a-snap-in"></a>EEN MODULE REGISTREREN

Een Windows Power shell-module is een programma dat is geschreven in een .NET Framework taal die in een. dll-bestand is gecompileerd. Als u de providers en cmdlets in een module wilt gebruiken, moet u eerst de module registreren (Voeg deze toe aan het REGI ster).

De meeste modules bevatten een installatie programma (een exe-of MSI-bestand) dat het dll-bestand voor u registreert. Als u echter een module ontvangt als een dll-bestand, kunt u deze registreren op uw systeem. Zie [cmdlets, providers en hosttoepassingen registreren](https://go.microsoft.com/fwlink/?LinkID=143619) in de MSDN-bibliotheek voor meer informatie.

Als u alle geregistreerde modules op uw systeem wilt ophalen of als u wilt controleren of een module is geregistreerd, typt u:

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a>DE MODULE TOEVOEGEN AAN DE HUIDIGE SESSIE

Gebruik de cmdlet Add-PsSnapin om een geregistreerde module toe te voegen aan de huidige sessie. Als u bijvoorbeeld de module Microsoft SQL Server wilt toevoegen aan de sessie, typt u:

```powershell
Add-PSSnapin sql
```

Nadat de opdracht is voltooid, zijn de providers en cmdlets in de module beschikbaar in de sessie. Ze zijn echter alleen beschikbaar in de huidige sessie, tenzij u ze opslaat.

### <a name="saving-the-snap-ins"></a>DE MODULES OPSLAAN

Als u een module in toekomstige Windows Power shell-sessies wilt gebruiken, voegt u de opdracht Add-PsSnapin toe aan uw Windows Power shell-profiel. Of Exporteer de module namen naar een console bestand.

Als u de Add-PSSnapin opdracht aan uw profiel toevoegt, is deze beschikbaar in alle toekomstige Windows Power shell-sessies. Als u de namen van de modules in uw sessie exporteert, kunt u het export bestand alleen gebruiken als u de modules nodig hebt.

Als u de Add-PsSnapin opdracht wilt toevoegen aan uw Windows Power shell-profiel, opent u uw profiel, plakt of typt u de opdracht en slaat u het profiel op. Zie about_Profiles voor meer informatie.

Gebruik de cmdlet Export-Console om de modules op te slaan vanuit een sessie in het console bestand (. psc1). Als u bijvoorbeeld de modules in de huidige sessie configuratie wilt opslaan in het NewConsole. psc1-bestand in de huidige map, typt u:

```powershell
Export-Console NewConsole
```

Zie voor meer informatie exporteren-console.

### <a name="opening-windows-powershell-with-a-console-file"></a>WINDOWS POWER SHELL OPENEN MET EEN CONSOLE BESTAND

Als u een console bestand wilt gebruiken dat de module bevat, start u Windows Power shell (PowerShell.exe) vanaf de opdracht prompt in Cmd.exe of in een andere Windows Power shell-sessie. Gebruik de para meter PsConsoleFile om het console bestand op te geven dat de module bevat. Met de volgende opdracht wordt bijvoorbeeld Windows Power shell gestart met het console bestand NewConsole. psc1:

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

De providers en cmdlets in de module zijn nu beschikbaar voor gebruik in de sessie.

### <a name="removing-a-snap-in"></a>EEN MODULE VERWIJDEREN

Als u een Windows Power shell-module uit de huidige sessie wilt verwijderen, gebruikt u de cmdlet Remove-PsSnapin. Als u bijvoorbeeld de module SQL Server wilt verwijderen uit de huidige sessie, typt u:

```powershell
Remove-PSSnapin sql
```

Met deze cmdlet wordt de module uit de sessie verwijderd. De module is nog geladen, maar de providers en cmdlets die worden ondersteund, zijn niet meer beschikbaar.

### <a name="built-in-commands"></a>INGEBOUWDE OPDRACHTEN

In Windows Power Shell 2,0 en in oudere host-Program ma's in Windows Power Shell 3,0 en hoger, worden de ingebouwde opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules die automatisch aan elke Windows Power shell-sessie worden toegevoegd.

Vanaf Windows Power Shell 3,0, in nieuwere-stijl hostgroepen, waarmee sessies worden gestart met behulp van de methode InitialSessionState. CreateDefault2. de ingebouwde opdrachten zijn verpakt in modules. De uitzonde ring is micro soft. Power shell. core, dat altijd als een module wordt weer gegeven. De kern module is standaard opgenomen in elke sessie. De ingebouwde modules worden automatisch geladen bij het eerste gebruik.

Opmerking: externe sessies, met inbegrip van sessies die zijn gestart met behulp van de cmdlet New-PSSession, zijn oudere sessies waarin de ingebouwde opdrachten zijn verpakt in modules.

De volgende modules (of modules) worden geïnstalleerd met Windows Power shell.

- Micro soft. Power shell. core: bevat providers en cmdlets die worden gebruikt voor het beheren van de basis functies van Windows Power shell. Het bevat het bestands systeem, het REGI ster, de alias, de omgeving, de functie en de variabele providers en de basis-cmdlets zoals Get-Help, Get-Command en Get-History.

- Micro soft. Power shell. host-bevat cmdlets die worden gebruikt door de Windows Power shell-host, zoals Start-Transcript en stop-transcript.

- Micro soft. Power shell. Management-bevat cmdlets, zoals Get-Service en Get-ChildItem die worden gebruikt voor het beheren van Windows-functies.

- Micro soft. Power shell. Security: bevat de certificaat provider en cmdlets die worden gebruikt voor het beheren van Windows Power shell-beveiliging, zoals Get-ACL, Get-AuthenticodeSignature en ConvertTo-SecureString.

- Micro soft. Power shell. Utility: bevat cmdlets die worden gebruikt voor het bewerken van objecten en gegevens, zoals Get-member, write-host en Format-list.

- Micro soft. WSMan. Management: bevat de WSMan-provider en-cmdlets waarmee de Windows Remote Management-service wordt beheerd, zoals Connect-WSMan en Enable-WSManCredSSP.

## <a name="logging-snap-in-events"></a>GEBEURTENISSEN VAN MODULE LOGBOEK REGISTRATIE

Vanaf Windows Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets in Windows Power shell-modules en-modules door de eigenschap LogPipelineExecutionDetails van modules en modules in te stellen op TRUE. Zie [about_EventLogs](about_EventLogs.md)voor meer informatie.

## <a name="see-also"></a>ZIE OOK

[Add-PsSnapin](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[Get-PsSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[Remove-PsSnapin](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[Exporteren-console](xref:Microsoft.PowerShell.Core.Export-Console)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[about_Profiles](about_Profiles.md)

[about_Modules](about_Modules.md)

## <a name="keywords"></a>WOORD

about_Snapins, about_Snap_ins, about_Snap-invoeg toepassingen
