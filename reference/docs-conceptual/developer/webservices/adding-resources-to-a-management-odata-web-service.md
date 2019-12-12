---
title: Resources toevoegen aan een management OData-webservice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352288"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Resources toevoegen aan een Management OData-webservice

In dit voor beeld ziet u hoe u een resource kunt toevoegen aan een bestaande Management OData-webservice met behulp van de Management OData-schema ontwerper. Het [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -voor beeld maakt een webservice waarmee het proces en de Server bronnen worden getoond. In dit voor beeld voegt u een virtuele machine (VM)-resource toe aan de webservice.

## <a name="prerequisites"></a>Vereisten

In dit onderwerp wordt ervan uitgegaan dat u het [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -voor beeld hebt gedownload en geïnstalleerd zoals beschreven in [een Windows Power shell-webservice maken](./creating-a-management-odata-web-service.md)en dat u de [Management OData-schema ontwerper](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)hebt gedownload en geïnstalleerd. In dit onderwerp wordt ervan uitgegaan dat u de Hyper-V Windows Power shell-module hebt geïnstalleerd op de computer waarop u het management Odata-eind punt hebt ingesteld.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>VM als resource toevoegen aan de webservice

De eerste stap is het importeren van het schema van het bestaande Management OData-eind punt in de schema ontwerper. In de volgende procedure wordt beschreven hoe u dit doet.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Een bestaand schema importeren in de schema ontwerper

1. Open de Management OData-schema ontwerper.

2. Selecteer in het menu **bestand** de optie **bestand** . **Nieuw** ; **Bestand**. Het dialoog venster **nieuw bestand** wordt weer gegeven.

3. Klik op **beheer OData-model**en klik vervolgens op **openen**.

4. Met de rechter muisknop in het hoofd venster en klik op **schema bestand** . **Importeren**. Het dialoog venster **openen** wordt weer gegeven.

5. Navigeer naar de map waarin u de Management OData-webservice voor het [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -voor beeld hebt ingesteld. Als u het Windows Power shell-script hebt gebruikt dat bij dat voor beeld is opgegeven om het eind punt in te stellen zonder het script te wijzigen, is de map **C:\inetpub\wwwroot\Modata**. Selecteer schema. mof en klik op **openen**.

   Open nu het schema. mof-en schema. XML-bestanden in een tekst editor en Let erop dat ze toewijzingen voor het proces en de service resources bevatten. Het schema. MOF-bestand maakt gebruik van [Distributed Management Task Force](https://www.dmtf.org/) (DTMF) Managed object (MOF) standaard. Het schema. XML-bestand maakt gebruik van een XML-schema dat wordt beschreven in het [resource toewijzings schema](./resource-mapping-schema.md).

   In de volgende procedure wordt beschreven hoe u Hyper-V-cmdlets in kunt importeren in het schema model.

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlets importeren in het schema

1. Klik met de rechter muisknop op een leeg gebied van het schema Designer-venster en vervolgens op **cmdlets importeren**. Het dialoog venster wizard voor het **importeren van cmdlets** wordt weer gegeven.

2. Zorg ervoor dat **lokale computer** is geselecteerd en klik op **volgende**.

3. Zorg ervoor dat geïnstalleerde Windows Power shell-modules is geselecteerd en selecteer Hyper-V in de vervolg keuzelijst. Klik op **volgende**. Klik op **Volgende**.

4. Selecteer **virtuele machine**in de lijst met **zelfstandig naam woorden** . Klik op **Volgende**

5. In dit voor beeld worden alleen de opdrachten Get en DELETE met cmdlets gebonden. Schakel de selectie vakjes **maken** en **bijwerken** uit en zorg ervoor dat de selectie vakjes **ophalen** en **verwijderen** zijn ingeschakeld. Zorg ervoor dat de cmdlet `Get-VM` is geselecteerd voor **Get**en dat de cmdlet `Remove-VM` is geselecteerd voor **verwijderen**.

6. Omdat de meta gegevens voor de VM-cmdlets geen uitvoer type opgeven, moet u de cmdlet uitvoeren om het uitvoer type op te geven. Selecteer **uitvoer type opgeven** en klik op **cmdlet uitvoeren**. Het dialoog venster **cmdlet uitvoeren** wordt weer gegeven. Klik op **Run**. Het vak **CLR-type** is ingevuld met het `VirtualMachine` type. Klik op **OK**en vervolgens op **volgende**.

7. Standaard zijn alle eigenschappen van het object VirtualMachine geselecteerd. U kunt alle eigenschappen wissen die u niet wilt als onderdeel van de gegevens die worden geretourneerd wanneer u deze bron aanvraagt bij de webservice. Klik op **Volgende**.

8. U moet ten minste één eigenschap selecteren die moet worden gebruikt als sleutel. Selecteer **naam** in de lijst en klik op **volgende**.

9. In het volgende venster kunt u eigenschappen van de Management OData-resource toewijzen aan eigenschappen van de onderliggende cmdlets. De wizard wijst standaard eigenschappen met identieke namen toe. Bijvoorbeeld, de eigenschap `ComputerName` van de resource wordt toegewezen aan de eigenschap `ComputerName` van de cmdlets.  Zo kunt u de eigenschap `ComputerName` opgeven in een aanvraag voor de webservice en de waarde die u opgeeft, door geven aan de `Get-VM`-cmdlet. `Id` en `Name` worden standaard ook toegewezen.

   10. Klik op **volgende**en vervolgens op **volt ooien**.

       De VM-resource wordt nu weer gegeven in het venster schema Designer. U kunt de eigenschappen en bewerkingen controleren die zijn gekoppeld aan de resource. Vervolgens exporteert u de bijgewerkte schema bestanden naar de virtuele map voor de webservice.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Schema bestanden uit de schema ontwerper exporteren

1. Klik met de rechter muisknop op een leeg gebied van het schema Designer-venster en op **schema bestand** . **Exporteren**. Het dialoog venster **Opslaan als** wordt weer gegeven.

2. Ga naar de map waarin u het MOF-bestand hebt geïmporteerd. Noem het bestand hetzelfde als het oorspronkelijke MOF-bestand (standaard schema. MOF) en klik op **Opslaan**. Bevestig dat u het bestaande bestand wilt overschrijven.

   Hoewel het niet expliciet wordt vermeld in het dialoog venster **Opslaan als** , worden zowel de schema. MOF-als de schema. XML-bestanden vervangen.

## <a name="next-steps"></a>Volgende stappen

Voordat u toegang krijgt tot de nieuwe VM-resource van de Management OData-webservice, moet u het RbacConfiguration. XML-bestand bijwerken om toegang te geven tot de Hyper-V Windows Power shell-module, zoals beschreven in [autorisatie op basis van rollen configureren](./configuring-role-based-authorization.md). u moet ook de webservice opnieuw opstarten.