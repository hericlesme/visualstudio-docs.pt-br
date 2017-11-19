---
title: "Criando o Editor de núcleo usando a API herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a82f420203b88bb94531401d061493621f3eba93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Criando o Editor de núcleo usando a API herdado
O editor é responsável por funções, como inserção, exclusão, copiar e colar de edição de texto. Ele combina essas funções com aqueles fornecidos pelos serviços de idioma, como cor de texto, recuo e conclusão de instrução do IntelliSense.  
  
 Você pode instanciar uma instância do editor de núcleo de uma das três maneiras:  
  
-   Crie explicitamente uma instância do núcleo do editor em uma janela.  
  
-   Forneça uma fábrica de editor que retorna uma instância do editor de núcleo  
  
-   Abra um arquivo da hierarquia de projeto.  
  
 As seções a seguir descrevem como usar a API herdada para instanciar o editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Abrindo explicitamente uma instância do Editor de núcleo  
 Ao obter explicitamente uma instância do editor principais:  
  
-   Obter um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para manter o objeto de dados de documento que está sendo editado.  
  
-   Criar uma representação de linha orientada do objeto de dados de documento, criando uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> de interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface.  
  
-   Definir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como o objeto de dados de documento para uma instância da implementação padrão do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interface, usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> método.  
  
     Host de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instância em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> método.  
  
 Neste ponto, exibindo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface fornece uma janela que contém uma instância do editor de núcleo.  
  
 No entanto, isso não é uma instância muito útil, porque ele não tem teclas de atalho, ou acesso a recursos avançados. Para obter acesso a recursos avançados e teclas de atalho:  
  
-   Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método associar um serviço de idioma e o objeto de dados de documento que usa o editor.  
  
-   Crie suas próprias teclas de atalho, ou use o padrão do sistema, definindo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objetos exibem propriedades. Para fazer isso, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propriedade.  
  
     Para obter e usar as teclas de atalho não padrão, gerá-los usando o arquivo. VSCT. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Como usar uma fábrica de Editor para obter o Editor de núcleo  
 Ao implementar um editor de núcleo com um editor de fábrica usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, siga todas as etapas descritas na seção anterior para hospedar explicitamente um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> usando um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de dados de documento, em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.  
  
 Para exibir o texto, obter um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> de interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto e chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para fornecer um serviço de idioma para o editor, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método dentro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para obter padrão teclas de atalho, diferentemente da seção anterior, você usar o contexto do comando retornado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método ao obter o editor de núcleo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método retorna o mesmo comando GUID como o editor de texto, a instância do editor de núcleo obtém automaticamente o padrão teclas de atalho.  
  
 Para obter informações gerais, consulte [passo a passo: Criando um Editor de núcleo e registrando um tipo de arquivo do Editor de](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Abrir e salvar itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Passo a passo: Criando um Editor de núcleo e registrando um tipo de arquivo do Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)