---
title: Fornecimento de empacotamento e informações de implantação em itens de projeto | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0c12c01566011ed93d83cd9ecc0dd417edd0b1b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Fornecendo informações de pacote e implantação em itens de projeto
  Todos os itens de projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] têm propriedades que você pode usar para fornecer dados adicionais quando o projeto é implantado no SharePoint. Estas são as seguintes propriedades:  
  
-   Propriedades do recurso  
  
-   Receptores de recurso  
  
-   Referências de saída do projeto  
  
-   Entradas de controle de segurança  
  
 Essas propriedades aparecem no **propriedades** janela.  
  
## <a name="feature-properties"></a>Propriedades do recurso  
 Use o **as propriedades do recurso** propriedade para especificar os dados que usa o recurso. Dados de propriedades de recurso são um conjunto de valores (armazenados como pares chave/valor) que acompanha um recurso quando implanta no SharePoint. Depois que o recurso é implantado, você pode acessar os valores de propriedade em seu código.  
  
 Quando você adiciona um valor de propriedade de recurso para um item de projeto, o valor é adicionado como um elemento no manifesto do recurso do item. Em um projeto de modelo de conectividade de dados de negócios (BDC), por exemplo, a propriedade de recurso ModelFileName aparece como:  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Depois de definir um valor de propriedade de recurso, ele é adicionado como um elemento de FeatureProperty no arquivo. spdata do projeto. Para obter informações sobre como acessar as propriedades no SharePoint, consulte [SPFeaturePropertyCollection classe](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Valores de propriedade de recurso idênticas de todos os itens de projeto são mesclados no manifesto do recurso. No entanto, se dois itens de projeto diferente especificam a mesma chave de propriedade de recurso com valores não correspondentes, ocorrerá um erro de validação.  
  
 Para adicionar propriedades de recurso diretamente para o arquivo de recurso (* .feature), chame o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] método de modelo de objeto do SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Se você usar esse método, lembre-se de que a mesma regra sobre como adicionar valores de propriedade de recurso idêntico nas propriedades de recurso também se aplica a propriedades adicionadas diretamente para o arquivo de recurso.  
  
## <a name="feature-receiver"></a>Receptor de recursos  
 Receptores de recurso são o código que é executado quando ocorrem determinados eventos para um item de projeto que contém recursos. Por exemplo, você pode definir receptores de recurso que é executado quando o recurso é instalado, ativado ou atualizado. Uma maneira de adicionar um receptor de recursos é para adicioná-lo diretamente para um recurso, conforme descrito em [passo a passo: Adicionar receptores de evento de recurso](../sharepoint/walkthrough-add-feature-event-receivers.md). É outra maneira de fazer referência a um nome de classe do receptor de recurso e o assembly de **receptor de recursos** propriedade.  
  
### <a name="direct-method"></a>Método direto  
 Ao adicionar um destinatário de recurso diretamente a um recurso, um arquivo de código está sob o **recurso** nó no Gerenciador de soluções. Quando você cria sua solução do SharePoint, o código é compilado em um assembly e implanta no SharePoint. Por padrão, as propriedades do recurso **Assembly do receptor** e **classe receptora** referenciar o nome da classe e o assembly.  
  
### <a name="reference-method"></a>Método Reference  
 É outra maneira de adicionar um receptor de recursos usando o **receptor de recursos** propriedade de um item de projeto para referenciar um assembly do receptor de recursos. O valor da propriedade receptor de recursos tem dois subpropriedades: **Assembly** e **nome da classe**. O assembly deve usar seu totalmente qualificado, nome "forte" e o nome da classe devem ser o nome de tipo completo. Para obter mais informações, consulte [Assemblies com nome forte](http://go.microsoft.com/fwlink/?LinkID=169573). Depois de implantar a solução no SharePoint, o recurso usa o receptor referenciado para tratar eventos de recurso.  
  
 No momento da compilação de solução, os valores de propriedade do receptor de recursos em seus projetos e o recurso mesclam para definir os atributos ReceiverAssembly e ReceiverClass do elemento recurso no manifesto do recurso do arquivo de solução (. wsp) do SharePoint. Portanto, se os valores de propriedade do Assembly e o nome da classe de um item de projeto e um recurso forem especificados, os valores de propriedade de recurso e o item de projeto devem corresponder. Se os valores não coincidirem, você receberá um erro de validação. Se você quiser que um item de projeto para fazer referência a um assembly do receptor de recurso que não usa o recurso, movê-lo para outro recurso.  
  
 Se você fizer referência a um assembly do receptor de recurso não ainda estiver no servidor, você também deve incluir o arquivo de assembly no pacote. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não adicioná-lo para você. Quando você implanta o recurso, o arquivo de assembly é copiado do sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] ou a pasta Bin no diretório físico do SharePoint. Para obter mais informações, consulte como: [como: adicionar e remover Assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Para obter mais informações sobre os destinatários de recurso, consulte [receptor de evento de recurso](http://go.microsoft.com/fwlink/?LinkID=169574) e [eventos de recurso](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Referências de saída do projeto  
 A propriedade de referências de saída do projeto especifica uma dependência, como um assembly, que o item de projeto precisa ser executada. Por exemplo, suponha que sua solução tem um projeto BDC e um projeto de classe. Se o projeto BDC tem uma dependência no assembly que é a saída do projeto de classe, você pode referenciar o assembly na propriedade de referências de saída do projeto do projeto BDC. Quando o projeto BDC é empacotado, o assembly dependente está incluído no pacote.  
  
 Referências de saída do projeto são geralmente assemblies, mas em alguns casos (por exemplo, projetos do Silverlight) podem ser outros tipos de arquivo.  
  
 Para obter mais informações, consulte [como: adicionar uma referência de saída do projeto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Entradas de controle de segurança  
 O SharePoint fornece um mecanismo de segurança, chamado de entradas de controle de segurança, para limitar o acesso de usuários não confiáveis para alguns controles. Por design, o SharePoint permite que usuários não confiáveis carregar e criar páginas ASPX no servidor do SharePoint. Para impedir que esses usuários adicionando o código não seguro para páginas ASPX, SharePoint limita o acesso a *controles seguros*. Controles seguros são ASPX controles e Web parts consideradas segura e que pode ser usado por qualquer usuário em seu site. Para obter mais informações, consulte [etapa 4: adicionar a Web Part à lista de controles](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Cada item de projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tem uma propriedade chamada **entradas de controle de segurança** que tem dois subpropriedades booleanas: **seguro** e **seguro contra Script**. A propriedade de segurança Especifica se os usuários não confiáveis podem acessar um controle. A propriedade de segurança contra Script Especifica se os usuários não confiáveis podem exibir e alterar as propriedades do controle.  
  
 Entradas de controle de segurança são referenciadas em uma base de assembly. Adicionar entradas de controle de segurança ao assembly do projeto inserindo-os no item de projeto **entradas de controle de segurança** propriedade. No entanto, você também pode adicionar entradas de controle de segurança para o assembly do projeto por meio de **avançado** guia o **Package Designer** quando você adiciona um assembly adicional para o pacote. Para obter mais informações, consulte [como: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) ou [Registrando um Assembly de parte da Web como um controle seguro](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Entradas de XML para controles seguros  
 Quando você adiciona uma entrada de controle de segurança para um item de projeto ou assembly do projeto, uma referência é gravada para o manifesto de pacote no seguinte formato:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Estendendo o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  