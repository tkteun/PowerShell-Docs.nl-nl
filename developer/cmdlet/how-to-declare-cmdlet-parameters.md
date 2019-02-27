---
title: Het Cmdlet-Parameters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850587"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet-parameters declareren

Deze voorbeelden laten zien hoe met de naam, positionele, vereist, optioneel declareren en verwissel de parameters. Deze voorbeelden laten ook zien hoe een parameteralias definiëren.

## <a name="how-to-declare-a-named-parameter"></a>Hoe u een benoemde Parameter declareren

- Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code. Wanneer u de Parameter-kenmerk toevoegen, laat de `Position` sleutelwoord uit het kenmerk.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Hoe u positionele Parameter declareren

- Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code. Wanneer u de Parameter-kenmerk toevoegen, stelt de `Position` trefwoord op de positie van het argument. Een waarde van 0 geeft aan dat de eerste positie.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Hoe u een verplichte Parameter declareren

- Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code. Wanneer u de Parameter-kenmerk toevoegen, stelt de `Mandatory` trefwoord `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Hoe u een optionele Parameter declareren

- Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code. Wanneer u de Parameter-kenmerk toevoegen, laat de `Mandatory` trefwoord.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Hoe u een Switch-Parameter declareren

- Een openbare eigenschap definiëren als type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), en vervolgens het parameterkenmerk declareren.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Hoe u een Parameter met de aliassen declareren

- Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code. Een Alias-kenmerk met een lijst met de aliassen voor de parameter toevoegen. In dit voorbeeld worden drie aliassen zijn gedefinieerd voor dezelfde parameter. De eerste alias bevat een snelkoppeling naar. De tweede en derde aliassen opgeven namen die voor verschillende scenario's kunt u.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie voor meer informatie over het kenmerk Alias [Alias kenmerkdeclaratie](./alias-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Kenmerk parameterdeclaratie](./parameter-attribute-declaration.md)

[De declaratie van de alias-kenmerk](./alias-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
