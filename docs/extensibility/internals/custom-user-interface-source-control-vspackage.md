---
title: "Interface de usuário personalizada (VSPackage de controle do código-fonte) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d3c223b45d0228781779a73f057ef3518374344
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface de usuário personalizada (VSPackage de controle de origem)
Um VSPackage declara seus itens de menu e seus estados de padrão por meio do arquivo de tabela de comando do Visual Studio (. VSCT). O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) exibe os itens de menu em seus estados padrão até que o VSPackage é carregado. Subsequentemente, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é chamado para habilitar ou desabilitar itens de menu.  
  
 Um VSPackage pode definir uma chave do registro para que o VSPackage possa ser carregado automaticamente dependendo do contexto de interface do usuário de um usuário de comando, embora normalmente uma fonte de controlar VSPackage deve carregar sob demanda em vez de simplesmente alternar para um determinado contexto de interface do usuário. Para obter mais informações sobre a chave de registro AutoLoadPackages, consulte [Gerenciando VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interface de usuário VSPackage  
 Um pacote de controle de origem é implementado como um VSPackage e não usa nenhuma interface do usuário do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada controle de origem VSPackage deve especificar seus próprio elementos de interface do usuário como itens de menu, grupos de menus, janelas de ferramentas, barras de ferramentas e qualquer interface de usuário necessária para definir opções específicas para o controle de origem VSPackage. Esses elementos de interface do usuário podem ser habilitados estática ou dinamicamente. Elementos de interface do usuário estáticos são definidos em um arquivo. VSCT e são exibidos se o VSPackage está carregado ou não. Elementos de interface do usuário dinâmicos podem estar visíveis dependendo de contexto de interface do usuário um comando específico, como <xref:EnvDTE.Constants.vsContextNoSolution>, ou como resultado de uma chamada para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. A visibilidade dos elementos de interface do usuário dinâmicas está em conformidade com a estratégia para carregamento atrasado de VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Restrições de interface do usuário em VSPackages de controle do código-fonte  
 Como não é possível remover o controle de origem VSPackage IDE depois que ela é carregada, o VSPackage deve ser capaz de entrar em um estado inativo. Quando um VSPackage recebe notificação que ele não está mais ativo, o VSPackage desabilita sua interface de usuário e ignora qualquer interação externa do IDE. Implementação do VSPackage o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método deve ocultar comandos quando o VSPackage não está ativo.  
  
 Cada controle de origem VSPackage deve implementar o `IVsSccProvider` interface. Dois métodos na interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, deve ser implementada pelo VSPackage.  
  
 O controle de origem VSPackage pode se inscreveu para vários eventos IDE, que são implementados pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>e assim por diante. Além disso, o VSPackage pode ter implementado interfaces habilitadas para registro de retorno de chamada, como o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Estes devem todas ser ignorados quando inativo.  
  
 A lista a seguir mostra as interfaces com o estado ativo de um controle de origem VSPackage:  
  
-   Rastrear eventos de documentos do projeto.  
  
-   Eventos de solução.  
  
-   Interfaces de persistência de solução. Quando inativo, pacotes não devem gravar os arquivos. sln e. suo.  
  
-   Extensores de propriedade.  
  
 Obrigatório <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e também quaisquer interfaces opcionais associados a controle de origem, não são chamados quando o controle de origem VSPackage está inativo.  
  
 Quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE inicia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] define o contexto de interface do usuário de comando para a identificação do controle de origem padrão atual ID VSPackage. Isso faz com que a interface do usuário estático do controle de origem ativa VSPackage apareça no IDE sem carregar realmente o VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]faz uma pausa para o VSPackage registrar com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> antes de fazer qualquer chamada para o VSPackage.  
  
 A tabela a seguir descreve os detalhes específicos sobre como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta diferentes itens de interface do usuário.  
  
|Item de interface do usuário|Descrição|  
|-------------|-----------------|  
|Menus e barras de ferramentas|O pacote de controle de origem deve definir os estados de visibilidade inicias do menu e barra de ferramentas para a ID de pacote de controle de origem no [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) seção do arquivo. VSCT. Isso permite que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE para definir o estado dos itens de menu adequadamente sem carregar o VSPackage e chamar uma implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.|  
|Janelas de ferramentas|O controle de origem VSPackage oculta quaisquer janelas de ferramentas que possui quando ela se torna inativo.|  
|Opções de controle de origem específico VSPackage páginas|A chave do registro HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts permite que um VSPackage defina os contextos em que ele requer que suas páginas de opções a serem exibidos. Uma entrada de registro sob essa chave precisa ser criada usando o serviço SID (ID) do serviço de controle de origem e atribuindo um valor DWORD de 1. Sempre que ocorre um evento de interface do usuário em um contexto VSPackage é registrado com o controle de origem, o VSPackage será chamado se ele estiver ativo.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gerenciar VSPackages](../../extensibility/managing-vspackages.md)