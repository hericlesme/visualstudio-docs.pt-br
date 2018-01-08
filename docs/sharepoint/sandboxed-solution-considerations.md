---
title: "Considerações sobre a solução em área restrita | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2dcf8040217a13688dc1ff33183f237f0f58bbcf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sandboxed-solution-considerations"></a>Considerações de solução em área restrita
  *Soluções em modo seguro* são um recurso do Microsoft SharePoint 2010 que permite que os usuários da coleção de site carregar suas próprias soluções de código personalizado. Uma solução em área restrita comum é carregar suas próprias Web Parts de usuários.  
  
 Um aplicativo em modo seguro do SharePoint é executado em um processo monitorado seguro que tem acesso a uma parte limitada do Web farm. Microsoft SharePoint 2010 usa uma combinação de recursos, galerias de solução, solução de monitoramento e uma estrutura de validação para habilitar soluções em modo seguro.  
  
## <a name="specifying-project-trust-level"></a>Especificar o nível de confiança do projeto  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dá suporte a soluções em modo seguro através de uma propriedade booleana projeto chamadas *solução em área restrita*. Essa propriedade pode ser definida a qualquer momento no projeto, ou ele pode ser especificado quando você cria o projeto no **Assistente de personalização do SharePoint**.  
  
> [!NOTE]  
>  Alterando o *solução em área restrita* propriedade de um projeto após sua criação pode causar erros de validação.  
  
 A solução é considerada uma solução com escopo de farm se o *solução em área restrita* está definida como **false** ou escolher a **implantar como uma solução de farm** opção. No entanto, a solução é tratada Diferentemente de uma solução de farm se o *solução em área restrita* está definida como **true** ou escolher a **implantar como uma solução em área restrita** opção no assistente.  
  
## <a name="sharepoint-site-hierarchy"></a>Hierarquia de Site do SharePoint  
 Para entender as soluções em modo seguro como trabalho, é importante para saber que os sites do SharePoint são hierárquicos no escopo. O elemento superior é conhecido como o Web farm, e outros elementos são subordinados a ele:  
  
 Farm da Web  
  
 Aplicativo Web A  
  
 Site coleção A1  
  
 A1a do site  
  
 Aplicativo Web B  
  
 B1 de coleção do site  
  
 B1a do site  
  
 B1b do site  
  
 Site coleção B2  
  
 B2a do site  
  
 Como você pode ver, farms da Web podem conter um ou mais aplicativos Web, que por sua vez, podem conter uma ou mais coleções de sites, que podem ter subsites e assim por diante. Alterações feitas em um efeito de coleta de site somente quando o conjunto de sites e nenhum outro. No entanto, as alterações feitas no nível do farm da Web afetam todos os conjuntos de sites no farm.  
  
 Windows SharePoint Services (WSS) 3.0 permite que você implante soluções somente para o nível de farm, mas [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] permite que você implante o nível do farm (solução de farm) ou o nível de conjunto de sites (solução em área restrita).  
  
## <a name="why-sandboxed-solutions"></a>Por que as soluções em modo seguro?  
 No WSS 3.0, soluções podem ser implantadas somente para o nível do farm. Isso significa que potencialmente perigosos ou desestabilizar soluções podem ser implantadas que afetado do Web farm inteiro e todos os conjuntos de sites e aplicativos que são executados sob ele. No entanto, usando soluções em modo seguro, você pode implantar suas soluções para uma subárea do farm, um conjunto de sites específicas. Para fornecer proteção adicional, o assembly da solução não é carregado no principal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo (w3wp.exe). Em vez disso, ele é carregado em um processo separado (SPUCWorkerProcess.exe). Esse processo é monitorado e implementa cotas e limitação para proteger o farm de soluções em modo seguro que executam atividades prejudiciais, como a execução de loops rígidos que consomem os ciclos de CPU.  
  
## <a name="site-collection-solution-gallery"></a>Galeria de soluções do conjunto de sites  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]2010 tem um recurso que é conhecido como a "Galeria de soluções de coleta de site". Você pode acessar esse recurso na página do SharePoint 2010 Central Administration ou abrindo o **ações do Site** menu, escolha **configurações de Site**e, em seguida, escolhendo o **soluções** link em **galerias** no site do SharePoint. Galerias de solução são repositórios de soluções que permitem que os administradores de coleção de sites gerenciar soluções em seus conjuntos de sites.  
  
 A Galeria de soluções é uma biblioteca de documentos armazenada na raiz da Web do site do SharePoint. A Galeria de soluções substitui os modelos de site e oferece suporte a pacotes de solução. Quando um arquivo de pacote (. wsp) de solução do SharePoint é carregado, ele é processado como uma solução em área restrita.  
  
## <a name="sandboxed-solution-limitations"></a>Limitações da solução em área restrita  
 Quando uma solução em área restrita é implantada, a matriz de funcionalidade do SharePoint disponível para ele é limitada para ajudar a reduzir as vulnerabilidades de segurança pode ter. Algumas dessas limitações incluem o seguinte:  
  
-   Soluções em modo seguro tem um subconjunto restrito de elementos de solução de implantação disponíveis para eles. Modelos de projeto do SharePoint vulneráveis, como definições de site e fluxos de trabalho, não estão disponíveis.  
  
-   SharePoint executa código da solução em área restrita em um processo (SPUCWorkerProcess.exe) separado da principal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo (w3wp.exe) do pool de aplicativos.  
  
-   Pastas mapeadas não podem ser adicionadas ao projeto.  
  
-   Tipos no [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft.Office.Server não pode ser usado em soluções em modo seguro. Além disso, somente tipos no [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint podem ser usados em soluções em modo seguro.  
  
 É importante observar que especificar uma solução do SharePoint como uma solução em área restrita não tem nenhum efeito no servidor do SharePoint; ela só determina como o projeto do SharePoint é implantado no SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e quais assemblies associa ao. Ele não afeta o arquivo. wsp gerado e o arquivo. wsp não tem dados que correlacionam diretamente para o *solução em área restrita* propriedade.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Recursos e elementos em soluções em modo seguro  
 Soluções em modo seguro suportam os recursos e os elementos a seguir:  
  
-   Tipos de conteúdo/campos  
  
-   Ações personalizadas  
  
-   Fluxos de trabalho declarativos  
  
-   Receptores de evento  
  
-   Textos explicativos de recurso  
  
-   Definições de lista  
  
-   Instâncias de lista  
  
-   Arquivos do módulo  
  
-   Navegação  
  
-   onet.XML  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Suporte para todas as Web Parts que derivam de`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web Parts  
  
-   Elementos de recurso WebTemplate (em vez de webtemp)  
  
-   Visual Web Parts  
  
 Soluções de área restrita não dão suporte a recursos e os elementos a seguir:  
  
-   Páginas de aplicativo  
  
-   Grupo de ação personalizado  
  
-   Recursos de escopo de farm  
  
-   Elemento `HideCustomAction`  
  
-   Recursos de escopo do aplicativo Web  
  
-   Fluxos de trabalho com código  
  
## <a name="see-also"></a>Consulte também  
 [Diferenças entre a área restrita e soluções em Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  