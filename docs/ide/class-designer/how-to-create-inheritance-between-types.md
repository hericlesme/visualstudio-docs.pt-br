---
title: "Como criar herança entre tipos (Designer de Classe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b939da3ae4020cc6412f9b1767d5bef8bce05472
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Como criar herança entre tipos (Designer de Classe)
Para criar uma relação de herança entre dois tipos em um diagrama de classes usando o Designer de Classe, conecte o tipo de base ao seu tipo ou tipos derivados. Você pode ter uma relação de herança entre duas classes, entre uma classe e uma interface ou entre duas interfaces.  
  
### <a name="to-create-an-inheritance-between-types"></a>Para criar uma herança entre tipos  
  
1.  No seu projeto localizado no Gerenciador de Soluções, abra um arquivo de diagrama de classes (.cd).  
  
     Se você não possuir um diagrama de classes, crie um. Consulte [Como adicionar diagramas de classe a projetos](how-to-add-class-diagrams-to-projects.md).  
  
2.  Na **Caixa de Ferramentas**, no **Designer de Classe**, clique em **Herança**.  
  
3.  No diagrama de classes, desenhe uma linha de herança entre os tipos que você deseja, começando de:  
  
    -   Uma classe derivada para uma classe base  
  
    -   Uma classe de implementação para uma interface implementada  
  
    -   Uma interface em extensão para uma interface estendida  
  
4.  Se desejar, quando você tiver um tipo derivado de um tipo genérico, clique na linha de herança. Na janela **Propriedades**, defina a propriedade **Argumentos de Tipo** para corresponder ao tipo que você deseja para o tipo genérico.  
  
    > [!NOTE]
    >  Se uma classe abstrata pai contiver pelo menos um membro abstrato, todos os membros abstratos serão implementados como classes de herança não abstratas.  
    >   
    >  Embora você possa visualizar os tipos genéricos existentes, não é possível criar novos tipos genéricos. Você também não pode alterar os parâmetros de tipos genéricos existentes.  
  
## <a name="see-also"></a>Consulte também
[Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
[Noções básicas sobre herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
[Como exibir herança entre tipos](how-to-view-inheritance-between-types.md)   
[Classes do Visual C++ no Designer de Classe](visual-cpp-classes.md)