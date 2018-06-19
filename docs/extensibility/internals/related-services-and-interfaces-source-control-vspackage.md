---
title: Interfaces (VSPackage de controle de origem) e serviços relacionados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f9e8e90fdda61524a9af107df452bc2b13cd90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135346"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces (VSPackage de controle de origem) e serviços relacionados
Esta seção lista todas as interfaces relacionadas VSPackage de controle de fonte do [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. O controle de origem VSPackage implementa algumas dessas interfaces e usa outros para realizar tarefas de controle de origem.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por e para VSPackages de controle do código-fonte  
 As seguintes interfaces são descritas no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], e o controle de origem VSPackage implementa um subconjunto delas dependendo de seu conjunto de recursos desejados. Algumas interfaces são marcados como obrigatório e deve ser implementado por cada VSPackage do controle de origem.  
  
 Para interfaces que não implementa um pacote, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece uma implementação padrão. Observe que a implementação padrão foi criada para o caso quando nenhum VSPackage é registrado e nenhum projeto é controlado. Um controle do código-fonte escrito corretamente VSPackage implementa interfaces todas as mídias necessárias em vez de deixá-lo para a implementação padrão dessas interfaces.  
  
 Um controle de origem VSPackage deve implementar um serviço particular que encapsula a algumas ou todas as interfaces a seguir.  
  
 Interfaces são:  
  
-   Obrigatório: A entidade apropriada (projeto de controle de origem VSPackage, Stub de controle do código-fonte,) deve implementar a interface.  
  
-   Recomendável: A entidade deve implementar essa interface; Caso contrário, a funcionalidade de controle de origem pode ser limitada.  
  
-   Opcional: a entidade pode implementar essa interface para fornecer um conjunto de recursos mais avançado.  
  
|Interface|Finalidade|Implementado pelo|Implementar?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editores de chamar essa interface antes de modificar ou salvar um arquivo. O controle de origem VSPackage pode check-out do arquivo ou negar a operação se o check-out falhar.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Essa interface fornece funcionalidade de controle de origem básico para projetos, como registrar e cancelar o registro de projetos com controle de origem e dando suporte a marcas de controle de origem básico.|Controle de origem VSPackage|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Essa interface é obtida a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> usando o <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> função, ou simplesmente convertendo o objeto que implementa `IVsHierarchy` para `IVsSccProject2`. Ele é usado para obter os arquivos sob controle de origem em um projeto ou para informar o projeto do status atual de controle de origem ou local.|Projeto|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|O módulo de integração usa essa interface para definir o VSPackage ativado atual.|Controle de origem VSPackage|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Essa interface é baseada em um modelo de assinatura. Qualquer VSPackage pode sinalizar que deseja receber eventos de documento e ser avisados pelo shell em eventos que estão prestes a ocorrer. Ele está implementado e controlado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que passa eventos Implementando o `IVsTrackProjectDocumentsEvents2` para o VSPackage.|Stub de controle do código-fonte|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Essa interface fornece processamento em lotes, as operações de leitura/gravação sincronizados e um avançado `OnQueryAddFiles` método.|Stub de controle do código-fonte|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Gerenciador de soluções** e projetos chamam esta interface quando novos arquivos são adicionados aos projetos, ou quando arquivos e pastas são renomeadas ou excluídas de projetos. O controle de origem VSPackage pode check-out do arquivo de projeto ou cancelar a operação.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Gerenciador de soluções** e projetos de chamar essa interface em resposta a chamadas para os métodos da interface IVstrackProjectDocuments3. O controle de origem VSPackage pode controlar operações em lotes, sincronizadas operações de leitura/gravação e trabalhar com mais avançados `OnQueryAddFiles` método.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Essa interface fornece suporte para projetos Web do gerenciamento de inscrição.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Essa interface é usada para recuperar as dicas de ferramenta para os arquivos de controle do código-fonte nos projetos.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Essa interface fornece suporte à extensão de namespace.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|O VSPackage usa essa interface para integrar uma extensão de namespace para o **novo**, **abrir**, ou **salvar** caixas de diálogo. Consequentemente, projetos podem ser automaticamente adicionados ao controle de origem na criação ou adicionados ao controle de origem quando salvar operação está em vigor.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|O VSPackage usa essa interface para definir glifos adicionais como glifos de controle de origem para nós **Gerenciador de soluções**.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|O **adicionar** caixa de diálogo para projetos Web usa essa interface. Fornece métodos para navegar para um local de controle de origem e para abrir um projeto Web adicionado anteriormente no repositório de controle de origem nesse local.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Essa interface fornece suporte para o carregamento assíncrono (em segundo plano) de projetos de controle de origem.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Essa interface permite que os projetos observar o progresso de carregamento assíncrono iniciado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Projeto|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Essa interface permite que o IDE consultar o controle de origem ativa VSPackage. O IDE consulta o valor de configurações de controle de origem que têm significado, mesmo quando não há nenhum controle de origem ativa que VSPackage registrado. Essa interface é implementada e manipulada pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub de controle do código-fonte|Necessária|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Essa interface é usada no registro de controle de origem VSPackage.|Stub de controle do código-fonte|Necessária|  
|<xref:EnvDTE.SourceControl>|Essa interface é usada na automação. Como tal, ele expõe apenas as funções que podem ser executadas sem exibir nenhuma interface do usuário.|Controle de origem VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Essa interface é usada para salvar a fonte de configurações de controle no arquivo de solução (. sln). As configurações incluem o local do controle de origem e os sinalizadores de status de controle do código-fonte.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Essa interface é usada para salvar as configurações de controle de origem no arquivo de opções (. suo) da solução. Isso pode incluir configurações de controle de origem específicas do usuário, como local de inscrição do usuário atual.|Controle de origem VSPackage|Recomendado|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Essa interface é usada para monitorar eventos para executar operações como check-in de arquivos de projeto antes de fechar soluções ou obter novos arquivos de controle de origem ao abrir um projeto.|Controle de origem VSPackage|Recomendado|  
  
## <a name="see-also"></a>Consulte também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)