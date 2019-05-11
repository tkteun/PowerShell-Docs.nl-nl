---
title: Over het schrijven van een binaire waarde PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229331"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Een binaire PowerShell-module schrijven

Een binaire module kan assembly (.dll) met de cmdlet-klassen zijn. Standaard worden alle cmdlets in de assembly geïmporteerd wanneer de binaire module wordt geïmporteerd. U kunt echter de cmdlets die worden geïmporteerd met het maken van een module-manifest waarvan root-module de assembly is beperken. (Bijvoorbeeld de CmdletsToExport-sleutel van het manifest kan worden gebruikt voor het exporteren van alleen die cmdlets die nodig zijn.) Een binaire module kan bovendien extra bestanden, een mapstructuur en andere stukjes nuttig beheergegevens dat één cmdlet niet kan bevatten.

De volgende procedure wordt beschreven hoe u maken en een binaire PowerShell-module te installeren.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Het maken en een binaire PowerShell-module installeren

1. Maken van een binaire PowerShell-oplossing (zoals een cmdlet die zijn geschreven in C#), met alle mogelijkheden die u nodig hebt en zorg ervoor dat deze correct kan worden uitgevoerd.

   Vanuit het oogpunt van code is de kern van een binaire module gewoon een cmdlet-assembly. PowerShell wordt in feite een assembly één cmdlet behandelen als een module in termen van laden en verwijderen met geen extra moeite van de ontwikkelaar. Zie voor meer informatie over het schrijven van een cmdlet [schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Maak indien nodig de rest van uw oplossing: (andere cmdlets, XML-bestanden, enzovoort) en deze worden beschreven met een module-manifest.

   Naast het met een beschrijving van de cmdlet-assembly's in uw oplossing, kan een module-manifest wordt beschreven hoe u wilt dat uw module geëxporteerd en geïmporteerd, welke cmdlets weergegeven en wat extra bestanden gaat in de module.
   Zoals eerder gezegd echter, kan PowerShell een binaire cmdlet, zoals een module met geen extra moeite behandelen.
   Een module-manifest is daarom handig hoofdzakelijk bestemd voor meerdere bestanden combineren in één pakket, of voor het beheren van expliciet publicatie voor een bepaalde assembly.
   Zie voor meer informatie, [over het schrijven van een PowerShell-Module-Manifest](how-to-write-a-powershell-module-manifest.md).

   De volgende code is een zeer eenvoudige C# codeblok met drie cmdlets in hetzelfde bestand dat kan worden gebruikt als een module.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Verpakt uw oplossing en het pakket opslaan naar een locatie in het pad van de module PowerShell.

   De `PSModulePath` globale omgevingsvariabele beschrijft de standaardpaden dat door PowerShell wordt gebruikt om te vinden van uw module. Bijvoorbeeld, een algemeen pad naar het opslaan van een module op een systeem zouden worden `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Als u niet de standaardpaden gebruikt, moet u de locatie van uw module expliciet status tijdens de installatie. Zorg dat u maakt een map voor het opslaan van uw module in, zoals u de map voor het opslaan van meerdere assembly's en bestanden voor uw oplossing moet mogelijk.

   Houd er rekening mee dat technisch u niet hoeft te installeren op uw module overal op de `PSModulePath` -dit zijn gewoon de standaardlocaties bevinden dat PowerShell wordt gezocht naar de module. Maar deze wordt beschouwd als aanbevolen procedure om dit te doen, tenzij u een goede reden voor het opslaan van uw module ergens anders hebt. Zie voor meer informatie, [een PowerShell-Module installeren](./installing-a-powershell-module.md) en [wijzigen van de PowerShell-Module Installation Path](./modifying-the-psmodulepath-installation-path.md).

4. De module te importeren in PowerShell met een aanroep naar [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Aanroepen naar [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) uw module in het actieve geheugen wordt geladen. Als u met behulp van PowerShell 3.0 en hoger, gewoon de naam van de module aanroepen in de code ook importeren wordt. Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Module-assembly's importeren als Modules

De cmdlets en providers die zijn opgenomen in de module-assembly's kunnen worden geladen als binaire modules. Wanneer de module-assembly's geladen als binaire modules zijn, cmdlets en providers in de module zijn beschikbaar voor de gebruiker, maar de klasse-module in de assembly wordt genegeerd en de module is niet geregistreerd. De beschikbare Windows PowerShell cmdlets in het vak-module kan niet als gevolg hiervan de module detecteren zelfs als de cmdlets en providers beschikbaar voor de sessie zijn.

Bovendien kunnen niet alle opmaak of typen bestanden waarnaar wordt verwezen door de module worden geïmporteerd als onderdeel van een binaire module.
U moet een module-manifest te maken om de opmaak en typen bestanden te importeren.
Zie, [over het schrijven van een PowerShell-Module-Manifest](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
