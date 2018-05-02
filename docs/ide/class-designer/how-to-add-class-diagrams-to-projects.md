---
title: Como adicionar diagramas de classe a projetos (Designer de Classe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 962df3467b8ff37a15c181a764e646ae3fb1e980
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-class-diagrams-to-projects-class-designer"></a>Como adicionar diagramas de classe a projetos (Designer de Classe)

Para criar, editar e refatorar classes e outros tipos, adicione um diagrama de classe ao projeto em C#, Visual Basic ou C++. Para visualizar diferentes partes do código em um projeto, adicione vários diagramas de classes ao projeto.

Não é possível criar diagramas de classes a partir de projetos que compartilham o código por meio de diversos aplicativos. Para criar diagramas de classe UML, consulte [Criar diagramas e projetos de modelagem UML](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="to-add-a-blank-class-diagram-to-a-project"></a>Para adicionar um diagrama de classes em branco a um projeto

1.  No Gerenciador de Soluções, clique com o botão direito do mouse no nome do projeto. Em seguida, escolha **Adicionar Novo Item** ou **Adicionar** > **Novo Item**.

2.  Na lista de modelos, escolha o **Diagrama de Classe**. Para projetos do Visual C++, procure em **Modelos** e em **Utilitário** para localizar esse modelo.

     O diagrama de classes é aberto no Designer de Classe e aparece como um arquivo que possui uma extensão .cd no Gerenciador de Soluções na hierarquia do projeto. Use a caixa de ferramentas Designer da Classe para arrastar formas e linhas até o diagrama.

3.  Para adicionar vários diagramas de classes, repita as etapas deste procedimento.

## <a name="to-add-a-class-diagram-based-on-existing-types"></a>Para adicionar um diagrama de classes com base em tipos existentes

- No **Gerenciador de Soluções**, abra o menu de contexto do arquivo de classe e escolha **Exibir Diagrama de Classe**.

     -ou-

     Em **Modo de Exibição de Classe**, abra o namespace ou o menu de contexto de tipo e escolha **Exibir em Diagrama de Classe**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Para exibir o conteúdo de um projeto completo em um diagrama de classe

- No **Gerenciador de Soluções** ou no Modo de Exibição de Classe, clique com o botão direito do mouse no projeto e escolha **Exibir** e, em seguida, escolha **Exibir Diagrama de Classe**.

     Um diagrama de classe populado automaticamente é criado.

## <a name="see-also"></a>Consulte também

- [Como criar tipos usando o Designer de Classe](how-to-create-types.md)
- [Como exibir tipos existentes](how-to-view-existing-types.md)
- [Projetar e exibir classes e tipos](designing-and-viewing-classes-and-types.md)
- [Exibir tipos e relações](viewing-types-and-relationships.md)
- [Trabalhar com diagramas de classe](working-with-class-diagrams.md)
