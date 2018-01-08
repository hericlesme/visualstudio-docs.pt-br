---
title: 'Passo a passo: Adicionando recursos para um Editor personalizado | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3c207b80686a66d9a06b8c50321b4dce2257ada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Passo a passo: Adicionando recursos para um Editor personalizado
Depois de criar um editor personalizado, você pode adicionar mais recursos a ele.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Para criar um editor para um VSPackage  
  
1.  Crie um editor personalizado usando o modelo de projeto de pacote do Visual Studio.  
  
     Para obter mais informações, consulte [passo a passo: Criando um Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decida se deseja que o editor para dar suporte a um modo de exibição único ou vários modos de exibição.  
  
     Um editor que ofereça suporte a **nova janela** de comando, ou com exibição de formulário e exibição de código, requer que os objetos de dados de documento separado e objetos de exibição do documento. Em um editor que oferece suporte a apenas um modo de exibição, o objeto de dados de documento e o objeto de exibição de documento podem ser implementados no mesmo objeto.  
  
     Para obter um exemplo de vários modos de exibição, consulte [dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementar uma fábrica de editor Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
     Para obter mais informações, consulte [fábricas](../extensibility/editor-factories.md).  
  
4.  Decida se deseja que o editor para usar a ativação no local ou simplificado inserindo para gerenciar a janela de objeto de exibição do documento.  
  
     Uma janela do editor de inserção simplificada hospeda uma visualização de documento padrão, enquanto uma janela do editor de ativação no local hospeda um controle ActiveX ou em outro objeto ativo como seu modo de exibição do documento. Para obter mais informações, consulte [simplificado inserindo](../extensibility/simplified-embedding.md) e [ativação no local](../extensibility/in-place-activation.md).  
  
5.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface para lidar com comandos.  
  
6.  Fornece persistência de documento e resposta a alterações de arquivo externo, fazendo o seguinte:  
  
    1.  Para manter o arquivo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> no objeto de dados de documento do editor.  
  
    2.  Para responder às alterações de arquivo externo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> no objeto de dados de documento do editor.  
  
        > [!NOTE]
        >  Chamar `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obter um ponteiro para `IVsFileChangeEx`.  
  
7.  Coordene eventos de edição de documentos com controle do código fonte. Para fazer isso:  
  
    1.  Obter um ponteiro para `IVsQueryEditQuerySave2` chamando `QueryService` em <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Quando ocorre o primeiro evento de edição, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método.  
  
         Isso solicita que o usuário fazer check-out do arquivo se ele já não é check-out. Certifique-se de lidar com uma condição "não check-out file" para evitar erros  
  
    3.  Da mesma forma, antes de salvar o arquivo, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> método.  
  
         Esse método solicita ao usuário para salvar o arquivo se ele não tiver sido salvo, ou se ele foi alterado desde a última gravação.  
  
8.  Habilitar o **propriedades** janela para exibir as propriedades de texto selecionado no editor. Para fazer isso:  
  
    1.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada seleção de texto de hora for alterado, passando na implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Chamar `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service para obter um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permitir que os usuários arrastar e soltar itens entre o editor e o **caixa de ferramentas**, ou entre editores externos (como o Microsoft Word) e o **caixa de ferramentas**. Para fazer isso:  
  
    1.  Implementar `IDropTarget` em seu editor de IDE de alerta que o editor é um destino de soltar.  
  
    2.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface no modo de exibição para o editor pode habilitar e desabilitar itens de **caixa de ferramentas**.  
  
    3.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chame `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service para obter um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Isso permite que o VSPackage adicionar novos itens de **caixa de ferramentas**.  
  
10. Decida se deseja que os outros recursos opcionais para o editor.  
  
    -   Se você deseja que o editor para dar suporte a localizar e substituir comandos, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Se você quiser usar uma janela de ferramentas da estrutura de tópicos de documento em seu editor, implemente `IVsDocOutlineProvider`.  
  
    -   Se você quiser usar uma barra de status em seu editor, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> e chame `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> para obter um ponteiro para `IVsStatusBar`.  
  
         Por exemplo, um editor pode exibir linha / informações de coluna, o modo de seleção (transmitir / caixa) e o modo de inserção (Inserir / sobrescrever).  
  
    -   Se você deseja que o editor para dar suporte a `Undo` de comando, o método recomendado é usar o modelo do Gerenciador de desfazer OLE. Como alternativa, você pode ter o identificador do editor de `Undo` comando diretamente.  
  
11. Crie registro de informações, incluindo os GUIDs para o VSPackage, os menus, o editor e outros recursos.  
  
     Este é um exemplo genérico de código que você deve colocar o script do arquivo. rgs para demonstrar como se registrar corretamente um editor.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementa o suporte a Ajuda contextual.  
  
     Isso permite que você forneça suportam a Ajuda de F1 e a janela Ajuda dinâmica para itens em seu editor. Para obter mais informações sobre isso, consulte [como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Expor um modelo de objeto de automação do seu editor Implementando o `IDispatch` interface.  
  
     Para obter mais informações, consulte [que contribuem para o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programação robusta  
  
-   A instância de editor é criada quando o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. Se o editor oferece suporte a vários modos de exibição `CreateEditorInstance` cria dados de documento e os objetos de exibição do documento. Se o objeto de dados de documento já está aberto, não null `punkDocDataExisting` valor é passado para `IVsEditorFactory::CreateEditorInstance`. A implementação de fábrica de editor deve determinar se um objeto de dados de documento existente é compatível por meio de consulta para interfaces apropriadas nele. Para obter mais informações, consulte [dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Se você usar a abordagem de incorporação simplificada, implemente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface.  
  
-   Se você decidir usar a ativação no local, implemente as seguintes interfaces:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  O `IOleInPlaceComponent` interface é usada para evitar a mesclagem de menus OLE 2.  
  
     O `IOleCommandTarget` implementação controla como os comandos **Recortar**, **cópia**, e **colar**. Ao implementar `IOleCommandTarget`, decidir se seu editor requer seu próprio arquivo. VSCT para definir sua própria estrutura de menu de comando ou se ela pode implementar comandos padrão definidos pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Normalmente, editores de usarem e estendem os menus do IDE e definem suas próprias barras de ferramentas. No entanto, muitas vezes é necessário para um editor definir seus próprios comandos específicos, além de usar o conjunto de comando padrão do IDE. Para fazer isso, seu editor deve declarar os comandos padrão, ele usa e, em seguida, defina quaisquer novos comandos menus de contexto, menus de nível superior e barras de ferramentas em um arquivo. VSCT. Se você criar uma ativação in-loco editor, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e defina os menus e barras de ferramentas para o editor em um arquivo. VSCT em vez de usar a mesclagem de menus OLE 2.  
  
-   Para evitar que o comando de menu lotado na interface de usuário, você deve usar os comandos existentes no IDE antes da criação de novos comandos. Comandos compartilhados são definidos em SharedCmdDef.vsct e ShellCmdDef.vsct. Esses arquivos são instalados por padrão no subdiretório VisualStudioIntegration\Common\Inc do seu [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalação.  
  
-   `ISelectionContainer`pode expressar único e de várias seleções. Cada objeto selecionado é implementado como um `IDispatch` objeto.  
  
-   Implementa o IDE `IOleUndoManager` como um serviço acessível de uma <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou como um objeto que pode ser instanciado pelo <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementa o editor de `IOleUndoUnit` interface para cada `Undo` ação.  
  
-   Há dois locais um editor personalizado pode expor objetos de automação:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Consulte também  
 [Que contribuem para o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md)