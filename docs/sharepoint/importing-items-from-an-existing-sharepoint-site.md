---
title: Importando itens de um Site do SharePoint existente | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a542a74bf162c4fc2bb2fe2c725b02742d568547
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="importing-items-from-an-existing-sharepoint-site"></a>Importando itens de um local do SharePoint existente
  O modelo de projeto Importar pacote de solução do SharePoint permite a reutilização elementos como tipos de conteúdo e campos de sites do SharePoint existentes em uma nova [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] soluções do SharePoint. Embora você possa executar a maioria das soluções importadas sem modificação, há certas restrições e questões a serem consideradas, especialmente se você modificar os itens após importá-los.  
  
> [!NOTE]  
>  Para importar fluxos de trabalho reutilizáveis, use o modelo de projeto importar fluxo de trabalho reutilizável. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Diretrizes para importar fluxos de trabalho reutilizáveis](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Soluções do SharePoint com suporte  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]oferece suporte para a importação de soluções criadas no [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]não oferece suporte a importação de soluções criadas nos seguintes aplicativos:  
  
-   [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
-   [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
-   [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
-   O Microsoft SharePoint Designer 2007  
  
-   [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
 Embora muitas vezes com êxito, você pode importar soluções criadas por esses aplicativos, essa funcionalidade não é testada e não tem suporte.  
  
## <a name="item-import-restrictions"></a>Restrições de importação de item  
 Embora a maioria dos itens do SharePoint podem ser importados de um arquivo. wsp existente, os itens a seguir não têm suporte e podem exigir modificações para funcionar corretamente:  
  
-   Entidades BDC  
  
-   Código de elementos de associação de fluxo de trabalho  
  
-   Fluxos de trabalho de código  
  
-   Visual Web parts (. ascx)  
  
-   Serviços da Web (. asmx)  
  
-   Associações de tipo de conteúdo  
  
-   Receptores de evento  
  
-   Definições de lista (modelos)  
  
-   Definições de site  
  
 Quando você exporta uma solução de [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], esses itens são automaticamente excluídos do arquivo. wsp. No entanto, outros arquivos. wsp gerados a partir de ferramentas de suporte podem conter esses itens. (Consulte "Suporte para soluções do SharePoint" anteriormente neste tópico.)  
  
## <a name="what-happens-when-you-import-a-solution"></a>O que acontece quando você importar uma solução  
 Quando você importa uma solução com o modelo de pacote de solução do SharePoint importar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia todo o conteúdo do arquivo. wsp e tentará reconciliar e reter quantos associações e referências entre elementos importados e seus arquivos possível.  
  
 Copiar todos os itens importados para pastas correspondentes em **Gerenciador de soluções**. Por exemplo, os tipos de conteúdo aparecem sob a pasta **tipos de conteúdo** e listar as instâncias são exibidos em **listar instâncias**. Arquivos associados a um item importado também são copiados para a pasta do item. Por exemplo, uma instância de lista importada inclui módulos, formulários e páginas ASPX.  
  
### <a name="dependent-items"></a>Itens dependentes  
 Se você selecionar um item no Assistente Importar pacote de solução do SharePoint, mas não seus itens dependentes, uma caixa de mensagem informa que os itens dependentes também devem ser selecionados antes de importar.  
  
### <a name="what-are-features"></a>Quais são os recursos?  
 Os usuários do SharePoint Designer podem ver os arquivos de inesperado, chamados *recursos*, aparecem em suas soluções importadas no **Gerenciador de soluções.** Embora recursos existiam na solução do SharePoint Designer, eles foram ocultos na exibição. Recursos agora estão visíveis no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Recursos são contêineres para itens do SharePoint. Cada recurso mantém uma referência para cada item, como tipos de conteúdo e definições de lista, que ele contém. Quando você importar sua solução, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] configura recursos para todos os elementos importados e tenta manter as relações do elemento de recurso para os arquivos. Todos os arquivos cujas referências não puderam ser resolvidas são colocados no **outros arquivos importados** pasta.  
  
 Para obter mais informações sobre recursos, consulte [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md) e [trabalhando com recursos](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handling-special-cases"></a>Tratamento de casos especiais  
 Em alguns casos, o Visual Studio não é possível reconciliar um item com seus arquivos dependentes. Os arquivos que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não foi possível resolver aparecem sob a pasta **outros arquivos importados**. Além disso, seus **tipo de implantação** propriedades são definidas como **NoDeployment** para que eles não são implantados com a solução.  
  
 Por exemplo, se você importar a definição de lista ExpenseForms, uma definição de lista com esse nome aparecerá sob o **lista definições de** pasta **Solution Explorer** juntamente com seu Elements e Arquivos Schema. No entanto, seus formulários ASPX e HTML associados podem ser colocados em uma pasta chamada **ExpenseForms** sob o **outros arquivos importados** pasta. Para concluir a importação, mova esses arquivos sob a definição da lista ExpenseForms em **Solution Explorer** e altere o **tipo de implantação** propriedade para cada arquivo de **NoDeployment** para **ElementFile**.  
  
 Ao importar receptores de evento, o arquivo Elements é copiado para o local correto, mas você deve incluir manualmente o assembly no pacote de solução para que ele implanta a solução. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]como fazer isso, consulte [como: adicionar e remover Assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Ao importar fluxos de trabalho, formulários do InfoPath são copiados para o **outros arquivos importados** pasta. Se o arquivo. wsp contém um modelo de Web, ele é definido como a página de inicialização na **Gerenciador de soluções**.  
  
## <a name="importing-fields-and-property-bags"></a>Importando campos e recipientes de propriedade  
 Quando você importa uma solução que tem vários campos, todas as definições de campo separadas são mescladas em um único arquivo Elements. XML em um nó em **Solution Explorer** chamado **campos**. Da mesma forma, todas as entradas de recipiente de propriedade são mescladas em um arquivo Elements. XML em um nó chamado **PropertyBags**.  
  
 Campos no SharePoint são colunas de um tipo de dados especificado, como um texto, booleano ou pesquisa. Para obter mais informações, consulte [blocos de construção: colunas e tipos de campo](http://go.microsoft.com/fwlink/?LinkId=182304). Recipientes de propriedade permitem adicionar propriedades aos objetos no SharePoint, tudo de um farm em uma lista em um site do SharePoint. Recipientes de propriedade são implementados como uma tabela de hash de valores e nomes de propriedade. Para obter mais informações, consulte [gerenciamento de configuração do SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) ou [configurações de recipiente de propriedades do SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="deleting-items-in-the-project"></a>A exclusão de itens no projeto  
 A maioria dos itens em soluções do SharePoint tem um ou mais itens dependentes. Por exemplo, listar as instâncias dependem de tipos de conteúdo e tipos de conteúdo dependem de campos. Depois de importar uma solução do SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não notificá-lo de qualquer problema de referência se você excluir um item da solução, mas não seus itens dependentes, até que você tentar implantar a solução. Por exemplo, se uma solução importada tem uma instância de lista que depende de um tipo de conteúdo e excluir esse tipo de conteúdo, um erro pode ocorrer na implantação. O erro ocorre se o item dependente não está presente no servidor do SharePoint. Da mesma forma, se um item excluído também tiver um recipiente de propriedades relacionadas, em seguida, exclua as entradas do recipiente de propriedade do **PropertyBags** arquivo Elements. Portanto, se você excluir todos os itens de uma solução importada e você obtiver erros de implantação, verifique se todos os itens dependentes devem também ser excluídas.  
  
## <a name="restoring-missing-feature-attributes"></a>Restaurando atributos de recurso ausente  
 Ao importar soluções, alguns atributos opcionais são omitidos do manifesto de recurso importada. Se você deseja restaurar esses atributos no novo arquivo de recurso, identificar os atributos ausentes, comparando o arquivo original do recurso ao manifesto do recurso novo e siga as instruções no tópico [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Detecção de conflito de implantação não é executada em instâncias de lista interna  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]não executa a detecção de conflitos de implantação em instâncias de lista interna (ou seja, lista instâncias padrão que vêm com o SharePoint). Não executar a detecção de conflito é feito para evitar a substituição de instâncias de lista interna no SharePoint. A lista interna instâncias ainda são implantado ou atualizado, mas é nunca excluída ou substituída. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint empacotamento e implantação de solução de problemas](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="importing-sharepoint-server-2010-workflows"></a>Importando fluxos de trabalho do SharePoint Server 2010  
 Se você importar um fluxo de trabalho criado em [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], ele não será executado corretamente depois de implantá-lo. O fluxo de trabalho não será executado corretamente porque faltam determinados assemblies e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] fluxos de trabalho contêm os formulários do InfoPath que atualmente não têm suporte em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] soluções de fluxo de trabalho. No entanto, importado [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] fluxos de trabalho podem ser feitos para funcionar corretamente depois de corrigir alguns itens, como a adição de referências para o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] assemblies e reconectar-se os formulários do InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importando fluxos de trabalho do SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Limite de caracteres de nome de item  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tem um limite de 260 caracteres total para o projeto e nomes de item de projeto, incluindo o caminho. Ao importar uma solução, se um nome de item exceder esse limite, você receberá o erro:  
  
 **O caminho especificado, o nome do arquivo ou ambos são muito longos. O nome de arquivo totalmente qualificado deve ter menos de 260 caracteres e o nome do diretório deve ter menos de 248 caracteres.**  
  
 Quando você receber esse erro, o item não é criado. Esse problema geralmente ocorre com módulos importados. Para evitar esse problema, faça o seguinte:  
  
-   Use nomes curtos para seu projeto quando você as insere no **adicionar novo projeto** caixa de diálogo.  
  
-   Crie o projeto em um local como próximo a pasta raiz quanto possível, para reduzir o caminho.  
  
## <a name="the-sharepointproductversion-attribute"></a>O atributo SharePointProductVersion  
 Se você importar uma solução criada em uma versão anterior do SharePoint como [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], altere o valor do atributo SharePointProductVersion no manifesto do pacote para a versão 12.0, ou inserir um controle de Gerenciador de script em todos os Web importada páginas e deixe SharePointProductVersion definido como 14.0. Caso contrário, importados formulários da Web não serão exibidos no SharePoint.  
  
### <a name="background"></a>Informações preliminares  
 Soluções em [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] incluir um atributo chamado SharePointProductVersion. O SharePoint usa esse atributo em seus manifestos de pacote para determinar a versão do SharePoint, a solução foi projetada para. Os dois valores válidos são 12.0 e 14.0. Um valor de 12.0 indica se o item foi projetado para [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; um valor de 14.0 indica se o item foi projetado para [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Para aumentar a segurança ao renderizar páginas ASPX, [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] exigem que todos os ASPX ou páginas mestras contenham um controle do Gerenciador de script. Para obter mais informações sobre o Gerenciador de script, consulte [visão geral do controle ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Porque o controle do Gerenciador de script não estava disponível em [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] e [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], um deve ser adicionado a qualquer [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] página é atualizada para [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Páginas ASPX que usam uma página mestra padrão não exigem um controle do Gerenciador de script porque um já foi adicionado para a página mestra padrão. No entanto, as páginas ASPX que não use uma página mestra ou uma página mestre personalizada devem adicionar um controle de script para funcionar [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 A ausência de um controle do Gerenciador de script pode ser um problema quando você importa um [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projeto em [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], pois o atributo SharePointProductVersion de todos os novos projetos é definido como 14.0. Se você implantar um projeto atualizado que tenha um formulário da Web sem um Gerenciador de script, o formulário não será exibido no SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Importar itens de um Site do SharePoint existente](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Diretrizes para importar fluxos de trabalho reutilizáveis](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Passo a passo: Importar um fluxo de trabalho reutilizável do Designer do SharePoint no Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Como adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
  
  