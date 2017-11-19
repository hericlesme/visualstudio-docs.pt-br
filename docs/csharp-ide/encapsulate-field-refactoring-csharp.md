---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "Encapsular campo refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Refatoração Encapsular Campo (C#)
O **encapsular campo** a operação de refatoração permite criar rapidamente uma propriedade de um campo existente e, em seguida, atualize seu código perfeitamente com referências para a nova propriedade.  
  
 Quando um [campo](/dotnet/csharp/programming-guide/classes-and-structs/fields) é [pública](/dotnet/csharp/language-reference/keywords/public), outros objetos têm acesso direto ao campo e pode modificá-la, sem ser detectado pelo objeto que é proprietária desse campo. Usando [propriedades](/dotnet/csharp/programming-guide/classes-and-structs/properties) para encapsular campo, você pode impedir o acesso direto aos campos.  
  
 Para criar a nova propriedade, o **encapsular campo** operação altera o modificador de acesso para o campo que você deseja para encapsular a [privada](/dotnet/csharp/language-reference/keywords/private)e, em seguida, gera [obter](/dotnet/csharp/language-reference/keywords/get)e [definir](/dotnet/csharp/language-reference/keywords/set) acessadores para esse campo. Em alguns casos, somente um `get` acessador é gerado, como quando o campo é declarado como somente leitura.  
  
 O mecanismo de refatoração atualiza seu código com referências para a nova propriedade nas áreas especificadas no **atualização referências** seção o **encapsular campo** caixa de diálogo.  
  
### <a name="to-create-a-property-from-a-field"></a>Para criar uma propriedade de um campo  
  
1.  Criar um aplicativo de console chamado `EncapsulateFieldExample`e, em seguida, substitua `Program` com o código de exemplo a seguir.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  No [Editor de códigos](../ide/writing-code-in-the-code-and-text-editor.md), posicione o cursor na declaração, no nome do campo que você deseja encapsular. No exemplo a seguir, coloque o cursor na palavra `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Sobre o **refatorar** menu, clique em **encapsular campo**.  
  
     O **encapsular campo** caixa de diálogo é exibida.  
  
     Você também pode digitar o atalho de teclado CTRL + R, E para exibir o **encapsular campo** caixa de diálogo.  
  
     Você pode também clique o cursor, aponte para **refatorar**e, em seguida, clique em **encapsular campo** para exibir o **encapsular campo** caixa de diálogo.  
  
4.  Especifique as configurações.  
  
5.  Pressione ENTER ou clique o **Okey** botão.  
  
6.  Se você tiver selecionado o **visualizar alterações de referência** opção, então o **visualizar alterações de referência** janela será aberta. Clique o **aplicar** botão.  
  
     O seguinte `get` e `set` acessador código é exibido no arquivo de origem:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     O código de `Main` método também é atualizado para o novo `Width` nome da propriedade.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Comentários  
 O **encapsular campo** operação só é possível quando o cursor é posicionado na mesma linha da declaração de campo.  
  
 Para declarações de declarar vários campos, **encapsular campo** usa a vírgula como um limite entre campos e inicia a refatoração no campo que é o mais próximo do cursor e na mesma linha como o cursor. Você também pode especificar qual campo você deseja encapsular selecionando o nome do campo na declaração.  
  
 O código que é gerado por essa operação de refatoração é modelado pelo recurso de trechos de código encapsular campo. Os trechos de código são modificáveis. Para obter mais informações, consulte [Trechos de Código](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)   
 [Trechos de código do Visual C#](../ide/visual-csharp-code-snippets.md)