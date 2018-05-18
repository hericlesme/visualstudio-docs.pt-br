---
title: Args | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0452d590395198528788cb433f6ccf9b4a4396b7
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2018
---
# <a name="args"></a>Args
A opção **Args** de VSPerfCmd.exe especifica uma lista de argumentos passados para o aplicativo de destino do subcomando **Launch**.  
  
 **Args** pode ser usado somente quando **Launch** também for especificado na linha de comando. **Args** é opcional quando **Inicialização** for especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)