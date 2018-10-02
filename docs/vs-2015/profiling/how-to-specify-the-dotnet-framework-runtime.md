---
title: Como especificar o tempo de execução do .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d7d9e63f5ab5581960f08d32f920b24f2f9906
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462334"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Como especificar o tempo de execução do .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar o tempo de execução do .NET Framework](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-dotnet-framework-runtime).  
  
Com o lançamento do [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], os aplicativos podem ser compostos de módulos que foram compilados usando versões diferentes do tempo de execução do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Por padrão, as Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] analisam o primeiro tempo de execução que é carregado pelo aplicativo. Você pode especificar o tempo de execução a ser analisado ao iniciar um aplicativo com o criador de perfil e ao anexar o criador de perfil a um aplicativo que já esteja em execução.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao iniciar um aplicativo com o criador de perfil  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho, clique em **Propriedades** e, em seguida, clique em **Avançado**.  
  
     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que estão instaladas no computador.  
  
2.  Execute uma das seguintes etapas:  
  
    -   Clique na versão do CLR que você deseja analisar.  
  
    -   Clique em **Automático** para analisar a primeira versão que é carregada pelo aplicativo.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao anexar o criador de perfil a um aplicativo  
  
1.  No menu Analisar, aponte para Criador de Perfil e, em seguida, clique em Anexar/Desanexar.  
  
2.  Na caixa de diálogo Anexar Criador de Perfil a Processo, clique no processo você deseja analisar.  
  
     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que estão instaladas no computador.  
  
3.  Execute uma das seguintes etapas:  
  
    -   Clique na versão do CLR que você deseja analisar.  
  
    -   Clique em **Automático** para analisar a versão que é carregada quando o criador de perfil se anexa ao aplicativo.



