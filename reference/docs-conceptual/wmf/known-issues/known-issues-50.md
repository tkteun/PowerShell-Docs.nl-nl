---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.0
ms.openlocfilehash: 1db656884736c742ef78354b7452879e319d4a0a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564122"
---
# <a name="known-issues-in-wmf-50"></a>Bekende problemen in WMF 5.0

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Power shell-snelkoppelingen worden verbroken wanneer deze voor de eerste keer worden gebruikt

**Oplossing:** Voer een van de volgende acties uit:

1. Klik met de rechter muisknop op de Power shell-snelkoppeling. Selecteer Windows Power shell om in een niet-verhoogde modus te starten.
2. Klik met de rechter muisknop op de Power shell-snelkoppeling. Klik met de rechter muisknop op Windows Power shell en selecteer als administrator uitvoeren om in een verhoogde modus te starten.

Wanneer u een van de bovenstaande acties hebt uitgevoerd, werken de Power shell-sneltoetsen. Deze acties moeten slechts één keer worden uitgevoerd.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Power shell-modules en DSC-Resources rapporteren fouten over ExecutionPolicy in Windows 7

In Windows 7 kan het gebruik van Power shell-modules en DSC-resources leiden tot fouten die zijn gerapporteerd over ExecutionPolicy.

**Oplossing:** Stel de ExecutionPolicy in op **RemoteSigned** door de volgende opdracht uit te voeren in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Verbinding maken met een oud extern Exchange-eind punt veroorzaakt een crash

Het oude Exchange-eind punt wordt omgeleid naar een nieuw eind punt. Er is een fout in de omleidings logica die resulteert in een crash.

**Oplossing:** Maak rechtstreeks verbinding met het nieuwe eind punt.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>De functie logboek registratie van software-inventarisatie is foutief gestopt na de installatie van WMF 5,0 op Windows Server 2012 R2

Bij de installatie van WMF 5,0 op een Windows Server 2012 R2 waarop SIL al wordt uitgevoerd, wordt de functie logboek registratie van software-inventarisatie na installatie foutief gestopt.

**Oplossing:** Voer de `Start-SilLogging` cmdlet eenmaal na de WMF-installatie uit, terwijl het installatie proces de functie voor logboek registratie van software-inventarisatie foutievelijk stoppen.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem`werkt niet als-LiteralPath en-recursieve samen worden gebruikt

Als een mapnaam een ongeldig Joker teken bevat, worden er `Get-ChildItem` geen verwachte resultaten gegenereerd wanneer zowel LiteralPath als-recursief worden gebruikt.

**Oplossing:** Niet ideaal, maar de huidige tijdelijke oplossing is het implementeren van recursie in het script in plaats van te vertrouwen op de cmdlet.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep mislukt na installatie van WMF 5,0

Er zijn twee tijdelijke oplossingen voor dit probleem, afhankelijk van de versie van Windows Server die u gebruikt.

**Opgelost**

- Voor systemen met **Windows Server 2008 R2**
  1. Power shell openen als beheerder
  2. Voer de volgende opdracht uit

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. Voer de opdracht uit en negeer de fout, zoals ze worden verwacht.

     ```powershell
     Publish-SilData
     ```

  4. De bestanden in de map \Windows\System32\Logfiles\SIL\ verwijderen

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Installeer alle beschik bare belang rijke Windows-updates en start de Sysyprep-bewerking normaal.

- Voor systemen met **Windows Server 2012**
  1. Meld u aan als beheerder nadat u WMF 5,0 op de server hebt geïnstalleerd als Sysprep.
  2. Kopieer Generize. XML vanuit `\Windows\System32\Sysprep\ActionFiles\` een map naar een locatie buiten de Windows-map, `C:\` bijvoorbeeld.
  3. Open uw generaliseer. XML-kopie met Klad blok.
  4. Zoek en verwijder de volgende tekst, één exemplaar van elke moet worden verwijderd (ze worden bijna het einde van het document).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Sla de bewerkte kopie van generaliseer. XML op en sluit het bestand.
  6. Open een opdracht prompt als beheerder
  7. Voer de volgende opdracht uit om eigenaar te worden van het bestand generalize. XML in de map System32:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Voer de volgende opdracht uit om de juiste machtigingen voor het bestand in te stellen:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Beantwoord Ja bij de vraag om bevestiging.
     - Houd er rekening mee dat `<AdministratorUserName>` moet worden vervangen door de gebruikers naam die beheerder is op de computer. Bijvoorbeeld ' Administrator '.

  9. Kopieer het bestand dat u hebt bewerkt en opgeslagen naar de Sysprep-map met behulp van de volgende opdracht:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Antwoord Ja om te overschrijven (Houd er rekening mee dat als er geen prompt is om te overschrijven, Controleer het ingevoerde pad).
     - Er wordt van uitgegaan dat uw bewerkte kopie van generalize. XML is gekopieerd naar C:\.

  10. Generalize. XML wordt nu bijgewerkt met de tijdelijke oplossing. Voer Sysprep uit met de optie generalize ingeschakeld.
