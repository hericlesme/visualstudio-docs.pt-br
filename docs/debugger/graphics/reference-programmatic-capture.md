---
title: "Referência (Captura programática) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 899211452a776931e3d0d9742e499ed8ba78a652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="reference-programmatic-capture"></a>Referência (captura programática)
Diagnóstico de gráficos dá suporte a controle programático sobre seus recursos de captura, por meio de captura programática API. Você pode usar essa API para alternar e adicionar mensagens para o diagnóstico de gráficos HUD (visor), inicializar e criar gráficos arquivos de log e capturar informações de gráficos.  
  
## <a name="programmatic-capture-apis"></a>APIs de captura programática  
  
### <a name="classes"></a>Classes  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Classe VsgDbg](vsgdbg-class.md)|Representa a interface por meio do qual o componente no aplicativo de diagnóstico de gráficos é controlado por meio de programação.|  
  
### <a name="preprocessor-symbols"></a>Símbolos de pré-processamento  
  
|Nome|Descrição|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Define sua presença se o arquivo de log do gráfico é salvo para o diretório de arquivos temporários do usuário.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Define o nome de arquivo padrão do arquivo de log do gráfico.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Define sua presença se uma instância padrão do `VsgDbg` classe é fornecida.|  
  
## <a name="related-articles"></a>Artigos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Capturando informações de gráficos](capturing-graphics-information.md)|Mostra como capturar informações de gráficos do seu aplicativo com base em DirectX para que você possa usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para diagnosticar problemas de renderização.|  
|[Visão Geral](overview-of-visual-studio-graphics-diagnostics.md)|Mostra como o diagnóstico de gráficos podem ajudá-lo a depurar erros de processamento em aplicativos e jogos do DirectX.|