---
title: Como implementar uma interface (Designer de Classe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3626d35867902f96b7f3d48d0b7528fa16fc7a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464533"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Como implementar uma interface (Designer de Classe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: implementar uma Interface (Designer de classe)](https://docs.microsoft.com/visualstudio/ide/how-to-implement-an-interface-class-designer).  
  
No Designer de Classe, você pode implementar uma interface no diagrama de classe conectando-a a uma classe que fornece código para os métodos de interface. O Designer de Classe gera uma implementação de interface e exibe a relação entre a interface e a classe como uma relação de herança. É possível implementar uma interface desenhando uma linha de herança entre a interface e a classe ou arrastando a interface do Modo de Exibição de Classe.  
  
> [!TIP]
>  Você pode criar interfaces da mesma maneira como cria outros tipos. Se a interface existir, mas não aparecer no diagrama de classe, exiba-a primeiro. Para obter mais informações, consulte [Como criar tipos usando o Designer de Classe](../ide/how-to-create-types-by-using-class-designer.md) e [Como exibir tipos existentes (Designer de Classe)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Para implementar uma interface desenhando uma linha de herança  
  
1.  No diagrama de classe, exiba a interface e a classe que a implementará.  
  
2.  Desenhe uma linha de herança da classe e da interface.  
  
     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface.  
  
 Para obter mais informações, consulte [Como criar herança entre tipos (Designer de Classe)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Para implementar uma interface da janela do Modo de Exibição de Classe  
  
1.  No diagrama de classe, exiba a classe cuja interface você deseja implementar.  
  
2.  Abra o Modo de Exibição de Classe e localize a interface.  
  
    > [!TIP]
    >  Se o Modo de Exibição de Classe não estiver aberto, abra-o no menu **Exibir**. Para obter mais informações sobre o Modo de Exibição de Classe, consulte [Exibindo classes e seus membros](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Arraste o nó da interface para a forma de classe no diagrama.  
  
     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface. Neste ponto, a interface é implementada.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar tipos usando o Designer de Classe](../ide/how-to-create-types-by-using-class-designer.md)   
 [Como exibir tipos existentes (Designer de Classe)](../ide/how-to-view-existing-types-class-designer.md)   
 [Como criar herança entre tipos (Designer de Classe)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refatorando classes e tipos (Designer de Classe)](../ide/refactoring-classes-and-types-class-designer.md)



