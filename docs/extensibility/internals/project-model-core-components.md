---
title: Componentes principais do modelo de projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cfb9db9c354eb4c10ece0f5a8259f3d4a104e28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133089"
---
# <a name="project-model-core-components"></a>Componentes principais do projeto modelo
As tabelas a seguir expandem o modelo de projeto. As tabelas presentes breves descrições das interfaces e serviços identificados no modelo e as interfaces e os serviços associados a objetos específicos. Além disso, as tabelas de detalham de outras interfaces que são opcionais na criação do projeto e na manutenção dependendo dos requisitos do seu tipo de projeto específico.  
  
 Para obter mais informações, consulte [ferramentas de navegação de símbolo de suporte](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objeto de pacote  
  
|Interface|Comentários|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa um VSPackage no IDE e torna os seus serviços disponíveis para o IDE.|  
  
### <a name="project-factory-object"></a>Objeto de fábrica de projeto  
  
|Interface|Comentários|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gerencia a criação de novos projetos e abrir projetos existentes.|  
  
### <a name="project-objects"></a>Objetos do projeto  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gerencia a adição e remoção de itens de projeto, abre editores e mantém o mapeamento entre cada moniker do documento e o `VSITEMID`. Herda de `IVsProject` e `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gerencia as propriedades de navegação e exibição e fornece eventos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita comando execução semelhante do `IOleCommandTarget` para comandos como Recortar e renomear que se aplicam somente quando o foco está no Gerenciador de soluções.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Serve como a interface de destino do comando primário para uma hierarquia de projeto. É a interface padrão para consultar os objetos para os comandos de status ou o estado e a execução do comando. Disponível quando você não definiu o foco na janela do projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordena a persistência do estado do projeto. Normalmente, o estado do projeto é armazenado como um arquivo de projeto, mas pode ser adaptado para sistemas de armazenamento que não são baseados em arquivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite que o projeto gerenciar todos os aspectos de persistência para os itens de projeto, como arquivos em disco ou objetos em outros sistemas de armazenamento. O `IVsPeristHierarchyItem2` interface é usada para itens que não implementam a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordena as interações com controle do código fonte.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite que os projetos gerenciar informações de configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gerencia objetos de configuração de projeto, como configurações de depuração/versão. Criar, implantar e depurar operações sejam coordenadas por meio de objetos de configuração do projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por hierarquias para controlar a exclusão (destrutiva) ou remover opções (não destrutiva) para itens de hierarquia. Chamar a Interface de consulta no `IVsHierarchyDeleteHandler` de interface do `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornece a opção de implementação de com o objeto que suporta o `IVsCfgProvider2` interface em uma identidade diferente de COM que o objeto de projeto que implementa o `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface opcional implementada para tornar o seu projeto extensível por outros desenvolvedores. O `IVsProjectStartupServices` interface permite que um VSPackage de terceiros registrar um GUID que você manter em seu arquivo de projeto para que toda vez que o projeto é carregado, você carrega o GUID do serviço de terceiros em seu arquivo de projeto e chame `QueryService` para GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por hierarquias de origem em um `UIHierarchy` janela coordenar operações de área de transferência como Recortar, copiar e colar. Use o `AdviseClipboardHelperEvents` interface para registrar eventos de área de transferência.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornece informações sobre um item arrastado em relação a sua fonte de dados durante uma operação de arrastar e soltar em uma janela de hierarquia de interface do usuário. Chamado a partir de `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornece informações sobre um item arrastado em relação ao seu destino de soltar durante uma operação de arrastar e soltar em uma janela de hierarquia de interface do usuário. Chamado a partir de `IVsHierarchy` interface.|  
  
### <a name="configuration-object"></a>Objeto de configuração  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornece informações sobre uma configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite que os projetos gerenciar informações de configuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite que um projeto ser executado sob o controle do depurador.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por projetos de implantação que executam operações de implantação para outros projetos.|  
  
### <a name="configuration-builder-object"></a>Objeto de configuração de construtor  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gerencia a operação de criação de uma configuração projeto.|  
  
### <a name="additional-project-objects"></a>Objetos de projeto adicionais  
  
|Interfaces|Comentários|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Exibe propriedades de item de **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Exibe os resultados para implantação.|  
  
 A tabela a seguir apresenta uma breve descrição dos serviços identificados no modelo de projeto.  
  
### <a name="services"></a>Serviços  
  
|Serviço|Comentários|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usado por VSPackages que implementam os tipos de projeto para registrar que sua fábrica de projeto existe no IDE. O VSPackage deve chamar `QueryService` para esse serviço e registrar o alocador de seu projeto quando `IVsPackage::SetSite` método é chamado. Se o `SetSite` método não for chamado, o projeto não é instanciado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece acesso a noção de interno, interna do IDE da solução atual, como a capacidade de enumerar os projetos, criar novos projetos, observar as alterações do projeto e assim por diante.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chamado por projetos que desejo participar no controle de origem.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantém uma tabela de documentos abertos para determinar se um ou mais dos seus itens de projeto já estão abertos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contém as interfaces e métodos chamados para realmente abrir um item de projeto usando o editor padrão ou um editor específico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve ser chamado por todos os projetos ao adicionar, remover ou renomear seus itens.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gerencia alterações para um arquivo ou diretório e notifica os clientes quando os arquivos selecionados foram alterados no disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve ser chamado por todos os projetos e editores antes de serem sujas itens ou salvá-los.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gerencia a ordem das operações de compilação e implantação para configurações de projeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornece acesso aos serviços de nível baixo de depurador usado para a maioria dos controles de depuração.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita o acesso de VSPackages para obter informações sobre as seleções atuais e permite a comunicação com o **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece a funcionalidade básica do IDE relacionados à interface do usuário, como a capacidade de criar e enumerar janelas de ferramentas ou janelas de documentos ou relatar um erro para o usuário.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornece acesso à barra de status do IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Usado para implementar o modelo de automação. O modelo de projeto, você retornará um objeto de propriedades que permite que você cria uma instância do objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Usado para implementar eventos de área de transferência no objeto de projeto na hierarquia. `SVsUIHierWinClipboardHelper` permite que você corretamente identificador recortar, copiar e colar.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Não está em compilação: usando Classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)