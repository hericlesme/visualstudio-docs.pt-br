---
title: Adição de serviços Web para sistemas de projeto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 80de75b1b10a761e88b86c0982c0dc925c6eeeb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464716"
---
# <a name="adding-web-services-to-project-systems"></a>Adição de serviços Web para sistemas de projeto
Serviços Web XML são, em geral, os recursos endereçáveis por URL que retornam informações de programação para o sistema de projeto usando o protocolo SOAP (Simple Object Access Protocol). Você pode integrar serviços da Web para seu sistema de projeto de VSPackage usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interface.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Para adicionar um serviço Web ao seu sistema de projeto  
  
1.  Chame `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> por meio da interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> service.  
  
2.  Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>. Se você passar `pDiscoverySession` parâmetro conforme `NULL`, uma sessão de descoberta é criada para você e a sessão é armazenado em cache para que ele esteja disponível para uso subsequente pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> método retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>. Passe o objeto de automação para a pasta de referências de serviço da Web como o `pUnkWebReferenceFolder` parâmetro. Ambiente do Visual Studio, em seguida, verifica se o serviço Web já está presente. Se o serviço Web não estiver presente, o ambiente de baixa e adiciona o serviço Web para uma pasta e arquivos adicionais (como arquivos. WSDL) para os nós filho da pasta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>