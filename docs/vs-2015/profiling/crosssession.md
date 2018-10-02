---
title: CrossSession | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c4306f89b41639ba70e581ed6b3b4ce70089c01
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47587883"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CrossSession](https://docs.microsoft.com/visualstudio/profiling/crosssession).  
  
A opção **CrossSession** do VSPerfCmd.exe permite que o criador de perfil colete dados de qualquer sessão de console. A opção **CrossSession** deve ser usada com a opção **Iniciar**.  
  
 Você pode usar a abreviação **CS** no lugar de **CrossSession**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="valid-options"></a>Opções válidas  
 Para habilitar a criação de perfil em outra sessão, a opção **CrossSession** deve ser especificada com a opção **Iniciar**. **CrossSession** também deve ser especificado em qualquer comando **Anexar do VSPerfCmd** e **Desanexar** subsequente.  
  
 **Iniciar:** `Method`  
 A opção **Iniciar** inicializa o criador de perfil para o método de criação de perfil especificado.  
  
 **Anexar:** _PID_[**,**_PID_]  
 Inicia a criação de perfil dos processos especificados.  
  
 **Desanexar**[**:**_PID_[,_PID_]]  
 Para a criação de perfil dos processos especificados.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a opção **CrossSession** é usada para anexar a um aplicativo que foi iniciado em outra sessão de console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)



