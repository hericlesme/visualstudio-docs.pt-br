---
title: Constantes IDE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 817c95d511ff1b02558010f3046827684b72d4f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ide-constants"></a>Constantes IDE
O <xref:Microsoft.VisualStudio.VSConstants> classe fornece constantes que são específicos para o ambiente de desenvolvimento integrado (IDE) e que foram definidos anteriormente apenas em arquivos de cabeçalho.  
  
## <a name="logical-and-physical-views"></a>Modos de exibição lógicos e físicos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores devem passar esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obter o **abrir com** caixa de diálogo, neste caso sobre possíveis modos de exibição de código.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores passam esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obter o **abrir com** caixa de diálogo, nesse caso é populada com possíveis <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> depuração modos de exibição que mapeiam para a mesma exibição da <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores passam esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obter o **abrir com** caixa de diálogo, nesse caso para **Exibir formulário** exibições do designer.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores passam esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obter o **abrir com** caixa de diálogo, neste caso, o modo de exibição padrão/primário da fábrica de editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores passam esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obter o **abrir com** caixa de diálogo para uma exibição de editor de texto do documento ou dados.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` manipuladores passam esse valor para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método que solicita ao usuário para escolher qual modo de exibição definida pelo usuário a ser usado.|  
  
## <a name="editor-factory-flags"></a>Sinalizadores de fábrica de editor  
  
|Valor|Descrição|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Um sinalizador obsoleto bit a bit como o primeiro parâmetro de combinado a <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Combinação bit a bit como o primeiro parâmetro do <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, método, isso indica que a fábrica do editor deve executar as correções necessárias.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Combinação bit a bit como o primeiro parâmetro do <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , esse sinalizador é mutuamente do <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Combinação bit a bit como o primeiro parâmetro do <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método, isso indica que a fábrica do editor deve criar o editor sem exibir uma interface do usuário (IU).|  
  
## <a name="visual-studio-errors"></a>Erros do Visual Studio  
  
|Valor|Descrição|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Uma constante retornada por interfaces com comportamento assíncrono quando o objeto em questão no já está ocupado|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para "dados de documento incompatível".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica que o "Pacote não foi carregado."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica que o "Projeto já existe".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica "Falha na configuração de projeto".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica "Projeto não carregado."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica "Solução já está aberta."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica "Solução não está aberta."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retornado por interfaces de compilação que têm parâmetros para especificar uma matriz do <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interface, mas a implementação pode aplicar somente o método para todas as saídas.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|O <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método retorna esse valor se o documento possui um formato que não pode ser aberto no editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Um valor HRESULT que indica que o usuário pressione o botão Voltar em uma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] assistente.|  
  
## <a name="visual-studio-constants"></a>Constantes do Visual Studio  
  
|Valor|Descrição|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Um erro HRESULT que é específico para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e que indica "Projeto encaminhado".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Uma constante que é específica para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para um "marcador de caixa de ferramentas".|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Uma constante que é específica para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para transmitir uma mensagem de notificação por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica o início do modalidade.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Uma constante que é específica para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para transmitir uma mensagem de notificação por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica o fim do modalidade.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Uma constante que é específica para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para transmitir uma mensagem de notificação por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método indicando que as métricas de barra de comando foram alteradas.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Uma constante que é específica para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que indica que um cookie não foi definido.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|Um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador do item que representa a ausência de um item de projeto. Esse valor é usado quando não houver nenhuma seleção atual.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|Um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador do item que representa a raiz de uma hierarquia de projeto e é usado para identificar a toda a hierarquia, em vez de um único item.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|Um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador do item que representa o item selecionado no momento ou itens, que podem incluir a raiz da hierarquia.|  
  
## <a name="ivsselectionevents"></a>IVsSelectionEvents  
 Descreve qual componente do IDE apenas foi selecionado, em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> chamar, por exemplo.  
  
|Constante|Valor|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## <a name="vsselelemid"></a>VSSELELEMID  
 Constantes usadas para indicar um novo estado de seleção.  
  
|Constante|Valor|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## <a name="component-selector-dialog-constants"></a>Constantes de caixa de diálogo de seletor de componente  
  
|Constante|Valor|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|  
  
## <a name="see-also"></a>Consulte também  
 [Comandos definidos pelo IDE para estender sistemas de projeto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)