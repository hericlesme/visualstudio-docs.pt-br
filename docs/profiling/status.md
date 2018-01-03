---
title: Status | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1168fb27330f49a714e64478fc7ab167569dadb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="status"></a>Status
A opção VSPerfCmd.exe **Status** exibe informações sobre o estado do criador de perfil e todos os processos que estão atualmente sendo perfilados.  
  
 A opção **Status** deve ser a única opção especificada na linha de comando. O criador de perfil deve ser inicializado com a opção VSPerfCmd.exe **Status** antes de qualquer status poder ser exibido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="remarks"></a>Comentários  
 A opção **Status** exibe as seguintes informações de estado para o criador de perfil.  
  
 **Nome do arquivo de saída**  
 O caminho e o nome do arquivo de dados atual do criador de perfil.  
  
 **Modo de coleta**  
 SAMPLE ou TRACE  
  
 **Processos Máximos**  
 O número máximo de processos que podem ser perfilados ao mesmo tempo e o número de processos ativos no momento.  
  
 **Threads Máximos**  
 O número máximo de threads que podem ser perfilados ao mesmo tempo.  
  
 **Número de Buffers**  
 O número de buffers de memória dedicada a gravação de dados de criação de perfil.  
  
 **Tamanho dos Buffers**  
 O tamanho em bytes do buffer de memória.  
  
 A opção **Status** exibe as seguintes informações de estado para cada processo que está atualmente sendo perfilado.  
  
 **Processo**  
 O nome do processo perfilado.  
  
 **ID do Processo**  
 O identificador de sistema do processo.  
  
 **Num Threads**  
 Número de threads em execução atualmente.  
  
 **Iniciar/Parar Contagem**  
 A contagem do criador de perfil principal interno para controlar a coleta de dados para esse processo. A contagem deve ser igual a um para coletar dados. Iniciar/Parar Contagem pode ser manipulada por APIs do criador de perfil e as opções de VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.  
  
 **Suspender/Retomar Contagem**  
 A contagem do criador de perfil secundário interno para controlar a coleta de dados para esse processo. A contagem deve ser menor ou igual a zero para coletar dados. A opção **Suspender/Retomar** contagem pode ser manipulada somente pela APIs do criador de perfil.  
  
 **Usuários com direitos de acesso para monitorar**  
 Lista os nomes de usuários que têm acesso para o criador de perfil. Usuários adicionais podem ser concedidos acesso por meio da opção VSPerfCmd.exe **Admin**  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)