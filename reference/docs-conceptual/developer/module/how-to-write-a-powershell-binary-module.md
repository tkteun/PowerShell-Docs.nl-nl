---
title: Een binaire Power shell-module schrijven | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 92395bd6b8be1bd3741888eb3716d62f0253e213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779264"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Een binaire PowerShell-module schrijven

Een binaire module kan een assembly (. dll) zijn die cmdlet-klassen bevat. Standaard worden alle cmdlets in de assembly geïmporteerd wanneer de binaire module wordt geïmporteerd. U kunt echter de cmdlets die worden geïmporteerd beperken door een module manifest te maken waarvan de basis module de assembly is. (De sleutel CmdletsToExport van het manifest kan bijvoorbeeld worden gebruikt voor het exporteren van alleen de cmdlets die nodig zijn.) Daarnaast kan een binaire module extra bestanden, een mapstructuur en andere delen van nuttige beheer gegevens bevatten die één cmdlet niet kan.

In de volgende procedure wordt beschreven hoe u een binaire Power shell-module maakt en installeert.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Een binaire Power shell-module maken en installeren

1. Maak een binaire Power Shell-oplossing (zoals een cmdlet die is geschreven in C#) met de mogelijkheden die u nodig hebt, en zorg ervoor dat deze goed wordt uitgevoerd.

   Vanuit een code perspectief is de kern van een binaire module gewoon een cmdlet-assembly. In feite behandelt Power shell een enkele cmdlet-assembly als module, in termen van laden en verwijderen, zonder extra inspanningen voor het deel van de ontwikkelaar. Zie [een Windows Power shell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)voor meer informatie over het schrijven van een cmdlet.

2. Indien nodig, kunt u de rest van uw oplossing maken: (extra cmdlets, XML-bestanden enzovoort) en deze beschrijven met een module manifest.

   Naast het beschrijven van de cmdlet-assembly's in uw oplossing, kan een module manifest beschrijven hoe u de module wilt exporteren en importeren, welke cmdlets worden weer gegeven en welke extra bestanden er in de module worden geplaatst.
   Zoals eerder is aangegeven, kan Power shell een binaire cmdlet beschouwen als een module zonder extra inspanning.
   Als zodanig is een module manifest vooral nuttig voor het combi neren van meerdere bestanden in één pakket, of voor het expliciet beheren van de publicatie voor een bepaalde assembly.
   Zie [een Power shell-module manifest schrijven](how-to-write-a-powershell-module-manifest.md)voor meer informatie.

   De volgende code is een uiterst eenvoudig C#-code blok dat drie cmdlets bevat in hetzelfde bestand dat kan worden gebruikt als een module.

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

3. Verpak uw oplossing en sla het pakket ergens op in het pad van de Power shell-module.

   Met de `PSModulePath` variabele globale omgeving worden de standaard paden beschreven die Power shell gebruikt om uw module te zoeken. Bijvoorbeeld, een gemeen schappelijk pad om een module op een systeem op te slaan zou zijn `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` . Als u de standaard paden niet gebruikt, moet u de locatie van de module tijdens de installatie expliciet aangeven. Zorg ervoor dat u een map maakt om uw module op te slaan in, omdat u de map mogelijk nodig hebt om meerdere assembly's en bestanden voor uw oplossing op te slaan.

   Houd er rekening mee dat u de module niet hoeft te installeren. dit `PSModulePath` zijn gewoon de standaard locaties die Power shell zoekt naar uw module. Het wordt echter wel best practice om dit te doen, tenzij u een goede reden hebt om uw module ergens anders op te slaan. Zie [een Power shell-module installeren](./installing-a-powershell-module.md) en het installatiepad van [de Power shell-module aanpassen](./modifying-the-psmodulepath-installation-path.md)voor meer informatie.

4. Importeer uw module in Power shell met een aanroep van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Bij het aanroepen van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) wordt uw module in het actieve geheugen geladen. Als u Power Shell 3,0 en hoger gebruikt, kunt u gewoon de naam van uw module in code aanroepen. Zie [een Power shell-module importeren](./importing-a-powershell-module.md)voor meer informatie.

## <a name="importing-snap-in-assemblies-as-modules"></a>Module-Assembly's importeren als modules

Cmdlets en providers die in module-assembly's voor komen, kunnen als binaire modules worden geladen. Wanneer de module-assembly's als binaire modules worden geladen, zijn de cmdlets en providers in de module beschikbaar voor de gebruiker, maar de module klasse in de assembly wordt genegeerd en de module is niet geregistreerd. Als gevolg hiervan kunnen de module-cmdlets van Windows Power shell de module niet detecteren, zelfs niet als de cmdlets en providers beschikbaar zijn voor de sessie.

Daarnaast kunnen opmaak of typen bestanden waarnaar wordt verwezen door de module, niet worden geïmporteerd als onderdeel van een binaire module.
Als u de indeling en typen bestanden wilt importeren, moet u een module manifest maken.
Zie [een Power shell-module manifest schrijven voor meer informatie](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)
