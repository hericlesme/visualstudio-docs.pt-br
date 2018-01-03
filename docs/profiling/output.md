---
title: "Saída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7452ad6aa8d7f190eebbc35d4be087c14dcd51a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="output"></a>Saída
A opção **Saída** especifica o nome do arquivo de dados de criação de perfil para a sessão de desempenho. **Saída** deve ser usado com a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `FileName`  
 O nome do arquivo de dados. Caminhos completos e parciais são aceitos. Se um caminho não for especificado, o arquivo será criado no diretório atual.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Saída** deve ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 Especifica o nome do arquivo de saída.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o arquivo de dados de criação de perfil é criado no diretório atual.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)