---
title: Suporte de automação para páginas de opções | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128566"
---
# <a name="automation-support-for-options-pages"></a>Suporte de automação para páginas de opções
VSPackages pode fornecer personalizado **opções** caixas de diálogo para o **ferramentas** menu (páginas de opções de ferramentas) em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e pode torná-los disponíveis para o modelo de automação.  
  
## <a name="tools-options-pages"></a>Páginas de opções de ferramentas  
 Para criar um **opções de ferramentas** página, um VSPackage deve fornecer uma implementação de controle de usuário retornada para o ambiente por meio da implementação do VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método (ou para código gerenciado a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método).  
  
 É opcional, mas é altamente recomendável, para permitir o acesso a esta página nova por meio do modelo de automação. Você pode fazer isso através das seguintes etapas:  
  
1.  Estender o <xref:EnvDTE._DTE.Properties%2A> objeto por meio da implementação de um objeto derivada de IDispatch.  
  
2.  Retornar uma implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (ou para código gerenciado a <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) para o objeto derivada de IDispatch.  
  
3.  Quando um consumidor de automação chama o <xref:EnvDTE._DTE.Properties%2A> método em um personalizado **opção** página de propriedade, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obter um personalizado **Ferramentas opções** automação da página implementação.  
  
4.  O objeto de automação do VSPackage é usado para fornecer a cada <xref:EnvDTE.Property> retornado por <xref:EnvDTE._DTE.Properties%2A>.  
  
 Para obter um exemplo de implementação de uma página de opções de ferramentas personalizada, consulte [VSSDK exemplos](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Consulte também  
 [Expor objetos do projeto](../../extensibility/internals/exposing-project-objects.md)