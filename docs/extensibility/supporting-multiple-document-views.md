---
title: "Dando suporte a várias exibições de documento | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4efd76830356996bdf75c923f457d19d2381763c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-document-views"></a>Dando suporte a várias exibições de documento
Você pode fornecer mais de uma exibição de um documento com a criação de dados de documento separado e objetos de exibição de documento para o editor. Estes são alguns casos em que uma exibição de documento adicionais seria útil:  
  
-   Novo suporte de janela: você deseja que o editor para fornecer dois ou mais exibições do mesmo tipo, para que um usuário que já tem uma janela aberto no editor pode abrir uma nova janela, selecionando o **nova janela** comando o **janela** menu.  
  
-   Exibir o formulário e o código de suporte: você deseja que o editor para fornecer exibições de tipos diferentes. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por exemplo, fornece uma exibição de formulário e um modo de exibição de código.  
  
 Para obter mais informações sobre isso, consulte o procedimento CreateEditorInstance no arquivo EditorFactory.cs no projeto editor personalizado criado pelo modelo de pacote do Visual Studio. Para obter mais informações sobre esse projeto, consulte [passo a passo: Criando um Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Sincronizando modos de exibição  
 Quando você implementa vários modos de exibição, o objeto de dados de documento é responsável por manter todos os modos de exibição sincronizados com os dados. Você pode usar o evento tratamento interfaces em <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar os vários modos de exibição com os dados.  
  
 Se você não usar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para sincronizar os vários modos de exibição, em seguida, você deve implementar seu próprio sistema de eventos para controlar as alterações feitas no objeto de dados de documento. Você pode usar diferentes níveis de granularidade para manter várias exibições atualizadas. Com uma configuração de granularidade máximo, conforme você digita em um modo de exibição os outros modos de exibição são atualizados imediatamente. Com granularidade mínimo, outros modos de exibição não serão atualizados até que elas são habilitadas.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinar se dados de documento ainda estiver aberto  
 A tabela de documento (RDT) em execução no ambiente de desenvolvimento integrado (IDE) ajuda a controlar se os dados para um documento já estão abertos, conforme mostrado no diagrama a seguir.  
  
 ![Gráfico de DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Várias exibições  
  
 Por padrão, cada modo de exibição (objeto de exibição de documento) está contido no seu próprio quadro de janela (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Como já observado, no entanto, os dados de documento podem ser exibidos em vários modos de exibição. Para habilitar isso, o Visual Studio faz o RDT para determinar se o documento em questão já está aberto em um editor. Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para criar o editor, um valor não nulo é retornado no `punkDocDataExisting` parâmetro indica que o documento já está aberto em outro editor. Para obter mais informações sobre como as funções RDT, consulte [tabela de documento executando](../extensibility/internals/running-document-table.md).  
  
 No seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementação, examine o objeto de dados de documento retornado no `punkDocDataExisting` para determinar se os dados de documento são apropriados para seu editor. (Por exemplo, apenas os dados HTML devem ser exibidos por um editor de HTML.) Se for o caso, sua fábrica de editor deve fornecer um segundo modo de exibição para os dados. Se o `punkDocDataExisting` parâmetro não é `NULL`, é possível ou que o objeto de dados de documento é aberto em outro editor, ou, mais provavelmente, que já estão abertos em uma exibição diferente com o mesmo que o editor de dados de documento. Se os dados de documento está abertos em um editor diferente que não oferece suporte a sua fábrica de editor, Visual Studio Falha ao abrir a fábrica do editor. Para obter mais informações, consulte [como: anexar modos de exibição para dados de documento](../extensibility/how-to-attach-views-to-document-data.md).