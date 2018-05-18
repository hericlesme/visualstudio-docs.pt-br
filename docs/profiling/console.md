---
title: Console | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7fb90261453caab8dbe54fce79605c1d891d537
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2018
---
# <a name="console"></a>Console
A opção **Console** VSPerfCmd.exe inicia o aplicativo especificado em uma nova janela de prompt de comando. O **Console** só pode ser usado com a opção **Iniciar** VSPerfCmd. Se o aplicativo não é um aplicativo de linha de comando, o **Console** não tem nenhum efeito.  
  
## <a name="syntax"></a>Sintaxe  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="required-options"></a>Opções obrigatórias  
 O **Console** só pode ser especificado em uma linha de comando que também tem a opção **Iniciar**.  
  
 **Inicialize:** `AppName`  
 Inicia o criador de perfil e o aplicativo especificado por `AppName`.  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)