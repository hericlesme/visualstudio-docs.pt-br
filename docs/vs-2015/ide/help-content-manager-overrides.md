---
title: Substituições do Gerenciador de Conteúdo da Ajuda | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fae83a05b3f6f8774e7ed119483274f22c4ddc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465835"
---
# <a name="help-content-manager-overrides"></a>Substituições do Gerenciador de Conteúdo da Ajuda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Ajuda do Gerenciador de conteúdo substitui](https://docs.microsoft.com/visualstudio/ide/help-content-manager-overrides).  
  
Você pode modificar o Registro para alterar o comportamento padrão do Visualizador da Ajuda e dos recursos relacionados à Ajuda na IDE do Visual Studio.  
  
|Tarefa|Chave do Registro|Valor e definição|  
|----------|------------------|--------------------------|  
|Define o ponto de extremidade do serviço exclusivo|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Defina a opção online e offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp--Insira `0` para especificar a Ajuda local e insira `1` para especificar a Ajuda online.|  
|Define o ponto de extremidade F1 exclusivo|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Substituir a prioridade do trabalho BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (em um computador de 64 bits)\Microsoft\Help\v2.2|BITSPriority – Use um dos seguintes valores: **foreground**, **high**, **normal** ou **low**.|  
|Desabilitar online (e opção online do IDE)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (em um computador de 64 bits)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--Definido como 1 para desabilitar o acesso ao conteúdo da Ajuda online.|  
|Desabilitar o gerenciamento do conteúdo|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (em um computador de 64 bits)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled – Definido como 1 para desabilitar a guia **Gerenciar Conteúdo** no Visualizador da Ajuda.|  
|Aponte para o repositório de conteúdo local no compartilhamento de rede|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath=”*ContentStoreNetworkShare*”|  
|Desabilitar a instalação de conteúdo na primeira inicialização do recurso do Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (em um computador de 64 bits)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--Definido como 1 para desabilitar os recursos da Ajuda que são configurados na primeira vez que o Visual Studio é iniciado.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia do administrador do Help Viewer](../ide/help-viewer-administrator-guide.md)



