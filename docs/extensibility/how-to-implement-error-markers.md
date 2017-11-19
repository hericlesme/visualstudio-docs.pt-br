---
title: 'Como: implementar marcadores de erro | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d926a498549e868e478d83b7930f5e569f49ce20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-error-markers"></a>Como: implementar marcadores de erro
Marcadores de erro (ou um sublinhado vermelho ondulado) é as personalizações do editor de texto para implementar mais difícil. No entanto, os benefícios que eles oferecem aos usuários do seu VSPackage agora podem exceder o custo para fornecê-los. Marcadores de erro sutilmente marcam o texto que o analisador de linguagem considerar incorreto com uma linha vermelha curvada ou ondulada. Este indicador ajuda a programadores visualmente exibindo o código incorreto.  
  
 Use marcadores de texto para implementar um sublinhado vermelho ondulado. Como regra, serviços de linguagem adicionar um sublinhado vermelho ondulado para o buffer de texto como uma passagem de plano de fundo, em tempo ocioso ou em um thread em segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar o recurso de sublinhado vermelho ondulado  
  
1.  Selecione o texto no qual você deseja colocar o sublinhado vermelho ondulado.  
  
2.  Criar um marcador do tipo `MARKER_CODESENSE_ERROR`. Para obter mais informações, consulte [como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Depois disso, passar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ponteiro de interface.  
  
 Esse processo também permite que você crie o texto da dica ou um menu de contexto especiais sobre um marcador de determinado. Para obter mais informações, consulte [como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
 Os seguintes objetos serão necessários para que os marcadores de erro podem ser exibidos.  
  
-   Um analisador.  
  
-   Um provedor de tarefa (ou seja, uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) que mantém um registro das alterações nas informações de linha para identificar as linhas para ser analisado novamente.  
  
-   Eventos de alteração de um filtro de exibição de texto que captura o cursor do modo de exibição usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) método.  
  
 O analisador, o provedor de tarefas e o filtro fornecem a infraestrutura necessária possibilitar a marcadores de erro. As etapas a seguir fornecem o processo de exibição de marcadores de erro.  
  
1.  Em uma exibição que está sendo filtrada, o filtro obtém um ponteiro para o provedor de tarefa associado aos dados do modo de exibição.  
  
    > [!NOTE]
    >  Você pode usar o mesmo filtro de comando para o método dicas, conclusão de instrução, marcadores de erro e assim por diante.  
  
2.  Quando o filtro recebe um evento indicando que você tiver movido para outra linha, uma tarefa é criada para verificar se há erros.  
  
3.  O manipulador de tarefa verifica se a linha foi alterada. Nesse caso, ele analisa a linha de erros.  
  
4.  Se forem encontrados erros, o provedor de tarefas cria uma instância do item de tarefa. Esta instância cria o marcador de texto que usa o ambiente como um marcador de erro no modo de exibição de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)