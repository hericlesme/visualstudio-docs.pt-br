---
title: Criação de editores personalizados e Designers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0dbc0db9d5116e372d96b43059a393ac8f4b5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-custom-editors-and-designers"></a>Criação de Designers e editores personalizados
O ambiente de desenvolvimento integrado (IDE) do Visual Studio pode hospedar diferentes tipos de editor:  
  
-   Editor de núcleo do Visual Studio  
  
-   Editores personalizados  
  
-   Editores externos  
  
-   Designers  
  
 As informações a seguir o ajudará a escolher o tipo de editor que é necessário.  
  
## <a name="types-of-editor"></a>Tipos de Editor  
 Para obter informações sobre o editor de núcleo do Visual Studio, consulte [estendendo o Editor e o idioma serviços](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Editores personalizados  
 Um editor personalizado é aquele que foi projetado para trabalhar em casos especializados. Por exemplo, você pode criar um editor cuja função é ler e gravar dados em um repositório específico, como um servidor Microsoft Exchange. Se você quiser um editor que funciona com o tipo de projeto ou se você deseja que um editor com apenas alguns comandos específicos, escolha um editor personalizado. No entanto, observe que os usuários não poderão usar um editor personalizado para editar padrão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos.  
  
 Um editor personalizado pode usar uma fábrica de editor e adicionar informações sobre o editor do registro. No entanto, o tipo de projeto associado com o editor personalizado pode instanciar o editor personalizado de outras maneiras.  
  
 Um editor personalizado pode usar a ativação no local ou inserindo simplificada para implementar uma exibição.  
  
##### <a name="external-editors"></a>Editores externos  
 Editores externos são editores que não são integrados ao Visual Studio, como Microsoft Word, o bloco de notas ou o Microsoft FrontPage. Você pode chamar esse um editor se, por exemplo, você estiver passando o texto a ele de seu VSPackage. Editores externos se registrem e podem ser usados fora do Visual Studio. Quando você chamar um editor externo, e pode ser incorporado em uma janela do host, ele aparece em uma janela no IDE. Caso contrário, o IDE criará uma janela separada para ele.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método define a prioridade do documento usando o <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração. Se o `DP_External` valor for especificado, o arquivo pode ser aberto por um editor externo.  
  
## <a name="editor-design-decisions"></a>Decisões de Design do Editor  
 As seguintes questões de design ajudará você a escolher o tipo de editor melhor adequado para seu aplicativo:  
  
-   Seu aplicativo salvará os dados em arquivos ou não? Se salvará os dados nos arquivos, eles estará em um formato personalizado ou padrão?  
  
     Se você usar um formato de arquivo padrão, outros tipos de projeto, além de seu projeto será capazes de abrir e dados de leitura/gravação a elas. Se você usar um formato de arquivo personalizado, no entanto, o tipo de projeto será capaz de abrir e dados de leitura/gravação a elas.  
  
     Se seu projeto usa arquivos, você deve personalizar o editor padrão. Se seu projeto não usa arquivos, mas em vez disso, usa itens em um banco de dados ou outro repositório, você deve criar um editor personalizado.  
  
-   O editor é necessário hospedar controles ActiveX?  
  
     Se seu editor de hospedar controles ActiveX, em seguida, implementar um editor de ativação no local, conforme descrito na [ativação no local](../extensibility/in-place-activation.md). Se ele não hospedar controles ActiveX, em seguida, use um editor de incorporação simplificado ou personalizar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor padrão.  
  
-   O editor oferecerá suporte a vários modos de exibição? Se você quiser que os modos de exibição do editor para ser visíveis ao mesmo tempo como o editor padrão, você deve suportar vários modos de exibição.  
  
     Se seu editor precisa dar suporte a vários modos de exibição, os dados de documento e objetos de exibição de documento para o editor deverá ser objetos separados. Para obter mais informações, consulte [dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
     Se o editor oferece suporte a vários modos de exibição, você planeja usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal a implementação do buffer do editor de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto) para seu objeto de dados de documento? Ou seja, você deseja dar suporte a seu editor exibição-lado a lado com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal? A capacidade de fazer isso é a base do designer de formulários.  
  
-   Se você precisar hospedar um editor externo, pode o editor ser incorporado dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Se ele pode ser inserido, você deve criar uma janela do host para o editor externo e, em seguida, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método e defina o <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valor de enumeração para `DP_External`. Se o editor não pode ser inserido, o IDE criará automaticamente uma janela separada para ele.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passo a passo: Criar um editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explica como criar um editor personalizado.  
  
 [Passo a passo: Adicionar recursos a um editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explica como adicionar recursos a um editor personalizado.  
  
 [Inicialização do designer e configuração de metadados](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explica como inicializar um designer.  
  
 [Fornecer suporte à função desfazer para designers](../extensibility/supplying-undo-support-to-designers.md)  
 Explica como dar suporte ao comando Desfazer designers.  
  
 [Coloração de sintaxe em editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explica a diferença entre as cores no editor de núcleo e nos editores personalizados de sintaxe.  
  
 [Dados de documentos e exibição de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explica como implementar dados de documentos e exibições de documento em editores personalizados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explica como acessar o editor de núcleo por meio da API herdada.  
  
 [Desenvolver um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explica como implementar um serviço de linguagem.  
  
 [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>