---
title: Automação de configuração e objetos de SelectedItem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4ac269664136aed51542e53900ffc1c87f21fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação de configuração e objetos de SelectedItem
Você pode automatizar a compilação e os processos do item selecionado no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automação de compilações  
 Compilação ou a configuração tem um modelo de automação que é fornecido quando você implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obter mais informações, consulte [Understanding Build Configurations (Noções básicas sobre configurações de build)](../../ide/understanding-build-configurations.md).  
  
 Se você criar um VSPackage e controlar as opções de configuração, você deve usar o modelo de automação.  
  
## <a name="automation-for-selecteditem"></a>Automação de SelectedItem  
 Você não precisa fornecer uma implementação para o `SelectedItem` porque o Visual Studio contém uma implementação padrão do objeto. No entanto, você pode implementar o `SelectedItem` se você preferir do objeto. Você deve implementar um objeto que contém o `SelectedItem` de interface e retornar uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com VSITEMID definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Que contribuem para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)