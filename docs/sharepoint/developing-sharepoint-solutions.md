---
title: "Desenvolver soluções do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 848ddab54dd9e7617cce7758fa06d939700f2c3b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="developing-sharepoint-solutions"></a>Desenvolvendo soluções do SharePoint
  Vários modelos de tipo de projeto do SharePoint estão disponíveis em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para a criação de sites do SharePoint e os elementos do site. Para obter uma lista dos tipos de projeto disponíveis, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md). A seguir está uma descrição dos elementos e propriedades de um projeto do SharePoint.  
  
 Para obter informações sobre os suplementos do SharePoint e SharePoint 2013, consulte [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) e [suplementos do SharePoint criar](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx).  
  
## <a name="elements-of-a-sharepoint-project"></a>Elementos de um projeto do SharePoint  
 Os nós em um projeto do SharePoint são conhecidos como *itens do SharePoint*. Itens do SharePoint também podem conter um ou mais subarquivos, conhecidos como *arquivos de item do SharePoint*, como [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivos de configuração, forms. aspx e muito mais.  
  
 Em vez de criar projetos usando modelos de projeto que já foram preenchidos com arquivos de item de projeto, você pode usar o **projeto vazio** modelo para criar um projeto vazio do SharePoint e, em seguida, adicionar itens de projeto manualmente. Projetos SharePoint também podem conter um ou mais arquivos de recursos (de ativação no SharePoint) e um arquivo de pacote no qual a distribuir o projeto.  
  
### <a name="special-nodes"></a>Nós especiais  
 Cada projeto do SharePoint contém dois nós que não podem ser renomeados, excluídos, recortar, copiados ou arrastados do projeto. Esses nós são como segue:  
  
-   Recursos  
  
-   Pacote  
  
 Ambos os nós sempre aparecem em todos os projetos do SharePoint, mesmo se nenhum recurso ou os pacotes são definidos para o projeto.  
  
#### <a name="features-node"></a>Nó de recursos  
 O **recursos** nó contém um ou mais recursos de projeto do SharePoint. Um recurso é um contêiner de extensões para o SharePoint. Depois que um recurso é implantado no servidor do SharePoint, pode ser incluído nas definições do site ou ativado individualmente por administradores do SharePoint nos sites do SharePoint. Para obter mais informações, consulte [trabalhando com recursos](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Quando você adicionar um item, como um tipo de conteúdo ou uma instância de lista, para um projeto do SharePoint, ele é adicionado a um recurso no **recursos** nó. O escopo do item determina se ele é adicionado a um recurso novo ou existente. Se o novo item tem o mesmo escopo de um recurso existente, ele é adicionado a esse recurso. Caso contrário, o item é adicionado a um novo recurso.  
  
 Para adicionar manualmente um recurso, execute o **adicionar recurso** comando no menu de atalho do nó de recurso. Você pode exibir ou alterar o conteúdo de um recurso usando o Designer de recursos. Para obter mais informações, consulte [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Quando um recurso é adicionado a um projeto do SharePoint, ele aparece na **Solution Explorer** como um nó com o padrão de nome de recurso*x*.feature, onde *x* é um número exclusivo. Depois que um recurso é implantado no servidor do SharePoint, um administrador do SharePoint pode ativar o, tornando-o disponível aos usuários do site do SharePoint.  
  
#### <a name="package-node"></a>Nó de pacote  
 O **pacote** nó contém um único arquivo que serve como o mecanismo de distribuição para o projeto do SharePoint. Esse arquivo, conhecido como um *solução**pacote*, é. Com base em CAB com um. Extensão WSP. Um pacote de solução é um arquivo implantável e reutilizável que contém um conjunto de recursos, definições de site e assemblies que se aplicam a sites do SharePoint e que você pode habilitar ou desabilitar individualmente. O **pacote** nó também sempre contém um arquivo chamado Package.wspdef, um [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivo de definição para o pacote. Quando um pacote é implantado para o servidor que está executando o SharePoint, o administrador do SharePoint pode instalá-lo e ativar seus recursos.  
  
 Você pode exibir ou alterar o conteúdo do pacote no Designer de pacote, clicando duas vezes no nó do pacote ou abrindo o menu de atalho e, em seguida, escolhendo **abrir**. Para obter mais informações, consulte [criando pacotes da solução SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Projeto do SharePoint e as propriedades de Item de projeto  
 Projetos do SharePoint, assim como outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos, exibir propriedades na janela Propriedades e a página de propriedades. As propriedades que são exibidas dependem do nó selecionado.  
  
 Quando um projeto do SharePoint, o item de projeto ou o nó de arquivo do item de projeto está selecionado no **Solution Explorer**, as propriedades a seguir aparecem na janela Propriedades ou a página de propriedades:  
  
### <a name="project-properties"></a>Propriedades do projeto  
  
|Nome da Propriedade|Descrição|  
|-------------------|-----------------|  
|Configuração de implantação ativa|Especifica a série de etapas executadas durante a implantação. Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Destino de implantação do assembly|Determina onde *assemblies de aplicativo do SharePoint* estão localizados. Valores do local do assembly válido são *GlobalAssemblyCache* (padrão), ou *WebApplication*.<br /><br /> Se o *solução em área restrita* está definida como **true**, em seguida, essa propriedade está desabilitada.|  
|Cancele automaticamente após a depuração|Especifica se a solução implantada retira automaticamente do SharePoint depois de executar o aplicativo no modo de depuração em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quando selecionada, a solução retira quando volta o IDE para criar modo de exibição após a depuração. Quando desmarcada, a solução não cancele. Para obter mais informações, consulte [cancelamento de uma solução](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Editar configurações|Especifica a configuração de implantação a ser usado para o projeto. Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [atualizar os pacotes de solução do SharePoint, publicação e implantação](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Habilitar a depuração Silverlight (em vez de depuração de Script)|Quando selecionada, o depurador do Silverlight se anexa ao processo de depuração. Quando desmarcada, o depurador de scripts anexa ao processo de depuração. Para obter mais informações, consulte [visão geral de depuração do Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Incluir o Assembly no pacote|Especifica se o assembly de projeto é empacotado em tempo de compilação ou não.|  
|Linha de comando de pós-implantação|Especifica os comandos para executar depois de implantar a solução do SharePoint. Essa linha dá suporte a comandos de lote, bem como a resolução de variáveis do MSBuild. Para obter mais informações, consulte [como: definir comandos de implantação do SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Linha de comando de pré-implantação|Especifica os comandos a serem executados antes de implantar a solução do SharePoint. Essa linha dá suporte a comandos de lote, bem como a resolução de variáveis do MSBuild. Para obter mais informações, consulte [como: definir comandos de implantação do SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Arquivo de Projeto|O nome do arquivo que contém a compilação, configuração e outras informações sobre o projeto.|  
|Pasta do projeto|O local do arquivo do projeto no sistema. (Somente leitura.)|  
|Solução em área restrita|Especifica se o projeto deve ser implantado como um *solução em área restrita*, também conhecido como um *solução criados pelo usuário*. Soluções de área restrita não são necessariamente confiáveis. Um valor de **true** significa que o projeto é implantado como uma solução em modo seguro, um valor de **false** significa que o projeto é implantado como uma solução de farm. Para obter mais informações, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md) e [diferenças entre em modo seguro e soluções de Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|URL do site|Especifica o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] do site de destino para este projeto.|  
|Item de inicialização|Especifica o primeiro item no projeto para ser executado.|  
  
 Quando você escolhe um arquivo de item do SharePoint (como um fluxo de trabalho ou um recurso no nó recursos), as propriedades a seguir aparecem na janela de propriedades:  
  
### <a name="project-item-properties"></a>Propriedades de Item de projeto  
  
|Nome da Propriedade|Descrição|  
|-------------------|-----------------|  
|Resolução do Conflito de Implantação|Especifica a ação a ser tomada ao implantar um item de projeto cujas propriedades são idênticas às de um item já está no servidor. Para obter mais informações, consulte [de solução de problemas do SharePoint empacotamento e implantação](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Propriedades do recurso|Especifica um conjunto de valores (armazenados como pares chave/valor) que acompanha um recurso quando implanta no SharePoint. Depois que o recurso é implantado, você pode acessar os valores de propriedade em seu código. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Receptor de recursos|Fornece código que é executado quando ocorrem determinados eventos para um item de projeto que contém recursos. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nome da Pasta|O nome da pasta do item de projeto do SharePoint.|  
|Referências de saída do projeto|Especifica uma dependência, como um assembly, que o item de projeto precisa ser executada. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Entradas de controle de segurança|Especifica os controles de seguros para usuários não confiáveis editar. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Propriedades do arquivo do Item de projeto  
  
|Nome da Propriedade|Descrição|  
|-------------------|-----------------|  
|Ação de compilação|Especifica como o arquivo se relaciona aos processos de compilação e implantação. Para obter mais informações, consulte [propriedades do arquivo](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Copiar para diretório de saída|Especifica se os arquivos de origem serão copiados para o diretório de saída. Pode ser um dos seguintes valores:<br /><br /> -   *Não copiar*<br />-   *Sempre copiar*<br />-   *Copiar se mais recente*<br /><br /> Para obter mais informações, consulte [propriedades do arquivo](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Ferramenta personalizada|Especifica o nome de uma ferramenta, se houver, que transforma o arquivo em tempo de design e coloca a saída da transformação em outro arquivo. Por exemplo, um conjunto de dados (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) arquivo tem uma ferramenta personalizada padrão. Para obter mais informações, consulte [propriedades do arquivo](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Namespace de ferramenta personalizada|O namespace em que a saída da ferramenta personalizada é copiada. Para obter mais informações, consulte [propriedades do arquivo](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Local de implantação|O caminho totalmente qualificado do arquivo no servidor do SharePoint. Esse caminho é composto de subpropriedades de raiz de implantação e o caminho de implantação.|  
|Caminho de implantação|O caminho relativo do arquivo no arquivo do SharePoint Server, como Workflow1\\. O caminho totalmente qualificado para o arquivo é criado concatenando o *caminho de implantação* valor ao final do *raiz de implantação* valor.<br /><br /> Selecionar um valor de *RootFile* para o *tipo de implantação* alterações de propriedade de *raiz de implantação* propriedade {SharePointRoot}\\, resultando em um o caminho totalmente qualificado do {SharePointRoot} \Workflow1\\. Para obter mais informações, consulte [empacotamento e implantação de soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Raiz de implantação|Cadeia. A pasta raiz onde o arquivo é implantado no servidor do SharePoint. Por exemplo, {SharePointRoot} \Template\Features\\{FeatureName}\\.<br /><br /> O valor da *raiz de implantação* propriedade é determinada pelo *tipo de implantação* configuração.|  
|Tipo de implantação|Tipo de implantação do arquivo, que determina o *raiz de implantação* valor. Pode ser um dos seguintes valores:<br /><br /> NoDeployment: \<nenhum valor ><br /><br /> ElementManifest: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> ElementFile: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> TemplateFile: {SharePointRoot} \Template\\<br /><br /> RootFile: {SharePointRoot}\\<br /><br /> GlobalResource: {SharePointRoot} \Resources\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> Para obter mais informações, consulte <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nome do Arquivo|O nome do arquivo ou pasta para o arquivo do item.|  
|Caminho completo|O local do arquivo para o item. (Somente leitura.)|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Projeto do SharePoint e Modelos de Item de Projeto](../sharepoint/sharepoint-project-and-project-item-templates.md)|Descreve o projeto do SharePoint e modelos de item de projeto disponíveis em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Como adicionar itens a um Projeto do SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Descreve como adicionar itens novos ou existentes para um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint.|  
|[Instruções passo a passo: criar uma coluna de site, tipos de conteúdo e listas para o SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Orienta você passo a passo na criação de um cliente campo, tipo de conteúdo, definição de lista e instância de lista.|  
|[Como criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)|Descreve como adicionar um receptor de eventos para o projeto criado no [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Criando soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Descreve como criar projetos de fluxo de trabalho que inclui os formulários de associação de fluxo de trabalho e formulários de iniciação do fluxo de trabalho.|  
|[Criando páginas para o SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Descreve como você pode criar páginas como páginas de aplicativo e layouts de página, páginas mestras e páginas do site do SharePoint.|  
|[Criando Web Parts para o SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Descreve como adicionar controles que permitem aos usuários modificar diretamente o conteúdo, a aparência e o comportamento das páginas do site do SharePoint usando um navegador.|  
|[Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Descreve como criar controles de usuário que podem ser consumidos por páginas de aplicativos e Web Parts que são executados no SharePoint.|  
|[Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Descreve como integrar dados de serviços Web e aplicativos de servidor back-end em um aplicativo do SharePoint.|  
|[Criando definições de site do SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Descreve como criar definições de site: modelos que são usados para criar sites do SharePoint.|  
|[Importando itens de um site existente do SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Descreve como importar itens como módulos e tipos de conteúdo de um site do SharePoint existente em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint.|  
|[Usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Descreve como usar módulos para implantar os arquivos de seu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto para o site do SharePoint.|  
|[Navegando em conexões do SharePoint usando o Gerenciador de Servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Descreve como procurar sites locais do SharePoint usando o Gerenciador de servidores.|  
|[Fornecendo informações de pacote e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Descreve como usar propriedades de item de projeto para fornecer informações de empacotamento e implantação de projetos, como entradas de controle de segurança, as referências de saída do projeto e as propriedades do recurso.|  
|[Como adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Descreve como mapeadas pastas podem ser adicionados ao seu projeto para facilitar o acesso aos recursos do SharePoint.|  
|[Considerações de solução em área restrita](../sharepoint/sandboxed-solution-considerations.md)|Descreve os problemas associados a soluções de área restrita.|  
|[Segurança das soluções do SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Descreve as considerações de segurança para desenvolver soluções do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Caixa de diálogo Seletor de URL &#40; Desenvolvimento do SharePoint no Visual Studio &#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Descreve uma caixa de diálogo que você pode usar para adicionar referências de caminho a recursos em seu projeto ou no servidor do SharePoint local.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Introdução &#40; Desenvolvimento do SharePoint no Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Pesquisa de conexões do SharePoint usando o Gerenciador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  