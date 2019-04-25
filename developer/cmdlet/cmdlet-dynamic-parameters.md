---
title: Cmdlet dynamische Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068535"
---
# <a name="cmdlet-dynamic-parameters"></a>Dynamische cmdlet-parameters

Cmdlets kunt parameters definiëren die beschikbaar voor de gebruiker in speciale omstandigheden zijn, zoals wanneer het argument van een andere parameter is voor een specifieke waarde. Deze parameters worden toegevoegd tijdens runtime en worden aangeduid als *dynamische parameters* omdat ze worden toegevoegd wanneer ze wel nodig zijn. U kunt bijvoorbeeld een cmdlet die door verschillende parameters worden toegevoegd als een specifieke switch-parameter is opgegeven ontwerpen.

> [!NOTE]
> Providers en -functies van Windows PowerShell kunnen u ook dynamische parameters definiëren.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Dynamische Parameters in Windows PowerShell-Cmdlets

Windows PowerShell maakt gebruik van dynamische parameters in een aantal van de provider-cmdlets. Bijvoorbeeld, de `Get-Item` en `Get-ChildItem` cmdlets toevoegen een `CodeSigningCert` parameter tijdens runtime wanneer de `Path` parameter van de cmdlet geeft u het pad naar de provider van het certificaat. Als de `Path` parameter van de cmdlet geeft u het pad voor een andere provider de `CodeSigningCert` parameter is niet beschikbaar.

De volgende voorbeelden ziet u hoe de `CodeSigningCert` parameter tijdens runtime wordt toegevoegd wanneer de `Get-Item` cmdlet wordt uitgevoerd.

In het eerste voorbeeld, de Windows PowerShell-runtime is toegevoegd met de parameter en de cmdlet is voltooid.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Een bestandssysteem-station is opgegeven in het tweede voorbeeld, en wordt een fout geretourneerd. Het foutbericht geeft aan dat de `CodeSigningCert` parameter kan niet worden gevonden.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Ondersteuning voor dynamische Parameters

Ter ondersteuning van dynamische parameters, moet de cmdlet-code de volgende elementen bevatten.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) deze interface biedt de methode waarmee de dynamische parameters worden opgehaald.

Voorbeeld:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) deze methode haalt het object dat de definities van de dynamische parameter bevat.

Voorbeeld:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

Dynamische Parameter-klasse deze klasse definieert de parameters moeten worden toegevoegd. Deze klasse moet een parameterkenmerk voor elke parameter en een optionele Alias en validatie aan de kenmerken die nodig zijn door de cmdlet bevatten.

Voorbeeld:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Zie voor een compleet voorbeeld van een cmdlet die ondersteuning biedt voor dynamische parameters, [hoe u dynamische Parameters declareren](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Hoe u dynamische Parameters declareren](./how-to-declare-dynamic-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
