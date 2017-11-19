---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Reordenar parâmetros refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Refatoração Reordenar Parâmetros (C#)
`Reorder Parameters`é um Visual C# a operação de refatoração que fornece uma maneira fácil de alterar a ordem dos parâmetros de métodos, indexadores e delegados. `Reorder Parameters`Altera a declaração, e em todos os locais onde o membro é chamado, os parâmetros são reorganizados para refletir a nova ordem.  
  
 Para executar o `Reorder Parameters` operação, coloque o cursor no ou ao lado de um método, indexador ou delegado. Quando o cursor estiver na posição, invoque o `Reorder Parameters` operação, pressionando as teclas de atalho ou clicando no comando no menu de atalho.  
  
> [!NOTE]
>  Não é possível reorganizar o primeiro parâmetro em um método de extensão.  
  
### <a name="to-reorder-parameters"></a>Para reordenar parâmetros  
  
1.  Criar uma biblioteca de classes chamada `ReorderParameters`e, em seguida, substitua `Class1` com o código de exemplo a seguir.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Coloque o cursor na `MethodB`, na declaração de método ou a chamada do método.  
  
3.  Sobre o **refatorar** menu, clique em **reordenar parâmetros**.  
  
     O **reordenar parâmetros** caixa de diálogo é exibida.  
  
4.  No **reordenar parâmetros** caixa de diálogo, selecione `int i` no **parâmetros** lista e, em seguida, clique no botão para baixo.  
  
     Como alternativa, você pode arrastar `int i` depois `bool b` no **parâmetros** lista.  
  
5.  No **reordenar parâmetros** caixa de diálogo, clique em **Okey**.  
  
     Se o **visualizar alterações de referência** opção é selecionada no **reordenar parâmetros** caixa de diálogo, o **visualizar alterações - reordenar parâmetros** caixa de diálogo será exibida. Ele fornece uma visualização das alterações na lista de parâmetros para `MethodB` na assinatura do e a chamada do método.  
  
    1.  Se o **visualizar alterações - reordenar parâmetros** caixa de diálogo for exibida, clique em **aplicar**.  
  
         Neste exemplo, a declaração de método e todos os o chamada de método sites para `MethodB` são atualizadas.  
  
## <a name="remarks"></a>Comentários  
 Você pode reordenar parâmetros de uma declaração de método ou uma chamada de método. Posicione o cursor em ou próximo a declaração de método ou delegate, mas não no corpo.  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)