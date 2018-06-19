---
title: Visão geral de cor e de fonte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8185d5c931ccf0b3b15fba10405cf050eb7c6241
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130214"
---
# <a name="font-and-color-overview"></a>Visão geral de cor e de fonte
Este tópico discute as configurações de fonte e cor do texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Ele também apresenta os conceitos de categorias e itens de exibição e descreve como VSPackages e o editor de núcleo que usam atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>A página de propriedades de cores e fontes  
 Você pode gerenciar os atributos do texto exibido no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) por meio de **fontes e cores** página de propriedades. Para localizar o **fontes e cores** página de propriedade, no **ferramentas** menu, clique em **opções**. Expanda **ambiente**e, em seguida, clique em **fontes e cores**.  
  
## <a name="categories-and-display-items"></a>Categorias e itens de exibição  
 Fontes e cores são organizadas em **categorias** e **itens de exibição**.  
  
-   Um **categoria** é um contêiner lógico ou funcional para um número de **itens de exibição**.  
  
     Uma lista de **categorias** está no **Mostrar configurações de** caixa de lista suspensa do **fontes e cores** página de propriedades.  
  
-   Um **exibir o Item** é uma entidade de texto bem definido como um comentário, uma cadeia de caracteres ou uma estrutura de controle que deve ser coloridos quando exibido.  
  
 Cada **exibir o Item** exclusivamente é definido dentro do **categoria** que o contém. Consequentemente, mais de um **categoria** pode ter um **exibir o Item** com o mesmo nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Controle de VSPackage fontes e cores  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite VSPackages para:  
  
-   Definir fontes e cores **categorias**.  
  
-   Especificar as fontes e cores usadas para apresentar **itens de exibição**.  
  
-   Interagir com o **fontes e cores** página de propriedades.  
  
-   Vários agregação **categorias** em grupos.  
  
-   Manter as alterações nas configurações padrão.  
  
 Há duas formas de interagir com as seleções de fonte e cor dentro de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Uma maneira é conhecida como *coloração de sintaxe*. Ele é usado por um VSPackage que personaliza existente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor implementar um serviço de linguagem e criar uma fonte de editor.  
  
     Apenas uma **categoria** oferece suporte a esse mecanismo, ou seja, o **Editor de texto**.  
  
-   Uma alternativa mais geral dá suporte a todos os outros **categorias** e componentes de interface do usuário que não seja o editor de fonte ao exibir texto. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Configurações de texto do Editor de núcleo  
 Configurações de fontes e cores para o editor de núcleo de um objeto de serviço de linguagem são administradas pelo **texto EditorCategory** encontrado no **Mostrar configurações de** caixa de lista suspensa do **fontes e cores** página de propriedades.  
  
 Ao trabalhar com editores, você deve usar a fonte especializada e o mecanismo de controle de cor que fornece o serviço de linguagem para controlar e estender o **Editor de texto** configurações. O mecanismo é conhecido como *cores de sintaxe* e fornece:  
  
-   Uma técnica simplificada para gerenciar as fontes e cores de itens de exibição.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Um mecanismo de colorização bem definidos e otimizada.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   A capacidade de usar itens de exibição interna do **EditorCategory texto** e estendê-las.  
  
     Para obter mais informações, consulte [como: Use itens internos de pode ser colorido](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [itens pode ser colorido personalizados](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistência automática do atual estado de ambas as internas e personalizada exibir itens com o **Editor de texto** categoria.  
  
 Para obter mais informações sobre a sintaxe cores consulte [coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)