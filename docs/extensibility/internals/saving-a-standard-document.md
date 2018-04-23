---
title: Salvar um documento padrão | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45fa2c5acfad8195ed2853d7e21413b77262a6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="saving-a-standard-document"></a>Salvar um documento padrão
O ambiente trata a salvar, salvar como e salvar todos os comandos. Quando um usuário seleciona **salvar**, **Salvar como**, ou **Salvar tudo** do **arquivo** menu ou fecha a solução, resultando em um  **Salvar todos os**, ocorre o seguinte processo.  
  
 ![Editor padrão](../../extensibility/internals/media/public.gif "pública")  
Salvar, salvar como e tratamento de um editor padrão de comando Salvar tudo  
  
 Esse processo é detalhado nas etapas a seguir:  
  
1.  Quando o **salvar** e **Salvar como** comandos são selecionados, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de serviço para determinar a janela do documento ativo e, portanto, os itens devem ser salvos. Depois que a janela do documento ativo é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador de item (itemID) para o documento na tabela de documento em execução. Para obter mais informações, consulte [tabela de documento executando](../../extensibility/internals/running-document-table.md).  
  
     Quando o **Salvar tudo** comando estiver selecionado, o ambiente usa as informações na tabela de documento em execução para compilar a lista de todos os itens para salvar.  
  
2.  Quando a solução recebe um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chamada, itera por meio do conjunto de itens selecionados (ou seja, as várias seleções expostas pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> serviço).  
  
3.  Em cada item na seleção, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar se o **salvar** comando de menu deve ser habilitado. Se um ou mais itens estiverem sujos, em seguida, o **salvar** comando está ativado. Se a hierarquia usa um editor padrão, em seguida, os representantes de hierarquia consultando sujas status para o editor chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.  
  
4.  Em cada item selecionado que foi alterado, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método nas hierarquias apropriados.  
  
     É comum para a hierarquia usando um editor padrão para editar o documento. Nesse caso, os dados de documento de objeto para esse editor deve oferecer suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface. Após receber a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> chamada de método, o projeto deve informar o editor que o documento está sendo salvo chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> método no objeto de dados de documento. O editor pode permitir que o ambiente lidar com o **Salvar como** caixa de diálogo, chamando `Query Service` para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interface. Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface. O editor deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> método, passando um ponteiro para o editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementação por meio do `pPersistFile` parâmetro. O ambiente, em seguida, executa a operação de salvamento e fornece o **Salvar como** caixa de diálogo para o editor. O ambiente, em seguida, chama de volta para o editor com <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Se o usuário está tentando salvar um documento sem título (ou seja, um documento não salvo anteriormente), um comando Salvar como, na verdade, é executado.  
  
6.  Para o comando Salvar como, o ambiente exibe a caixa de diálogo Salvar como, solicitar ao usuário um nome de arquivo.  
  
     Se o nome do arquivo foi alterado, a hierarquia é responsável por atualizar o quadro do documento informações armazenadas em cache chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Se o **Salvar como** comando move o local do documento e a hierarquia é sensível ao local do documento, a hierarquia é responsável pelo envio de propriedade da janela de documento aberto para outra hierarquia. Por exemplo, isso ocorre se o projeto controla se o arquivo é um arquivo (arquivo diverso) interno ou externo em relação ao projeto. Use o procedimento a seguir para alterar a propriedade de um arquivo ao projeto arquivos diversos.  
  
## <a name="changing-file-ownership"></a>Alterar o proprietário do arquivo  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para alterar a propriedade de arquivo ao projeto arquivos diversos  
  
1.  Consultar o serviço para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interface.  
  
     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> é retornado.  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) método para transferir o documento para a nova hierarquia. A hierarquia de executar o comando Salvar como chama esse método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)