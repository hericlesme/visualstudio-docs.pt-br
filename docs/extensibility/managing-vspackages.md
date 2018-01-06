---
title: Gerenciando VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3c3201c032d0cae645460e614b6d4138297e4a93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-vspackages"></a>Gerenciando VSPackages
Na maioria dos casos você não precisa se preocupar em Gerenciar VSPackages, desde que os modelos de projeto e item registrar e carregar o pacote automaticamente. No entanto, em algumas circunstâncias você precisará saber um pouco mais para gerenciar seu pacote.  
  
## <a name="using-the-experimental-instance"></a>Usando a instância experimental  
 Para obter mais informações sobre a instância experimental, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrando e Cancelando o registro VSPackages  
 Para saber como registrar e cancelar o registro VSPackages e outros tipos de extensão, consulte [Registrando e Cancelando o registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Carregando um VSPackage  
 VSPackages pode ser definidos como autoload quando um determinado que CMDUICONTEXT GUID está ativado. Para obter mais informações, consulte [VSPackages carregar](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Usando AsyncPackage para carregar VSPackages em segundo plano  
 A classe AsyncPackage permite que o pacote de carregamento em um thread em segundo plano para melhor capacidade de resposta da interface do usuário no Visual Studio. Para obter mais informações, consulte [como: Use AsyncPackage para VSPackages de carregamento em segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interface do usuário baseada em regras para extensões  
 Com base em regras de contextos de interface do usuário permite que os autores de extensão definir as condições precisas sob a qual um contexto de interface do usuário é ativado e carregados VSPackages associados. Para obter mais informações, consulte [como: contexto de interface do usuário baseada em regras de uso de extensões do Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnóstico de desempenho de extensão  
Extensões podem afetar o desempenho de carga de inicialização e a solução. Saiba como o impacto de extensão do Visual Studio é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como um impacto de extensão de desempenho. Para obter mais informações, consulte [como: diagnosticar extensão desempenho](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Solucionando problemas de VSPackages  
 Descubra as técnicas para solucionar problemas de VSPackages que não carregam ou estão apresentando erros: [VSPackages de solução de problemas](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)