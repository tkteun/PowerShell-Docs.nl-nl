---
title: Cmdlet-para meters declareren | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 97e86a1eb715f149a8383a1a4529c00da4f0eba8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774385"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet-parameters declareren

In deze voor beelden ziet u hoe u para meters met de naam, positioneel, required, optional en switch declareert. In deze voor beelden ziet u ook hoe u een parameter alias definieert.

## <a name="how-to-declare-a-named-parameter"></a>Een benoemde para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, laat u het `Position` tref woord weg uit het kenmerk.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-positional-parameter"></a>Een positionele para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, stelt u het `Position` tref woord in op de argument positie. De waarde 0 geeft de eerste positie aan.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-mandatory-parameter"></a>Een verplichte para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, stelt u het `Mandatory` sleutel woord in op `true` .

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-an-optional-parameter"></a>Een optionele para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Als u het parameter kenmerk toevoegt, laat u het `Mandatory` tref woord weg.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Een para meter voor een switch declareren

- Definieer een open bare eigenschap als type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)en Declareer vervolgens het parameter kenmerk.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-parameter-with-aliases"></a>Een para meter met aliassen declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Voeg een alias kenmerk toe met een lijst met de aliassen voor de para meter. In dit voor beeld worden drie aliassen gedefinieerd voor dezelfde para meter. De eerste alias biedt een snelkoppeling. De tweede en derde alias geven namen op die u voor verschillende scenario's kunt gebruiken.

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

Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie over het alias kenmerk.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Declaratie van het kenmerk Parameter](./parameter-attribute-declaration.md)

[Declaratie van het kenmerk Alias](./alias-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
