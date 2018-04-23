---
title: Desativar avisos de compatibilidade para Plug-ins de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d3cffbd6a8b6c21aa6e958495b88eb51a5724a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como: desativar avisos de compatibilidade para Plug-ins de controle de origem
Um usuário pode ver várias avisos de compatibilidade ao utilizar o controle de origem no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os avisos apresentados dependem dos recursos de plug-in de controle de origem e podem ser desabilitados como detalhada aqui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desabilitar o aviso: "para garantir a integração de controle de origem ideal com o Visual Studio..."  
  
-   Defina a seguinte entrada do registro (adicionando o valor se necessário):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Esse aviso é exibido para todos os não -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desabilitar o aviso: "o provedor de controle do código-fonte instalado não oferece suporte a todos os recursos..."  
  
-   Defina os seguintes dois valores do registro (adicionando os valores se necessário):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Esse aviso é exibido se o plug-in de controle de origem não explicitamente suporta reentrada para vários projetos (ou seja, se ele pode verificar em apenas um projeto e um arquivo por vez).  
  
     É melhor dar suporte a reentrada (`SCC_CAP_REENTRANT` capacidade); portanto irá remover este aviso. No entanto, se esse suporte não for possível, essas entradas do Registro podem ser definidas.  
  
## <a name="see-also"></a>Consulte também  
 [Sinalizadores de recurso](../extensibility/capability-flags.md)