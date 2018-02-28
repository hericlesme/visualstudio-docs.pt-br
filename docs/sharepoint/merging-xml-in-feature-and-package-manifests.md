---
title: Mesclando XML em um recurso e pacote manifestos | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 81e6f83dd4fc825e885843a47d45485918f7dabe
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Mesclando XML em manifestos de funcionalidade e pacote
  Recursos e pacotes são definidos pela [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivos de manifesto. Esses pacotes manifestos são uma combinação de dados gerados por designers e personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] inseridos no modelo de manifesto pelos usuários. No momento de empacotamento, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mescla personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instruções com o designer fornecido [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para formar o pacote [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivo de manifesto. Elementos semelhantes, com as exceções disponível mais adiante exceções de mesclagem, são mesclados para evitar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] erros de validação depois de implantar os arquivos para o SharePoint e para fazer o manifesto arquivos menores e mais eficiente.  
  
## <a name="modifying-the-manifests"></a>Modificando os manifestos  
 Você não pode modificar diretamente os arquivos de manifesto de pacote até que você desabilitar os designers de recurso ou pacote. No entanto, você pode adicionar manualmente personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos ao modelo de manifesto por meio de designers de recurso e pacote ou [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Para obter mais informações, consulte [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Processo de mesclagem de manifesto do recurso e pacote  
 Ao combinar elementos personalizados em conjunto com elementos fornecida pelo designer, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa o processo a seguir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verifica se cada elemento tem um valor de chave exclusivo. Se um elemento não tiver nenhum valor de chave exclusivo, ele é adicionado ao arquivo de manifesto do pacote. Da mesma forma, os elementos que têm várias chaves não podem ser mesclados. Portanto, eles são adicionados ao arquivo de manifesto.  
  
 Se um elemento tem uma chave exclusiva, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compara os valores do designer e chaves personalizadas. Se os valores coincidirem, eles mesclagem em um único valor. Se os valores forem diferentes, o valor da chave designer é descartado e o valor de chave personalizado é usado. Coleções também são mescladas. Por exemplo, se o gerado pelo designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] e personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tanto contém uma coleção de Assemblies, o manifesto de pacote contém apenas um conjunto de módulos (assemblies).  
  
## <a name="merge-exceptions"></a>Exceções de mesclagem  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]mescla a maioria dos designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto com personalizada semelhante [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos, desde que eles têm um atributo de identificação único e exclusivo. No entanto, alguns elementos não têm o identificador exclusivo, necessário para [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] a mesclagem. Esses elementos são conhecidos como *mesclar exceções*. Nesses casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não mescla personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto com o designer fornecido [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos, mas em vez disso, acrescenta-os ao arquivo de manifesto do pacote.  
  
 Esta é uma lista de exceções de mesclagem para o recurso e pacote [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivos de manifesto.  
  
|Designer|Elemento XML|  
|--------------|-----------------|  
|Designer de recursos|ActivationDependency|  
|Designer de recursos|UpgradeAction|  
|Designer de pacote|SafeControl|  
|Designer de pacote|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementos de manifesto do recurso  
 A tabela a seguir é uma lista de todos os elementos de manifesto de recurso que podem ser mesclados e sua chave exclusiva que é usada para correspondência.  
  
|Nome de elementos|Chave exclusiva|  
|------------------|----------------|  
|Recurso (todos os atributos)|*Nome do atributo* (cada nome de atributo do elemento recurso é uma chave exclusiva.)|  
|ElementFile|Local|  
|ElementManifests/ElementManifest|Local|  
|Propriedades/propriedade|Chave|  
|CustomUpgradeAction|Nome|  
|CustomUpgradeActionParameter|Nome|  
  
> [!NOTE]  
>  Porque é a única maneira de modificar o elemento CustomUpgradeAction no personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, o efeito de mesclagem não é baixo.  
  
## <a name="package-manifest-elements"></a>Elementos de manifesto de pacote  
 A tabela a seguir é uma lista de todos os elementos de manifesto de pacote que podem ser mesclados e sua chave exclusiva que é usada para correspondência.  
  
|Nome de elementos|Chave exclusiva|  
|------------------|----------------|  
|Solução (todos os atributos)|*Nome do atributo* (cada nome de atributo do elemento de solução é uma chave exclusiva.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Local|  
|Assemblies/Assembly|Local|  
|ClassResources/ClassResource|Local|  
|DwpFiles/DwpFile|Local|  
|FeatureManifests/FeatureManifest|Local|  
|Recursos/recursos|Local|  
|RootFiles/RootFile|Local|  
|SiteDefinitionManifests/SiteDefinitionManifest|Local|  
|WebTempFile|Local|  
|TemplateFiles/TemplateFile|Local|  
|SolutionDependency|ID da solução|  
  
## <a name="manually-add-deployed-files"></a>Adicione manualmente os arquivos implantados  
 Alguns elementos de manifesto, como ApplicationResourceFile e DwpFiles, especifique um local que inclui um nome de arquivo. No entanto, adicionar uma entrada de nome de arquivo para o modelo de manifesto não adicionar o arquivo de base para o pacote. Você deve adicionar o arquivo ao projeto para incluí-lo no pacote e defina sua propriedade de tipo de implantação de acordo.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  