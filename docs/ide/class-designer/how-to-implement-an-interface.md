---
title: Como implementar uma interface (Designer de Classe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c926da09cb8bbb191d0d307dd9e8ce16cfef3c20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-interface-class-designer"></a>Como implementar uma interface (Designer de Classe)
No Designer de Classe, você pode implementar uma interface no diagrama de classe conectando-a a uma classe que fornece código para os métodos de interface. O Designer de Classe gera uma implementação de interface e exibe a relação entre a interface e a classe como uma relação de herança. É possível implementar uma interface desenhando uma linha de herança entre a interface e a classe ou arrastando a interface do Modo de Exibição de Classe.  
  
> [!TIP]
>  Você pode criar interfaces da mesma maneira como cria outros tipos. Se a interface existir, mas não aparecer no diagrama de classe, exiba-a primeiro. Para obter mais informações, consulte [Como criar tipos usando o Designer de Classe](how-to-create-types.md) e [Como exibir tipos existentes](how-to-view-existing-types.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Para implementar uma interface desenhando uma linha de herança  
  
1.  No diagrama de classe, exiba a interface e a classe que a implementará.  
  
2.  Desenhe uma linha de herança da classe e da interface.  
  
     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface.  
  
 Para obter mais informações, consulte [Como criar herança entre tipos](how-to-create-inheritance-between-types.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Para implementar uma interface da janela do Modo de Exibição de Classe  
  
1.  No diagrama de classe, exiba a classe cuja interface você deseja implementar.  
  
2.  Abra o Modo de Exibição de Classe e localize a interface.  
  
    > [!TIP]
    >  Se o Modo de Exibição de Classe não estiver aberto, abra-o no menu **Exibir**. Para obter mais informações sobre o Modo de Exibição de Classe, consulte [Exibindo classes e seus membros](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Arraste o nó da interface para a forma de classe no diagrama.  
  
     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface. Neste ponto, a interface é implementada.  
  
## <a name="see-also"></a>Consulte também
[Como criar tipos usando o Designer de Classe](how-to-create-types.md)   
[Como exibir tipos existentes](how-to-view-existing-types.md)   
[Como criar herança entre tipos](how-to-create-inheritance-between-types.md)   
[Refatorando classes e tipos](refactoring-classes-and-types.md)