---
title: Personalizando o Gerenciador de modelos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: eac91df1a07e54b80e88538695b1cc22353396d6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-the-model-explorer"></a>Personalizando o Gerenciador de Modelos
Você pode alterar a aparência e comportamento do explorer para o seu designer de linguagem específica de domínio da seguinte maneira:  
  
-   Altere o título da janela.  
  
-   Altere o ícone de guia.  
  
-   Altere os ícones para nós.  
  
-   Oculte nós.  
  
## <a name="changing-the-window-title"></a>Alterar o título da janela  
 Para alterar o título da janela do explorer gerado, selecione **Explorer comportamento** no **DSL Explorer**e, em seguida, no **propriedades** janela, defina o  **Título** propriedade para o título que você deseja.  
  
## <a name="changing-the-tab-icon"></a>Alterando o ícone de guia  
 Para alterar o ícone de guia para o Pesquisador de objetos, use o ícone 16x16 pixels em um arquivo. bmp. Coloque o arquivo de ícone na pasta \DslPackage\Resources\ e, em seguida, altere o nome de arquivo para **ModelExplorerToolWindowBitmaps.bmp**. Por exemplo, você pode alterar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico ícone de arquivo no formato. bmp e renomeá-lo como **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. O designer gerado exibirá esse ícone na guia do explorer quando ela estiver encaixada junto com **Gerenciador de soluções**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Definindo ícones personalizados em nós do Pesquisador de objetos  
 Você pode personalizar nós em seu gerenciador usando as configurações de nó do Pesquisador de objetos. O procedimento a seguir mostra como adicionar um ícone para um nó.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Para adicionar um ícone para um nó do Pesquisador de objetos  
  
1.  Criar um [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solução usando o modelo de solução de fluxo de tarefas.  
  
2.  Colocar um arquivo. bmp que contém um ícone de 16 x 16 pixels no **Dsl\Resources** pasta da solução.  
  
3.  No **DSL Explorer**, com o botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novas configurações do Gerenciador de nó**.  
  
     Um **ExplorerNodeSettings** nó aparece sob o **configurações personalizadas do nó** nó.  
  
4.  Selecione **ExplorerNodeSettings**e, em seguida, o **propriedades** janela, defina **classe** para **ator**.  
  
5.  Definir **ícone para exibição** para o caminho do arquivo de ícone.  
  
6.  Transformar todos os modelos e, em seguida, compilar e executar a solução.  
  
7.  No designer de gerado, abra o diagrama de exemplo.  
  
     O Pesquisador de objetos, haverá três **ator** nós que têm o ícone.  
  
> [!NOTE]
>  Se você tiver definido um ícone de nó para qualquer elemento que é exibido no Gerenciador de gerado, todos os nós do explorer exibirá o ícone. Se nenhum ícone foi definida, os nós exibirá o ícone padrão.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Alterar o nome exibido em um nó do Pesquisador de objetos  
 Você pode alterar como os nomes de elementos de modelo são exibidos em seu gerenciador. O procedimento a seguir mostra como exibir o nome do **tarefa** que é referenciado por um **comentário** no nó de comentário.  
  
#### <a name="to-display-a-property"></a>Para exibir uma propriedade  
  
1.  Abra a solução que você criou no procedimento anterior.  
  
2.  Verifique se o **comentário** faz referência a uma classe de domínio único, definindo a multiplicidade da função com o nome da propriedade **assuntos** para entre 0 e 1. O nome da propriedade deve se tornar **assunto**, e o nome da relação deve se tornar **CommentReferencesSubject**.  
  
3.  No **DSL Explorer**, com o botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novas configurações do Gerenciador de nó**.  
  
     Um **ExplorerNodeSettings** nó aparece sob o **configurações personalizadas do nó** nó.  
  
4.  Selecione **ExplorerNodeSettings**e, em seguida, o **propriedades** janela, defina **classe** para **comentário**.  
  
5.  Clique com botão direito do **comentário** nó e, em seguida, clique **adicionar novo caminho de propriedade**.  
  
     Um novo nó aparece chamado **propriedade exibida**.  
  
6.  Selecione **propriedade exibida**e, em seguida, no **propriedades** janela, clique no campo de valor de **caminho para a propriedade**. Selecione **comentário**, em seguida, **CommentReferencesSubject**, em seguida, **FlowElement**. O caminho resultante deve se assemelhar **CommentReferencesSubject.Subject/! Entidade**.  
  
7.  No campo de valor de **propriedade**, selecione **nome**.  
  
8.  Transformar todos os modelos e, em seguida, compilar e executar sua solução.  
  
9. No designer de gerado, abra o diagrama de exemplo.  
  
10. Desenhar um **comentário conector** entre o elemento de comentário e o **Task1** elemento no diagrama.  
  
     O nó do Pesquisador de objetos deve exibir o comentário como **Task1**.  
  
## <a name="hiding-nodes"></a>Nós ocultos  
 Você pode ocultar um nó em seu gerenciador, adicionando o caminho para o **nós ocultos** nó do **DSL Explorer**. O procedimento a seguir mostra como ocultar **comentário** nós.  
  
#### <a name="to-hide-an-explorer-node"></a>Para ocultar um nó do Pesquisador de objetos  
  
1.  Abra a solução que você criou no procedimento anterior.  
  
2.  No **DSL Explorer**, com o botão direito **Explorer comportamento** e, em seguida, clique em **adicionar novo domínio caminho**.  
  
     Um **caminho domínio** nó aparece no **nós ocultos**.  
  
3.  Selecione **caminho domínio**e, em seguida, no **propriedades** janela, clique no campo de valor de **definição caminho**. Selecione **fluxos**, em seguida, **FlowGraphHasComments**. O caminho resultante deve se assemelhar **FlowGraphHasComments.Comments**  
  
4.  Transformar todos os modelos e, em seguida, compilar e executar sua solução.  
  
5.  No designer de gerado, abra o diagrama de exemplo.  
  
     O Gerenciador de deve mostrar apenas um **atores** nó e não deve exibir o **comentários** nó.  
  
## <a name="see-also"></a>Consulte também

[Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)