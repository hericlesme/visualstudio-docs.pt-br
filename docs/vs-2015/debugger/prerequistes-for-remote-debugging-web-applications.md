---
title: Pré-requisitos para aplicativos Web de depuração remota | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465561"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Pré-requisitos para aplicativos Web de depuração remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [pré-requisitos para aplicativos de Web de depuração remota](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
Com o depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode depurar um aplicativo Web de maneira transparente no computador local ou em um servidor remoto. Isso significa que o depurador funciona da mesma maneira e permite que você use os mesmos recursos em qualquer computador. Para que a depuração remota funcione corretamente, no entanto, há alguns pré-requisitos.  
  
-   Os componentes da depuração remota do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devem estar instalados no servidor que você deseja depurar. Para obter mais informações, consulte [Configurando a depuração remota](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Por padrão, o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado como um processo de usuário do ASPNET. Como resultado, você deve ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado para depurá-lo. O nome do processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, consulte [como: localizar o nome do processo do ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)



