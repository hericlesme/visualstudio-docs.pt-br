---
title: Localizar e substituir texto
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106746"
---
# <a name="find-and-replace-text"></a>Localizar e substituir texto

Localize e substitua um texto no editor do Visual Studio usando [Localizar e Substituir](#find-and-replace-control) ou [Localizar/Substituir em Arquivos](#find-in-files-and-replace-in-files).

> [!TIP]
> Se você está renomeando os símbolos de código, como variáveis e métodos, é melhor *[refatorá-los](../ide/reference/rename.md)* em vez de usar o recurso Localizar e Substituir. A refatoração é inteligente e reconhece o escopo, enquanto o recurso Localizar e Substituir substitui cegamente todas as instâncias.

A funcionalidade Localizar e Substituir está disponível no editor, em algumas outras janelas baseadas em texto, como as janelas **Localizar Resultados**, em janelas do designer como o Designer XAML e o Designer de Formulários do Windows e nas janelas de ferramentas.

É possível definir o escopo das pesquisas para o documento atual, a solução atual ou um conjunto personalizado de pastas. Também é possível especificar um conjunto de extensões de nome de arquivo para pesquisas em vários arquivos. Personalize a sintaxe de pesquisa usando [expressões regulares](../ide/using-regular-expressions-in-visual-studio.md) do .NET.

> [!TIP]
> A caixa [Localizar/Comando](../ide/find-command-box.md) está disponível como um controle de barra de ferramentas, mas não fica visível por padrão. Para exibir a caixa **Localizar/Comando**, selecione **Adicionar ou Remover Botões** na barra de ferramentas **Padrão** e, em seguida, selecione **Localizar**.

## <a name="find-and-replace-control"></a>Controle Localizar e Substituir

O controle **Localizar e Substituir** aparece no canto superior direito da janela do editor de código. O controle **Localizar e Substituir** realça imediatamente todas as ocorrências da cadeia de caracteres de pesquisa fornecida no documento atual. Você pode navegar de uma ocorrência para outra escolhendo o botão **Localizar próximo** ou o botão **Localizar anterior** no controle de pesquisa.

![Controle Localizar e Substituir](media/find-and-replace-box.png)

Você pode acessar opções de substituição escolhendo o botão ao lado da caixa de texto **Localizar**. Para fazer uma substituição por vez, escolha o botão **Substituir próximo** ao lado da caixa de texto **Substituir**. Para substituir todas as correspondências, escolha o botão **Substituir tudo**.

Para alterar a cor de realce das correspondências, escolha o menu **Ferramentas**, selecione **Opções** e, em seguida, escolha **Ambiente** e selecione **Fontes e Cores**. Na lista **Mostrar configurações de**, selecione **Editor de Texto** e, na lista **Exibir Itens**, selecione **Localizar Realce (Extensão)**.

### <a name="search-tool-windows"></a>Janelas de ferramentas de pesquisa

Use o controle **Localizar** em janelas de texto ou de código, como janelas **Saída** e janelas **Localizar Resultados** selecionando **Editar** > **Localizar e Substituir** ou pressionando **Ctrl+F**.

Uma versão do controle **Localizar** também está disponível em algumas janelas de ferramentas. Por exemplo, você pode filtrar a lista de controles na janela **Caixa de Ferramentas** inserindo o texto na caixa de pesquisa. Outras janelas de ferramentas que permitem pesquisar seu conteúdo incluem o **Gerenciador de Soluções**, a janela **Propriedades** e o **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Localizar nos arquivos e substituir nos arquivos

**Localizar/substituir em Arquivos** funciona como o controle **Localizar e Substituir**, mas você pode definir um escopo para a pesquisa. Você pode pesquisar não apenas o arquivo atual aberto no editor, mas também todos os documentos abertos, toda a solução, o projeto atual e conjuntos de pastas selecionados. Você também pode pesquisar por extensão de nome de arquivo. Para acessar a caixa de diálogo **Localizar/Substituir em Arquivos**, selecione **Localizar e Substituir** no menu **Editar** ou pressione **Ctrl+Shift+F**.

![Caixa de diálogo Localizar nos Arquivos](media/find-in-files-box.png)

### <a name="find-results"></a>Localizar Resultados

Quando você escolhe **Localizar tudo**, uma janela **Localizar Resultados** é aberta e lista as correspondências da pesquisa. Selecionar um resultado na lista exibe o arquivo associado e realça a correspondência. Se o arquivo ainda não estiver aberto para edição, ele será aberto em uma guia de visualização no lado direito da guia. É possível usar o controle **Localizar** para pesquisar na lista **Localizar Resultados**.

### <a name="create-custom-search-folder-sets"></a>Criar conjuntos de pastas de pesquisa personalizados

Você pode definir o escopo da pesquisa escolhendo o botão **Escolher Pastas de Pesquisa** (ele se parece com **...** ) ao lado da caixa **Examinar**. Na caixa de diálogo **Escolher Pastas de Pesquisa**, especifique um conjunto de pastas a ser pesquisado e salve a especificação para reutilizá-la mais tarde.

> [!TIP]
> Se você mapeou a unidade de um computador remoto para o computador local, especifique as pastas a serem pesquisadas no computador remoto.

### <a name="create-custom-component-sets"></a>Criar conjuntos de componentes personalizados

Você pode definir conjuntos de componentes como o escopo da pesquisa escolhendo o botão **Editar conjunto de componentes personalizados** ao lado da caixa **Examinar**. Você pode especificar componentes COM ou .NET instalados, projetos do Visual Studio incluídos em sua solução ou qualquer assembly ou biblioteca de tipos (*.dll*, *.tlb*, *.olb*, *.exe* ou *.ocx*). Para pesquisar referências, selecione a caixa **Examinar referências**.

## <a name="see-also"></a>Consulte também

- [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refatorar um código no Visual Studio](../ide/refactoring-in-visual-studio.md)