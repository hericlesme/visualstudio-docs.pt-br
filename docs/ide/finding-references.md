---
title: "Localizando referências no código | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92c12e4d51255849843f938c032ca17b611eeeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="finding-references-in-your-code"></a>Localizando referências no código  
Você pode usar o comando **Localizar Todas as Referências** para localizar onde elementos de código específicos são referenciados em toda a base de código. O comando **Localizar Todas as Referências** está disponível no menu de contexto (acessado com o clique do botão direito do mouse) do elemento cujas referências você deseja localizar. Ou, se você estiver usando o teclado, pressione **Shift + F12**.  

Os resultados serão exibidos em uma janela de ferramentas chamada **referências do '*elemento*'**, em que *elemento* é o nome do item que você está procurando. Uma barra de ferramentas na janela **referências** permite que você:  
- Altere o escopo da pesquisa em uma caixa de listagem suspensa. É possível optar por examinar apenas documentos alterados até a solução inteira.  
- Copie o item referenciado selecionado ao selecionar o botão **Copiar**.  
- Escolha os botões para acessar o local anterior ou seguinte na lista. Também é possível pressionar as teclas **F8** e **Shift + F8** para fazer isso.  
- Remova todos os filtros nos resultados retornados, escolhendo o botão **Limpar Todos os Filtros**.  
- Altere a forma em que os itens retornados são agrupados escolhendo uma configuração na caixa de listagem suspensa **Agrupar por:**.  
- Mantenha a janela de resultados da pesquisa atual ao escolher o botão **Manter Resultados**. Ao selecionar este botão, os resultados da pesquisa atual ficam nessa janela, e novos resultados da pesquisa são exibidos em uma nova janela de ferramentas.  
- Pesquisar cadeias de caracteres nos resultados da pesquisa inserindo texto na caixa de texto **Pesquisar Localizar Todas as Referências**.  

Também é possível passar o mouse sobre qualquer resultado da pesquisa para obter uma visualização da referência.  

![Janela de ferramentas Localizar Todas as Referências](../ide/media/vside_findallreferences.png)  

### <a name="navigate-to-references"></a>Navegue até referências
Você pode usar os seguintes métodos para navegar para as referências na janela **referências**:  

- Pressione **F8** para acessar a próxima referência ou **Shift + F8** para acessar a referência anterior.  
- Pressione a tecla **Enter** em uma referência ou clique duas vezes nela para acessá-la no código.  
- No menu de contexto de uma referência, escolha os comandos **Ir ao Local Anterior** ou **Ir ao Próximo Local**.  
- Use as teclas **Seta para cima** e **Seta para baixo** (se elas estiverem habilitadas na caixa de diálogo Opções). Para habilitar essa funcionalidade, na barra de menus, selecione **Ferramentas**, **Opções**, **Ambiente**, **Guias e Janelas**, **Guia Visualizar** e, em seguida, selecione as caixas **Permitir que novos arquivos sejam abertos na guia de visualização** e **Visualizar arquivos selecionados em Localizar Resultados**.  

### <a name="change-reference-groupings"></a>Alterar agrupamentos de referência  
Por padrão, as referências são agrupadas por projetos, depois por definição. No entanto, é possível mudar essa ordem de agrupamento, alterando a configuração na caixa de listagem suspensa **Agrupar por:** na barra de ferramentas. Por exemplo, é possível alterá-la na configuração padrão de **Projeto em vez de definição** para **Definição em vez de projeto** e também para outras configurações.  

**Definição** e **Projeto** são dois agrupamentos padrão usados, mas é possível adicionar outros ao escolher o comando **Agrupamento** no menu de contexto do item selecionado. Pode ser útil adicionar mais agrupamentos se sua solução tem muitos arquivos e caminhos.  

## <a name="see-also"></a>Consulte também  
[Navegando no código](../ide/navigating-code.md)  