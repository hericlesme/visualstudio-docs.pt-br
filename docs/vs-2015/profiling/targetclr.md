---
title: TargetCLR | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 915ca4a859b4c80f785262f1c05698c4d34a683b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461969"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [TargetCLR](https://docs.microsoft.com/visualstudio/profiling/targetclr).  
  
A opção **TargetCLR** especifica a versão do CLR (Common Language Runtime) cujo perfil deverá ser criado quando mais de uma versão do CLR for carregada em um aplicativo.  
  
 Por padrão, as Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] têm como destino a primeira versão do CLR carregada pelo aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ClrVersion`  
 O número de versão do CLR. Use o formato de versão **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **TargetCLR** pode ser usada somente com as opções de **Inicialização** ou **Anexar**.  
  
 **Inicialize:** `AppName`  
 Inicia o aplicativo especificado e a criação de perfil.  
  
 **Anexar:** `PID`  
 Começa a criar o perfil do processo especificado.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a opção TargetCLR é usada para garantir que a versão 4.0.11003 do CLR tenha um perfil criado.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```



