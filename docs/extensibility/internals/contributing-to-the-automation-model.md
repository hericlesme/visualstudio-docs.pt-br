---
title: Que contribuem para o modelo de automação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8333ed5c107f7f62e736ccd62e1b79723b5eb8f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130512"
---
# <a name="contributing-to-the-automation-model"></a>Que contribuem para o modelo de automação
Visual Studio fornece um conjunto de interfaces de automação para personalizar o ambiente. O modelo de automação é o modelo de objeto que permite que os usuários finais criem Visual Studio add-ins e extensões.  
  
 Além disso, é apropriado para você, como desenvolvedor VSPackage, contribuir para o modelo de automação. ao fazer isso, você habilitar os usuários finais do seu VSPackage criar suplementos e geralmente fornecem uma experiência de usuário consistente de modelo ao usarem o VSPackage no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para tornar o usuário final experiência consistente, você pode seguir um conjunto de diretrizes ao criar o VSPackage para que o modelo de automação para o VSPackage segue as ideias em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)  
 Define o modelo de automação como um grupos de objetos que controlam os principais aspectos do ambiente comum. Esse conjunto de objetos é mostrado em um diagrama do modelo de automação.  
  
 [Fornecer automação a VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Discute as duas maneiras de fornecer automação para o VSPackage.  
  
 [Expor objetos do projeto](../../extensibility/internals/exposing-project-objects.md)  
 Fornece instruções passo a passo para a criação de objetos específicos de VSPackage.  
  
 [Modelagem do projeto](../../extensibility/internals/project-modeling.md)  
 Explica os objetos de projeto padrão que são necessárias para criar a automação para o novo tipo de projeto e ilustra o caminho a seguir de automação de projeto. Este tópico também fornece uma lista de declarações e a implementação de classes.  
  
 [Exposição de eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fornece instruções passo a passo para a criação de eventos para o seu modelo de automação.  
  
 [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)  
 Descreve como retornar um objeto de automação para dar suporte a propriedades de um VSPackage personalizado **opções** caixa de diálogo de **ferramenta** menu estendendo o `DTE.Properties` objeto.  
  
 [Fornecer automação para código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica o que a criação de um modelo de automação para o seu código não é necessário. No entanto, um link é fornecido neste tópico que fornece informações profundas em modelos de código.  
  
 [Como fornecer automação para o Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica o que fornece automação é uma boa ideia sempre que você deseja disponibilizar os objetos de automação em uma janela, e o ambiente já não fornecem um objeto de automação prontos. Discute a automação para janelas de ferramentas e janelas de documentos.  
  
 [Usar o modelo de automação](../../extensibility/internals/using-the-automation-model.md)  
 Fornece dois exemplos de código que mostram como um consumidor de automação obtém o projeto inicial objetos de automação.  
  
 [Automação de configuração e objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fornece informações sobre a automação para opções de configuração e automação para itens selecionados.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornece um exemplo de código que mostra como um VSPackage participa no modelo de objeto de automação de DTE. Lista de parâmetros, valores de retorno e comentários selecionados.  
  
## <a name="related-sections"></a>Seções relacionadas