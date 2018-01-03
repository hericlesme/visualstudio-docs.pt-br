---
title: GC (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6a57cb824ca6c2ec4b2f52a070ae407690f83d69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
A opção **GC** habilita a coleta de dados de alocação de memória do.NET Framework e dados de tempo de vida do objeto. A opção **GC** pode ser usada somente com o método de criação de perfil de amostragem e somente com a opção **Inicializar**.  
  
 Quando você estiver usando a opção **GC**, o comando VSPerfClrEnv **/sampleon** não é obrigatório.  
  
 Se nenhum parâmetro for especificado ou se o parâmetro **Alocação** for especificado, apenas os dados de alocação de memória do .NET Framework são coletados. Se o parâmetro **Tempo de Vida** for especificado, os dados de alocação de memória do .NET Framework e de tempo de vida do objeto do .NET Framework são coletados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 **Alocação**  
 Padrão. Coleta dados de alocação de memória do .NET Framework.  
  
 **Tempo de Vida**  
 Coleta dados de alocação de memória do .NET Framework e dados de tempo de vida do objeto do .NET Framework.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **GC** pode ser usada somente com a opção **Inicializar**.  
  
 **Inicialize:** `AppName`  
 Inicia o aplicativo especificado e começa a criação de perfil com o método de amostragem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia um aplicativo e coleta dados de alocação de memória do .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)