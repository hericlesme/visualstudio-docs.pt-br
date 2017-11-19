---
title: "Inicialização de Designer e a configuração de metadados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12ed4c42335590b7e48d0f6f0fed716a7f149bd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialização de Designer e a configuração de metadados
Manipulação dos atributos de metadados e o filtro associado a um designer ou um componente do designer fornece um mecanismo para aplicativos definir quais ferramentas são usadas por um designer específico para lidar com diferentes <xref:System.Type> objetos (como estruturas de dados classes ou entidades gráficas), quando o designer está disponível e como o Visual Studio IDE é configurado para oferecer suporte ao designer (para instância que **caixa de ferramentas** categoria ou guia está disponível).  
  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece vários mecanismos para facilitar o controle de inicialização de um designer ou designer do componente e a manipulação de seus metadados por um VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicializando metadados e informações de configuração  
 Como eles são carregados sob demanda, VSPackages não tenham sido carregados pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente antes da instanciação de um designer. Portanto, VSPackages não é possível usar o mecanismo padrão para a configuração de um designer ou o componente designer na criação, que é manipular um <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> eventos. Em vez disso, um VSPackage implementa uma instância das <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> de interface e se registra para fornecer personalizações, conhecidas como extensões de superfície de design.  
  
### <a name="customizing-initialization"></a>Personalizando a inicialização  
 Personalizar um designer, um componente ou uma superfície de design, envolve:  
  
1.  Modificando os metadados de designer e alterando efetivamente como um determinado <xref:System.Type> é acessado ou convertido.  
  
     Isso geralmente é feito por meio de <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.TypeConverter> mecanismos.  
  
     Por exemplo, quando <xref:System.Windows.Forms>-designers com base são inicializados, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente modifica o <xref:System.Drawing.Design.UITypeEditor> para <xref:System.Web.UI.WebControls.Image> objetos usados com o designer para usar o Gerenciador de recursos para obter bitmaps em vez do sistema de arquivos.  
  
2.  Integração com o ambiente, por exemplo, por eventos se inscrever ou obter informações de configuração de projeto. Você pode obter informações de configuração de projeto e assinar eventos obtendo o <xref:System.ComponentModel.Design.ITypeResolutionService> interface.  
  
3.  Modificação do ambiente do usuário ativando apropriado **caixa de ferramentas** categorias ou restringindo aplicabilidade do designer, aplicando uma instância do <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe para o designer.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicialização Designer por um VSPackage  
 Um VSPackage deve tratar designer inicialização por:  
  
1.  Criar um objeto que implementa o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.  
  
    > [!NOTE]
    >  O <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe nunca deve ser implementada no mesmo objeto, como o <xref:Microsoft.VisualStudio.Shell.Package> classe.  
  
2.  Registrar a classe que implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> como fornecer suporte para extensões de designer do VSPackage aplicando instâncias do <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> para a classe que fornece a implementação do VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Sempre que qualquer designer ou um componente do designer é criado, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
1.  Acessa cada provedor de extensão de superfície de design registrado.  
  
2.  Cria e inicializa uma instância de cada provedor de extensão de superfície de design <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto  
  
3.  Chama cada provedor de extensão de superfície de design <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> método ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> método (conforme apropriado).  
  
 Ao implementar o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> do objeto como um membro de um VSPackage, é importante entender que:  
  
1.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente não fornece controle sobre quais metadados ou outras configurações de um determinado `DesignSurfaceExtension` modifica do provedor. É possível que dois ou mais `DesignSurfaceExtension` modificando o mesmo recurso designer maneiras em conflito com a modificação final sendo definitiva de provedores. É indeterminado qual modificação é aplicada pela última vez.  
  
2.  É possível restringir explicitamente uma implementação do <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> designers específicos, aplicando as instâncias do objeto <xref:System.ComponentModel.ToolboxItemFilterAttribute> para que a implementação. Para obter mais informações sobre **caixa de ferramentas** item filtragem, consulte o <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Provisionamento de metadados adicionais  
 Um VSPackage pode alterar a configuração de um designer ou o componente designer diferente em tempo de design.  
  
 O <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe pode ser usada programaticamente, ou ser aplicada a um VSPackage fornecendo um designer.  
  
 Uma instância do <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe é usada para modificar os metadados de componentes criados em uma superfície de design. Por exemplo, um pode substituir um navegador de propriedade padrão usado pelo <xref:System.Windows.Forms.CommonDialog> objetos, com um navegador de propriedade personalizada.  
  
 Modificações fornecidas por uma instância de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> aplicada a implementação do VSPackage <xref:Microsoft.VisualStudio.Shell.Package> pode ter um dos dois escopos:  
  
-   Global – para todas as novas instâncias de um determinado componente  
  
-   Local – pertence somente a instância do componente criado em uma superfície de design fornecida pelo VSPackage atual.  
  
 O `IsGlobal` propriedade do <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instância aplicada a implementação do VSPackage <xref:Microsoft.VisualStudio.Shell.Package> determina neste escopo.  
  
 Aplicando o atributo a uma implementação de <xref:Microsoft.VisualStudio.Shell.Package> com o <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propriedade o <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objeto definido para `true`, abaixo, altera o navegador para todo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Se o sinalizador global foi definido como `false`, em seguida, a alteração de metadados é local para o designer atual suportado pelo VSPackage atual:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  No momento, a superfície de design oferece suporte apenas a criação de componentes e, portanto, somente os componentes podem ter metadados locais. No exemplo acima, está tentando modificar uma propriedade, como o `Color` propriedade de um objeto. Se `false` foi passado para o sinalizador global, `CustomBrowser` nunca será exibido como o designer, na verdade, nunca cria uma instância do `Color`. Definir o sinalizador global como `false` é útil para componentes, como controles, temporizadores e caixas de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Estendendo o suporte ao tempo de design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)