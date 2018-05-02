---
title: Caixa de diálogo Documentos, Ambiente, Opções
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb14ae44dd137d7bf600cec505fe17fa6e105a42
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="documents-environment-options-dialog-box"></a>Caixa de diálogo Documentos, Ambiente, Opções
Use esta página da caixa de diálogo **Opções** para controlar a exibição de documentos no IDE (ambiente de desenvolvimento integrado) e gerenciar alterações externas em documentos e arquivos. É possível acessar essa caixa de diálogo clicando em **Opções** no menu **Ferramentas** e selecionando **Documentos** no nó **Ambiente**. Se **Documentos** não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.

> [!NOTE]
> As opções disponíveis nas caixas de diálogo e os nomes os locais dos comandos de menu que você vê podem diferir do que é descrito na Ajuda, dependendo de suas configurações ativas ou da edição. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


 **Reutilizar janela do documento atual, se estiver salva** Quando estiver selecionado, fechará o documento atual se ele estiver salvo e abrirá um novo documento na mesma janela. Se o documento atual não tiver sido salvo, ele permanecerá aberto e o novo documento será aberto em uma janela separada. Quando essa opção está desmarcada, novos documentos sempre são abertos em janelas separadas.

 Se você executar operações de recortar e colar em vários documentos com pouca frequência e desejar minimizar o número de documentos e janelas abertas em seu espaço de trabalho, tente esta opção.

 **Detectar quando o arquivo foi alterado fora do ambiente** Quando essa opção está selecionada, uma mensagem notifica imediatamente sobre alterações em um arquivo aberto feitas por um editor fora do IDE. A mensagem permite recarregar o arquivo do armazenamento.

 **Carregar alterações automaticamente, se estiverem salvas** Quando **Detectar quando o arquivo foi alterado fora do ambiente** estiver selecionado e um arquivo aberto no IDE for alterado fora do IDE, uma mensagem de aviso será gerada por padrão. Se essa opção estiver habilitada, nenhum aviso será exibido e o documento será recarregado no IDE para acompanhar alterações externas.

 **Permitir a edição de arquivos somente leitura. Avisar ao tentar salvar** Quando essa opção estiver habilitada, você poderá abrir e editar um arquivo somente leitura. Quando tiver terminado, você deve usar o comando **Salvar como** para salvar o arquivo com um novo nome se quiser salvar um registro de suas alterações.

 **Abrir arquivo usando o diretório do documento ativo no momento** Quando selecionada, essa opção especifica que a caixa de diálogo **Abrir Arquivo** deve exibir o diretório do documento ativo. Quando essa opção está desmarcada, a caixa de diálogo **Abrir Arquivo** exibe o diretório que foi usado para abrir um arquivo pela última vez.

 **Verificar a consistência das terminações de linha ao carregar** Selecione esta opção para que o editor verifique as terminações de linha em um arquivo e exiba uma caixa de mensagem se forem detectadas inconsistências na forma como as terminações de linha estão formatadas.

 **Exibir aviso quando um desfazer global for modificar arquivos editados** Selecione esta opção para exibir uma caixa de mensagem quando o comando **Desfazer Global** for reverter alterações de refatoração feitas em arquivos que também foram alterados após a operação de refatoração. Retornar um arquivo ao seu estado pré-refatoração pode descartar alterações feitas posteriormente no arquivo.

 **Mostrar arquivos diversos no Gerenciador de Soluções** Selecione esta opção para exibir o nó **Arquivos Diversos** no **Gerenciador de Soluções**. Arquivos diversos são arquivos que não estão associadas um projeto ou solução, mas podem aparecer no **Gerenciador de Soluções** por questões de conveniência.

> [!NOTE]
> Selecione esta opção para habilitar o comando **Exibir no Navegador** no menu **Arquivo** para documentos da Web não incluídos no aplicativo Web ativo.

 **\<** *n* **> itens salvos no projeto arquivos diversos** Especifica o número de arquivos a serem persistidos na pasta **MiscellaneousFiles** do **Gerenciador de Soluções**. Esses arquivos são listados mesmo que não estejam mais abertos em um editor. É possível especificar qualquer número inteiro entre 0 e 256. O número padrão é 0.

 Por exemplo, se você definir essa opção como 5 e tiver 10 arquivos diversos abertos, quando você fechar todos os 10 arquivos, os 5 primeiros ainda aparecerão na pasta **Arquivos Diversos**.

 **Salvar documentos como Unicode quando os dados não puderem ser salvos em página de código** Selecione esta opção para fazer com que os arquivos que contenham informações incompatíveis com a página de código selecionada sejam salvos como Unicode por padrão.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
- [Arquivos diversos](../../ide/reference/miscellaneous-files.md)
- [Localizando e substituindo texto](../../ide/finding-and-replacing-text.md)