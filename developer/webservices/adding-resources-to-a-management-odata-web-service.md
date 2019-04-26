---
title: Toevoegen van Resources aan een Management OData-webservice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080778"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Resources toevoegen aan een Management OData-webservice

In dit voorbeeld ziet u hoe u een resource toevoegen aan een bestaande Management OData-webservice met behulp van de ontwerpfunctie voor Management OData-Schema's. De [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) maakt u een webservice die wordt aangegeven dat de proces- en serverbronnen. In dit voorbeeld voegt u een virtuele Machine (VM)-resource met de webservice.

## <a name="prerequisites"></a>Vereisten

In dit artikel wordt ervan uitgegaan dat u hebt gedownload en geïnstalleerd de [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) zoals beschreven in voorbeeld [het maken van een Windows PowerShell-webservice](./creating-a-management-odata-web-service.md), en die u hebt gedownload en geïnstalleerd de [Management OData-Schema Designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). In dit onderwerp wordt ook van uitgegaan dat u hebt de Hyper-V Windows PowerShell-module geïnstalleerd op de computer waar u het beheer van Odata-eindpunt instellen.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Virtuele machine toe te voegen als een Resource met de webservice

De eerste stap is het schema van de bestaande Management OData-eindpunt in de ontwerpfunctie voor schema's importeren. De volgende procedure wordt beschreven hoe u dat doet.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importeren van een bestaand schema in de ontwerpfunctie voor schema

1. Open de ontwerpfunctie voor Management OData-Schema.

2. Uit de **bestand** in het menu **bestand** ; **Nieuwe** ; **Bestand**. De **nieuw bestand** dialoogvenster wordt weergegeven.

3. Klik op **Management OData-Model**, en klik vervolgens op **Open**.

4. Met de rechtermuisknop in het hoofdvenster en klikt u op **schemabestand** ; **Importeren**. De **Open** dialoogvenster wordt weergegeven.

5. Navigeer naar de map waarin u instellen om het beheer van OData-webservice voor de [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) voorbeeld. Als u de Windows PowerShell-script dat bij dat voorbeeld gebruikt het instellen van het eindpunt zonder te wijzigen van het script, wordt die map **C:\inetpub\wwwroot\Modata**. Selecteer Schema.mof en op **Open**.

   Op dit moment de Schema.mof en Schema.xml-bestanden in een teksteditor te openen en u ziet dat ze toewijzingen voor de proces- en Service-resources bevatten. Maakt gebruik van het bestand Schema.mof [Distributed Management Task Force](https://www.dmtf.org/) (DTMF) beheerde Object (MOF) standaard. Het bestand schema.xml maakt gebruik van een XML-schema dat wordt beschreven in [Resource toewijzen Schema](./resource-mapping-schema.md).

   De volgende procedure wordt beschreven hoe u Hyper-V-cmdlets in importeren naar de schema-model.

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlets importeren in het schema

1. Met de rechtermuisknop op een leeg gebied in het ontwerpfunctievenster schema, en klikt u op **Cmdlets voor importeren**. De **Cmdlet Import-Wizard** dialoogvenster wordt weergegeven.

2. Zorg ervoor dat **lokale Computer** is geselecteerd en klik op **volgende**.

3. Zorg ervoor dat Windows PowerShell-Modules geïnstalleerd is geselecteerd en selecteer Hyper-V in de vervolgkeuzelijst. Klik op **volgende**. Klik op **Volgende**.

4. In de **Cmdlet zelfstandig naamwoord** in de lijst met **VM**. Klik op **Volgende**

5. In dit voorbeeld gekoppeld we alleen de Get en Delete-opdrachten met cmdlets. Schakel de **maken** en **UPDATE** selectievakjes, en zorg ervoor dat de **ophalen** en **verwijderen** selectievakjes zijn geselecteerd. Zorg ervoor dat de `Get-VM` cmdlet is geselecteerd voor **ophalen**, en de `Remove-VM` cmdlet is geselecteerd voor **verwijderen**.

6. Omdat de metagegevens voor de VM-cmdlets een uitvoertype niet is opgegeven, moet u de cmdlet om op te geven van het uitvoertype uitvoeren. Selecteer **Geef uitvoertype** en klikt u op **cmdlet uitvoeren**. De **Cmdlet uitvoeren** dialoogvenster wordt weergegeven. Klik op **Run**. De **CLR-Type** vak wordt gevuld met de `VirtualMachine` type. Klik op **OK**, klikt u vervolgens op **volgende**.

7. Alle van de eigenschappen van het object VirtualMachine zijn standaard geselecteerd. U kunt alle eigenschappen die u niet als onderdeel van de gegevens die worden geretourneerd wanneer u deze resource bij de webservice aanvragen wilt wissen. Klik op **Volgende**.

8. U moet ten minste één eigenschap moet worden gebruikt als een sleutel selecteren. Selecteer **naam** in de lijst en klikt u op **volgende**.

9. Het volgende venster kunt u eigenschappen van de Management OData-resource toewijzen aan eigenschappen van de onderliggende-cmdlets. De wizard worden eigenschappen met dezelfde naam standaard toegewezen. Bijvoorbeeld, de `ComputerName` eigenschap van de resource is toegewezen aan de `ComputerName` eigenschap van de cmdlets.  Hiermee kunt u om op te geven de `ComputerName` eigenschap in een aanvraag naar de webservice, en hebben de waarde die u opgeeft worden doorgegeven aan de `Get-VM` cmdlet. `Id` en `Name` ook standaard worden toegewezen.

   10. Klik op **volgende**, klikt u vervolgens op **voltooien**.

       De VM-resource wordt nu weergegeven in het ontwerpfunctievenster schema. U kunt de eigenschappen en bewerkingen die zijn gekoppeld aan de bron controleren. U wordt vervolgens de schemabestanden bijgewerkt exporteren naar de virtuele map voor de webservice.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Schema-bestanden exporteren vanuit de ontwerpfunctie voor schema

1. Met de rechtermuisknop op een leeg gebied in het ontwerpfunctievenster schema, en klikt u op **schemabestand** ; **Exporteren**. De **OpslaanAls** dialoogvenster wordt weergegeven.

2. Navigeer naar dezelfde map waar u het MOF-bestand geïmporteerd. Noem het bestand gelijk zijn aan het oorspronkelijke MOF-bestand (Schema.mof standaard), en klikt u op **opslaan**. Bevestig dat u wilt het bestaande bestand overschrijven.

   Hoewel het niet expliciet is opgegeven de **OpslaanAls** dialoogvenster dit vervangt de Schema.mof en Schema.xml bestanden.

## <a name="next-steps"></a>Volgende stappen

Voordat u toegang krijgt de nieuwe VM-resource van het Management OData-webservice tot, moet u het bestand RbacConfiguration.xml voor toegang tot de Hyper-V Windows PowerShell-module zoals beschreven in bijwerken [autorisatie op basis van rollen configureren](./configuring-role-based-authorization.md), en moet u ook de webservice opnieuw te starten.