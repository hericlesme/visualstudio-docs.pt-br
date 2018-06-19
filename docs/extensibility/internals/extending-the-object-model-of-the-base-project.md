---
title: Estendendo o modelo de objeto do projeto Base | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9cffbecf585f6f8be4174531a91e466f65ab9a72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130551"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Estendendo o modelo de objeto do projeto Base

Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes locais:

-   Project.Extender ("\<ProjectSubtypeName >")-isso permite que um subtipo de projeto oferece um objeto com métodos personalizados do <xref:EnvDTE.Project>. Um subtipo de projeto pode usar extensores de automação para expor o `Project` objeto. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal deve oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondente a um `itemid` valor [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >")-isso permite que um subtipo de projeto oferece um objeto com métodos personalizados de um determinado <xref:EnvDTE.ProjectItem> objeto dentro do projeto. Um subtipo de projeto pode usar extensores de automação para expor esse objeto. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondente a um desejado <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Properties - desta coleção expõe as propriedades de configuração independente do `Project` objeto. Para obter mais informações sobre propriedades do projeto, consulte <xref:EnvDTE.Project.Properties%2A>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para o `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondente a um `itemid` valor [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - esta coleção expõe as propriedades dependentes de configuração do projeto para uma configuração específica (por exemplo, Debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal oferece seu objeto para o CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondente a um `itemid` valor [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). O <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface é usada para diferenciar um objeto de configuração de procura do outro.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>