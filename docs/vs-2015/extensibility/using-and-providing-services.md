---
title: Usar e fornecer serviços | Microsoft Docs
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
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: facf0bb9968e3ffbc9a68eb8eee906f300eb1859
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476118"
---
# <a name="using-and-providing-services"></a>Usando e fornecendo serviços
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Using e fornecendo serviços](https://docs.microsoft.com/visualstudio/extensibility/using-and-providing-services).  
  
Um serviço é um contrato entre dois VSPackages. Um VSPackage oferece um conjunto específico de interfaces para outro VSPackage consumir. Por exemplo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oferece o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de serviço a qualquer VSPackage ele carrega. Esse serviço fornece o <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, que pode ser usado para gravar no log de atividade. Para obter mais informações, consulte [como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages podem oferecer serviços de suas próprias por usar o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...  
  
 O Visual Studio oferece serviços importantes, como o seguinte:  
  
|Serviço IDE|Descrição|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornece acesso ao IDE services lidar com a funcionalidade básica, os VSPackages e o registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece janelas básicas e funcionalidade relacionada à interface do usuário no IDE, como a capacidade de criar ferramentas e janelas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece a funcionalidade básica de relacionadas à solução, como a capacidade de enumerar os projetos, criar novos projetos e monitorar as alterações do projeto.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Fundamentos do serviço](../extensibility/internals/service-essentials.md)  
 Apresenta os elementos importantes de um serviço do Visual Studio.  
  
 [Como obter um serviço](../extensibility/how-to-get-a-service.md)  
 Descreve como solicitar (consumir) um serviço.  
  
 [Como fornecer um serviço](../extensibility/how-to-provide-a-service.md)  
 Discute como fornecer um serviço.  
  
 [Como fornecer um serviço assíncrono do Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Discute como fornecer um serviço assíncrono.  
  
 [Como solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md)  
 Aborda problemas comuns e apresenta soluções para eles.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)

