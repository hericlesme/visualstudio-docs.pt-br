---
title: Como criar tipos usando o Designer de Classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fe4eaf38f20ed358263bb6cc07d4be5c9632cd5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-types-by-using-class-designer"></a>Como criar tipos usando Designer de Classe
Para o design de novos tipos para projetos do Visual C# .NET and Visual Basic .NET, crie-os em um diagrama de classes. Para ver os tipos existentes, consulte [Como exibir tipos existentes](how-to-view-existing-types.md).  
  
-   [Criar um novo tipo](#CreateType)  
  
-   [Aplicar um atributo personalizado a um tipo](#CustAttributeType)  
  
-   [Aplicar um atributo personalizado a um membro de tipo](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Criar um novo tipo  
  
1.  Na Caixa de Ferramentas, em Designer de Classe, arraste um dos itens abaixo para um diagrama de classes:  
  
    -   **Classe** ou **Classe Abstrata**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **Estrutura** (VB) ou **Struct** (C#)  
  
    -   **Delegado**  
  
    -   **Módulo** (apenas VB)  
  
2.  Dê um nome ao tipo. Selecione o nível de acesso.  
  
3.  Selecione o arquivo em que deseja adicionar o código inicial para o tipo:  
  
    -   Para criar um novo arquivo e adicioná-lo ao projeto atual, selecione **Criar novo arquivo** e dê um nome ao arquivo.  
  
    -   Para adicionar código a um arquivo existente, selecione **Adicionar a arquivo existente**.  
  
         Se sua solução tiver um projeto que compartilha código entre vários aplicativos, você poderá adicionar um novo tipo a um diagrama de classes no projeto do aplicativo, mas somente se o arquivo de classe correspondente estiver no mesmo projeto de aplicativo ou no projeto compartilhado.  
  
4.  Agora adicione outros itens para definir o tipo:  
  
    |||  
    |-|-|  
    |**Para**|**Adicionar**|  
    |Classes, classes abstratas, estruturas ou structs|Métodos, propriedades, campos, eventos, construtores (método), destruidores (método) e constantes que definem o tipo|  
    |Enums|Valores de campo que compõem a enumeração|  
    |Interfaces|Métodos, propriedades e eventos que compõem a interface|  
    |delegado|Parâmetros que definem o representante|  
    |Módulo|Métodos, propriedades, campos, eventos, construtores (método) e constantes que definem o módulo|  
  
     Consulte [Criando membros](creating-and-configuring-type-members.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Aplicar um atributo personalizado a um tipo  
  
1.  Clique na forma do tipo em um diagrama de classes.  
  
2.  Na janela Propriedades, ao lado da propriedade **Atributos Personalizados** do tipo, clique no botão de reticências (…).  
  
3.  Adicione um ou mais atributos personalizados, um por linha. Não os coloque entre colchetes.  
  
     Quando terminar, os atributos personalizados são aplicados ao tipo.  
  
##  <a name="CustAttributeMember"></a> Aplicar um atributo personalizado a um membro de tipo  
  
1.  Clique no nome do membro na forma de seu tipo em um diagrama de classes ou em sua linha na janela Detalhes da Classe.  
  
2.  Na janela Propriedades, localize a propriedade **Atributos Personalizados** do membro.  
  
3.  Adicione um ou mais atributos personalizados, um por linha. Não os coloque entre colchetes.  
  
     Quando terminar, os atributos personalizados são aplicados ao tipo.  
  
## <a name="see-also"></a>Consulte também
[Como criar herança entre tipos](how-to-create-inheritance-between-types.md)  
[Como criar associações entre tipos](how-to-create-associations-between-types.md)
[Criando e configurando membros de tipo](creating-and-configuring-type-members.md)   
[Trabalhando com diagramas de classe](working-with-class-diagrams.md)   
[Projetando classes e tipos](designing-classes-and-types.md)