---
title: Como criar e remover dependências do projeto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3626cc4c13600b0a6f20cc40713bd77f4527a3ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467922"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Como criar e remover dependências de projeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: criar e remover dependências de projeto](https://docs.microsoft.com/visualstudio/ide/how-to-create-and-remove-project-dependencies).  
  
Ao compilar uma solução que contém vários projetos, pode ser necessário compilar determinados projetos primeiro, para gerar o código usado por outros projetos. Quando um projeto consome o código executável gerado por outro projeto, o projeto que gera o código é chamado de uma dependência de projeto do projeto que consome o código. Esses relacionamentos de dependência podem ser definidos na caixa de diálogo **Dependências do Projeto**.  
  
### <a name="to-assign-dependencies-to-projects"></a>Para atribuir dependências a projetos  
  
1.  No Gerenciador de Soluções, selecione um projeto.  
  
2.  No menu **Projeto**, escolha **Dependências do Projeto**.  
  
     A caixa de diálogo **Dependências do Projeto** é aberta.  
  
    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  
  
3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  
  
4.  No campo **Depende de**, marque a caixa de seleção de qualquer outro projeto que deve ser compilado antes desse projeto.  
  
 A solução deve consistir em mais de um projeto antes que seja possível criar dependências de projeto.  
  
### <a name="to-remove-dependencies-from-projects"></a>Para remover dependências de projetos  
  
1.  No Gerenciador de Soluções, selecione um projeto.  
  
2.  No menu **Projeto**, escolha **Dependências do Projeto**.  
  
     A caixa de diálogo **Dependências do Projeto** é aberta.  
  
    > [!NOTE]
    >  A opção **Dependências do Projeto** está disponível apenas em uma solução com mais de um projeto.  
  
3.  Na guia **Dependências**, selecione um projeto no menu suspenso **Projeto**.  
  
4.  No campo **Depende de**, desmarque as caixas de seleção ao lado de outros projetos que não são mais dependências desse projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)



