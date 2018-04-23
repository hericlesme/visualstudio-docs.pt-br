---
title: Interface de usuário de propriedades do projeto | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 788107666f8103a77753b93fa7c1febc73f9b97f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="project-property-user-interface"></a>Interface de usuário de propriedades do projeto
Um subtipo de projeto pode usar os itens no projeto **páginas de propriedade** caixa de diálogo conforme eles são fornecidos pelo projeto base, ocultar ou tornar os controles somente leitura e páginas inteiras fornecido ou adicionar páginas de subtipo específicas do projeto para o **Páginas de propriedade** caixa de diálogo.

## <a name="extending-the-project-property-dialog-box"></a>Estendendo a caixa de diálogo de propriedades do projeto
 Um subtipo de projeto implementa extensores de automação e procurar objetos de configuração do projeto. Esses extensores implementam o <xref:EnvDTE.IFilterProperties> interface fazer determinadas propriedades ocultos ou somente leitura. O **páginas de propriedade** caixa de diálogo do projeto base, implementado pelo projeto base, respeita a filtragem executada pelos extensores de automação.

 O processo de estender uma **propriedade do projeto** caixa de diálogo é descrita a seguir:

-   O projeto base recupera os Extensores do subtipo de projeto, Implementando a <xref:EnvDTE80.IInternalExtenderProvider> interface. A procura, automação de projeto e os objetos de procura de configuração de projeto do projeto base todos os implementam esta interface.

-   A implementação de <xref:EnvDTE80.IInternalExtenderProvider> para o objeto de procura de projeto e o objeto de automação do projeto delegar para o <xref:EnvDTE80.IInternalExtenderProvider> implementação do agregador de subtipo de projeto (ou seja, eles `QueryInterface` para <xref:EnvDTE80.IInternalExtenderProvider> no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto de projeto).

-   O objeto de procura de configuração de projeto base também implementa <xref:EnvDTE80.IInternalExtenderProvider> para conectar diretamente no extensor de automação do objeto de configuração do subtipo de projeto. Sua implementação delega para o <xref:EnvDTE80.IInternalExtenderProvider> interface implementada pelo agregador de subtipo do projeto.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado pelo objeto de procura de configuração de projeto, retorna o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, também é implementado pelo objeto de procura de configuração de projeto, retorna o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objeto.

-   Um subtipo de projeto pode determinar as CATIDs apropriadas para os diversos objetos extensíveis do projeto base em tempo de execução, recuperando o seguinte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores:

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

Para determinar as CATIDs do escopo do projeto, o subtipo de projeto recupera as propriedades acima para [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) do `VSITEMID typedef`. Um subtipo de projeto talvez também queira controlar quais **páginas de propriedade** páginas da caixa de diálogo são exibidas para o projeto, configuração dependente e independentes de configuração. Alguns subtipos de projeto talvez seja necessário remover as páginas internas e adicionar a páginas específicas do subtipo de projeto. Para habilitar isso, o projeto de cliente gerenciado chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para as seguintes propriedades:

-   `VSHPROPID_PropertyPagesCLSIDList` – uma lista separada por ponto-e-vírgula de CLSIDs de páginas de propriedades de configuração independente.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` uma lista separada por ponto-e-vírgula de CLSIDs de páginas de propriedades de configuração dependente.

Porque o projeto de agregações de subtipo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> do objeto, ele pode substituir a definição dessas propriedades para controlar quais **páginas de propriedade** caixas de diálogo são exibidas. O subtipo de projeto pode recuperar essas propriedades do projeto base interno e, em seguida, adicionar ou remover CLSIDs conforme necessário.

Novas páginas de propriedade adicionadas por um subtipo de projeto são passadas a um objeto de procura de configuração de projeto da implementação do projeto de base. Esse objeto de procura de configuração de projeto oferece suporte a extensores de automação. Para obter mais informações sobre AutomationExtenders, consulte [implementando e extensores de automação usando](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). As páginas de propriedades implementadas pela chamada de subtipo de projeto <xref:EnvDTE.Project.Extender%2A> para recuperar seu próprio projeto subtipo configuração Procurar objeto que estende o objeto de procura de configuração do projeto base.

## <a name="see-also"></a>Consulte também

- <xref:EnvDTE.IFilterProperties>
- [Caixa de diálogo páginas de propriedades](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)