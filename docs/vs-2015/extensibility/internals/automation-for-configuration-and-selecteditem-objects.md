---
title: Automação de configuração e objetos SelectedItem | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9d5da07c4505aef38fbef22b8680a8c0914056a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463986"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação de configuração e objetos SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [automação de configuração e objetos SelectedItem](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-for-configuration-and-selecteditem-objects).  
  
Você pode automatizar a compilação e os processos do item selecionado no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="automation-for-builds"></a>Automação de compilações  
 Compilação ou a configuração tem um modelo de automação que é fornecido quando você implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obter mais informações, consulte [Understanding Build Configurations (Noções básicas sobre configurações de build)](../../ide/understanding-build-configurations.md).  
  
 Se você criar um VSPackage e deseja controlar as opções de configuração, você deve usar o modelo de automação.  
  
## <a name="automation-for-selecteditem"></a>Automação para SelectedItem  
 Você não precisa fornecer uma implementação para o `SelectedItem` porque o Visual Studio contém uma implementação padrão do objeto. No entanto, você pode implementar o `SelectedItem` objeto se você preferir. Você deve implementar um objeto que contém o `SelectedItem` da interface e retorna uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com VSITEMID definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuindo para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)

