---
title: Classe VsgDbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1a3810f6f0c2de6bffb2f97c2f1fc446ea3b6d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Representa uma interface para o controle programático do componente no aplicativo do diagnóstico de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Membros  
 O `VsgDbg` classe oferece suporte aos seguintes membros.  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)|Constrói uma instância do `VsgDbg` de classe e, opcionalmente, prepara o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e gravar informações de gráficos.|  
|[VsgDbg::~VsgDbg (Destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)|Destrói a uma instância do `VsgDbg` classe.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Adiciona uma mensagem personalizada para o diagnóstico de gráficos HUD (visor).|  
|[BeginCapture](begincapture.md)|Inicia um intervalo de captura terminará com `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Captura o restante do quadro atual para o arquivo de log do gráfico.|  
|[Copiar (captura programática)](copy-programmatic-capture.md)|Copia o conteúdo do arquivo de log (.vsglog) de elementos gráficos ativos em um novo arquivo.|  
|[EndCapture](endcapture.md)|Termina um intervalo de captura foi iniciado com `BeginCapture`.|  
|[Init](init.md)|Prepara o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e gravar informações de gráficos.|  
|[ToggleHUD](togglehud.md)|Alterna a sobreposição de diagnóstico HUD gráficos ativado ou desativado.|  
|[UnInit](uninit.md)|Finaliza o arquivo de log do gráfico, fecha e libera os recursos que foram usados enquanto o aplicativo foi ativamente gravando informações de gráficos.|  
  
## <a name="remarks"></a>Comentários  
 O `VsgDbg` classe representa uma interface que você pode usar para controlar os recursos de diagnóstico de gráficos programaticamente. Você pode usar alguns recursos, mesmo quando você estiver ativamente capturar e registrar informações de elementos gráficos; Isso inclui o `AddMessage` função de membro e `ToggleHUD` função de membro. As outras funções de membro ou preparar o componente no aplicativo de diagnóstico de gráficos para iniciar ou parar a captura de ativa de informações de gráficos ou devem ser chamadas enquanto o aplicativo está ativamente capturando e gravar informações de elementos gráficos em um arquivo de log do gráfico.