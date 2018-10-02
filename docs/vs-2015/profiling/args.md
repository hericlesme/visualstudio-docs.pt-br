---
title: Args | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4092a0f75808942eabf170a10f4dcec0836ca337
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462013"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Args](https://docs.microsoft.com/visualstudio/profiling/args).  
  
A opção **Args** de VSPerfCmd.exe especifica uma lista de argumentos passados para o aplicativo de destino do subcomando **Launch**.  
  
 **Args** pode ser usado somente quando **Launch** também for especificado na linha de comando. **Args** é opcional quando **Inicialização** for especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Arguments`  
 Uma lista de argumentos para o aplicativo de destino do comando **Launch**.  
  
## <a name="required-options"></a>Opções obrigatórias  
 **Inicialize:** `AppName`  
 Inicia o aplicativo especificado e começa a criação de perfil com o método de amostragem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a opção **Args** para passar argumentos para TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)



