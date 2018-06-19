---
title: Detalhes de configuração de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc10c7602f3298b532b4af76e66b43d469416ba5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134120"
---
# <a name="source-control-configuration-details"></a>Detalhes de configuração de controle de origem
Para implementar o controle de origem, você precisa configurar corretamente o sistema de projeto ou o editor para fazer o seguinte:

-   Solicitar permissão para fazer a transição para estado de alteração

-   Solicitar permissão para salvar um arquivo

-   Solicitar permissão para adicionar, remover ou renomear arquivos no projeto

## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permissão para fazer a transição para estado de alteração
 Um editor ou projeto deve solicitar permissão para fazer a transição para o estado (sujo) alterada chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e receber aprovação para alterar o documento do ambiente antes de retornar `True` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Um projeto é essencialmente um editor para um arquivo de projeto e tem como resultado, a responsabilidade mesmo para implementar o acompanhamento de estado alterado para o arquivo de projeto como um editor de texto para seus arquivos. O ambiente controla o estado de alteração da solução, mas você deve tratar o estado de alteração de qualquer objeto, a solução referencia, mas não armazena, como um arquivo de projeto ou seus itens. Em geral, se o projeto ou o editor é responsável por gerenciar a persistência de um item, é responsável por implementar o acompanhamento de estado alterado.

 Em resposta ao `IVsQueryEditQuerySave2::QueryEditFiles` chamada, o ambiente pode fazer o seguinte:

-   Rejeitar a chamada para alterar, caso em que o editor ou projeto deve permanecer no estado inalterado (limpo).

-   Indica que os dados de documento devem ser recarregados. Para um projeto, o ambiente será recarregar os dados para o projeto. Um editor deve recarregar os dados do disco por meio de seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementação. Em ambos os casos, o contexto do projeto ou o editor pode alterar quando os dados são recarregados.

 É uma tarefa complexa e difícil fazer ajustes apropriado `IVsQueryEditQuerySave2::QueryEditFiles` chamadas em uma base de código existente. Como resultado, essas chamadas devem ser integradas durante a criação do projeto ou no editor.

## <a name="request-permission-to-save-a-file"></a>Solicitar permissão para salvar um arquivo
 Antes de um editor ou projeto salva um arquivo, ele deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Para arquivos de projeto, estas chamadas são automaticamente preenchidas pela solução, que sabe quando salvar um arquivo de projeto. Editores são responsáveis por fazer essas chamadas, a menos que a implementação do editor de `IVsPersistDocData2` usa a função auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Se seu editor implementar `IVsPersistDocData2` dessa maneira, a chamada para `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` é feita para você.

> [!NOTE]
>  Sempre fazer essas chamadas preventivamente — ou seja, quando o editor for capaz de receber um cancelamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permissão para adicionar, remover ou renomear arquivos no projeto
 Antes de um projeto pode adicionar, renomear ou remover um arquivo ou diretório, ele deve chamar o `IVsTrackProjectDocuments2::OnQuery*` método para solicitar permissão do ambiente. Se a permissão é concedida, o projeto deve concluir a operação e, em seguida, chamar o `IVsTrackProjectDocuments2::OnAfter*` método para notificar o ambiente que a operação foi concluída. O projeto deve chamar os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface para todos os arquivos (por exemplo, arquivos especiais) e não apenas o pai. Chamadas de arquivo são obrigatórias, mas as chamadas de diretório são opcionais. Se o projeto tiver informações de diretório, ele deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos, mas se ele não tiver essas informações, o ambiente deduzirá informações do diretório.

 O projeto não deve chamar os métodos de `IVsTrackProjectDocuments2` no projeto abrir ou fechar. Os ouvintes que quiser que essas informações durante a inicialização podem aguardar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> eventos e iterar por meio da solução para encontrar as informações necessárias. Durante o desligamento, essas informações não são necessárias. `IVsTrackProjectDocuments2` é fornecido pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Para cada adicionar, renomear e remover ação, há um `OnQuery*` método e uma `OnAfter*` método. Chamar o `OnQuery*` método pedir permissão para adicionar, renomear ou remover o arquivo ou diretório. Chamar o `OnAfter*` método depois que o arquivo ou diretório foi adicionado, renomeado ou removido e o estado do projeto reflete o novo estado.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)