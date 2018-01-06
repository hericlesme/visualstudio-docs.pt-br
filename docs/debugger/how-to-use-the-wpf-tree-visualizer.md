---
title: "Como: usar o Visualizador de árvore WPF | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78806b2ace7872db06ff403bcae28bb6eff21cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Como usar o Visualizador de Árvore WPF
Você pode usar o visualizador de árvore do WPF para explorar a árvore visual de um objeto do WPF e exibir as propriedades de dependência do WPF para os objetos contidos nessa árvore. Para obter mais informações sobre árvores visual, consulte [árvores no WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Para obter mais informações sobre propriedades de dependência, consulte [visão geral de propriedades de dependência](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Quando você abre o Visualizador de árvore WPF, você verá dois painéis: o **árvore Visual** à esquerda e o **propriedades de** *nome***:**  *Tipo* painel à direita. Selecione qualquer objeto no **árvore Visual** painel e o **propriedades de** *nome***:***tipo* é de painel atualizado automaticamente para mostrar as propriedades desse objeto.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir o visualizador de árvore do WPF  
  
1.  Em um DataTip **inspecionar** janela, **Autos** janela, ou **locais** janela, ao lado de um nome de objeto do WPF, clique na seta no ícone de lupa adjacente.  
  
     Uma lista de visualizadores é exibida.  
  
2.  Clique em **Visualizador de árvore WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Para pesquisar a árvore visual  
  
-   No **árvore Visual** painel, digite a cadeia de caracteres que você deseja procurar no **pesquisa** caixa.  
  
     O visualizador de árvore do WPF localiza imediatamente o primeiro objeto na árvore visual que corresponde à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.  
  
    -   Para ir para a próxima correspondência dentro da árvore visual, clique em **próximo**.  
  
    -   Para voltar à correspondência anterior, clique em **Prev**.  
  
    -   Para limpar os critérios de pesquisa, clique em **limpar**.  
  
### <a name="to-search-the-properties-list"></a>Para pesquisar a lista de propriedades  
  
-   No **propriedades de** *nome***:***tipo* painel, digite a cadeia de caracteres você deseja procurar no **filtrar**caixa.  
  
     O visualizador de árvore do WPF localiza imediatamente as propriedades que correspondem à cadeia de caracteres digitada; agora, a lista exibe apenas as propriedades que correspondem à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.  
  
    -   Para limpar os critérios de pesquisa, clique em **limpar**.  
  
### <a name="to-close-the-visualizer"></a>Para fechar o visualizador  
  
-   Clique o **fechar** ícone no canto superior direito da caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Árvores no WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Visão geral das propriedades da dependência](/dotnet/framework/wpf/advanced/dependency-properties-overview)