---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856355"
---
# <a name="known-issues-in-wmf-50"></a>Bekende problemen in WMF 5.0

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell-snelkoppelingen worden verbroken wanneer voor de eerste keer gebruikt

**Oplossing:** Voer een van de volgende acties uit:

1. Klik met de rechtermuisknop op de PowerShell-snelkoppeling. Selecteer 'Windows PowerShell' om te starten in een modus zonder verhoogde bevoegdheden.
2. Klik met de rechtermuisknop op de PowerShell-snelkoppeling. Klik met de rechtermuisknop op 'Windows PowerShell' en selecteer 'als Administrator uitvoeren"om te starten in een modus met uitgebreide bevoegdheden.

Wanneer u een van de bovengenoemde stappen hebt uitgevoerd, werkt de PowerShell-snelkoppelingen. Deze acties moeten slechts één keer worden uitgevoerd.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-Modules en DSC-Resources fouten rapporteren over het uitvoeringsbeleid in Windows 7

Op Windows 7, kan met behulp van PowerShell-modules en DSC-resources leiden tot fouten gerapporteerd over ExecutionPolicy.

**Oplossing:** Het uitvoeringsbeleid instellen op **RemoteSigned** door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Verbinding maken met een oude externe Exchange-eindpunt zorgt ervoor dat een crash

Het eindpunt van de oude Exchange leidt naar een nieuw eindpunt. Er is een fout in de logica voor de omleiding die het resultaat is in een crash.

**Oplossing:** Rechtstreeks verbinding maken met het nieuwe eindpunt.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Software Inventory Logging functie is ten onrechte gestopt na de installatie van WMF 5.0 op Windows Server 2012 R2

Bij het installeren van WMF 5.0 op een Windows Server 2012 R2 waarop SIL al wordt uitgevoerd, wordt de functie logboekregistratie van Software-inventaris per ongeluk gestopt na de installatie.

**Oplossing:** Voer de `Start-SilLogging` cmdlet eenmaal na de installatie van WMF, als het installatieproces foutievelijk stopt met de functie logboekregistratie van Software-inventaris.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` werkt niet als LiteralPath - en - Recurse samen worden gebruikt

Als de naam van een map klikt u vervolgens een ongeldige jokerteken bevat `Get-ChildItem` wordt geen verwachte resultaten opleveren wanneer zowel - LiteralPath en -Recurse samen worden gebruikt.

**Oplossing:** Niet ideaal, maar de huidige oplossing is het implementeren van recursie in het script in plaats van afhankelijk zijn van de cmdlet.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep is mislukt na de installatie van WMF 5.0

Er zijn twee oplossingen voor dit probleem, afhankelijk van de versie van Windows Server die wordt uitgevoerd.

**Oplossing:**

- Voor systemen met **Windows Server 2008 R2**
  1. Open PowerShell als beheerder
  2. De volgende opdracht uitvoeren

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. Voer de opdracht en de fout negeren als ze worden verwacht.

     ```powershell
     Publish-SilData
     ```

  4. De bestanden in de map \Windows\System32\Logfiles\SIL\ verwijderen

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Alle beschikbare belangrijke Windows-Updates installeren en Sysyprep bewerking normaal beginnen.

- Voor systemen met **Windows Server 2012**
  1. Na de installatie van WMF 5.0 op de server als 'd Sysprep, meld u aan als beheerder.
  2. Kopieer Generize.xml vanuit `\Windows\System32\Sysprep\ActionFiles\` naar een locatie buiten de map Windows `C:\` bijvoorbeeld.
  3. Uw exemplaar Generalize.xml Open met Kladblok.
  4. Zoeken en verwijderen van de volgende tekst, één exemplaar van elke moet worden verwijderd (ze zijn aan het einde van het document).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Sla de bewerkte kopie van Generalize.xml op en sluit het bestand.
  6. Open een opdrachtprompt als beheerder
  7. Voer de volgende opdracht uit om eigenaar te worden van het bestand Generalize.xml in de map system32:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Voer de volgende opdracht om de juiste machtigingen instellen voor het bestand:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Antwoord Ja bij de prompt om bevestiging.
     - Houd er rekening mee dat `<AdministratorUserName>` moet worden vervangen door de gebruikersnaam die beheerder is op de machine. Bijvoorbeeld: 'Beheerder'.

  9. Kopieer het bestand dat u bewerkt en opgeslagen via de Sysprep-map met de volgende opdracht:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Antwoord Ja om door te overschrijven (Let erop dat als er geen prompt overschrijven, controleer dan het opgegeven pad).
     - Wordt ervan uitgegaan dat de bewerkte kopie van Generalize.xml C:\ is gekopieerd.

  10. Generalize.XML wordt nu bijgewerkt met de oplossing. Voer Sysprep uit met de generalize optie is ingeschakeld.