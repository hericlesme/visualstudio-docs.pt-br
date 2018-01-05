---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Remova os parâmetros de refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 549914476db028cc5135de3c954ac841ab2da628
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-parameters-refactoring-c"></a>Refatoração Remover Parâmetros (C#)
`Remove Parameters`é uma operação de refatoração que fornece uma maneira fácil de remover parâmetros de métodos, indexadores ou delegados. Remova as alterações de parâmetros de declaração; em todos os locais onde o membro é chamado, o parâmetro é removido para refletir a nova declaração.  
  
 Primeiro posicionando o cursor em um método, indexador ou representante para executar a operação de remover parâmetros. Enquanto o cursor estiver na posição, para invocar a remover `Parameters` operação, clique no **refatorar** menu, pressionar o atalho de teclado, ou selecione o comando no menu de atalho.  
  
> [!NOTE]
>  Você não pode remover o primeiro parâmetro em um método de extensão.  
  
### <a name="to-remove-parameters"></a>Para remover parâmetros  
  
1.  Criar um aplicativo de console chamado `RemoveParameters`e, em seguida, substitua `Program` com o código a seguir.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Coloque o cursor no método `A`, na declaração de método ou a chamada do método.  
  
3.  Do **refatorar** menu, selecione **remover parâmetros** para exibir o **remover parâmetros** caixa de diálogo.  
  
     Você também pode digitar o atalho de teclado CTRL + R V para exibir o **remover parâmetros** caixa de diálogo.  
  
     Você pode também clique o cursor, aponte para **refatorar**e, em seguida, clique em **remover parâmetros** para exibir o **remover parâmetros** caixa de diálogo.  
  
4.  Usando o **parâmetros** campo, posicione o cursor na `int i`e, em seguida, clique em **remover**.  
  
5.  Clique em **OK**.  
  
6.  No **visualizar alterações — remover parâmetros** caixa de diálogo, clique em **aplicar**.  
  
## <a name="remarks"></a>Comentários  
 Você pode remover parâmetros de uma declaração de método ou uma chamada de método. Posicione o cursor no nome de declaração ou o representante do método e remover parâmetros de invocação.  
  
> [!CAUTION]
>  Remova habilita parâmetros que você remova um parâmetro que é referenciado no corpo do membro, mas não remover as referências a esse parâmetro no corpo do método. Isso pode causar erros de compilação em seu código. No entanto, você pode usar o **visualizar alterações** caixa de diálogo para revisar seu código antes de executar a operação de refatoração.  
  
 Se um parâmetro que está sendo removido é modificado durante a chamada para um método, a remoção do parâmetro também removerá a modificação. Por exemplo, se uma chamada de método é alterada de  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 para  
  
```csharp  
MyMethod(param2);  
```  
  
 Por que a operação de refatoração, `param1` não será incrementado.  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)