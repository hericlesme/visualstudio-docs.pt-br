---
title: Elemento VisibilityItem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
O `VisibilityItem` elemento determina a visibilidade estática de comandos e barras de ferramentas. Cada entrada identifica um comando ou menu e um contexto de interface do usuário de comando associado. O Visual Studio detecta comandos, menus e barras de ferramentas e sua visibilidade, sem carregar os VSPackages que defini-los. O IDE usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método para determinar se um contexto de interface do usuário de comando está ativo.  
  
 Após o VSPackage é carregado, o Visual Studio espera visibilidade de comando seja determinado pelo VSPackage em vez de `VisibilityItem`. Para determinar a visibilidade do comando, você pode implementar o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> manipulador de eventos ou o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, dependendo de como você implementou o comando.  
  
 Um comando ou o menu tem uma `VisibilityItem` elemento aparece somente quando o contexto associado está ativo. Você pode associar um único comando, um menu ou barra de ferramentas com um ou mais contextos de interface do usuário de comando, incluindo uma entrada para cada combinação de contexto do comando. Se um comando ou menu estiver associado a vários contextos de interface do usuário de comando, em seguida, o comando ou o menu é visível quando qualquer um dos contextos de interface do usuário de comando associado está ativo.  
  
 O `VisibilityItem` elemento só se aplica a comandos, menus e barras de ferramentas, não a grupos. Um elemento que não tem um relacionados `VisibilityItem` elemento estiver visível, sempre que o menu pai está ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O GUID do identificador de comando GUID ID.|  
|id|Necessário. A ID do identificador de comando GUID ID.|  
|contexto|Necessário. O contexto de interface do usuário no qual o comando fica visível.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|O `VisibilityConstraints` elemento determina a visibilidade estática dos grupos de comandos e barras de ferramentas.|  
  
## <a name="remarks"></a>Comentários  
 Os contextos de interface de usuário do Visual Studio padrão são definidos no *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Common\Inc\vsshlids.h arquivo, bem como no <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classes. Um conjunto mais completo de contextos de interface do usuário é definido no <xref:Microsoft.VisualStudio.VSConstants> classe.  
  
## <a name="example"></a>Exemplo  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)