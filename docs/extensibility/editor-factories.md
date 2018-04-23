---
title: Fábricas de editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>Fábricas de editor
Uma fábrica de editor cria objetos do editor e o coloca em um quadro de janela, conhecido como um modo de exibição físico. Ele cria os dados de documento e objetos de exibição de documento que são necessários para criar editores e designers. Uma fábrica de editor é necessário para criar o editor de núcleo do Visual Studio e qualquer editor padrão. Um editor personalizado também pode ser criado com uma fábrica de editor.  
  
 Criar uma fábrica de editor Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. O exemplo a seguir ilustra como implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para criar uma fábrica de editor:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Um editor é carregado na primeira vez que você abre um tipo de arquivo tratado pelo editor. Você pode optar por abrir um editor específico ou o editor padrão. Se você selecionar o editor padrão, o ambiente de desenvolvimento integrado (IDE) determina o editor correto para abrir e abre-lo. Para obter mais informações, consulte [determinar qual Editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrar fábricas de Editor  
 Antes de usar um editor que você criou, primeiro você deve registrar informações sobre ele, incluindo as extensões de arquivo que pode manipular.  
  
 Se seu VSPackage é escrito em código gerenciado, você pode usar o método gerenciado pacote MPF (estrutura) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para registrar a fábrica do editor após o VSPackage é carregado. Se seu VSPackage é escrito em código não gerenciado, você deve registrar a fábrica do editor usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> service.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrar uma fábrica de Editor usando código gerenciado  
 Você deve registrar sua fábrica de editor no seu VSPackage o `Initialize` método. Primeiro chamar `base.Initialize`e, em seguida, chame <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada fábrica de editor  
  
 No código gerenciado, não é necessário para cancelar o registro de uma fábrica de editor, pois o VSPackage tratará isso para você. Além disso, se sua fábrica de editor implementar <xref:System.IDisposable>, ele é descartado automaticamente quando ele está registrado.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrar uma fábrica de editor usando código não gerenciado  
 No <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação para seu pacote do editor, use o `QueryService` método chamar `SVsRegisterEditors`. Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método passando sua implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. Você deve mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> em uma classe separada.  
  
## <a name="the-editor-factory-registration-process"></a>O processo de registro de fábrica de Editor  
 O seguinte processo ocorre quando o Visual Studio carrega seu editor usando a fábrica do editor:  
  
1.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chamadas do sistema de projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Esse método retorna a fábrica do editor. Atrasos de Studio Visual ao carregar o pacote do editor, no entanto, até que um sistema de projeto realmente precisa do editor.  
  
3.  Quando um sistema de projeto requer o editor, o Visual Studio chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, um método especializado que retorna o modo de exibição de documento e o documento de objetos de dados.  
  
4.  Se chamadas pelo Visual Studio para a fábrica do editor usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> retornar um objeto de dados de documento e um objeto de exibição de documento, o Visual Studio, em seguida, cria a janela do documento, coloca o objeto de exibição de documento nele e cria uma entrada no documento em execução tabela (RDT) para o objeto de dados de documento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabela de documentos em execução](../extensibility/internals/running-document-table.md)