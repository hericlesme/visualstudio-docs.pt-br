---
title: "Suporte de automação para páginas de opções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ffc56e4b36814a8bed7a0f93d66cc87c0b6fc466
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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